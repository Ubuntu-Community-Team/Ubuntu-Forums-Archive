---
title: "Using PXE to boot a floppy disk image file"
date: 2009-08-08
forum: General Help
---

### Post by whiskey72 on 2009-08-08
I'm wondering if anyone would be able to help me out with a project I'm working on. I have this setup working on a laptop running windows 2003 server using RIS but I'd really like to get this up and running on a Linux (Ubuntu) installation. 

My current configuration is a windows 2003 server which is using RIS acts as my server. I have windows clients boot using PXE network boot. The clients load a floppy disk image from that is served from the 2003 server. This launches Ghost and connects the workstations to a ghost multicast session. I use this in an environment where we re-image rooms of 20 - 30 workstations at a time. But I could be doing a single cast to one computer or 30 at a time.

I would really like to replicate this using Ubuntu. I simply want to have a group of workstations boot using PXE. The Linux (Ubuntu) server would have to perform the following tasks using Ghost or Clonezilla or some other multicast capable product:
- give the client workstations an ip via DHCP
- boot the client workstation using PXE network boot to join a pre-configured multicast session on the Ubuntu server
- wait until a preselected number of clients successfully join the session and then start imaging the clients

Note - I must be able to easily choose the image file to server & I must be able to easily select the number of clients to wait for

If anyone has some thoughts on how I could accomplish this I would really appreciate the input. Maybe this has already been done somewhere but I haven't yet been able to find it.

---

