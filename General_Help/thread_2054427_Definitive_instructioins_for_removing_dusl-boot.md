---
title: "Definitive instructioins for removing dusl-boot?"
date: 2012-09-07
forum: General Help
---

### Post by Gordonbp531 on 2012-09-07
I have a Netbook that dual boots Ubuntu 12.04 and Windows XP.
It seems that the XP installation has borked itself and as I almost never use it I want to remove it and the entry in Grub.
I'm familiar with removing the XP partition and resizing the Ubuntu Partition with GParted, but what do I do about Grub?

---

### Post by cortman on 2012-09-07
> **gendibal said:**
> I have a Netbook that dual boots Ubuntu 12.04 and Windows XP.
It seems that the XP installation has borked itself and as I almost never use it I want to remove it and the entry in Grub.
I'm familiar with removing the XP partition and resizing the Ubuntu Partition with GParted, but what do I do about Grub?

After removing the partition, run

```
sudo update-grub
```

Grub will scan the HDD(s) and adjust itself accordingly.

---

### Post by Gordonbp531 on 2012-09-07
Thanks for that - I googled about it and nothing came up! (Found lots of pages about removing Ubuntu! :-( )
I presume I need to re-size the partition from outside of the Ubuntu install?

---

### Post by nothingspecial on 2012-09-07
Prefix changed from lubuntu to ubuntu.

You can use a live cd/usb

---

### Post by Gordonbp531 on 2012-09-07
OK.
It appears that sda2 is an EXTENDED partition, not a primary one and so I can't move or extend it into the free space that was the XP partition.
Is there any way out of this other than to re-install Ubuntu? (I'm on a capped broadband and don't really want to download all the updates again....)

If I use Gparted to copy the extended partition into the free space, remove the extended partition and extend the new (copy) partition, will it still boot?

---

### Post by Cheesemill on 2012-09-07
> **gendibal said:**
> OK.
It appears that sda2 is an EXTENDED partition, not a primary one and so I can't move or extend it into the free space that was the XP partition.
Yes you can, you just need to resize/move the actual extended partition before you can resize/move the partitions that it contains. All of this has to be done from a Live CD.

If you are unsure just post a screenshot of gparted.

---

### Post by coffeecat on 2012-09-07
@gendibal, apart from using Gparted from the live CD as Cheesemill says, if you have a swap partition which is a logical one, you need to highlight this in Gparted, right-click -> "swapoff". Swap partitions are mounted automatically by the live session and this locks the extended partition. Once you've clicked on swapoff, you should be able to resize the extended partition. After you've resized the extended partition, you will be able to resize your Ubuntu root partition assuming this is a logical partition.

---

### Post by Gordonbp531 on 2012-09-07
> **Cheesemill said:**
> Yes you can, you just need to resize/move the actual extended partition before you can resize/move the partitions that it contains. All of this has to be done from a Live CD.

If you are unsure just post a screenshot of gparted.

Thanks - must have missed something! It's resizing as I post this....

---

### Post by Gordonbp531 on 2012-09-07
Partition resized - now no boot.
Do I need to set the partition as active or re-install Grub, or something else?

---

### Post by jerome1232 on 2012-09-07
> **gendibal said:**
> Partition resized - now no boot.
Do I need to set the partition as active or re-install Grub, or something else?

What was the boot error?

---

### Post by Gordonbp531 on 2012-09-07
> **jerome1232 said:**
> What was the boot error?

There isn't one - just a blank screen with a flashing underscore cursor....

---

### Post by cortman on 2012-09-07
You may just need to reinstall grub to the MBR. Thankfully, it's pretty easy. A couple methods are outlined [here]("https://help.ubuntu.com/community/Grub2/Installing").

---

### Post by Gordonbp531 on 2012-09-07
> **cortman said:**
> You may just need to reinstall grub to the MBR. Thankfully, it's pretty easy. A couple methods are outlined [here]("https://help.ubuntu.com/community/Grub2/Installing").

I think I'll give up and just re-install.
This is what I got:
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt 
ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt/boot /dev/sda 
/usr/sbin/grub-setup: warn: This msdos-style partition label has no post-MBR gap; embedding won't be possible!. 
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged.. 
/usr/sbin/grub-setup: error: will not proceed with blocklists. 

Thanks for everyone's help....

---

### Post by coffeecat on 2012-09-07
Are you sure that your second command was:

```

ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt/boot /dev/sda 
```

And not:

```
ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt/boot /dev/sda5
```

?

You should only have got the embedding impossible error with the second command that I've posted. The first - as you quoted in your post - would be correct.

---

### Post by Gordonbp531 on 2012-09-07
> **coffeecat said:**
> Are you sure that your second command was:

```

ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt/boot /dev/sda 
```

And not:

```
ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt/boot /dev/sda5
```

?

You should only have got the embedding impossible error with the second command that I've posted. The first - as you quoted in your post - would be correct.

That post was a direct copy off the terminal screen....

---

### Post by coffeecat on 2012-09-07
> **gendibal said:**
> That post was a direct copy off the terminal screen....

Yes, I thought it might have been, but it was worth asking.

However, the error message you are getting is because grub thinks you are trying to install it to a partition, not the mbr of the drive. The fact that your command is for installing to the mbr of the drive means that something is wrong. I really don't know what, perhaps a problem in the partition table - I've not seen this before.

This might be worth investigating before you try a re-install. These may not produce any information that helps, but try running these commands in the live session:

```
sudo fdisk -lu
sudo blkid
sudo parted -l
```

And posting the output.

---

### Post by Gordonbp531 on 2012-09-07
Thanks for all your help - I did the deed a while ago and re-installed. Seemed to me to start off with a new format was a good thing. (There wasn't any data on it as such anyway).

It seems to me that this is a failing of the Ubuntu installer - if you choose the "side by side" option it puts Ubuntu into an extended partition instead of a primary one. I would have thought the installer would be sophisticated enough to see whether there was a spare primary partition available in the current disk setup. Seems not.
Maybe that's something that could be addressed in future releases..

---

### Post by coffeecat on 2012-09-07
> **gendibal said:**
> It seems to me that this is a failing of the Ubuntu installer - if you choose the "side by side" option it puts Ubuntu into an extended partition instead of a primary one. I would have thought the installer would be sophisticated enough to see whether there was a spare primary partition available in the current disk setup.

You mean a logical partition, not an extended one. An extended partition is simply a special type of primary used as a container for logical partition. It is certainly not a failing at all. Don't forget that Ubuntu also needs a separate swap partition, and separate /home partitions are popular. Also, you are viewing this from a Windows XP perspective. Windows 7 machines almost always come with three primary partitions already used, recovery, boot, and C: partitions, to which HP add a HP_TOOLS partition completely using up the 4 primary partition limitation.

Your situation of XP on one partition, and no other primary partitions is becoming unusual and dated. So...

> **gendibal said:**
> Maybe that's something that could be addressed in future releases..

I can't see that happening and, besides, with the increasing numbers of machines appearing with UEFI firmware and GUID partition tables, the old primary/logical issue will become increasingly moot.

---

