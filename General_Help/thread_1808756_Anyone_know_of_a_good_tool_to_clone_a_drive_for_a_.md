---
title: "Anyone know of a good tool to clone a drive for a server move?"
date: 2011-07-20
forum: General Help
---

### Post by Dustin2128 on 2011-07-20
I run an ubuntu web server on an extremely overpowered machine for the job that I'm giving to my brother. There's one major problem with a data move though- the drive is SATA, and I've only got 2 other machines in the house that have ports, one of which is my desktop, the other is a pentium 4 I'd been planning to move to for some time before it conveniently stopped booting last night. I figure what I'm going to do is grab my old 120GB PATA drive, stick it in the server and clone off the data, which leads to the question: what's a good tool to do that with? The main problem I can foresee is that I set up the drive to be encrypted for security reasons. 

I kinda doubt that ```
mount /dev/sda2 /backupdrive
sudo cp -R / /backupdrive
```is going to preserve my encryption settings exactly.

---

### Post by cbowman57 on 2011-07-20
I know nothing about running servers but [Clonezilla]("http://clonezilla.org/") might be worth a look.

---

### Post by jeffathehutt on 2011-07-20
Clonezilla for sure.  It will do a bit-for-bit copy of the drive, so all your encryption settings should be transferred to the new drive.  I haven't tested it with encryption though, so you should probably check to make sure before you wipe the original. :)

---

### Post by handy on 2011-07-21
3 times proves it. Clonezilla is the ducks guts when it comes to doing all of the things that it does... :)

---

