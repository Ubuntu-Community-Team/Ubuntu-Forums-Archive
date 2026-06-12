---
title: "Mount Webserver via ftp or ssh"
date: 2010-12-31
forum: General Help
---

### Post by rqtow on 2010-12-31
Hey Guys,

first i wish all of you a happy new year. Second:

I  am a new proud owner of a webserver. My hoster offers me a ftp and a  ssh connection. Last week i tried to mount my webserver via ftp through  curlftpfs on my home-computer. So far so good, but after mounting i  noticed, that it always took a long time to access the mounted folder or  subfolders of the mounted folder.
So my question is, does it  normally takes a long time to access such through ftp mounted folder or  is the type of mounting (curlftpfs) the problem?

If ftp is the problem, would ssh be faster?
If curlftpfs is the problem, which mounting type would you suggest.
My os: Ubuntu 10.10;
If you need some more information, just aks :)

--
greets

rqtow

---

### Post by rqtow on 2011-01-01
Ok, i have found an acceptable solution (at least for me).
>curlftpfs< doesn't work on Ubuntu 10.10 with a standard 16 Mbits/s connection or at least it needs a lot of time to access the folders.
I tried to mount the webserver via sshfs and was satisfied, after a while i noticed that i couldn't move and rename my files.
The solution was to add workaround=rename as fuse option.

Hope this will help someone.

--
Greets

rqtow

---

