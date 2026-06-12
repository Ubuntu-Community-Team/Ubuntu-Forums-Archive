---
title: "Problems with using sudo"
date: 2006-03-10
forum: General Help
---

### Post by trainwreck on 2006-03-10
Hey. When I connect to my server and try to use sudo it doesnt work. Below is the printout I get when I try to use the "sudo" command.
<start>
admin@ubuntu:~$ ls
dead.letter  g2data  mambo  mambov4.5.3h.tar.gz  uploads
admin@ubuntu:~$ sudo rm -rf mambov4.5.3h.tar.gz 
sudo: Can't open /var/run/sudo/admin/0: Read-only file system
collect: Cannot write ./dfk2AKCCkS006351 (bfcommit, uid=1000, gid=112): Read-only file system
queueup: cannot create queue file ./qfk2AKCCkS006351, euid=1000, fd=-1, fp=0x0: Read-only file system
Connection to 192.168.2.166 closed.
macen:~ mannen$ 
</start>

Does annybody have a clue about the problem? I´m quite a n00b so I don´t really know that much.. Is it a possibility that I`ve been hacked?

---

### Post by lamego on 2006-03-10
Did your system booted up properly ?
/var should always be writable...

---

### Post by Zelut on 2006-03-10
If you'd been hacked you'd probably see a connection entry in /var/log/syslog (unless they removed such).. but I doubt that is what happened.

It just sounds like permissions on your machine have become fouled up and so it can't write to the proper files when using sudo.  It sounds like your drive is mounted read-only, instead of read-write.  Do you know any reason it would be set up that way?

...did you ever set the root password? (you'd know if you did).  Does trying to use 'su' work any better than 'sudo'?

---

### Post by trainwreck on 2006-03-10
I havent set a root password, thats one of my problems. and I sure cant do it now when sudo isnt working, or can i? I havent changed the mtab so I dont se why the disk should me mounted read-only.

---

