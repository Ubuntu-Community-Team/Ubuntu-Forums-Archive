---
title: "Evolution: Sync read e-mail"
date: 2011-09-16
forum: General Help
---

### Post by Lovegain on 2011-09-16
Hi.

I'm using Evolution for e-mail on two computers running Ubuntu. One is my home desktop machine, and the other a Eee PC netbook. (Versions are 11.04 on desktop and Easy Peasy something on netbook.)

My problem is that I read e-mail on both machines, and they don't sync. So everytime I switch to the other computer, I have to check a lot of e-mail as read.

Can I set them up to sync my read e-mail?

---

### Post by pytheas22 on 2011-09-16
Probably the best solution would be just to use IMAP so you don't download your mail to either computer.  But failing that, one approach you could try would be to change the location where your Evolution files are stored to somewhere in the cloud, via a service like Dropbox or UbuntuOne.

On Ubuntu 11.04, Evolution stores its files in ~/.gconf/apps/evolution/.  If you moved the contents of that directory on both computers to something like ~/Dropbox/evolution and then symlinked .gconf/apps/evolution/ to point to that location, it should keep everything in sync.

I'd be careful to make sure the versions of Evolution that you're using on your two computers are compatible, however (or, ideally, identical).  You could possibly screw things up badly if you try to use the same configuration files for two different versions of Evolution.

---

