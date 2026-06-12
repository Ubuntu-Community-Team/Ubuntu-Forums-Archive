---
title: "SGI XFS file acess"
date: 2012-09-28
forum: General Help
---

### Post by JG Wentworth on 2012-09-28
Greetings everybody,

I am beyond stressed and have spent hours trying to fix this problem. Please, if you are able to help me I would greatly appreciate it. 

I have a Buffalo Linkstation. It has failed. They are sending me a new one, however, this doesn't help me right now and when it comes it would not fix my problem.

I had 2, 2TB drives in an array. Both drives contained the same content. I am trying to access that data right now via USB or Firewire. I downloaded a program called UFS Data Recovery. I purchased the program yet it will not copy my data. There is no support for this program so I'm screwed. It sees all of my files but IT WILL NOT copy them. 

I NEED MY DATA!

I just downloaded Ubuntu because a friend said I should be able to access these files and use it to copy them to another 2 TB drive I have in my computer right now. 

Can someone please give me a hand. I can even provide my cell number for a more direct contact. I have Face Time, Skype and every other gadget needed to communicate. Please, someone give me a hand.

Thanks

---

### Post by LewisTM on 2012-09-28
It should be quite simple. Just set your system to boot to CDROM, boot into the Live CD and choose to try out Ubuntu.
From your title, I assume you want to recover an XFS partition. That's no problem, Linux can read XFS. 
Once in the Live session, mount both your source and destination drives by clicking them on the desktop.
To copy from one to the other, type Alt-F2 and enter this command:
```
gksudo nautilus /media
```
That will spawn a file manager with full rw access to both your drives located in /media

Good luck!

---

