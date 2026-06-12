---
title: "LVM - not supported yet??"
date: 2010-01-30
forum: General Help
---

### Post by Fedia on 2010-01-30
Hi all!!

I've just reverted back to ubuntu (after using Fedora for two years) and the OS can't "see" one of my hard disks.

I've installed ubuntu on one disk and then (don't ask, please) reconnected my other disk (which has all my stuff).



[When I run the Disk Utility it shows this. (pic)]("http://i.imgur.com/v6rD3.png")

 It shows that my disk is made of 2 partitions, [(pic)]("http://i.imgur.com/ABiPX.png") one of those is LVM and "it isn't supported at this time".


[This is the fdisk output. (pic)]("http://i.imgur.com/w5Yy2.png")


[This is GParted output. (pic)]("http://i.imgur.com/4kLDz.png")

When I click the drive, i see the 200MB partition and none of my files.




Please please please help me getting all my stuff back.........



BTW, I'm running Karmic x64.

---

### Post by Leppie on 2010-01-30
hi and welcome to the community,

you may want to have a look at this post: [http://ubuntuforums.org/showpost.php?p=2592509&postcount=2](http://ubuntuforums.org/showpost.php?p=2592509&postcount=2)

---

### Post by Herman on 2010-01-30
Ubuntu has had support for LVM for as far back as I can remember.

You can install Ubuntu with LVM if you download an .iso for the Ubuntu 'Alternate' CD for your version of Ubuntu instead of the more popular 'Desktop' Live/Install CD.

The following link might interest you too, [Rescue an encrypted LUKS LVM volume]("http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html") - Ubuntu geek.

---

### Post by Fedia on 2010-01-31
First of all, THANK YOU Leppie & Herman!

I've managed to mount the drive and I am now able to use it.


Thanks again!!!!!

---

### Post by Leppie on 2010-01-31
> **Fedia said:**
> First of all, THANK YOU Leppie & Herman!

I've managed to mount the drive and I am now able to use it.


Thanks again!!!!!
you're welcome.

but how did you solve this? your solution may be useful to others as well ;)

---

### Post by extacy1 on 2010-05-20
mounting LVM2

```
sudo apt-get install lvm2
sudo vgchange -a y
```

---

