---
title: "Some write operations impossible in some cases"
date: 2010-01-30
forum: General Help
---

### Post by apaschou on 2010-01-30
Hi everybody.

My problem is so strange that I still can't believe it... nevertheless, let me explain it and if somebody is an expert on the subject, I will be very happy.

THE CONTEXT
I upgrade from Ubuntu 9.4 to Ubuntu 9.10 recently. The problem I describe was not happening at all on the 9.4 version.

THE PROBLEM
Only when connecting through wireless (no such issue when cable is connected), I can't do several operations of sending/writting. It will seem crazy, but I try to summarize all I saw:

a) Read/Write from network discs (SMB)
I can read whatever I want from my network disks, but I am unable to copy a file to such discs. The discs are on the local network. When I try to do the copy, the window that should give the progress appear, but then nothing special happens (no error message)

b) Read/Write to FTP
I can connect to any FTP and getting whatever I want. But for some reason I cannot write any file to an FTP. When I try, I get no more answer from the server, and I have to disconnect. Very strange: I am however able to create an empty folder on the remote FTP serveur...

As mentionned, these issues disappear if I connect to the same network via a cable instead of the wireless. I also need to mention that one Mac and one Windows are connected to the same wirless network and don't have such issue.

As a first approach, I was wondering if there was some firewall specific to wireless that would prevent some operations... is this hypothesis possible ?

Any help or advices welcome. I don't know any more what to try.

Regards.

---

### Post by humayun0156 on 2010-01-30
how to write a new thread in this forum? i'm new.

---

### Post by audiomick on 2010-01-30
@ humayun0156 : there is a button labelled "new thread" at the top of the page on the left. Click on that to start a new thread.

@ apaschou : can't really help, sorry. I would check the router to see if there is anything strange in there.

---

### Post by apaschou on 2010-02-16
Hi,

I bought a USB-Wifi dongle from D-link and disabled the internal one. This solved everything: I can not write on my network disc without any issue.

I guess that the problem was the next: With the integrated wifi card of my Toshiba Satellite L30-10T, the driver was unable to manage correctly the connection. The consequence was that as soon as the packet was too big, it didn't reach the destination. So short commands like FTP connection of file creation were working. But as soon as the content of the file was supposed to be transferred, this didn't work any more :-(.

In the meantime, I reinstalled the 9.4 version of Ubuntu. With this version, the driver was automatically working after the install and I don't have the same issue that I get with 9.10... Anyway, I can now use 9.10 with some network :-).

Regards.

---

### Post by akashiraffee on 2010-02-16
This will be a kernel issue then affecting that device.  You should try and find out exactly which module the internal wifi used and inquire to the developer about it, or at least file a bug report at ubuntu.  Either way, they have probably heard of it already and may be able to recommend something.  It may be fixed in a kernel version not updated to Ubuntu, and if you are willing to rebuild your kernel you could do that.

Of course, if you've already switched back to 9.04 then I guess that's fine.

---

### Post by Ric95 on 2010-02-16
It sounds like you need user permissions for the "wireless and ethernet networks" group.
Open your user or groups manager (I'm using xubuntu, Users and groups/user settings/me/properties) and add yourself to anything network related.

---

