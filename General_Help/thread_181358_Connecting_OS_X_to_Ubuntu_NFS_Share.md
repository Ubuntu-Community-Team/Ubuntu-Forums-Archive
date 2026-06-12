---
title: "Connecting OS X to Ubuntu NFS Share"
date: 2006-05-24
forum: General Help
---

### Post by bl0w on 2006-05-24
Hi, I'm trying to setup an ubuntu NFS share for OS X to connect to but am always getting a "Could not connect to the server because the name or password is not correct" message.

Here's what I've done, can anyone see anything missing or wrong:
- installed nfs-kernel-server
- Edited /etc/exports and added this line: /home 192.168.0.2(rw,sync)
- Exported the share: sudo exportfs -ra
- Restarted the NFS server: /etc/init.d/nfs-kernel-server restart
- Changed the username and uid to match the OS X ones.
- Changed the users group and guid to match the OS X ones.
- On the Mac, in Finder: nfs://ubuntu/home

Anyone successfully done this?

---

### Post by jlhughes on 2006-05-24
I use Samba and have no difficulty connecting between my Ubuntu box and my OS X machine. 

I'll admit it took me a while to figure out that I had to specify the username smb://ubuntu/john before the Mac would find the box.  (Ubuntu is the machine name in Samba.)

I'm a newbie in Unbuntu; no warranty is offered.

---

### Post by bl0w on 2006-05-24
Here's the solution:
In /etc/exports ensure that the parameter insecure is set, so for me it now reads:
/home 192.168.0.2(rw,insecure)

---

### Post by mike3k on 2006-10-01
> **bl0w said:**
> Hi, I'm trying to setup an ubuntu NFS share for OS X to connect to but am always getting a "Could not connect to the server because the name or password is not correct" message.

Here's what I've done, can anyone see anything missing or wrong:
- installed nfs-kernel-server
- Edited /etc/exports and added this line: /home 192.168.0.2(rw,sync)
- Exported the share: sudo exportfs -ra
- Restarted the NFS server: /etc/init.d/nfs-kernel-server restart
- Changed the username and uid to match the OS X ones.
- Changed the users group and guid to match the OS X ones.
- On the Mac, in Finder: nfs://ubuntu/home

Anyone successfully done this?

You need to add 'insecure' to the export. I also specify async, which is a lot faster.

---

### Post by bugboy on 2006-10-28
i've tried this my self with insecure and can't get it to work

---

