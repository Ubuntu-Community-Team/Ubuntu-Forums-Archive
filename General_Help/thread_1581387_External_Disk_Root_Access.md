---
title: "External Disk Root Access"
date: 2010-09-24
forum: General Help
---

### Post by Merthod on 2010-09-24
Please help. Somehow my external disk drive which I use in conjunction with my desktop environment is required by Ubuntu (10.04 LTS) to be mounted as root. When the machine is loading (and shows Ubuntu and the loading dots) it asks if I want to mount my external drive or skip the step. If the drive is not loaded in a started Ubuntu session, it cannot be mounted unless I'm root.

I want to remove all these access privileges and enable it to be mounted as any external drive. How do I achieve this?

---

### Post by robsoles on 2010-09-25
What file-system is the external drive using?

---

### Post by Merthod on 2010-09-25
I've successfully amended this problem, and it is easy.

I found the solution through terminal man research. It turns out that a file called **fstab** located in **/etc** needs to be changed. 

So from a terminal I navigate to /etc and launch gedit in super user mode (like "sudo gedit fstab"). Then locate my media in the content resulting in something like this:

[FONT="Courier New"]UUID=7010760C1075D994	/media/LaCie	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0[/FONT]

As the column headers in the file indicate, there are some options (terms separated by commas). I just needed to add "user" to these options and now I have non-root access to my media.

So in the line above in this section: 
[FONT="Courier New"]defaults,nosuid,nodev,locale=en_US.utf8[/FONT]

I just added user somewhere resulting in:
[FONT="Courier New"]defaults,**user**,nosuid,nodev,locale=en_US.utf8[/FONT]

Then saved it and that's it. I hope this helps anybody else. Thanks for your interest robsoles!

---

### Post by robsoles on 2010-09-25
You are welcome. Normally when calling a 'graphical' program like gedit we use 'gksudo' though. (sudo for binaries that run in terminal, gksudo for GUI/Desktop).

Please consider marking your thread as 'solved' using 'thread tools' in red above.

---

