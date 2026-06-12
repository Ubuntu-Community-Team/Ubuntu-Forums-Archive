---
title: "Upgrade"
date: 2006-05-27
forum: General Help
---

### Post by Mau on 2006-05-27
I was having driver problems, so I decided to upgrade to Dapper.  I went into adept changed the reps to dapper, and committed.  After about 2 hours of downloading, it started to configure, but it spit a whole bunch of errors at me.  Now when I start up I'm booted to the command line and no Internet connection.

So, I decided to boot into Windows and just download an ISO to do it that way.  My question is that because I backed up my home folder, are most of my files there already?  I know that all of my created files are there, but will mail from KMail be there?  My home folder is also in another partition -- should I still format it?

---

### Post by aysiu on 2006-05-27
One of the advantages of having a separate /home partition is not having to reformat it when you reinstall--just make sure you choose to **not** format and to **mount** it at **/home**.

And, yes, all your important stuff is in /home--personal settings, preferences, emails, etc.

---

### Post by Mau on 2006-05-27
Perfect, thanks.  One last question -- I have a MySQL database that I would love to get off my machine.  I have an external hard drive, but I don't know how to mount it via the command line (it's usually mounted to sda1).  How would I go about doing this?

---

### Post by aysiu on 2006-05-27
[QUOTE=Mau]Perfect, thanks.  One last question -- I have a MySQL database that I would love to get off my machine.  I have an external hard drive, but I don't know how to mount it via the command line (it's usually mounted to sda1).  How would I go about doing this?[/QUOTE] Can I assume this is a server install of some kind so that you don't have a graphical interface where it'll magically appear on the desktop?

These two tutorials should help you:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by Mau on 2006-05-27
It's a desktop install (I use it for development).  I decided just to move it to my home folder and run the installer.  Dapper installer is really smooth (graphical is great).

---

