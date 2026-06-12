---
title: "Why do I have to keep on manually mounting my second hard drive?"
date: 2010-08-02
forum: General Help
---

### Post by giddyup306 on 2010-08-02
Hello,

I added a second internal hard drive to my system.  It took a while to figure out how to mount it, and I thought all my problems were over.  I want to use this for storage for Transmission since this would keep all the files independent of my other hard drive.  One thing that I noticed is that when I restart my computer it doesn't automatically mount the drive (Transmission gives me an error message saying it's not able to access the drive).  So I remounted it, and noticed that it restarts all my torrents.  One thing that I noticed is that Transmission keeps the .torrent files in /tmp and IIRC there is an option to move them wherever you want to in Deluge (I don't know if this will help anything or not).  I don't like Deluge, but if it's somehow easier...

So how can I retain my settings prior to restarting and make this permanent?  I do like to turn my computer off from time to time, and I am quad booting with other distros that I like testing out.

Thanks.

---

### Post by snowpine on 2010-08-02
The solution is to add the drive to your /etc/fstab file:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

However, there are graphical "front end" applications that save you from having to manually edit fstab. Check out an app called pysdm (it's in the Ubuntu repos).

---

### Post by giddyup306 on 2010-08-02
> **snowpine said:**
> The solution is to add the drive to your /etc/fstab file:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

However, there are graphical "front end" applications that save you from having to manually edit fstab. Check out an app called pysdm (it's in the Ubuntu repos).

Silly me I forgot to mention that I added it to my fstab.  I used this tutorial.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Lemme try pysdm really quick.

---

### Post by giddyup306 on 2010-08-03
I guess this one is solved.  It was technically "mounted", but in order for other programs to recognize the drive I need to put it on my desktop?  Oh well I guess it's not that big of a deal to go to places --> 120 GB file system...

---

