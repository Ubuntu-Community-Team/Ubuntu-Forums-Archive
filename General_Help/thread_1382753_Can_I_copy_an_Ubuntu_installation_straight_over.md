---
title: "Can I copy an Ubuntu installation straight over?"
date: 2010-01-16
forum: General Help
---

### Post by rob_l_f on 2010-01-16
Hi there,

After having a laptop die on me, I have been running Ubuntu from an external hard drive for a bit, which is fine.  However, now that I have a new laptop I want to reinstall Ubuntu on the laptop's hard drive, rather than have to reinstall everything again I just wondered if I could do the following:

1. Reinstall Karmic on the laptop's hard drive (just to make sure the bootloader and MBR etc are set up properly
2. Just copy my entire Ubuntu installation from my external hard drive to my laptop hard drive

As is it the same machine all the hardware is obviously still the same, the only difference is that everything will now be running from sda instead of sdb.  Does anyone know if this would work, or will there be anything tied down to sdb now that I've installed it there?  Also, which directories should I copy?  Obviously I will ignore dev, proc, media and mnt, but what about boot?  Could I break things by overwriting the fresh bootloader, or would the fresh bootloader not like the fact that I am running a different kernel version to what it expects?

Sorry for such a confusing question!

Many thanks

Rob

---

### Post by jpmelos on 2010-01-16
Since no answers have been given yet, I'm giving you my **guess**... I would certainly **NOT** recommend it. Do a fresh install. What could happen? The worst is it taking you half hour to download updates and applications, set up the theme and your preferences...

---

### Post by nullmind on 2010-01-16
I have copied an installation before, and even on different hardware, although the CPU architecture has always been the same (not mixing 32-bit or 64-bit)

I've done this by copying the files manually to a new partition, or by copying the partition with GParted. When I manually copied the files it was because I was converting from JFS to XFS, and when you copy the partition with GParted it's like creating an image.

Usually I had to tweak my GRUB to look at the right place for the partition (/dev/sda3 became /dev/sda1 for example) and I also had to modify my /etc/fstab, but other than that I didn't have any problems.

If you do end up re-installing, you want to try a little trick I use. Launch the live CD and mount your drive. Move all the data you want to save (such as your home directory) to a new directory at /archive. Then install the new Ubuntu and when it boots you'll have your old data at /archive, and you can start moving it over.

---

### Post by bsh on 2010-01-16
yes, it is possible and quite easy.

---

### Post by ranch hand on 2010-01-16
Yup just use gparted and it is a copy/paste operation.

Do not cut/paste as you will probably need to use the OS on the external to get into your /etc/fstab to tweek where every thing is supposed to be mounted on the internal.

This may not be needed if your external has only Ubuntu on it and the same is true of the internal but I would rather be safe than sorry.  You can do what ever you want with the external when you know that it is working on the internal.

---

### Post by HeadHunter00 on 2010-01-16
It is possible, but don't do it. It's harder to do that than installing ubuntu. You have to change configurations, format the filesystem etc. You got the idea, right.

---

### Post by ranch hand on 2010-01-16
> **HeadHunter00 said:**
> It is possible, but don't do it. It's harder to do that than installing ubuntu. You have to change configurations, format the filesystem etc. You got the idea, right.
I have always found the gparted copy to be very accurate and easy.

The only configuration is if the partition number is different in which case you do need to change the fstab.

There is no need to format anything as it is a straight up copy of the partition from which it is coming.  That is already formatted.

---

### Post by Shazaam on 2010-01-16
Wouldn't a direct disk-to-disk clone with Clonezilla (or somthing similar) work? Granted the op would be going from an external to an internal, but I don't see where it would be a problem as long as the drives are the same size. The only problem then would be if the destination (new) drive is smaller. Resizing the external should take care of that.

---

### Post by ranch hand on 2010-01-16
I have never used clonezilla but hear that it works well.

I have never seen the need for it when you already have gparted on the LiveCD.

Kind of like the Super Grub Disk.  You already have all the tools you need on the LiveCD.

---

### Post by Leppie on 2010-01-16
> **ranch hand said:**
> The only configuration is if the partition number is different in which case you do need to change the fstab.
karmic uses UUID in both fstab and grub2, if you know how to set those up using the new uuid's i suppose you're good to go. otherwise i wouldn't really advise copying your system.

---

### Post by ranch hand on 2010-01-16
You have to do this from a Live CD while you are there and the "paste" is done you just run follow these instructions ignoring the editing files directions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

This is not tough.  If you are using symbolic menu entries instead of the generated ones they do not need updated in the normal coarse of things and they only need to have the partition definition edited 
if it is didfferent on your new drive.  If you are not update-grub and grub-install will take care ofit in a very short time.

---

### Post by jamesisin on 2010-01-16
You can use this post to help you get your UUID information.  That bit is near the end of the article:

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)

---

### Post by ranch hand on 2010-01-16
> **jamesisin said:**
> You can use this post to help you get your UUID information.  That bit is near the end of the article:

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)
Or just run;
```

sudo blkid

```

---

### Post by jamesisin on 2010-01-16
> **ranch hand said:**
> Or just run;
```

sudo blkid

```

Um, yeah, that would be in that bit near the end of the article.  But the article also includes useful instructions which a person not familiar with UUID's will appreciate.

---

### Post by rob_l_f on 2010-01-16
Wow, thanks for all the responses everyone.  The general consensus seems to be that this is definitely possible with (hopefully) no more than a tweak to Grub or fstab, which I'm fine with.  So I'll give it a go in the next couple of days and post the result back here!

---

