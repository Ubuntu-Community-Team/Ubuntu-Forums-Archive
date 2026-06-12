---
title: "SFTP unreliable in KDE (Lucid)"
date: 2010-05-18
forum: General Help
---

### Post by dvdram on 2010-05-18
Hi,

I seem to have huge reliability problems with SFTP in KDE (e.g. using Dolphin). Tonight for example, I was downloading a CD image. Using Dolphin to drag the file to the desktop and click 'Copy here,' it started downloading at an average of about 1.8-2.0MB/s, and after about 2 minutes it just stopped, no errors, but the network wasn't in use and the time remaining disappeared.

I used *scp* on the command line to get the file instead, and it downloaded the whole file at a much more realistic 7.9MB/s average.

I can't find any relevant bug reports on this. Has anyone else experienced a similar thing?

Alex

---

### Post by maybeway36 on 2010-05-18
I seem to remember KDE3's Konqueror not being a big fan of saving files properly to an SFTP server (it would give me an error when trying to rename the temporary file on the server to its final name), and I always had to use just FTP with it.

---

