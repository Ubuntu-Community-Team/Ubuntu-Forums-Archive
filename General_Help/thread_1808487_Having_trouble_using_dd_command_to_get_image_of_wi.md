---
title: "Having trouble using dd command to get image of windows machine"
date: 2011-07-20
forum: General Help
---

### Post by tom981 on 2011-07-20
Im fairly new at this stuff and this is a procedure that was put in place before i got here. We basically just install windows and then use this command to create the image
 
dd if=/dev/sda | gzip -c | split -b 2000m /mnt/foldername/filename.img.gz. 
 
i have been using this for a close to 2 years but have recently run into a problem where i am only getting part of the image. This is the first windows 7 64 bit machine that i have done it on so im not sure if that has to do with it. 
 
the error im getting is
dd: reading '/dev/sda' : input/output error
 
it is erroring out at the exact same point everytime i try it. any help would be awsome

---

### Post by seawolf167 on 2011-07-20
I'm not a dd expert so I can't really help you there, but I suggest using [Clonezilla]("http://www.clonezilla.org"), it works like a charm on everything I've tried and has a lot of configuration options.

---

### Post by dcstar on 2011-07-21
> **tom981 said:**
> Im fairly new at this stuff and this is a procedure that was put in place before i got here. We basically just install windows and then use this command to create the image
 
dd if=/dev/sda | gzip -c | split -b 2000m /mnt/foldername/filename.img.gz. 
 
i have been using this for a close to 2 years but have recently run into a problem where i am only getting part of the image. This is the first windows 7 64 bit machine that i have done it on so im not sure if that has to do with it. 
 
the error im getting is
dd: reading '/dev/sda' : input/output error
 
it is erroring out at the exact same point everytime i try it. any help would be awsome
Try:
```
**sudo** dd if=/dev/sda | gzip -c | split -b 2000m /mnt/foldername/filename.img.gz.
```

---

