---
title: "Moving OS from one HD to another"
date: 2011-01-06
forum: General Help
---

### Post by ZizzerZuz on 2011-01-06
Here's the idea ...

I want to move a 250GB IDE hard drive from a PC and repalce it with a smaller 40GB IDE HD.  Currently the 250 GB drive is dual loaded with WinXP and Ubuntu desktop.

This PC is a kiosk style touch screen that I use as a home stereo and some other entertainment and household tasks.  I have some hardware (touch screen, USB headset, wireless LAN card, sound card) that are proving to be problematic under Ubuntu.  Currently this box is very usable under windows and I would like to just continue using the current build but with the new smaller HD.

I want to move that 250GB drive (along with several others) to a cluster and make a shared network space for file storage, music streaming, etc. but that's a project for another day.

The windows forums say don't do it or buy something or try Linux.  Can this be done?  Is it more trouble than it's worth?  

Ziz

---

### Post by C.S.Cameron on 2011-01-06
You should be able to clone the Windows partition using dd:

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by seawolf167 on 2011-01-06
I'd give [Clonezilla ]("http://clonezilla.org/")a try. Resize your partitions so they fit on the smaller drive, then clone each partition over to your new drive after you set up the partition table.

---

### Post by ZizzerZuz on 2011-01-07
Thanks!

Clonezilla-live bootable CD created.

a simple test:
I have duplicated my laptop drive on to a spare of the same size.  A complete bootable replica of the drive.  Pretty cool.

Now, Things are going to get a bit more difficult.  Moving an OS from a bigger drive to a smaller drive will also require me to re-size the partitions, something I've never done.

If I understand I want to shrink the windows partition on the larger drive to the same size as the smaller drive.  I'm trying to keep it fairly simple, so I'll just use the entire smaller drive when I'm done.   

Off to find tools to resize a partition.

---

### Post by dbzkid on 2011-01-07
> **C.S.Cameron said:**
> You should be able to clone the Windows partition using dd:

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

Thank you for pointing this out, very useful guide! although not exactly beginner friendly, but sure is useful!

---

### Post by C.S.Cameron on 2011-01-07
> **ZizzerZuz said:**
> Thanks!

Clonezilla-live bootable CD created.

Off to find tools to resize a partition.

Try Partition Editor, (gparted), from the Live CD.

---

### Post by seawolf167 on 2011-01-07
> **ZizzerZuz said:**
> Off to find tools to resize a partition.

Before you resize the partitions, I strongly suggest making an image of the entire disk and saving it somewhere in case something goes wrong.

You should be able to resize the Windows partition with qtparted or gparted ([see this link]("https://help.ubuntu.com/community/WindowsDualBoot"), the bottom of the page).

You can also use [non-free proprietary software ]("http://www.acronis.com/enterprise/products/diskdirector-workstation/index.html")(only including it here because it's what I use at work for Windows machines and it works great)

As for your Ubuntu partition, simply boot off a Ubuntu LiveCD and use GParted.

I'd condense all partitions so you have just under your target size, and one massive (250-40=210GB) unallocated partition, then you should be able to clone each partition over to the new drive one at a time (I'd say do them all at once if the drives were the same size, but unfortunately since they are not, you don't have a lot of options)

---

### Post by ZizzerZuz on 2011-01-07
> **dbzkid said:**
> Thank you for pointing this out, very useful guide! although not exactly beginner friendly, but sure is useful!

Booting with the Clonezilla-live CD worked well for the laptop back up.

To help safe guard my experiment I need to back up the 250GB drive to another identical drive before I go resizing partitions.  I will try this with dd and reply with a comparison on the process.

Once the 250gb drive is backed up I'll get back to resizing the partition to fit on the smaller drive.

---

### Post by ZizzerZuz on 2011-01-07
> **dbzkid said:**
> Thank you for pointing this out, very useful guide! although not exactly beginner friendly, but sure is useful!

Wow ... I'm a bit lost trying to figure this out.  I'm thinking that I'll go back and try with Clonezilla.

I read the article top to bottom and I'm still not sure how to copy a 250GB drive to another 250GB drive.

Clonezilla is moving the data now.

---

### Post by C.S.Cameron on 2011-01-07
```
Sudo dd if=/dev/sda of=/dev/sdb
```

Where sda is the drive you wish to clone and sdb is the target drive.

The process might take a while with 250GB drives.

---

### Post by ZizzerZuz on 2011-01-07
> **C.S.Cameron said:**
> ```
Sudo dd if=/dev/sda of=/dev/sdb
```

Where sda is the drive you wish to clone and sdb is the target drive.

The process might take a while with 250GB drives.

Figures it would as simple as that.

---

### Post by hariks0 on 2011-01-07
> **C.S.Cameron said:**
> ```
Sudo dd if=/dev/sda of=/dev/sdb
```

Where sda is the drive you wish to clone and sdb is the target drive.

The process might take a while with 250GB drives.

Actually, the 's' in "sudo" is small not CAPITAL and be careful not to swap the sda and sdb. It will wipe the original drive.

---

### Post by C.S.Cameron on 2011-01-07
> **hariks0 said:**
> Actually, the 's' in "sudo" is small not CAPITAL and be careful not to swap the sda and sdb. It will wipe the original drive.

Thanks, good catch.

---

### Post by jim_deadlock on 2011-01-07
Newbie question here... I understand that the "to" media needs to be the same size or bigger than the "from" disk, but what if you have say a 40G disk and you want to copy it to an 80G disk which already has 10G of data on it, will it wipe the existing data on the 80G disk?

---

### Post by enochpc on 2011-01-07
If the data is on the same partition that you are copying to then yes it will.

---

### Post by C.S.Cameron on 2011-01-07
> **jim_deadlock said:**
> Newbie question here... I understand that the "to" media needs to be the same size or bigger than the "from" disk, but what if you have say a 40G disk and you want to copy it to an 80G disk which already has 10G of data on it, will it wipe the existing data on the 80G disk?

If you use sudo dd if=/dev/sda of=/dev/sdb, it will.

---

### Post by ZizzerZuz on 2011-01-07
> **C.S.Cameron said:**
> ```
Sudo dd if=/dev/sda of=/dev/sdb
```

Where sda is the drive you wish to clone and sdb is the target drive.

The process might take a while with 250GB drives.

I've managed to get the Windows partition down small enough that it should fit on the smaller drive.  gparted was simple enough to use.

Going back to what worked I tried clonezilla again and I can't seem to get it to work.  It'll let me copy sda to sdb but not sda1 to sdb.

Right now the drives are churning away from this command <sudo dd if=/dev/sda1 of=/dev/sdb> run from a terminal from the live CD, adapted from the post above.  I hope it works.

Thanks for all the help folks!

---

### Post by ZizzerZuz on 2011-01-08
well ... the data is moved but the drive won't boot.  I'm thinking the command I ran didn't move the MBR or something.

Leaving the drive to boot on it's own brings me to a blinking curser in the top left corner.  If I drop in the XP install disk I can get to the data via the recovery console but I don't know what to do from there.

I'll double check the dd article and see if I can come up with something.

Would going in and loading Ubuntu as a second OS on the drive load GRUB and solve my problem?

---

