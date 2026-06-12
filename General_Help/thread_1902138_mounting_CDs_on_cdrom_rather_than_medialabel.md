---
title: "mounting CDs on /cdrom rather than /media/label"
date: 2011-12-30
forum: General Help
---

### Post by rng on 2011-12-30
I am using lubuntu oneiric and it is mounting CDs on /media/cd-label folder. How can I set it up so that the CDs are automatically mounted on /cdrom folder (that folder already exists). Thanks for your help.

---

### Post by HermanAB on 2011-12-30
Howdy,

The short answer is that you cannot do that.  The reason is because Linux desktop systems are now designed to handle multiple CDROMs and USB devices and uses the labels to prevent ambiguity.

The long answer is probably on [http://tldp.org](http://tldp.org), but as explained above, it may not be a good idea.

---

### Post by rng on 2011-12-30
Can I mount an already mounted CD to /cdrom also by some command? Will following work?
```
mount /dev/sr0 /cdrom
```

---

### Post by HermanAB on 2011-12-30
$ sudo mount /dev/sr0 /mnt/cdrom

---

### Post by rng on 2011-12-30
Thanks. It worked. How can I manage this from /etc/fstab file so that I do not have to give this command every time?

---

### Post by rng on 2011-12-31
If I add one of the following lines in /etc/fstab , will the CDs be always mounted to this folder? What is the exact line that I should choose?
```
/dev/cdrom      /media/cdrom    udf,iso9660  noauto,user,ro    
or
/dev/cdrom     /media/cdrom     auto     ro,noauto,user,exec     0 0
```

---

### Post by rng on 2012-01-04
I am using a windows program through wine. Wine has set up /cdrom as the CD-ROM drive folder. However, ubuntu always mounts inserted CD on a newly created subfolder in /media with subfolder name as the label of CD, eg /media/14558975. Hence the program running in wine cannot find the CD. I can mount the CD with 'sudo mount /dev/sr0 /cdrom' command but when I have to change the CD, I have to umount it and remount the next CD. 

Can this be changed so that CDs are automatically mounted to /cdrom?

---

### Post by rng on 2012-01-07
I believe HAL can be configured to automatically mount inserted CDs to a particular folder, say /cdrom, by changing the settings in /etc/hal/fdi/policy/preferences.fdi  

But I am not sure of the steps. Please help.

---

### Post by rng on 2012-01-08
I found the answer on following sites. This line in /etc/fstab works well- automounts cd on /media/cd folder: 
```
/dev/sr0         /media/cd   auto    ro,user,noauto,unhide   0      0
```
[https://bbs.archlinux.org/viewtopic.php?id=115424](https://bbs.archlinux.org/viewtopic.php?id=115424)
[http://forum.winehq.org/viewtopic.php?p=58359#58359](http://forum.winehq.org/viewtopic.php?p=58359#58359)

---

