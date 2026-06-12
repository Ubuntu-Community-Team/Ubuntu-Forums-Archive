---
title: "File syncronisation"
date: 2010-03-14
forum: General Help
---

### Post by gmport on 2010-03-14
I am running Ubuntu 9.10 with Windows xp installed as VirtualBox guest, I also run a Windows xp only machine. Both machines and VB guest can connect via Samba to a network drive.
 For a long time I have been searching for a folder synchronisation application to run on the Ubuntu machine to sync my Home directories to the network drive. After trying many sync applications, I have come to the conclusion that very few will sync to a Samba share and the those that do are unreliable. I run Deja Dup for my backups and this works very well, but I would like to sync my files so that the available to both machines.
 Has anyone been able to do this? I have only been using Linux since Christmas 2009, so perhaps I'm doing something wrong. I would be most grateful for any advice.


Regards to all
gmport

---

### Post by TitanusEramius on 2010-03-14
I would recommend rsync without a doubt, but it isn't very friendly to new users and I can only point you in the right direction since I use rsync in another way:

[http://www.manpagez.com/man/1/rsync/](http://www.manpagez.com/man/1/rsync/)

But like I said, it's a lot of work to get it going, but once you get it to go you won't find a better solution for backups and synchronization :D

---

### Post by Andreas1 on 2010-03-14
> **TitanusEramius said:**
> I would recommend rsync without a doubt, but it isn't very friendly to new users and I can only point you in the right direction since I use rsync in another way:

[http://www.manpagez.com/man/1/rsync/](http://www.manpagez.com/man/1/rsync/)

But like I said, it's a lot of work to get it going, but once you get it to go you won't find a better solution for backups and synchronization :D

there is also a graphical frontend to rsync, *grsync*, i don't know if it covers all features that rsync offers.

---

### Post by gmport on 2010-03-14
Thank you both for your replies, I must get to grips with rsync. It does seem rather complicated, but if that's what it takes I shall have to persevere. I must admit that I have been taking the soft option so far and going for a graphical interface. 
Thanks again, I'm now off to [http://www.manpagez.com/man/1/rsync/](http://www.manpagez.com/man/1/rsync/)

Regards
gmport

---

### Post by sgosnell on 2010-03-14
grsync is a GUI frontend to rsync, and will let you set up your sync easily.  You can quickly reverse the sync direction, set folders, pretty much anything you like.

---

