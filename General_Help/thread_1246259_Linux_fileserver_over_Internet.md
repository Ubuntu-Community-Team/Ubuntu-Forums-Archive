---
title: "Linux fileserver over Internet"
date: 2009-08-21
forum: General Help
---

### Post by Jeinhor on 2009-08-21
Hello,

I have a file server at one physical location (running Ubuntu Jaunty 9.04), a couple of clients at another physical location (both Linux and Windows clients). I would like a simple way to transfer, modify, delete, rename, etc files and folders on this file server from the clients.

Ideally I would like:
[LIST]
[*]A client that works both on Linux and Windows
[*]Secure connection
[*]Simple client GUI (mounted as a network drive in Windows and perhaps Linux)
[/LIST]

Anyone have any idea what I can use?

Thanks in advance!

---

### Post by bear24rw on 2009-08-21
on the file server install openssh-server
```
sudo aptitude install openssh-server
```
make sure you foward port 22 on the router
for the clients use filezilla (cross platform) or in ubuntu you can do the connect to server option under Places

---

### Post by Jeinhor on 2009-08-23
Works great, and was really simple to setup! Thanks a bunch for the tip!

I guess best practice is to create a separate user with permission only to the files needed, right?

I'm also looking for a way to mount the Linux server as a network drive in Windows, will try NetDrive (free for home use) and ExpanDrive (not free).

---

### Post by Jeinhor on 2009-08-23
I tried NetDrive, didn't support SFTP. I tried Dokan which worked, but was buggy.

ExpanDrive will probably work, but it is not free. Strange there's no open source alternative... or maybe not very strange, considering it works great on Ubuntu =)

---

