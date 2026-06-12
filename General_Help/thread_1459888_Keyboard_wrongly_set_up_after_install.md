---
title: "Keyboard wrongly set up after install"
date: 2010-04-22
forum: General Help
---

### Post by defenestratos on 2010-04-22
Hello,
I have a problem with my new Ben Q Joybook Lite U102.
The keyboard has been wrongly detected. It is strange because as far as I can tell it works in the log in window and then is wrong in the session. 
The fn button does nothing and the letters where you can toggle numbers with the fn button are automatically numbers.
How can I identify my type of keyboard and tell Linux to use it?
THanks

---

### Post by dcstar on 2010-04-22
> **defenestratos said:**
> Hello,
I have a problem with my new Ben Q Joybook Lite U102.
The keyboard has been wrongly detected. It is strange because as far as I can tell it works in the log in window and then is wrong in the session. 
The fn button does nothing and the letters where you can toggle numbers with the fn button are automatically numbers.
How can I identify my type of keyboard and tell Linux to use it?
THanks

System-Preferences-Keyboard-Layouts-Model

---

### Post by defenestratos on 2010-04-22
> System-Preferences-Keyboard-Layouts-Model
That would be great if I knew which keyboard I was using.Unfortunately no matter which keyboard I select from the list, whether from my manufacturer (Benq) or from generic it is the same problem.
Windows thinks it is a standard 101 / 102 key keyboard.
It works in Linux too but only in the login screen.

---

### Post by klemes on 2010-04-22
There is a console script used to choose keyboard type,layout screen fonts and number of tty's.You invoke it simply by typing in a terminal:

```
sudo dpkg-reconfigure console-setup
```

This will reconfigure everything keyboard related in your system.
In keyboard type if you do not find your manufacturer choose PC(101).

---

