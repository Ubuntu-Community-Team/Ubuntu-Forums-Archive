---
title: "Help please,what is this?"
date: 2010-01-22
forum: General Help
---

### Post by darko.baruh on 2010-01-22
After installing add-on status address bar 1.7 ( it's experimental ) I started to get error message (screen shot below) after every other add-on install even after starting firefox, I uninstalled that add-on but I still got the message.Please help.

---

### Post by Saiko Berry on 2010-01-22
"it's experimental"

gg.

What is terminal saying. Check syslog.
gnome-system-log > syslog

---

### Post by zine92 on 2010-01-22
Try removing the firefox in ubuntu software centre and reinstall.

---

### Post by darko.baruh on 2010-01-22
I reinstalled firefox and still have the problem.But I dont know did I uninstalled correctly becouse after installation I had the same settings and add-ons from previous installation. I run the sys log comannd in the terminall and stoped there.I dont now what and where to click or look.Sorry totally noob.

---

### Post by darko.baruh on 2010-01-22
Anyone?

---

### Post by pastalavista on 2010-01-22
to completely reinstall firefox use this in terminal ```
sudo apt-get purge firefox 

sudo apt-get install firefox
```

or use Synaptic Package Manager, find firefox and select "Remove Completely" (that's what the purge command does)

---

### Post by 3rdalbum on 2010-01-22
> **darko.baruh said:**
> I reinstalled firefox and still have the problem.But I dont know did I uninstalled correctly becouse after installation I had the same settings and add-ons from previous installation.

Yes, you did. Reinstalling software **just replaces the program on disk** with a fresh copy from the repositories. It doesn't touch your preferences files, which are stored in your home directory under the .mozilla folder. (it's hidden - press Control-H in your home directory to show hidden files and folders).

Rename the .mozilla folder to something else like .mozilla-old and a fresh profile will be created for you when you next start Firefox. This should fix your problem.

Reinstalling a program only helps if the program binary itself gets corrupted, which almost never happens on Linux.

---

### Post by darko.baruh on 2010-01-22
[3rdalbum]("http://ubuntuforums.org/member.php?u=61044"): Thanks it's ok now after using your method with renaming the mozzila folder.

---

