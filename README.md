# greedy-algorithms-python
# Greedy Algorithms: Assign Cookies Problem 🍪

This repository contains a clean, optimized Jupyter Notebook implementation solving the **Assign Cookies** problem using a **Greedy Algorithm approach**. 

## 🌍 Real-World Impact
Greedy algorithms are crucial foundational patterns used across standard software engineering systems. They make locally optimal choices at each step with the goal of finding a globally optimal solution. 
Real-world engineering applications include:
* **Resource Allocation:** Maximizing tasks processed given bounded server CPU/Memory limits.
* **Network Routing:** OSPF (Open Shortest Path First) protocols calculating minimal-cost network hops.
* **Logistics & Scheduling:** Bandwidth throttling and delivery window optimizations.

---

## 🚀 Problem Statement
A festival organizer must distribute cookies to children. Each child has a specific **happiness/greed requirement**, and each cookie has a **size**. The objective is to maximize the total number of content children using the available resources.

* **Children (g):** Array where \(g[i]\) is the minimum cookie size child i will accept.
* **Cookies (s):** Array where \(s[j]\) is the size of cookie j.
* **Constraint:** A child is satisfied if \(s[j] \ge g[i]\). Each child can receive at most one cookie.

---

## 💡 Greedy Strategy Explanation
To maximize the satisfied children, we employ the **Greedy Choice Property**:
1. **Sort both inputs:** Arrange the children's requirements (`g`) and cookie sizes (`s`) in ascending order.
2. **Optimal Matching:** Iterate using a two-pointer technique. For each child, we look for the *smallest available cookie* that meets or exceeds their target constraint.
3. **Why this works:** Wasting a massive cookie on a child with a low greed factor limits our capability to satisfy a highly demanding child later. Matching the smallest viable resource preserves valuable, larger cookies for harder-to-satisfy requirements.

---

## 🛠️ Code Implementation

```python
def findContentChildren(g: list[int], s: list[int]) -> int:
    # Sort both arrays to evaluate choices greedily
    g.sort()
    s.sort()
    
    child_ptr = 0
    cookie_ptr = 0
    
    # Two-pointer traversal
    while child_ptr < len(g) and cookie_ptr < len(s):
        # If the cookie satisfies the child's minimum requirement
        if s[cookie_ptr] >= g[child_ptr]:
            child_ptr += 1  # Move to next child (satisfied)
        
        cookie_ptr += 1     # Always consume/skip to next cookie
        
    return child_ptr
```

---

## 📊 Complexity Analysis

* **Time Complexity:** \(\mathcal{O}(N \log N + M \log M)\), where N is the number of children and M is the number of cookies. This is driven by the sorting step (Timsort). The subsequent two-pointer traversal takes linear time \(\mathcal{O}(N + M)\).
* **Space Complexity:** \(\mathcal{O}(1)\) auxiliary space if sorted in place, or up to \(\mathcal{O}(N + M)\) depending on the language's sorting internal memory structures.

---

## 📂 Project Structure
```text
├── assign_cookies_greedy.ipynb   # Step-by-step Jupyter Notebook walkthrough
└── README.md                     # Documentation and algorithm analysis
```

## ⚙️ Setup and Running Instructions
1. Clone this repository:
   ```bash
   git clone https://github.com<your-username>/<your-repo-name>.git
   ```
2. Navigate to the directory and launch Jupyter:
   ```bash
   jupyter notebook
   ```
3. Open `assign_cookies_greedy.ipynb` and execute the cells sequentially.
