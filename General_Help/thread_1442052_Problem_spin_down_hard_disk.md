---
title: "Problem: spin down hard disk"
date: 2010-03-29
forum: General Help
---

### Post by ult_avatar on 2010-03-29
hi,

I have the following problem:

if I spin down my usb-harddisk it immediately spins back up.

It doesn't matter how I do it ( I prefer sg_start though), the disk starts spinning up again without even a second of standby. 

I tried laptop mode - didn't matter.

fuser -c doesn't show any usage.

I tried unmounting - didn't mattter.

Any suggestions ?

EDIT: I forgot to mention: the drives are LVMs. But I didn't have these problems under debian though...

---

### Post by ult_avatar on 2010-03-29
this seems to be the bug report:

[https://bugs.launchpad.net/ubuntu/+source/sdparm/+bug/444818](https://bugs.launchpad.net/ubuntu/+source/sdparm/+bug/444818)

and buried in here is a quick fix:

[https://bugs.launchpad.net/ubuntu/+bug/117713](https://bugs.launchpad.net/ubuntu/+bug/117713)



> ssergeje  wrote on 2009-08-11:  	  #49

Hello again. I'm happy to say that spinning down correctly works for me on jaunty.

The problem is in udev rules.
To keep it short: I needed to copy the 60-persistent-storage.rules file, modify ACTION!="add|change" to ACTION!="add". This way sdparm commands work.

You can visit [http://ssergeje.wordpress.com/2009/08/11/unmounting-external-usb-drives-in-ubuntu/](http://ssergeje.wordpress.com/2009/08/11/unmounting-external-usb-drives-in-ubuntu/) for the details and to grab a script which does all the things


---

