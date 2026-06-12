---
title: "Fstab syntax or mounting a /home/userid from an old disk"
date: 2011-03-02
forum: General Help
---

### Post by SalishSea on 2011-03-02
Recovering from a crash...

I now have two drives, "A" and "B".  A now has Ubuntu 10.04 and B has a couple years worth of content - largely in /home/rob .[B used to have Ubuntu 10.04 until some cryptic process introduced a kernel panic on that disk, but that's just blood under the bridge.] 

I'd like to mount /home/rob from drive B as /home/rob on drive A, thereby reducing all sorts of headaches about various .xxx settings, e.g. firefox, etc but all of the fstab discussions I have read assume you are mounting the "head "of a  disk to some point in the new filestructure, but I don't want the "head" of the old "B" disk, I want a subfolder...

What I want is an fstab entry something like 

UUID=86c1a470-67ab-4355-82d3-e6a8a930cf70/home/rob /home/rob 	  ext2  

where UUID86c... is drive "B"

Is this possible?

thanks,



Thanks,

---

### Post by Krytarik on 2011-03-02
You have to mount the "device" before you can link your home directory to the respective directory on that drive. To link them you can either use a regular symlink, like this:
```
ln -s /media/drive-b/home/rob /home/rob
```or use fstab to "bind" it, like this:```

UUID=86c1a470-67ab-4355-82d3-e6a8a930cf70 /media/drive-b ext2
/media/drive-b/home/rob /home/rob bind
```I'd prefer the latter one.

---

