---
title: "64-bits system using only 5,6GB RAM of installed 16GB"
date: 2011-11-17
forum: General Help
---

### Post by petri on 2011-11-17
Uppgraded hardware to i5 and 16GB RAM from E8400 and 8GB. The previous setup worked but this new one doesn't go over 5,6GB and starts behaving sluggish as it did before when RAM was full. Swap is empty.

---

### Post by TBABill on 2011-11-17
Are you sure it's a memory problem instead of a maxed CPU on one of the applications you are using? Causing that machine to creep to a halt with so little of its memory in use suggests something is bogging it down severely. You can use the command 'top' without quotes in a terminal to see if your % CPU indication skyrockets when it happens. You can just open a terminal, type in top and let it run in the background till you see the problem coming on. Then just identify which process is causing it and kill that process. It won't solve the problem, but it'll let you know where to start looking for an answer.

---

### Post by petri on 2011-11-17
Ok, thanks seems like you are right.

---

