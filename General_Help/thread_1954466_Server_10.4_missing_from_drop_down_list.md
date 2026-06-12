---
title: "Server 10.4 missing from drop down list"
date: 2012-04-08
forum: General Help
---

### Post by lurcherdog on 2012-04-08
Hi all, firstly I'd like to say how great Linux is as an OS, I've used various versions over the years as an alternative to other well known os's and always enjoyed using it!
 
I have come up against my first problem when trying to use a USB stick, I've downloaded the iso. from the website, checked its all there and everything is ready to go, but:
 
I want to try Linux 10.4 64bit Server LTS on a spare machine at home to see how it compares agains Win serv 2008 but I cannot find it on the drop down list!
I want to install it from a USB stick, I've downloaded the Universal USB Installer but no matter how hard I look the 10.4 64 bit Server LTS in not there in the list, I've tried clicking on other versions but obviously I need the right one to load onto the flash drive....
 
Is this an error or do I need to select a different version in the drop down or just forget using 10.4 server 64 bit LTS altogether? 
 
Many thanks,
 
Mark.

---

### Post by lechien73 on 2012-04-08
Hi & welcome to the forums,

According to the pendrivelinux.com website, it looks like 10.04 server is not supported. You could try choosing "Try Unlisted Linux ISO" at the end of the step 1 dropdown.

Alternatively, you could try using UNetbootin to create your bootable USB instead: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by lurcherdog on 2012-04-08
> **lechien73 said:**
> Hi & welcome to the forums,
 
According to the pendrivelinux.com website, it looks like 10.04 server is not supported. You could try choosing "Try Unlisted Linux ISO" at the end of the step 1 dropdown.
 
Alternatively, you could try using UNetbootin to create your bootable USB instead: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
 
 
Many thanks for the reply lechien73, I'll give both solutions a try and let you know what the outcome is!
Cheers,
Mark.

---

### Post by Cheesemill on 2012-04-08
If you want you can just use dd to copy the iso to a flash drive:
```
dd if=/path/to/ubuntu-10.04.4-server-amd64.iso of=/dev/sdb
```
Where sdb is your flash drive (make sure you get this bit right as the command will delete everything on the specified drive).

---

### Post by lurcherdog on 2012-04-08
Hi gents, I've had a partial success with using 'Other version' from the drop down and managed to load the iso onto the usb flash drive!
 
Sadly I cannot get any further after booting from USB as there are some initial drivers that are needed to boot, I get an error :
"Unknown keyword in configuration file: gfxboot vesamenu.32 not a com32R image"
 
Now that looks like graphics drivers to me, the mobo is a MSI (cannot remember ecxact model) with AMD 625 X3 and 4gb PC3200 ram. I'm using the onboard graphics card and ouputting VGA.
 
I've tried a few suggestions by looking at other threads but so far nothing changes.
 
I will keep trying!
 
Many thanks for all the replys,
Mark

---

