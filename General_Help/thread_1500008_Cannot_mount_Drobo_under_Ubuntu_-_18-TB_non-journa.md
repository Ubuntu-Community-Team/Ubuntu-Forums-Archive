---
title: "Cannot mount Drobo under Ubuntu - 18-TB non-journaled HFS+ volume"
date: 2010-06-02
forum: General Help
---

### Post by obruchez on 2010-06-02
Hello,

This is a message I originally posted on a Drobo forum, but I was advised to post it here:

My problem is the following: I cannot mount my Drobo under Ubuntu 10.04  LTS (anymore). I'm using non-journaled HFS+. The Drobo contains three  2-TB drives. I formatted it from my MacBook Pro. I clearly remember  being able to mount the Drobo under Ubuntu a few months ago (before upgrading to 10.04 LTS). I was able  to read and write files without any problem. At that time, the volume  was almost empty. Now, it's almost full. The error I get is the  following:

"Unable to mount 18 TB Filesystem

Error mounting: mount: wrong fs type, bad option, bad superblock on  /dev/sdb2,
      missing codepage or helper program, or other error
      In some cases useful info is found in syslog - try
      dmesg | tail  or so"

I would swear it appeared as a 16-TB volume a few months ago. Could it  be the reason why Ubuntu doesn't want to mount it? Is there a 16-TB limit anywhere?

Any solution?

Screenshots from Disk Utility (Mac OS):

[http://flickr.com/gp/bruchez/3o5xzR](http://flickr.com/gp/bruchez/3o5xzR)
[http://flickr.com/gp/bruchez/u7Vtzf](http://flickr.com/gp/bruchez/u7Vtzf)

Screenshot from Drobo Dashboard (Mac OS):

[http://flickr.com/gp/bruchez/GYLBf8](http://flickr.com/gp/bruchez/GYLBf8)

Screenshot from the error message (Ubuntu):

[http://flickr.com/gp/bruchez/708S23](http://flickr.com/gp/bruchez/708S23)

Screenshots from Disk Utility (Ubuntu):

[http://flickr.com/gp/bruchez/5j6Z67](http://flickr.com/gp/bruchez/5j6Z67)
[http://flickr.com/gp/bruchez/U4WmpN](http://flickr.com/gp/bruchez/U4WmpN)

Thanks,
Olivier

---

### Post by obruchez on 2010-06-03
So, does anybody know if Ubuntu supports volumes larger than 16 TB? What about HFS+ volumes?

Is there anything special to do to enable support for such large volumes?

---

### Post by obruchez on 2010-06-08
I've found an answer to my question:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=550010](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=550010)

Apparently, HFS+ volumes larger than 2 TB are not supported anymore (I was pretty sure it worked with a previous version of Ubuntu I tested a few months ago).

Hope it will be fixed soon...

---

### Post by sparkid on 2011-03-14
5 days ago.. try mount 4TB disk, a friend me modify, hfsplus.ko  in ubuntu  [http://is.gd/vp5APz](http://is.gd/vp5APz) an now is working my WD 4TB hfsplus formated with linux

this patch, permit mount only allocatable filesystem, work with 4TB, you tried 8, 12 16 ..8).

---

