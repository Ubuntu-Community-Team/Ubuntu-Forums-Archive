---
title: "Sudden problem updating"
date: 2010-11-05
forum: General Help
---

### Post by Jlb181 on 2010-11-05
Can anyone tell me what this means?

installArchives() failed: Preconfiguring packages ...

Preconfiguring packages ...

dpkg: parse error, in file '/var/lib/dpkg/status' near line 11756 package 'vinagre':

 `Depends' field, reference to `libgconf2-4': version contains ` '



I get it while trying to update my computer.

I'm using 10.10.

Thanks!
Jeff

---

### Post by plucky on 2010-11-05
> Can anyone tell me what this means?


It means the in the file var/lib/dpkg/status near line 11756 it has found a rogue character that it doesn't understand.

You can either edit the file using ```
sudo cp var/lib/dpkg/status var/lib/dpkg/status.backup
gksudo gedit var/lib/dpkg/status
``` and goto line 11756 and remove the offending character from `libgconf2-4':.

Or try this first

Open a terminal and ```
sudo mv var/lib/dpkg/status var/lib/dpkg/status.backup
sudo cp var/lib/dpkg/status-old var/lib/dpkg/status
```

The first command makes a backup copy of the original file and the second command copies the status-old file and makes it the current file.

Then run ```
sudo apt-get update
sudo apt-get upgrade
``` and see if that fixes the problem.

Good luck

---

### Post by Jlb181 on 2010-11-06
Plucky,

Thank you for your help!  Worked great!

Jeff

---

