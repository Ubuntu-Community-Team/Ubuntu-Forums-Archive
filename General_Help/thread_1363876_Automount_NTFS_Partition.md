---
title: "Automount NTFS Partition"
date: 2009-12-25
forum: General Help
---

### Post by cancer10 on 2009-12-25
Hi there,

I have an NTFS partition but it does not automount when I boot my OS (ubuntu 9.04)

Is there anyway I can have ubuntu automount my NTFS partition?


I followed  [this]("http://psychocats.net/ubuntu/mountwindowsfstab")  tutorial, but when I open the "NTFS Configuration Tool" it shows me the "Enable write support for internal device" as disabled (screeenshot attached).



I run the sudo fdisk -l command and it shows me a screen as attached screenshot.

and after doing the necessary changes, now my /etc/fstab  looks like the one as attached screenshot.


After doing all necessary changes and reboot my system, my ntfs partition disappeared. :(


So to get the ntfs partition back, i went ahead, edited the /etc/fstab file and commented the line which says

```
/dev/sda5 /windows ntfs-3g defaults,locale=en_IN 0 0
```


and after reboot my ntfs partition is back but my problem is still not resolved :(


Am I doing something wrong?

Pls help :)

Thanks

---

### Post by labinnsw on 2009-12-26
Try post #4 in [this thread]("http://ubuntuforums.org/showthread.php?t=850811")

Looks like you are using NTFS write configuration tool alongside the tutorial. You should probably be using one or the other but not both. I use only the NTFS write configuration tool

---

### Post by NFblaze on 2009-12-26
What version of Ubuntu are you using? ( you can also configure this to automatically display in your CP settings by the way so we dont have to ask.) As, I've never seen that tool before. 

So, if you reboot with that line commented out, and mount your NTFS partition (by way of nautilus or whatever) what does typing '*mount*' in the terminal say.

---

### Post by cancer10 on 2009-12-26
> **NFblaze said:**
> What version of Ubuntu are you using? ( you can also configure this to automatically display in your CP settings by the way so we dont have to ask.) As, I've never seen that tool before. 

So, if you reboot with that line commented out, and mount your NTFS partition (by way of nautilus or whatever) what does typing '*mount*' in the terminal say.

Hey I have mentioned the version in my post :)


I will try it and update this thread :)

---

### Post by mkeyes001 on 2009-12-26
here is my fstab file, you have to mount it using the UUID...you can get that info by running the sudo blkid command

blkid output
/dev/sda6: LABEL="Videos" UUID="87b30660-e5a4-4a0d-8152-906066438198" TYPE="ext3"


mount point in fstab
UUID="87b30660-e5a4-4a0d-8152-906066438198"    /media/Videos    ext3    defaults     0    0

---

### Post by cancer10 on 2009-12-26
Hey


That solved my problem.



many thanks :)

---

