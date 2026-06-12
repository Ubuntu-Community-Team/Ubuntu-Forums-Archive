---
title: "dd a bootable USB"
date: 2010-05-16
forum: General Help
---

### Post by charadeur on 2010-05-16
I have a Win PE boot USB thumb drive.  I want to clone it to other USB thumb drives.  I figured dd would be the easy way to do it.  However that has not proved to be the case.  

To create image:
```
dd if=/dev/sdb of=file.iso bs=4096 conv=notrunc,noerror
``` 

To write to the new drive I am using: 
```
dd if=file.iso of=/dev/sdb bs=4096 conv=notrunc,noerror
```

The new USB key will start to boot but then hang with no errors.  fdisk shows the new drive as bootable. 

I guess I could try this same experiment with a LINUX USB boot key and see if it is somehow related to the Bart PE created Windows MBR.  Somehow I doubt that it is but I will give it a shot of anyone thinks it is worth it.  

I know I could do this with Windows ghost but I want to understand what I am doing wrong with dd or if dd is not capable of doing this for some reason.

---

