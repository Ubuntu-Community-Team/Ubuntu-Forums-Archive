---
title: "boot problem"
date: 2009-11-08
forum: General Help
---

### Post by hawk_eyes on 2009-11-08
I am using ubuntu hardy heron 8.04. I hav grub installed. Somehow i messed up with my root directory that my grub no longer loads and shows "grub error 15: file not found".
Googling gave me a lot of solutions. As dictated, I booted from a live ubuntu 6.06 cd, and tried to access my root directory in the hard drive. I mounted my root partition /dev/sda1 onto a directory /media/CHECK
My root directory already contained empty directories CHECK and CHECK1 created by me before. I tried to delete those useless dirs using the command:   ubuntu@ubuntu:/media/CHECK$sudo rm -r CHECK CHECK1 hoping it would delete both dirs at once. It dint ask for my sudo password. While the command was being executed, i could see some of my dirs inside /media/CHECK disappearing. I quicky pressed Ctrl+C and ended the command. Now I find my rooot dir's home dir empty. Now, i hav two problems :(

i)Did i screw up and deleted my home dir? Can i recover its contents? I hav many important files.?
ii) Is it possible to delete other users' file from a live cd without even giving the sudo password?
iii) I want to upgrade to grub2. I hav a 9.10 karmic koala cd.

---

### Post by SPr on 2009-11-08
Download [SystemRescueCD](http://www.sysresccd.org/Main_Page) and burn it to a CD.

Use Photorec to recover the deleted files. I can't remember any details about usage but I have used it successfully. You will need to store the recovered files on a different drive than you are recovering them from so buy or borrow an external HDD if you don't have one.

If the files are that important keep backups. Search the forums for backup solutions and get into a habit of making backups on a regular basis. SysRecueCD includes PartImage which makes restorable images of partitions.

---

