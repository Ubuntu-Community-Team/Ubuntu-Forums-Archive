---
title: "Goal Seek in Open Office Calc Not Working"
date: 2009-10-26
forum: General Help
---

### Post by linux4life88 on 2009-10-26
I tried to use goal seek feature in Open Office Calc and I got the following message:

Goal Seek not successful.
No exact value found.
Insert closest value (0.000)?

I'm not sure why I got this message. I got curios and saved the document as a .xls and opened it up on a friends laptop to try the goal seek feature in Excel. Low and behold it worked in Excel and I got the answers I was looking for 0.099 and 0.193. I was wondering why it does not work in Open Office Calc?

---

### Post by linux4life88 on 2009-10-27
I thought the numbers might help. These numbers are derived from formulas. These are just the ones that I'm having trouble with.

Formula Cell = $L$21 (value is 358111)
Target Value = 375000
Variable Cell = $L$23 (value is 0.115)
For this one I should get an answer of 0.099 (rounded)

Formula Cell = $L$36 (value is 237672
Target Value = 190000
Variable Cell = $L$38 (value is 0.115)
For this one I should get an answer of 0.193 (rounded)

I would not only like to figure out why Open Office Calc is not able to do this calculation. But more importantly I don't want to have to admit that a Microsoft Excel (a non open source program) works better. Any help would be much appreciated.

---

### Post by linux4life88 on 2009-10-28
I tried these calculations in Gnumeric and the goal seek function worked. But it gave me different answers:

.110 (rounded) compared to .099 (rounded)
.147 (rounded) compared to .193 (rounded)

I'm now curios why Open Office Calc didn't work and Gnumeric did. But also why the goal seek function in Gnumeric got a different answer than Excel. I'm really starting to get confused.

---

### Post by linux4life88 on 2009-10-29
bump

---

### Post by jongkind on 2009-10-29
It would help if you post the formula.

---

### Post by linux4life88 on 2009-11-02
There is nothing wrong with the formulas. It is simply that Open Office Calc and Gnumeric goal seek feature does not work. I will just have to get a copy of Excel because its goal seek feature does work. I hope that this bug in both programs will be fixed soon.

---

### Post by jongkind on 2009-11-02
> **linux4life88 said:**
> There is nothing wrong with the formulas. It is simply that Open Office Calc and Gnumeric goal seek feature does not work. I will just have to get a copy of Excel because its goal seek feature does work. I hope that this bug in both programs will be fixed soon.

I just want to reproduce it on my machine....

---

### Post by linux4life88 on 2009-11-02
> **jongkind said:**
> I just want to reproduce it on my machine....

1st One:

=L17+L19 (350305+7806)
=B19 (375000)
=B7 (0.115)

2nd one is very similar:

=L32+L34 (216855+20817)
=B34 (190000)
=B7 (0.115)

Thank you for the help, I really do appreciate it.

---

### Post by jongkind on 2009-11-03
I'm afraid that I don't understand what you want to achieve. The input for goal seek requires: 

[LIST=1]
[*]a formula cell
[*]a target value
[*]a variable cell
[/LIST]

I do not understand how this relates to your formulas. Can you help me with this?

---

