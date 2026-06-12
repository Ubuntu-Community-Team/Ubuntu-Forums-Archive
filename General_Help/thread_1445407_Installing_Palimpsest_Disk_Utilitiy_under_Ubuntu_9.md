---
title: "Installing Palimpsest Disk Utilitiy under Ubuntu 9.04"
date: 2010-04-02
forum: General Help
---

### Post by tackle on 2010-04-02
Hi everyone!

I'm having great trouble setting up a RAID1 with 2 disks under Ubuntu (it is truly an impossible task so far).

I've come to the conclusion that I need to install Palimpsest Disk Utility. Does anyone know if that is possible under Ubuntu 9.04? I cannot update to 9.10 since that requires 169MB more disk space free than I have on my 4GB compact flash card which the OS resides on.

I've downloaded a gnome-disk-utility pack which I've managed to run a configure script off of, but that one says I need gtk-doc (I think it was called that), which I downloaded and did the same thing with - ran the configure script. That one failed as well saying there was something wrong with a style XSL file, so no luck there.

Has anyone ever configured a RAID1 under Ubuntu 9.04 and care to share some secrets? So far the difficulty level on the most trivial things seem quite insane under Ubuntu. Perhaps I should only stick to Windows/MacOS, but I want to give this a try since I've heard so much good about it!

---

### Post by Mark Phelps on 2010-04-02
Given the frequent false positives that utility is infamous for producing, I can't see why you would WANT it installed!!

If what you want is to test the health of your hard drives, a far better solution would be to check the make and model of your drives and then go to the drive manufacture websites.  They nearly always offer downloadable drive testing utilities.

---

### Post by nem75 on 2010-04-02
If you cannot get gnome-disk-utility installed you might want to try to setup raid manually with mdadm, in which case this looks like a helpful howto: [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

Also you might want to post the error messages you got when running those configure scripts.

---

### Post by tackle on 2010-04-02
> **Mark Phelps said:**
> Given the frequent false positives that  utility is infamous for producing, I can't see why you would WANT it  installed!!

If what you want is to test the health of your hard drives, a far better  solution would be to check the make and model of your drives and then  go to the drive manufacture websites.  They nearly always offer  downloadable drive testing utilities.

The reason I want to install it is to try and create a RAID with it. I've tried with mdadm and it appears to create a RAID array but I can't access it.

> **nem75 said:**
> If you cannot get gnome-disk-utility installed you might want to try to setup raid manually with mdadm, in which case this looks like a helpful howto: [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

Also you might want to post the error messages you got when running those configure scripts.

Thanks for the tip nem. I've actually started out with that guide, using mdadm. I used the mdadm --create command and created an array with my two disks. However, I have no way of accessing the array after creating it, other than for formatting it with fdisk. That is the only way I can think of that I can interact with it.

The guide says:
> Once you've assembled the array, treat it the same way you would a  partition on a physical disk, and you can't really go wrong!

I believe the array IS assembled. I have formatted it as ext3 with no problem. It's just that I cannot find it afterwards. Trying "mount /dev/md0" just says it cannot be found in /etc/ folders. When opening up gparted I see my two drives just like before. Not sure if I should see the RAID array there, but I figure there ought to be some way to access it as a drive, to write files to.

---

### Post by nem75 on 2010-04-02
> **tackle said:**
> I believe the array IS assembled. I have formatted it as ext3 with no problem. It's just that I cannot find it afterwards. Trying "mount /dev/md0" just says it cannot be found in /etc/ folders. When opening up gparted I see my two drives just like before. Not sure if I should see the RAID array there, but I figure there ought to be some way to access it as a drive, to write files to.

It's been a while since I worked with mdadm, but you might want to post the exact error message you get as well as the output of

```
sudo fdisk -l
cat /etc/mdadm/mdadm.conf
```

---

