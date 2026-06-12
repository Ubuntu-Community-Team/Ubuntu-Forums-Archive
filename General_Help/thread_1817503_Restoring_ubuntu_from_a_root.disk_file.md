---
title: "Restoring ubuntu from a root.disk file"
date: 2011-08-03
forum: General Help
---

### Post by anuj27 on 2011-08-03
I was using Ubuntu, installed over Wubi in WindowsXP. Due to some hard disk issues, I was having some problems booting into Windows. But Ubuntu was working fine. So i backed up all my data from Ubuntu and somehow managed to back up the 'root.disk' from Windows.
That hard disk turned out to have some bad sectors. Now I am over a new hard disk with all my data and WindowsXP freshly installed. I want to have my old copy of Ubuntu back as I have the 'root.disk' file with me. How shall I proceed?

I tried installing a fresh copy of Ubuntu using Wubi and then replace the 'root.disk' file. But it showed some Grub error. So I don't know whether I was going in a right direction and I preferred taking some suggestions.
Please help...

---

### Post by bcbc on 2011-08-03
Check this out: [http://askubuntu.com/questions/54981/how-can-re-use-ubuntu-which-was-installed-via-wubi-on-windows-7/55029#55029](http://askubuntu.com/questions/54981/how-can-re-use-ubuntu-which-was-installed-via-wubi-on-windows-7/55029#55029) (look at the bottom: a bit more info to explain how a wubi install boots)
It should contain enough info for you to get the old root.disk booted. If not, just ask.

Also make sure you installed the same release of Wubi as the wubildr's aren't compatible between releases.

---

