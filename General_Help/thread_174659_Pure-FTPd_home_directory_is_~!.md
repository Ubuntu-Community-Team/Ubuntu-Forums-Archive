---
title: "Pure-FTPd home directory is ~!"
date: 2006-05-12
forum: General Help
---

### Post by W. Irving on 2006-05-12
I followed the instructions in the wiki on how to install Pure-FTPd with pureadmin, and the installation went well. The real shock hit me when I connected to the FTP server and found I was in the home folder of the current user!

That is not the most worrying thing though, as I noticed I can travel upwards in the file tree. Eventually I made my way to / and could browse other directories and files on the drive. It seems the home directory setting i pureadmin is ineffective (I am starting pureadmin with sudo or gksudo).

As home directory and fake root, I am using /home/ftpusers/user, a folder that exists. Owner is ftpuser and group is ftpgroup (I did chgrp and chown on /home/ftpusers with the -R option).

What's going on?

---

### Post by sYs^ on 2006-05-12
start pure-ftpd with option -A  (Chroot() everyone, but root.)

Edit: opps, so you're using pureadmin, then I dont know , lol :p
I think you shouldn't use pureadmin, it so easy to administrate pure-ftpd even in console.

[http://wiki.arslinux.com/FTP_Server_w/_Virtual_Users](http://wiki.arslinux.com/FTP_Server_w/_Virtual_Users)

---

### Post by W. Irving on 2006-05-12
I can't even stop the server! I can do
sudo /etc/init.d/pure-ftpd stop
as many times as I like, and still be able to connect!

An application that doesn't do what it's told... it's almost a bit like Windows! Help! How do I fix this?

---

### Post by W. Irving on 2006-05-12
Checking netstat, I found two instances of pure-ftpd. How do I kill those two instances once and for all?

(never mind, sorted; sudo kill -s TERM 13655)

---

### Post by W. Irving on 2006-05-12
```
sudo /usr/sbin/pure-ftpd -A
```

Doesn't work either.

---

