---
title: "Ubuntu  Customization Kit Problem"
date: 2009-12-06
forum: General Help
---

### Post by Vishnu V on 2009-12-06
Hai

I tried to make customized cd using ubuntu customization kit 
but when i select ubuntu iso image it says 
File /media/storage/Images/ubuntu9.10.iso does not seem to be a valid ISO9660 image

but  it is an iso image .i checked it using file command
```

vishnu@vishnu-laptop:~$ file /media/storage/Images/ubuntu9.10.iso 
/media/storage/Images/ubuntu9.10.iso: ISO 9660 CD-ROM filesystem data 'Ubuntu 9.10 i386               ' (bootable)

```

What is the problem ?

please help

Thanks

---

### Post by soupDragon on 2009-12-14
> **Vishnu V said:**
> Hai

I tried to make customized cd using ubuntu customization kit 
but when i select ubuntu iso image it says 
File /media/storage/Images/ubuntu9.10.iso does not seem to be a valid ISO9660 image

but  it is an iso image .i checked it using file command
```

vishnu@vishnu-laptop:~$ file /media/storage/Images/ubuntu9.10.iso 
/media/storage/Images/ubuntu9.10.iso: ISO 9660 CD-ROM filesystem data 'Ubuntu 9.10 i386               ' (bootable)

```

What is the problem ?

please help

Thanks
Hi
If you have aquired the "Ubuntu Customization Kit" from the repositories of Karmic Koala then you will be using Ubuntu Customization Kit  2.0.9. This version of the Ubuntu Customization Kit does not work when trying to customise a recent version of Ubuntu e.g. It will not work to create a customised version of the ubuntu9.10.iso

However if you use the latest  Ubuntu Customisation Kit i.e. UCK 2.0.10 that was released on 2009-11-06 then it should work and allow you to customise the latest versions of Ubuntu i.e. you should be able to customise ubuntu9.10.iso using UCK 2.0.10.

You will either have to wait for the repositories to contain the latest Ubuntu Customisation Kit or download and install the latest version from the Ubuntu Customisation kit website at:
[http://sourceforge.net/projects/uck/files/](http://sourceforge.net/projects/uck/files/)

ref:
[https://bugs.launchpad.net/uck/+bug/478311](https://bugs.launchpad.net/uck/+bug/478311)

I hope this is of some help :-)
All the best

---

### Post by Vishnu V on 2010-01-01
Thanks 
The new UCK solves the problem

---

### Post by sxmaxchine on 2010-01-18
had the same problem to glad i decided to check this out it fixed the problem for me to

---

### Post by klarissa on 2010-03-25
I use created by uck iso image to make usb bootable device. When I tried to boot from this usb I have "boot error" message. What should I do to fix it?

---

