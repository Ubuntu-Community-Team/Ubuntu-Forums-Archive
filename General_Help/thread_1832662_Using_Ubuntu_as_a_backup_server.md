---
title: "Using Ubuntu as a backup server"
date: 2011-08-25
forum: General Help
---

### Post by lampshuk on 2011-08-25
Hi, I am very new to Ubuntu but have been thinking about using it for a while. 

I installed the 10.4 (Long term support) version on an old-ish laptop yesterday and I am very impressed with the ease of use and more imnportantly the fact that it immediately "saw" the Windows 7 filesystem on our home network, including all the "shared" W7 files. This is something I still can't get my Windows XP laptop to do.

Which made me think that it could be an ideal platform for doing something I have been meaning to do for ages: create a "proper" network backup server. I have an old desktop system I can plug a bunch of hard drives into.

So, the question is: what is the best (meaning fairly flexible and easy to administer) backup utility for Ubuntu. I guess my requirements are:
Must support incremental backup
Must be able to work with Windows 7 filesystems (though these seem to be visible through the network anyway - so I guess they just look like regular Ubuntu remote filesystems)

It's years since I used Unix, so in many ways this is a trip down memory lane. It has come a looooong way!

Thanks to all involved in Linux and Ubuntu: I have so far been blown away at the usability of the OS!

---

### Post by ilantal on 2011-08-25
Maybe with an old computer 10.04 is a good choice, though I prefer the latest 11.04.
For backup, assuming it is under 5GB, you can use Ubuntu One. This has a HUGE advantage that the backup is not on your local computer, but in a cloud. Your computer can go up in flames and nothing is lost.

---

### Post by allwimb on 2011-08-25
if you don't like the cloud idea you can use backup manager which is a powerfull tool to make backup.

[spring login]("http://www.java-forums.org/blogs/spring-framework/531-login-forms-spring-security.html")

---

### Post by lampshuk on 2011-08-26
Ubuntu One sounds interesting.  I saw it on the desktop (or somewhere - not sure now) and will look into it in more detail. 

"Backup Manager" sounds like a decent place to start. Is that part of the standard OS? I'll look again....

---

### Post by bodhi.zazen on 2011-08-26
Take a look at rsync

there are graphical front ends , grsync I think, as well as web front ends

[http://www.debianadmin.com/rsync-backup-web-interfacefrontend-or-gui-tools.html](http://www.debianadmin.com/rsync-backup-web-interfacefrontend-or-gui-tools.html)

---

