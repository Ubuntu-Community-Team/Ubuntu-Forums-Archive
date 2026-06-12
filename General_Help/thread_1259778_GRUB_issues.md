---
title: "GRUB issues"
date: 2009-09-06
forum: General Help
---

### Post by ryane24 on 2009-09-06
I just installed ubuntu along side xp and vista. Each operating system is on its own hardrive. And when i turn on my computer it says GRUB about 8 million times, like its in an infinite loop of printf("GRUB"); or something. and i dont know what to do.

---

### Post by mac9416 on 2009-09-06
Hello, ryane24,

If I were you, I would reinstall GRUB. I am posting the steps I found here: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
> 
**GUI**

[LIST=1]
[*]Boot your computer up with Ubuntu CD
[*]Go through all the process until you reach "[!!!] Disk Partition"
[*]Select Manual Partition
[*]Mount your appropriate linux partions  / /boot swap ..... 
[*]DO NOT FORMAT THEM.
[*]Finish the manual partition
[*]Say "Yes" when it asks you to save the changes
[*]It will give you errors saying that "the system couldn't install ....." after that
[*]Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
[*]Jump to "Install Grub ...."
[*]Once it is finished, just restart your computer
[/LIST]

**Command line**

[LIST=1]
[*]Boot your computer up with Ubuntu CD
[*]Open a terminal window or switch to a tty.
[*]Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary.
[*]Type "grub"
[*]Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
[*]Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
[*]Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.
[*]Quit grub by typing "quit".
[*]Reboot and remove the bootable CD.
[/LIST]

Hope that helps.
-mac

---

### Post by ryane24 on 2009-09-06
I tried the top option and it said that no root file system was selected or something like that. and wouldnt let me continue in the partitioner thing.

---

### Post by ronparent on 2009-09-06
You have to select / for your mount point in the same screen where you select format type. See this link for gory details: [http://ubuntuforums.org/showthread.php?t=1259062](http://ubuntuforums.org/showthread.php?t=1259062)

---

