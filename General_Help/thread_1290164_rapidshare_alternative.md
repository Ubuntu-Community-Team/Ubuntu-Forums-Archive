---
title: "rapidshare alternative"
date: 2009-10-13
forum: General Help
---

### Post by prickee on 2009-10-13
I was wondering is there a way to do file hosting or share a file.  I have this edited video clip that I'm trying to share with another individual across the states and I just want to send him a email so all he/she would have to do is click the link and the file would start downloading.  I know there are rapidshare/filesvr/megauploads etc. but I would like to do this through my ubuntu installation.

thanks in advance

---

### Post by mimor on 2009-10-13
You could try setting up an **s**ftp server?

---

### Post by Lars Noodén on 2009-10-13
If the file is under 2GB, then you can use [Ubuntu One](https://one.ubuntu.com/).

Or [Google Docs](http://docs.google.com/) is another option.  

Or for video, the [VideoBay](http://thevideobay.org/) or [DailyMotion](http://dailymotion.com/).

As @ mimor writes, you can set up an **s**ftp server, using the Ubuntu package [OpenSSH-Server]("http://packages.ubuntu.com/jaunty/openssh-server").  That would be very easy and very secure.  ssh, scp, sftp, or filezilla can be used for file management.  

More complex variations based on ssh could include sshfs.

Going out on a limb you could install a web server with SSL and WebDAV.  

Getting wild-man, swing on a vine crazy, you could install bazaar, git or mercurial if you need version control.  One step further out there, you could go with OpenAFS...

Anyway, there are many more options but that gives a sampling of the choices and range of complexity.

---

