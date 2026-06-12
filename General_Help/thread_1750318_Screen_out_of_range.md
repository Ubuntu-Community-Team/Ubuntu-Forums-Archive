---
title: "Screen out of range"
date: 2011-05-05
forum: General Help
---

### Post by Zurfy on 2011-05-05
My screen is always telling me "signal out of range. 75.0 KHz / 60 Hz when I have my graphic card driver installed.

I have tried many ways to solve that problem and I have been tried many things that I read in many tutorials...
I don't know how to solve that and I've been trying new things for nearly 2 weeks.
I have tried the same thimgs in ubuntu 10.10, 9.10 and 9.04 but with no results.

Can you try to help me please?
By the way, I have ATI graphic card.

I have ubuntu 11 now.

---

### Post by DanneStrat on 2011-05-05
> **Zurfy said:**
> My screen is always telling me "signal out of range. 75.0 KHz / 60 Hz when I have my graphic card driver installed.

I have tried many ways to solve that problem and I have been tried many things that I read in many tutorials...
I don't know how to solve that and I've been trying new things for nearly 2 weeks.
I have tried the same thimgs in ubuntu 10.10, 9.10 and 9.04 but with no results.

Can you try to help me please?
By the way, I have ATI graphic card.

I have ubuntu 11 now.

Have you tried changing refresh rate for your

monitor? Some common values are 60, 70, and 75 Hz.

Can you also give the output of:

```
lspci | grep VGA
```

and

```
lsmod
```

---

### Post by Zurfy on 2011-05-05
I don't know how to do that of the refresh screens.

Also I have written your code in the terminal alt+f2 and it says "command not found"

What am I doing wrong?

btw, thanks for your reply before

---

### Post by DanneStrat on 2011-05-05
> **Zurfy said:**
> I don't know how to do that of the refresh screens.

Also I have written your code in the terminal alt+f2 and it says "command not found"

What am I doing wrong?

btw, thanks for your reply before

Press alt+f2 again and type:

```
gnome-terminal
```

This will open up terminal and

then post the output from the commands

I mentioned above.

---

### Post by Zurfy on 2011-05-06
> **DanneStrat said:**
> Have you tried changing refresh rate for your

monitor? Some common values are 60, 70, and 75 Hz.

Can you also give the output of:

```
lspci | grep VGA
```and

```
lsmod
```

- 02:00.0 VGA compatible controller: ATI Technologies Inc RV730 PRO [Radeon HD 4650]

and the other one:
<<it was hard to read all the text so I did a screenshot>>
[IMG]http://img836.imageshack.us/img836/4692/screenshotgpz.png[/IMG]
I was in the secure mode by that time

Also, when I was entering to the graphics mode in the secure mode Ubuntu told me:
"The monitor, the graphic card or the input device couldn't be detected correctly." -> I don't know whether this can help you.

---

### Post by Zurfy on 2011-05-06
How can I solve the problem, please?

---

