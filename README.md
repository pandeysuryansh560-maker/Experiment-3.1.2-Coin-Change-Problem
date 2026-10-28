# Experiment 3.1.2: Coin Change Problem

## 1. Aim
To find the minimum number of coins required to make a given amount using Dynamic Programming. Each coin can be used unlimited times. If the amount cannot be formed, return -1.

## 2. Software Required
- OS: Windows 10/11 or Linux
- Language: C++
- IDE: VS Code / CodeBlocks / Online Compiler

## 3. Test Cases

**Test Case 1**

Input: `coins = [1,2,5], amount = 11`

Output: `3`

Explanation: 11 = 5 + 5 + 1.

**Test Case 2**

Input: `coins = [2], amount = 3`

Output: `-1`

Explanation: Amount 3 cannot be formed using coins of denomination 2.

## 4. Pseudocode

```text
START
INPUT coins, amount
CREATE dp[amount + 1], initialized to amount + 1
SET dp[0] = 0

FOR i = 1 TO amount
    FOR each coin IN coins
        IF i >= coin
            dp[i] = MIN(dp[i], dp[i - coin] + 1)
RETURN -1 IF dp[amount] > amount
OTHERWISE RETURN dp[amount]
END
```

## 5. C++ Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int coinChange(vector<int>& coins, int amount) {
    vector<int> dp(amount + 1, amount + 1);
    dp[0] = 0;

    for (int i = 1; i <= amount; i++) {
        for (int coin : coins) {
            if (i >= coin)
                dp[i] = min(dp[i], dp[i - coin] + 1);
        }
    }

    return dp[amount] > amount ? -1 : dp[amount];
}

int main() {
    vector<int> coins = {1, 2, 5};
    int amount = 11;

    cout << coinChange(coins, amount) << endl;
    return 0;
}
```

## 6. Output

```text
3
```

## 7. Complexity
- Time: O(amount × n), where n is the number of coin denominations.
- Space: O(amount).

## 8. Learning Outcomes
1. Understood Dynamic Programming.
2. Learned to use a DP array.
3. Learned to find the minimum number of coins.
4. Improved problem-solving skills.

## 9. References
1. Data Structures and Algorithms Made Easy — Narasimha Karumanchi
2. Data Structures Using C++ — D. S. Malik

## 10. Conclusion
The Coin Change problem was solved using Dynamic Programming to find the minimum number of coins required for a given amount.


# Experiment 3.2: Longest Common Subsequence
**Subject:** CC-II (24CSP-339)

## 1. Aim
To find the length of the longest common subsequence of two strings using Dynamic Programming. A subsequence preserves character order but does not need to be continuous.

## 2. Software Required
- OS: Windows 10/11 or Linux
- Language: C++
- IDE: VS Code / CodeBlocks / Online Compiler

## 3. Test Cases

**Test Case 1**

Input: `text1 = "abcde", text2 = "ace"`

Output: `3`

Explanation: The longest common subsequence is `"ace"`.

**Test Case 2**

Input: `text1 = "abc", text2 = "def"`

Output: `0`

Explanation: The strings have no common characters.

## 4. Pseudocode

```text
START
INPUT text1, text2
CREATE dp[m+1][n+1] initialized to 0

FOR i = 1 TO m
    FOR j = 1 TO n
        IF text1[i-1] == text2[j-1]
            dp[i][j] = dp[i-1][j-1] + 1
        ELSE
            dp[i][j] = MAX(dp[i-1][j], dp[i][j-1])

RETURN dp[m][n]
END
```

## 5. C++ Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int longestCommonSubsequence(string text1, string text2) {
    int m = text1.size(), n = text2.size();
    vector<vector<int>> dp(m + 1, vector<int>(n + 1, 0));

    for (int i = 1; i <= m; i++) {
        for (int j = 1; j <= n; j++) {
            if (text1[i - 1] == text2[j - 1])
                dp[i][j] = dp[i - 1][j - 1] + 1;
            else
                dp[i][j] = max(dp[i - 1][j],
                               dp[i][j - 1]);
        }
    }

    return dp[m][n];
}

int main() {
    cout << longestCommonSubsequence("abcde", "ace")
         << endl;
    return 0;
}
```

## 6. Output

```text
3
```

## 7. Complexity Analysis
- **Time Complexity:** O(m × n)
- **Space Complexity:** O(m × n)

## 8. Learning Outcomes
1. Understood two-dimensional Dynamic Programming.
2. Learned to find the longest common subsequence.
3. Understood DP tables and recurrence relations.
4. Improved string-processing and problem-solving skills.

## 9. References
1. Data Structures and Algorithms Made Easy — Narasimha Karumanchi
2. Data Structures Using C++ — D. S. Malik
3. The C++ Programming Language — Bjarne Stroustrup

## 10. Conclusion
The Longest Common Subsequence problem was solved using Dynamic Programming to find the length of the longest subsequence common to both strings.
