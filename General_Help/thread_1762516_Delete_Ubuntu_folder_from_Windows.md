---
title: "Delete Ubuntu folder from Windows"
date: 2011-05-19
forum: General Help
---

### Post by Tieske909090 on 2011-05-19
Hey everybody,

I'm new to Ubuntu (and new to this forum), so I'm sorry if I would ask something stupid/impossible :P

I installed a program in /usr/share on Ubuntu 10.04, but the program was actually bigger than there was room on that partition.
It gave me some trouble, because when I tried to delete the folder, it said it couldn't move it to the Trash. When I restarted, it won't let me log in Ubuntu again...

Is it possible to delete this folder (/usr/share/IDE_SE) from Windows? or some other workaround to delete this folder in Ubuntu?

With kind regards and thanks in advance,
Thijs

---

### Post by F.G. on 2011-05-19
hi, the easiest way to do what your suggesting is probably to boot up with a live cd (ie run linux distro/ubuntu) directly from the cd. then navigate to the relevant folder (on your hard disk, not on the cd) and delete what you need to delete. otherwise, i'm surprised that you have this problem as I don't see how you could save a folder too large for a partition to that partition.
also, if you go to recovery mode, from grub, you should be able to start in root mode, just with a command prompt and then navigate to and delete what you want.
good luck.

ps. editing ubuntu from a windows partition is not so easy, I think you have to find a .exe (windows) program to be able to read the linux partition.

---

### Post by 3xp10r3r|X13 on 2011-05-19
[FONT=Courier New]Unfortunately it's not possible using windows, because that OS can't cope with ext 3/4 --> The consequence is that you can't access the partition.

You might want to use the ubuntu live cd.

Just boot from the cd and access "/". (In nautilus it will be called X gb file system)

So basically you navigate to that folder and delete it.

Should work! :)

questions?
[/FONT]

---

### Post by Tieske909090 on 2011-05-19
Thanks for the replies,, I'll try the recovery mode, as I dont have the CD here right now... If something does not work, ill be back :P

This is a great forum btw, with great people :D found lots of answers here..

---

### Post by Tieske909090 on 2011-05-19
Yay that worked,, used the command: 'sudo rm -rf /usr/share/IDE_SE'

It lets me log in again, and the folder is also gone :D

---

### Post by F.G. on 2011-05-19
hi, 
so just to clarify: if your going with recovery mode i think you'll need to go to: 'root shell with command prompt' from the recovery mode menu.  then you should see a terminal, 
type in: startx 
this should start the Xserver and you will be logged in as 'root' it will look like newly installed Ubuntu (you can do anything from here).
if 'startx' doesn't work, then you will have to navigate via the command line using some commands:

"cd /usr/share/IDE_SE"    this should take you to the 'IDE_SE' folder.
"ls"    this should show you what files are in that directory.
"rm filname"     replace 'filename' with the file you wish to remove

by default rm doesn't remove directories, so your best bet is going on by one, manually.  hope it all works out.

ps remember your logged in as root, so be careful what you delete
pps   also there is some program you can find online to edit linux partitions from windows, but i think its more hassle than its worth.

---

