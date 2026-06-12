---
title: "password error after update to 11.04 ?"
date: 2011-08-01
forum: General Help
---

### Post by dinofelis on 2011-08-01
Hello,

I have a strange error on my system.  I upgraded from 10.10 to 11.04 (64 amd), and had some serious problems due to apparently some corrupted package in the downloaded update.  I got around it by cleaning and re-installing ubuntu-desktop (in shell mode).  So now everything seems to be running fine, except for one annoying thing:
whenever I start something that needs root access through the desktop environment (graphical user interface), a dialog window pops up asking for my password, and when I type it, it returns telling me that my password is not valid.
However, if I use a terminal, and I sudo the same command, the shell asks me for my password, and accepts it without any problem.

For instance, if I launch synaptic from the Control Center, it doesn't accept my password.  If type in a terminal:
> sudo synaptic
<my password>
then everything works.  Not only for synaptic, but for anything I tried.

Pretty annoying.  How should I get rid of this ?

---

### Post by dinofelis on 2011-08-02
Ok I found the solution here:

[http://ubuntuforums.org/showpost.php?p=10854658&postcount=9](http://ubuntuforums.org/showpost.php?p=10854658&postcount=9)

---

### Post by FleshGordon on 2011-08-02
> **dinofelis said:**
> Ok I found the solution here:

[http://ubuntuforums.org/showpost.php?p=10854658&postcount=9](http://ubuntuforums.org/showpost.php?p=10854658&postcount=9)
I followed the advice and it didn't solve the problem. still no root password accepted via a GUI root password request :-(
Any further ideas available?

---

