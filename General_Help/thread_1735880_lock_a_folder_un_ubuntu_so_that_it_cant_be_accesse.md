---
title: "lock a folder un ubuntu so that it cant be accessed in windows"
date: 2011-04-21
forum: General Help
---

### Post by ayet on 2011-04-21
is there a way? i need to secure a folder without any programs installed in windows

---

### Post by Timmer1240 on 2011-04-21
windows cannot see the linux partition anyhow

---

### Post by ayet on 2011-04-21
what my current setup is i have windows xp in drive c and ubuntu in drive d, i want to be able save files in drive c that cant be accessed when iam in windows.

---

### Post by Mark Phelps on 2011-04-22
> **ayet said:**
> what my current setup is i have windows xp in drive c and ubuntu in drive d, i want to be able save files in drive c that cant be accessed when iam in windows.

Generally your "C" drive in Windows is your OS drive -- so preventing you from accessing file in "C" while in Windows makes no sense at all.

If what you mean was the "D" drive, Wubi installs Ubuntu into a single large file INSIDE your NTFS partition.  Windows is not able to understand the contents of that file.  So, if you save stuff while in Ubuntu (as long as you save it in your Linux filesystem), someone logged into Windows is not going to be able to examine it.

However, since your "D" drive is shared with Windows, if you save files while in Ubuntu OUTSIDE the Linux filesystem, then Windows users WILL be able to examine that file.

---

### Post by Rubi1200 on 2011-04-22
If someone had access to your Windows install, they could theoretically read and copy the contents of the root.disk using  [ext2read]("http://ext2read.blogspot.com/")

They would not, however, have direct access to the contents, if that is what you are concerned about.

---

### Post by doas777 on 2011-04-22
as the others have mentioned, there are some questionable installation choices in your configuration, but either way, the best bet is encryption. 
look at Truecrypt 
[http://www.truecrypt.org/](http://www.truecrypt.org/)

---

