---
title: "Live USB Install Reports &quot;disk full&quot;"
date: 2011-01-03
forum: General Help
---

### Post by JCollierDavis on 2011-01-03
My persistent USB install is reporting that there is no more space, even though it appears there is still quite a bit of space.

I installed Lucid on an 8Gb flash drive set up according to this instruction.
[http://ubuntuforums.org/showpost.php?p=10294917&postcount=7](http://ubuntuforums.org/showpost.php?p=10294917&postcount=7)

I only made one change and formatted home-rw as ext3 instead.
I have a 1.75Gb / partition as FAT32 
I have a 2Gb casper-rw partition EXT3 -This won't mount when the system 
I have a 4Gb homre-rw partition also EXT3

System Monitor reports the FAT partition at 50% capacity.
Casper-rw won't mount when the system is booted off the USB.  I assume this has something to do with how the persistence works.
Home-rw is nearly empty


Now, I'm trying to update Nessus plug-ins. But I'm constantly getting out of space errors.  

I also received these out of space errors when I just decided to install it on my daily driver laptop beside an existing Ubuntu distro.  I again received many "out of space" errors and aborted the installation.

Any ideas about how I can fix or diagnose this issue?

---

### Post by C.S.Cameron on 2011-01-03
The third partition should be home-rw not homre-rw.
It should also be hidden when booted from the device.

Are you using Update Manager when updating? even with persistence partitions this will quickly overfill the device.

Plug the USB into another running computer and have a look into casper-rw and home-rw.

---

### Post by JCollierDavis on 2011-01-03
The 3d partition is correctly labeled home-rw.  Just a typo on the post.

The output of ls -R --size is attached.

It still looks like it shouldn't be full, but I guess it could be.  It's causing all sorts of errors.  The failed install to HDD messed up my partition table now so when I boot to the regular install I don't have a /home any more.

PS the instructions you left in multiple threads were super easy to follow.  I'd spent all weekend trying to do it manually and not having any luck.

I'm thinking I'm going to start with a much smaller base to build my ISO with remastersys so I can keep the file size down.  This particular Live USB is >REALLY< slow.

---

### Post by dcstar on 2011-01-03
> **JCollierDavis said:**
> My persistent USB install is reporting that there is no more space, even though it appears there is still quite a bit of space.
........

The casper-rw filesystem can never give back deleted/recovered file space, as long as you keep writing to it eventually it will fill up.

Whenever this happens you have to copy off all the files on casper-rw, delete and recreate it, then copy them back.

---

### Post by C.S.Cameron on 2011-01-04
> **dcstar said:**
> The casper-rw filesystem can never give back deleted/recovered file space, as long as you keep writing to it eventually it will fill up.

Whenever this happens you have to copy off all the files on casper-rw, delete and recreate it, then copy them back.

Computer Janitor will recover some space on a persistent file or partition, (casper-rw).

---

### Post by JCollierDavis on 2011-01-08
> **C.S.Cameron said:**
>  The third partition should ... also be hidden when booted from the device.
I'm not sure how to make this hidden when booting from the device. I can easially see the root and home partitions, but can't access the casper when booted. What's the trick here?
 
> **C.S.Cameron said:**
>  
Are you using Update Manager when updating? even with persistence partitions this will quickly overfill the device.
I think i turned the updates off. It's possible that I updated some packages anyway. I'll go back next time and ensure that I don't do any updates unless absolutely required
 
> **C.S.Cameron said:**
>  
Plug the USB into another running computer and have a look into casper-rw and home-rw. 

 
I took a look at the various partitions on this USB, see the image attached. I still don't get how it kept telling me that the partition was full. I suppose there's the possibility that the update I was trying to do was >1Gb in size. It seemed to download pretty quickly which lead me to think that it wasn't that big. Perhaps it was very compressed? Is there any possiblity that the root partition will grow any or can I take the extra 750Mb from it and put it on the casper one?

---

### Post by C.S.Cameron on 2011-01-08
> I'm not sure how to make this hidden when booting from the device. I can easially see the root and home partitions, but can't access the casper when booted. What's the trick here?

Sorry, in my experience the home-rw partition is as hard to find as the casper-rw partition when booted from the device.
From your image of gparted everything looks ok.

You can adjust your partition sizes with gparted without messing anything up, if you wish.

---

