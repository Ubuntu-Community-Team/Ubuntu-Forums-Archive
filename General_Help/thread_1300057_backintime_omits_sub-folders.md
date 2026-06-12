---
title: "backintime omits sub-folders??"
date: 2009-10-24
forum: General Help
---

### Post by celem on 2009-10-24
I have been using the backintime backup software (version 0.9.26) on my Ubuntu 9.04 system. It seemed great and provided a nice GUI solution to directly using Rsync. However, I have detected a problem that I cannot seem to solve. Backintime is omitting the contents of subdirectories. For example the directory "/home/ecomer/finance" contains about 25 normal files (not hidden), yet my backups of "/home/ecomer" contain the "/home/ecomer/finance" folder but it is empty. This is true of other folders at this directory depth. Can anyone steer me towards a solution?

[http://backintime.le-web.org/]("http://backintime.le-web.org/")

---

### Post by pwicken on 2009-11-02
Bump?

I have the same problem. I.e. the folders and subfolders are there, but there are no files. And UbuntuOne report 0% used.

---

### Post by celem on 2009-11-02
When I reformatted my external usb hard drive from FAT to ext3 BackInTime recorded everything correctly. I executed BackInTime  from the command line to see what was going wrong and saw that there were error messages about the missing files, complaining about no permissions to change the group. Since FAT has no group entries, I reformatted to ext3 and all is well. So the lesson here is that if you are (like me) using an external usb drive that came from the factory with a FAT file system, BackInTime and rsync aren't going to work unless you reformat the drive to a Linux filesystem. FYI my drive is a little 250GB Western Digital Passport model WD2500MER. Instead of just deleting a bunch of preloaded Windows stuff I should of just reformatted it - BUT I had hoped to keep it as is for use on both Windows and Linux. Oh well, it is now for Linux use only :)

---

