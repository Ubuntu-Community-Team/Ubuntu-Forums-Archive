---
title: "Firefox 3.6"
date: 2010-01-22
forum: General Help
---

### Post by rene197705 on 2010-01-22
I googled for "firefox 3.6 karmic", followed the howto's to install the ppa, etc, etc.

But no ff3.6 for me;

Building dependency tree       
Reading state information... Done
firefox-3.6 is already the newest version.
The following packages were automatically installed and are no longer required:
  libqca2 libakonadiprivate1 libindicate-qt0 kdepimlibs5 kdepimlibs-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
rene@ekster:/media/500gb/data2/www/htdocs/htmlMicroscope-1.2.1$ firefox-3.6
firefox-3.6: command not found

namoroka wasn't found in Applications | Internet either.

So where do i find it?!?!

---

### Post by sgosnell on 2010-01-22
Apt-get says 3.6 is installed.  Firefox-3.6 is not the command to run it, though.  It's most likely just 'firefox'.  Try that, and then check Help/About for the version it runs.

---

### Post by lovinglinux on 2010-01-22
Try firefox-3.**5** or simply firefox.

What happens is that when you install the upgrades from the ppa, it upgrades firefox-3.**5** package, so you should use that as command. Unless you remove firefox-3.**5** and install firefox-3.**6** directly, then you need to use the regular command.

---

### Post by zine92 on 2010-01-22
I don't get what you need, but if you are looking for an alternatives to the default firefox. Navigate to firefox website and download the newest version, extract in /opt and remove the default firefox. Hope it helps.

---

### Post by lovinglinux on 2010-01-22
> **zine92 said:**
> I don't get what you need, but if you are looking for an alternatives to the default firefox. Navigate to firefox website and download the newest version, extract in /opt and remove the default firefox. Hope it helps.

The OP doesn't need that, since Firefox 3.6 is already installed. The problem is with the command to launch it. My previous post explains why and provides the solution.

---

### Post by rene197705 on 2010-01-23
uninstalling all firefox with

sudo apt-get remove firefox

then re-installing 3.6

sudo apt-get install firefox-3.6

did the trick..



thanks ppl.

---

