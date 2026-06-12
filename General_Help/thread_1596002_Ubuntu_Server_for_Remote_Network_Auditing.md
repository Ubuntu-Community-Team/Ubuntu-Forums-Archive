---
title: "Ubuntu Server for Remote Network Auditing"
date: 2010-10-13
forum: General Help
---

### Post by bcarl17 on 2010-10-13
I am an old school linux user.  I used to run Slackware years ago before I had a family that needs Windows boxes that are wife friendly for Media Center and Farmville :)  However I am going to have an unused Athlon XP machine that is being taken offline and I'd like to stick it in the basement to become a headless linux server.  I do a lot of remote family and friends computer work, and although I have filezilla set up to get any files I have on my Windows server at home to me remotely through FTP over SSL, I would really like to be able to have a linux server that I could SSH into and run some network auditing tools on the remote machine/network I'm working on without running a LiveCD of a Linux distro.

So has anyone else done this setup to any great success?  I am basically looking at being able to do nessus/snort/netcat etc

The server would be sitting behind a dd-wrt router.

Would standard ubuntu or ubuntu server be the way to go or any other suggestions would be great.

Thanks.

---

### Post by spikoley on 2010-10-13
I recommend installing the server edition.  It will work great for your project.  Instead of running Nessus you should run [OpenVAS]("http://www.openvas.org/") because it is the open source version.  I had great success setting up a server like this for file sharing purposes.  You probably will want to get a domain or use DynDNS to make it easier to reach the server from the net.

---

