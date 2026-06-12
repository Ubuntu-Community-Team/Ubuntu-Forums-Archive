---
title: "Ubuntu doesn't access some partitions that are accessible through Ubuntu CD and XP"
date: 2011-11-03
forum: General Help
---

### Post by Spiff-man on 2011-11-03
while reading and replying, assume I know nothing (newbie alert)
 
I installed Windows XP and then Ubuntu, in dual boot. Worked well during aeons of times. 
 
Then Windows XP wasn't booting. I trying to fixing by reinstalling GRUB2. Then I had just Windows XP booting and not Ubuntu, tried again and now I just have Ubuntu working, and XP doesn't boot up. 
 
I don't know if it's related to my Grub2 mess or not, but the weirder thing that I now Ubuntu doesn't recognize the other partitions, not even a NTFS partition that has no system on it. This partition use to be recognized by Ubuntu and the XP, when I was able to boot it. Also the Ubuntu CD perfectly recognizes the all the partition :( 
 
**[COLOR=red]EDIT[/COLOR]**: I am missing not just partitions but also the CD/DVD drive!!! Even thought I can reboot and run the Live CD, with no problem!! Why!?!
 
 
Does anyone has an idea of what's going on? Or better yet, how to fix the partition detection? 
 
Please be kind, this is my first post :) 
Many thanks in advance
 
version: Ubuntu 10.10

---

### Post by gordintoronto on 2011-11-03
Open Accessories/Terminal, then enter this command:
sudo update-grub
Enter your password when it's requested.

A reboot should offer Ubuntu or Windows.

---

### Post by Spiff-man on 2011-11-04
Thank you for the help. I end up using [supergrubdisk.org]("http://www.supergrubdisk.org/")

It worked very well. All drivers and partitions are showing in Ubuntu. Windows isn't booting though. It returns: 

[B]error: file not found. 
Grub rescue>[/B]

:( 

> **gordintoronto said:**
> Open Accessories/Terminal, then enter this command:
sudo update-grub
Enter your password when it's requested.

A reboot should offer Ubuntu or Windows.

---

