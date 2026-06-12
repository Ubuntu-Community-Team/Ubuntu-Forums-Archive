---
title: "fsck help!"
date: 2006-04-25
forum: General Help
---

### Post by wizzkid on 2006-04-25
Hi!.. I remember that my system scans on startup (at 30 kubuntu boot i think) but know, I just found out that It doesnt scan at all.

I used reiserfs as filesystems.

any ideas?

Thanks.

---

### Post by alamba on 2006-04-25
Use a livecd and the unmount your partition and then run fsck on it. Warning: UNMOUNT your current partition. fsck can totally render your system useless if used incorrectly.

A

---

### Post by wizzkid on 2006-04-25
isnt it there's a command that fsck on the next start? i think it sudo touch /force fsck.. but it doesnt work? and how to enable the auto fsck on after 30 restart? :)

Thanks.

---

### Post by Computeruser on 2006-04-25
I would like to know how to force fsck to run as well. My machine is virtual, so once it is "off", there is no way to deal with it. I have a machine on my desktop that takes a very long time to load. I did a "shrink" and that helped, but it is still slow. It was rudely turned off by mistake (not shut down) and that is why I would like to try running fsck when the machine starts. I could always rebuild it, but that seems like a defeat. I would like to see if fsck could help me. Thanks.

---

### Post by Herman on 2006-04-26
I don't know anything about virtual filesystems, but just for regular filesystems the c[ommand mentioned earlier]("http://users.bigpond.net.au/hermanzone/p10.htm#forcefsk") works for me. 
 Regards, Herman :D

---

### Post by Computeruser on 2006-04-29
Yes. I tried sudo touch /forcefsck and it forced a file system check on restart of the virtual machine. There was nothing wrong, and a "shrink" (which does a physical reorganization) made a significant improvement.

---

### Post by Ramses de Norre on 2006-04-30
An empty file called forcefsck will force fsck on remount, a file fastboot will override automated fsck.

---

