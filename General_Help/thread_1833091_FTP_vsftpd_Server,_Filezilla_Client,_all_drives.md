---
title: "FTP: vsftpd Server, Filezilla Client, all drives"
date: 2011-08-25
forum: General Help
---

### Post by weyland42 on 2011-08-25
I'm using FTP to share files between Ubuntu machines on a home wireless LAN. All are running **vsftpd** servers and **Filezilla** clients. The problem is that I potentially want to share all the hard drives for upload and dowload on all the machines, but can't see how to make anything except* /home/weyland* accessible for upload. That's what comes up when connection is made, and there's no obvious way to change it. 

Can't find anything on the web that helps, or at least that I can understand.

I imagine it's something simple that I just can't see. But what?

---

### Post by ajgreeny on 2011-08-25
Using filezilla you should be able to navigate all the folders/files of both the client and the server machines, provided you have the setup correct.  Or at least, that is what happens using ssh; maybe the vsftpd server is different.

What happens if you try to use the mouse as if using nautilus to navigate the filesystems of either machine?

---

