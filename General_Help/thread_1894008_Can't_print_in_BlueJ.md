---
title: "Can't print in BlueJ"
date: 2011-12-11
forum: General Help
---

### Post by joshswain123 on 2011-12-11
I'm currently running Lubuntu 11.10, and using the BlueJ Java IDE for the computer science class I'm taking. But for some reason, it won't print anything. I go to print, and it says 'printing', and then 'cancelled.'

---

### Post by MG&amp;TL on 2011-12-11
a) Can you print anything (i.e. from Abiword)

b) If BlueJ isn't working for you, use a different IDE.

---

### Post by joshswain123 on 2011-12-11
I can print everything else, just not BlueJ. And I'm not sure if I would be allowed to use a different IDE, because it's for a class.

---

### Post by joshswain123 on 2011-12-11
I found this:

> (Linux) Printing and Page setup don't work

There is a Java bug which prevents printing in some circumstances (please note the bug has been fixed in recent JDKs).

A suggested workaround is to change the orientation for every printer to something other than "automatic rotation" (using your system's printer configuration utility).

I tried the workaround, but it still didn't help.

---

### Post by MG&amp;TL on 2011-12-11
Hackish workaround:

Paste code into gedit (syntax highlighting!), print from there.

If you don't have gedit:

```
sudo apt-get install gedit
```

Not being allowed to use a different IDE is like not being allowed to have a different car. I don't agree with that, but it's your course. :D

---

### Post by Damascushead on 2012-02-08
Dont' know if your problem has been solved or not, but try updating to the lates version of blueJ. I have had some glitches as well, but updating (or reinstalling which doesn't take long) fixed both glitches in both situations.

---

