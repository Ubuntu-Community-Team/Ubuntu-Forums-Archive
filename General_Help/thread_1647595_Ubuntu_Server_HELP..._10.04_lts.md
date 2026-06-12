---
title: "Ubuntu Server HELP... 10.04 lts"
date: 2010-12-17
forum: General Help
---

### Post by jamesgrant on 2010-12-17
Hello all, i am a total nub at linux. 

Im looking to use my old hp machine to run ubuntu server 10.04 lts.

I'v never tackeled anything like a server before.

I already know to install the os and all that jazz.

but i need step by stem instrustion on how to configure it and make it work like i want.

so let me give you an idea

i want a file server for pictures videos music documents backup files. i want to access those files from my macs, pc, and linux machines. iwant to be able to view or play that content without it being physically on the client machine (files stay on the server). 

i want to have users or several passwords so that people on my net have to enter a pass to access the files on the server

will i be abel to acces the files from wireless and wired computer on my net?

i want to be able to administer it remotly from my pc (still on the lan).


i hope this is not to much to ask for.
:popcorn:

---

### Post by nothingspecial on 2010-12-17
There are many many ways to do this

Have a look at these for a start

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

I use ssh and sshfs but then I only run linux on my lan.

---

### Post by jamesgrant on 2010-12-17
I know i want to use Samba (without swat) but i dont want just anyone whos on  my net access the files

---

### Post by jamesgrant on 2010-12-17
I know i want to use samba, but ssh and sshfs are both the same right? except that sshfs is more secure correct? witch one is best for me

---

### Post by nothingspecial on 2010-12-17
No sshfs allows you to mount remote filesytems on your local one.

My pc, netbook, laptop and my wife and kids netbooks don`t have most of the household`s media physically on them.

They are mounted with sshfs.

---

### Post by jamesgrant on 2010-12-17
Then i guess ill go with sshfs then but what about a password or users to access certain files.

---

### Post by nothingspecial on 2010-12-17
You need ssh aswell, but my problem is I know nothing of windows or mac, so I can`t really help you reach your ultimate goal.

Someone will chime in in a minute or so though.

---

### Post by jamesgrant on 2010-12-17
well what i want to know is to acces those files remotes from my wired and wireless clients, do i need to install a client program or do i tell the pc to mount the remote filesystem ( like opening my computer and select a external hdd, except its on the other end of the network) a remote hdd

---

### Post by nothingspecial on 2010-12-17
On linux
```

sshfs -o idmap=user me@192.168.1.11:/media/backup/videos ~/videos && sshfs -o idmap=user me@192.168.1.11:/media/backup/music ~/music && sshfs -o idmap=user me@192.168.1.11:/media/backup/comix ~/comix && sshfs -o idmap=user me@192.168.1.11:/media/backup/photos ~/photos
```

This is all aliased.

You can do it automatically but as it`s my netbook (and I`m not actually at home) it is easier (for me) to alias it.

---

### Post by jamesgrant on 2010-12-17
Whats that mean?

---

### Post by nothingspecial on 2010-12-17
It`s multiple instances of the same command

```
sshfs -o idmap=user me@192.168.1.11:/media/backup/videos ~/videos
```sshfs - the command

-o I want options

idmap=user - because I have the same uid on both boxes.

me@192.168.1.11:/media/backup/videos - directory I want to mount

~/videos - where I want it mounted 

I know this must sound like gobldygook to you. You need to read the links :D

---

### Post by jamesgrant on 2010-12-17
ok so shhfs means that the client can mount the remote filesystem and ssh means what

---

### Post by nothingspecial on 2010-12-17
You can login remotely via the cli (and use guis if you like).

---

### Post by jamesgrant on 2010-12-17
which ones better?

---

### Post by nothingspecial on 2010-12-17
They are the same thing.

You need ssh for sshfs

sshfs allows you to mount over ssh

---

### Post by jamesgrant on 2010-12-17
so if i wanted to acess my servers files from over the web through a browser i would need lamp correct?

---

### Post by tad1073 on 2010-12-17
I am glad I looked into this thread. I have a couple of questions about sshfs. How do you umount it, can you put it in fstab to auto-mount at boot, can public and private keys be used and if so caould you pint me into the right direction.

Never mind, found it here:
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

