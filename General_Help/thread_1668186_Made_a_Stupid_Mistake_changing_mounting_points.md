---
title: "Made a Stupid Mistake changing mounting points"
date: 2011-01-16
forum: General Help
---

### Post by Steve Meynell on 2011-01-16
I did a very stupid thing.  I was trying to change the mounting point of a usb external drive from '/media/disk' to '/media/Movies'  

Here is were the stupid part takes over... I right clicked on the desktop icon for the device and selected Properties.  From there I selected the Volume tab and in there I changed the mounting point to '/media/Movies'  It accepted it and said the changed would take place when I unmounted it and remounted it.  However, when I did this it now says it cannot be mounted as it says mount_point contains invalid characters usually /

Unfortunately, now I cannot get back into the properties to remove my error.

Please help.
thanks,
Steve

---

### Post by sisco311 on 2011-01-16
Change the LABEL of the partition to *Movies* in palimpsest (System -> Administration -> Disk Utility).

---

### Post by Steve Meynell on 2011-01-16
> **sisco311 said:**
> Change the LABEL of the partition to *Movies* in palimpsest (System -> Administration -> Disk Utility).

Yes, that would probably have worked, except, I don't have this 'Disk Utility' you speak of.  I do have a Partition Editor(GParted), which would allow me to change the label but I didn't want to do that as a palimpsest because I didn't want to loose my data.  

And since now my problem has gone beyond the Label, I was hoping to be able to just change the mounting point back to what it was originally and live with the fact that I have one 500 gig drive that mounts to disk and an identical 500 gig drive that mounts to disk-1 and chock it up to one of lifes' hardships.

Any information of what file that information is stored in when you change an icons properties would be most good.  

Thanks again,
Steve

---

### Post by mc4man on 2011-01-16
I don't see where changing the volume label should affect any of the data on the drive.
Assuming your using hardy or thereabouts it's possible you can fix in gconf-editor, though this may not apply to usb drives (does to internal partitions

To ck. see here post 5
[http://ubuntuforums.org/showthread.php?t=912274](http://ubuntuforums.org/showthread.php?t=912274)


Edit: though haven't used hardy in a long time so don't know is you can easily change the volume label in gparted

---

### Post by Steve Meynell on 2011-01-16
> **mc4man said:**
> I don't see where changing the volume label should affect any of the data on the drive.
Assuming your using hardy or thereabouts it's possible you can fix in gconf-editor, though this may not apply to usb drives (does to internal partitions

To ck. see here post 5
[http://ubuntuforums.org/showthread.php?t=912274](http://ubuntuforums.org/showthread.php?t=912274)


Edit: though haven't used hardy in a long time so don't know is you can easily change the volume label in gparted

WOW this was great!!!  Thank you very much!!!  This thread was exactly what I needed.  

Thank You Thank You Thank You!

Thanks to all who helped!
Steve

---

