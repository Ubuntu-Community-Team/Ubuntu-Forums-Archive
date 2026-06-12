---
title: "Hosting Files on my local machine..."
date: 2009-07-27
forum: General Help
---

### Post by tylersontag on 2009-07-27
I've got some backpacking pics i want to host on my machine  and so do some of my friends.  Now these friends all live in different cities around the state and the 3 hour drive to the furthest one facilitates me wanting some sort of virtual connection to share them.

My first thought was: setup and FTP site with write permissions, they dump their files, grab mine, everyone wins.

So I've installed vsftpd and couldn't get it to work.... so i tried something with a frontend GUI, proftpd.... same scoop.... is there something glarring i'm doing wrong?  Does anyone have any FTP write-ups (or anything, FTP was just my first thought) i could look at?

Thanks

---

### Post by zzzBrett on 2009-07-28
What exactly can you not get working?  Can you not connect to it, does it not give you permission?

See if either of these helps:
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html)
[http://www.wikihow.com/Setup-vsftpd-FTP-on-Ubuntu-Linux](http://www.wikihow.com/Setup-vsftpd-FTP-on-Ubuntu-Linux)

---

### Post by tylersontag on 2009-08-03
I think its running fine…. But I can’t get an FTP client on another computer on my network to connect to it?  If say my IP address was 111.111.1.1  how would I format the connection string?  Ftp:\\ 111.111.1.1 ?  111.111.1.1 :anon?

---

### Post by bear24rw on 2009-08-03
forget ftp, use ssh

aptitude install openssh-server filezilla

forward port 22 on your router

use filezilla to connect to each other

---

