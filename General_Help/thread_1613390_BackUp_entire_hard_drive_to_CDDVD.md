---
title: "BackUp entire hard drive to CD/DVD"
date: 2010-11-04
forum: General Help
---

### Post by Paul1944 on 2010-11-04
I have spent considerable time installing and getting my Ubuntu 10.04 LTS (Lucid Lynx) to where I want it.  I am looking for something that would BackUp my entire hard drive to a CD/DVD (preferably bootable) --so-- if I crash -or- want to clone to another hard drive I would have the ability to a 'Restore' of the CD/DVD and simply be able to load the CD/DVD to an old / new hard drive and be back-in-business without a lot of hassle.  PLEASE tell me there is a simple method of doing this BackUp.
Tkanks,
Paul

---

### Post by yiannis66 on 2010-11-04
the best tool is remastersys
[http://www.geekconnection.org/remastersys/]("http://www.geekconnection.org/remastersys/")
Also clonezilla,but more in a hard drive
[http://clonezilla.org/]("http://clonezilla.org/")

---

### Post by nitstorm on 2010-11-04
[www.psychocats.net/ubuntu/backup]("http://ubuntuforums.org/www.psychocats.net/ubuntu/backup")

Check that out ( the second part using the dd command and below that)

---

### Post by ezsit on 2010-11-04
I use remastersys and have relied on it for years now, since ubuntu 7.10. I backup my files, music, data, vidoes **separately** to an external hard drive and use remastersys to backup and produce a live DVD of my system without my personal files. It works beautifully.

---

### Post by Boondoklife on 2010-11-04
+1 for clonezilla. That live environment of remastersys sounds interesting, but not sure how useful running "my" install to install an os would be. 

I realize this is not CD/DVD, but if you have a central box/fileserver running you could just network boot into a clonezilla prompt and restore/save an image from the network.

---

