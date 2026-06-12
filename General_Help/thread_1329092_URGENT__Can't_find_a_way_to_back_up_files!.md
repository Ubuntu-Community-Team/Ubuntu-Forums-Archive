---
title: "URGENT:  Can't find a way to back up files!"
date: 2009-11-17
forum: General Help
---

### Post by dgohn on 2009-11-17
Ok, my server is now offline, it won't boot as it hangs up on booting.  I am accessing the files by booting from a live cd using the rescue option.  I have a few gig's of files that I need to back up before wiping clean and performing a fresh install.  I can't burn anything to cd-rom for some reason as everything I have tried from people telling me how to do it just isn't working and it may be my burner.  I can't seem to mount the thumb drive I want to use because when I specify the file type as vfat (its a FAT16 file system formated thumb drive) it gives me a long error about wrong fs, codepages or something.  Can anyone suggest another means of backing these files up?  Please, I am desperate on this one.


Thanks in advance for any help and suggestions!

---

### Post by blazemore on 2009-11-17
Can you not format the flash drive? Is there anything else on it?

---

### Post by dgohn on 2009-11-17
I can format it, theres nothing on it, how would I go about doing so?

---

### Post by kozmo21 on 2009-11-17
You can do it from the "usb startup disk creator" . If the thumb drive is big enough, you could also put an image on it and save the files on there instead of using a CD.

---

### Post by blazemore on 2009-11-17
First type
```
sudo fdisk -l
```
To see which is the location of the tumb drive
I'm going to assume it's /dev/sdb1 but make sure you use the right one.

Then type
```
sudo umount /dev/sdb1
sudo mke2fs -t vfat /dev/sdb1
```

---

### Post by dgohn on 2009-11-17
Thanks alot.  Worked like a charm and now I am able to back up my system.

---

