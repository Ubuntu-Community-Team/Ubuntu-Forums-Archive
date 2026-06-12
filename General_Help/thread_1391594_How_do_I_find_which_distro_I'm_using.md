---
title: "How do I find which distro I'm using?"
date: 2010-01-27
forum: General Help
---

### Post by random_excess23 on 2010-01-27
Hello

   May sound like a bit of a silly question but I'm not sure which distro I'm using. The computer came to me with Linux preinstalled by a friend. Under system monitor it says Ubuntu release 8.04 (hardy) but several things are different from the hardy live CD I use on my laptop. Many of the programs from the live CD are not installed on my system, the layout is slightly different  and I have the xubuntu logo at start up and on the top panel next to the applications menu. So how do I find out definately what version I'm running.

   I'm about to do a fresh install and don't want any incompatibility issues. To hand I have CDs of hardy and jaunty so would prefer to use one of those but not sure if my system is too puny to handle them well. I'm using a 1.8GHz Pentium 4 with 1GB of ram and wondering if I'm using xubuntu or some kind of custom install for slighty older computers.

---

### Post by raktarok on 2010-01-27
Since you are in a ubuntu installation, you can check the file /etc/lsb-release to see which version you are running. 

```
cat /etc/lsb-release
```

You can also check the **about ubuntu** entry - it should be somewhere in the menu.

But if the system monitor says its hardy,thats probably true. It looks different than the hardy live cd maybe because its some distro based on hardy (there are quite a few of them, I think) Or maybe your friend customized the default hardy installation...

---

### Post by zaphod777 on 2010-01-27
system -> about ubuntu

Live CD sometimes has different apps on it than the base install.

---

### Post by random_excess23 on 2010-01-27
Thanks for the advice

   Under release in terminal, I'm getting Ubuntu 8.04.1 hardy as in system monitor. There is no About Ubuntu anywhere in my menu system but there is About Xfce and when I click on the help icon it opens the Xubuntu documentation page. So I'm guessing it must be hardy with the Xfce desktop environment instead of gnome and maybe a few other tweaks.

   I'm going to go ahead with a fresh install of hardy or jaunty and see if there's any performance loss, it'll be on a new hard drive so I've nothing to lose.

---

### Post by kdaemon on 2010-01-27
open a terminal and type "uname -a"

---

### Post by random_excess23 on 2010-01-27
Hmm...

Now that's just got me a bit confused, tried "uname -a" and the output produced was:

Linux [my computers name] 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux

To be perfectly frank this means very little to me.

---

### Post by NFblaze on 2010-01-27
Type *env* into the terminal.

It will list the GDM your using. GNOME, KDE, XFCE, LXDE etc...

everything else should be solved with raktarok's command.

---

