---
title: "making a server... i think?"
date: 2009-07-01
forum: General Help
---

### Post by Xender1 on 2009-07-01
Hey, so I have an extra desktop that I dont really use much anymore now that I got my laptop. I dont want it to just sit there and I have lots of ideas for it but not sure what I need to do.

What I am thinking is making it a server (I think thats the correct term). Essentially I want to be able to store files on there, movies, etc. and be able to access them from other computers on my network (like my laptop). I was also thinking of hosting stuff from it such as a website (maybe heh).

Just wondering if anyone could point me in the right direction as to what I need to do/consider to go about doing something like this. Mainly I want to do as a learning experience so if you have any ideas please let me know! Thanks.

---

### Post by t4thfavor on 2009-07-01
Ubuntu server and webmin. But if you want a more noob friendly server environment, just use the desktop cd, and install apache for website, samba for windows shares NFS for other shares (to linux) SSH for remote commandline administration, webmin for web based management. 

What else would you like to know? I have been doing the same things for a while now, and have gotten pretty good at it.

---

### Post by DGortze380 on 2009-07-01
Well, ssh for remote admin. Putty is a good Windows ssh client if you need one.
sshfs works well for simply accessing files if you're running Linux on all the machines. Otherwise look at Samba.

I use MediaTomb for upnp ... makes sharing/streaming media really easy on upnp enabled devices. Supposedly VLC supports it?? I haven't tried it. Works well with my PS3. Seen it work with XBox 360.

Darwin Streaming Server is awesome for video, but takes some work on the back end, you're basically limit to hinted .mov and hinted .mp4.

---

### Post by HermanAB on 2009-07-01
Linux is Linux is Linux...

You don't have to install anything special - desktop Ubuntu is good enough.  Just add whatever services you want.  Because Linux isn't Windows XP, it is no big deal really.

Want a web server? install Apache.  Want remote management? install SSH.  Want to play with email? install Postfix, Citadel, Zimbra...

Just do it!

---

### Post by Iowan on 2009-07-01
Already have a DHCP server? caching DNS server?
One of my favorite places for Ubuntu help is [https://help.ubuntu.com/]("https://help.ubuntu.com/")
Another is [howtoforge.com]("http://www.howtoforge.com/howtos/linux/ubuntu")

---

### Post by earthpigg on 2009-07-01
considered FreeNAS?

[http://en.wikipedia.org/wiki/Freenas](http://en.wikipedia.org/wiki/Freenas)

> FreeNAS is a free network-attached storage server, supporting: CIFS (Samba), FTP, NFS, rsync, AFP protocols, iSCSI, S.M.A.R.T., local user authentication, and software RAID (0,1,5), with a web-based configuration interface. FreeNAS takes less than 64 MB once installed on CompactFlash, hard drive or USB flash drive.[1] FreeNAS is currently distributed as an ISO image and in source form. It is possible to run FreeNAS from a Live CD, with the configuration files stored on an MS-DOS-formatted floppy disk.

---

### Post by t4thfavor on 2009-07-01
Linux is not Linux, a server kernel is different, It doesn't matter for this kind of use. But it definately matters for other things such as virtual machines, and VPS hosting.

---

