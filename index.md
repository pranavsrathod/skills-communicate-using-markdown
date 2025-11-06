# As if I have not tried this before :)

![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)

```python
from collections import Counter

class Solution:
    def findXSum(self, nums: List[int], k: int, x: int) -> List[int]:
        n = len(nums)
        ans = []
        
        for i in range(n - k + 1):
            sub = nums[i:i + k]
            freq = Counter(sub)
            
            # Sort by (frequency desc, value desc)
            sorted_items = sorted(freq.items(), key=lambda p: (p[1], p[0]), reverse=True)
            
            # Keep only top x frequent numbers
            top_x = {num for num, _ in sorted_items[:x]}
            
            # Sum elements from subarray that belong to top_x
            total = sum(num for num in sub if num in top_x)
            ans.append(total)
        
        return ans
```
