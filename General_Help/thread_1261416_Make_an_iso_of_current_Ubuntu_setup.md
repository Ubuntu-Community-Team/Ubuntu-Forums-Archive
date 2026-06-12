---
title: "Make an iso of current Ubuntu setup"
date: 2009-09-08
forum: General Help
---

### Post by rtbrick on 2009-09-08
New Ubuntu, and for that matter Linux, user here. Recently downloaded 9.04 and added a few extras and tweaks to my liking. My question is this: Once I have my Ubuntu the way I like it, how can I create an iso image of the configuration of what I have so I can use it elsewhere (like on my other computers, give it to friends - whatever)?

It would be a pain to have to painstakingly set Ubuntu over and over. Ubuntu came (downloaded) as an iso, so how is an iso like that created? Is it too hard for general users to create one that mirrors their current setup?

---

### Post by Vakman on 2009-09-08
> **rtbrick said:**
> New Ubuntu, and for that matter Linux, user here. Recently downloaded 9.04 and added a few extras and tweaks to my liking. My question is this: Once I have my Ubuntu the way I like it, how can I create an iso image of the configuration of what I have so I can use it elsewhere (like on my other computers, give it to friends - whatever)?

It would be a pain to have to painstakingly set Ubuntu over and over. Ubuntu came (downloaded) as an iso, so how is an iso like that created? Is it too hard for general users to create one that mirrors their current setup?

Well, you can make an image of your current Ubuntu installation, I will get to this. Or you can modify the LiveCD using Remastersys ([http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html))
To make an image of your partitions, try using [Clonezilla]("http://www.clonezilla.org/")
An disk image is > is a single file or storage device containing the complete contents and structure representing a data storage medium or device, such as a hard drive, floppy disk, CD, or DVD, although an image of an optical disc may be referred to as an optical disc image. A disk image is usually created by creating a complete sector-by-sector copy of the source medium and thereby perfectly replicating the structure and contents of a storage device. - From Wikipedia ([http://en.wikipedia.org/wiki/Disk_image#Hard_drive_imaging](http://en.wikipedia.org/wiki/Disk_image#Hard_drive_imaging))
Hope this helps.

---

### Post by aysiu on 2009-09-08
It's quite easy to do with Remastersys:
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

---

### Post by rtbrick on 2009-09-08
Thanks for the quick responses! Just what I was looking for!

---

### Post by Vakman on 2009-09-08
> **rtbrick said:**
> Thanks for the quick responses! Just what I was looking for!

No problem.

---

### Post by vk7krj on 2009-09-08
This is pretty much what I was going to ask- is there any way of doing this with the server version (no gui)?

Thanks, Ken
[www.vk7krj.com](www.vk7krj.com)

---

### Post by makariolewis on 2009-09-08
I think there's a server version of Clonezilla.
[https://help.ubuntu.com/community/Clonezilla_Server_Edition](https://help.ubuntu.com/community/Clonezilla_Server_Edition)

---

### Post by pythonscript on 2009-09-08
> **vk7krj said:**
> This is pretty much what I was going to ask- is there any way of doing this with the server version (no gui)?


Once you have remastersys installed, you can run 

```
sudo remastersys dist
```

from the terminal. This will create an iso of your current configuration (plus the installed remastersys, of course) in /home/remastersys/remastersys/*nameofyouriso*.iso. 

Also, be sure you add:
```
APT::Install-Recommends "0";
APT::Install-Suggests "0";

```

to your /etc/apt/apt.conf file (if it's not there, just create it) because otherwise, remastersys will pull in a ton of packages that you may or may not want.

---

### Post by earthpigg on 2009-09-08
disregard

---

