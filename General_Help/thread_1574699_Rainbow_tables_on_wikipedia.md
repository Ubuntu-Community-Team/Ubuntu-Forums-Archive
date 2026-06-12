---
title: "Rainbow tables on wikipedia?"
date: 2010-09-14
forum: General Help
---

### Post by J V on 2010-09-14
On wikipedia it is stated that:

"this use of multiple reduction functions approximately doubles the speed of lookups."

Why?

By my math, having generate multiple chains until the correct chain position is found takes much much longer than simply using a single reduction function and continuing until a match is found.

Or am I perhaps mistaken and does wikipedia mean by "Lookups" the total time to break an entire hash? (I understand it means the time to search through an entire chain)

A simple chain for example:

```
password1 > 5567 > password2 > 6678 > password 4 > 4882 > password3 > 6778 > password 5 > 4881
```
Assuming the "Average" position in the chain (The middle value is the average lookup time for both rainbow and normal tables though rainbow tables get anything towards the end faster and towards the beginning slower), we take a hash 4882 and run it through...

The original table runs it through 4 calculations and finds the end of the chain, then looks it up for another 5 calculations... 9 calculations

The rainbow table runs it through R-1, 2 calculations, R-2, 4 calculations, and R-3, 6 calculations to find the end of the chain, then another 5 calculations to get the plaintext: 17 calculations...

Last time I checked 17 calculations took longer than 9, so why are rainbow lookups faster?

---

