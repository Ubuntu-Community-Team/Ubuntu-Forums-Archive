---
title: "Brasero nonsense"
date: 2010-06-03
forum: General Help
---

### Post by Nonno Bassotto on 2010-06-03
I upgraded yesterday from 9.10 to 10.04. Now Brasero refuses to burn DVDs (i do not have CDs to try) at all.

Whenever I try to burn one, the first message I get is "Ejecting disk" and indeed the disk is ejected. Then Brasero complains about not finding a disk, and offers to save the error on a log file. BUT, it doesn't, so I cannot even look at the log file to find out what's happening.

:confused:

---

### Post by bodhi.zazen on 2010-06-03
Not a fix, but I have had not the best experience with Brasero either.

Personally I use K3b, it is a KDE app, but runs on Gnome and I find it to be more reliable.

If you want a lighter weight app (with less features) try xfburn.

---

### Post by Nonno Bassotto on 2010-06-04
Uhm... not really sure I want to install all of KDE base just to burn some DVDs. I may have a look at xfburn, but I guess the problem is the same with XFCE libraries. I'd rather find out what's going wrong.

---

### Post by Rodney9 on 2010-06-04
I use Xubuntu 10.4 and found Brasero and Xfburn both hopeless, so I installed K3b and now I can burn cd or dvd perfectly.

Installing K3b doesn't install all of KDE just a few small extra files.

---

### Post by wilee-nilee on 2010-06-04
> **Nonno Bassotto said:**
> Uhm... not really sure I want to install all of KDE base just to burn some DVDs. I may have a look at xfburn, but I guess the problem is the same with XFCE libraries. I'd rather find out what's going wrong.

You don't have to install the whole kde package set, just a couple like 3 I think.

---

### Post by pannerrammer on 2010-06-04
Brasero is hopeless, has been for several years! It should be dropped until it works. 

Have tried most alternatives (including Nero) and agree with the poster who recommends k3b. It is by far the best choice.

---

### Post by Linuxforall on 2010-06-04
Brasero works fine here but try Gnome CD baker which is a gnome based program that works well.

---

### Post by StuartN on 2010-06-04
Agreed, Brasero is lame and buggy (I hate the false "Disk burned, with errors" message).

I used Gnomebaker as a simple standalone replacement, but K3b is definitely a solid and featureful application.

---

### Post by Nonno Bassotto on 2010-06-04
> **wilee-nilee said:**
> You don't have to install the whole kde package set, just a couple like 3 I think.

It actually brings 69 packages of dependencies for a total of 244MB, ranging from Plasma to Soprano to Akonadi. I'm trying Gnomebaker now.

---

### Post by Nonno Bassotto on 2010-06-04
GnomeBaker is working fine. I still wonder what happened with Brasero... :confused:

---

### Post by philinux on 2010-06-04
> **Nonno Bassotto said:**
> GnomeBaker is working fine. I still wonder what happened with Brasero... :confused:

Well try the usual if you feel the need.

```
sudo apt-get purge brasero brasero-common
```

Delete the ~/.config/brasero folder and

~/.gconf/apps/brasero

Then reinstall.

---

### Post by Nonno Bassotto on 2010-06-04
Thank you, it worked! :-D

---

### Post by wilee-nilee on 2010-06-04
> **Nonno Bassotto said:**
> It actually brings 69 packages of dependencies for a total of 244MB, ranging from Plasma to Soprano to Akonadi. I'm trying Gnomebaker now.

Hmm I my computer none of that was added, but I also have the lxde desktop installed as well, and a fresh install of Lucid so Akonadi was already installed although I don't use it or know why, I use gnombaker mostly myself. Glad you found a working program.

---

