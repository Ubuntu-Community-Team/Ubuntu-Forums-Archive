---
title: "Installing Windows 7, will it remove Ubuntu?"
date: 2009-10-25
forum: General Help
---

### Post by Rlad78 on 2009-10-25
I'm trying to get rid of Ubuntu to make more room for 7. I have looked up many ways to get rid of Ubuntu and grub but I don't want to screw up anything and then not be able to install 7 at all. 

Is there a way I can remove all partitions from my computer and grub through installing Windows 7?

---

### Post by dv3500ea on 2009-10-25
What partitions do you have on your hard drive?

---

### Post by Rlad78 on 2009-10-25
Windows XP and Ubuntu 8

---

### Post by dv3500ea on 2009-10-25
Can't you just install it over the XP partition?

---

### Post by coffeecat on 2009-10-25
> **Rlad78 said:**
>  Is there a way I can remove all partitions from my computer and grub through installing Windows 7?

Let's make it simple - you say you want to "remove all partitions" in your first post. If you want to install Windows 7 to the whole of the hard drive, simply boot up an Ubuntu live CD, go to System > Administration > Partition editor (or System > Administration > Gparted if you're using a Karmic live CD - the menu is slightly different) and mark all partitions for deletion. Don't forget to click on the "Apply" button otherwise they don't actually get deleted. Apart from removing the Linux partitions, this will effectively remove all of grub except for stage 1 on the mbr which will be overwritten anyway when you install Windows 7.

Now boot up with the Windows 7 install DVD and install.

---

### Post by Rlad78 on 2009-10-25
> **dv3500ea said:**
> Can't you just install it over the XP partition?
Yes, but I'd like to free up more space for 7. I just had to uninstall a whole bunch of stuff because I ran out of space on my windows partition.

I was originally looking at this, but I just wanted to know if I could simply overwrite the partitions using the Windows 7 installation CD.

[http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630)

I have it burned to a CD in case I can't just use the 7 CD

---

### Post by coffeecat on 2009-10-25
**Rlad78**, you and I posted simultaneously and because of the way the forum notification works you may not have noticed my post, so I'm posting again. If you want to wipe out  the XP partition as well as the Linux ones, using an Ubuntu live CD is truly the easiest way to go. If you want to retain XP, just post back and we'll take it from there.

---

### Post by Rlad78 on 2009-10-25
> **coffeecat said:**
> **Rlad78**, you and I posted simultaneously and because of the way the forum notification works you may not have noticed my post, so I'm posting again. If you want to wipe out  the XP partition as well as the Linux ones, using an Ubuntu live CD is truly the easiest way to go. If you want to retain XP, just post back and we'll take it from there.
I want to retain XP and expand that partition in case something goes wrong with 7's installation. I also don't think I have a live CD anymore (I think I lent it to a friend...)

---

### Post by coffeecat on 2009-10-25
> **Rlad78 said:**
> I want to retain XP and expand that partition in case something goes wrong with 7's installation. I also don't think I have a live CD anymore (I think I lent it to a friend...)

Well - if you need to expand the XP partition and delete the Linux ones, I can only think of two ways of doing it. The first is with Gparted. If you can't get your Ubuntu CD back and don't want to download a full Linux CD just for Gparted, you could download the [Gparted live CD]("http://gparted.sourceforge.net/livecd.php") which is a smaller ISO, and use that. Before you use it to resize your XP partition, read what they say on their front page and on their FAQ.

The other way is to use a 3rd party partition manager from within XP. There is no suitable tool that comes with XP. There are good commercial ones, such as Acronis, but obviously you have to pay for them. I don't know of a good free one that you can use in XP.

---

### Post by Mark Phelps on 2009-10-26
> **coffeecat said:**
> ... I don't know of a good free one that you can use in XP.
EASUS Partition Manager is a free MS Windows-based partitioning tool, but since the original OS is XP, there's no compelling reason to use anything other than GParted -- it works fine on FAT32 and NTFS partitions.

---

### Post by Deeack on 2009-10-26
I would have thought you wouldn't have to wipe your Ubuntu partition nor delete Grub, usually when you do a windows install it comes up with it's own partition manager, so long as you have an idea of which one is your Ubuntu partition (IE knowing it's size on disk) you can just select that partition to be formatted by the windows installer then use it to install Windows 7 on.

Microsoft's boot loader will presumably overwrite the one that's there (Grub) too without you having to do anything special.

---

### Post by coffeecat on 2009-10-26
> **Deeack said:**
> I would have thought you wouldn't have to wipe your Ubuntu partition nor delete Grub, usually when you do a windows install it comes up with it's own partition manager, so long as you have an idea of which one is your Ubuntu partition (IE knowing it's size on disk) you can just select that partition to be formatted by the windows installer then use it to install Windows 7 on.

Unfortunately, there are two possible problems with that. Now that the OP has told us that he/she wants to resize the XP partition, the OP is going to need a "proper" partition manager. I don't think the Windows 7 installer is up to resizing an NTFS partition that it is not going to use - although I'm prepared to be corrected. So - far and away the best thing is for the OP to use Gparted, whether on a Linux live CD or the Gparted live CD.

The second problem is that there will not be a single Ubuntu partition. There will be two at least: root and swap. There might even be a separate /home. And it's a fair chance that the Ubuntu installer set up an extended partition with at least one logical partition for Ubuntu. So - what with a possible extended partition, an unknown number of logical partitions, and filesystems that Windows 7 will understand the square root of nothing much at all about, goodness knows what the Windows 7 installer will present as the contents of the hard drive when it is started up. **Much** simpler then to use Gparted to delete the unwanted partitions and present the W7 installer with unallocated space to format the way it needs to.

As you say, grub is a non-issue. Stage 2 will disappear with the Ubuntu root partition and stage 1 will be overwritten by the Windows mbr.

However, there is an issue that the OP may want to think about. Presumably they intend to end up with an XP/W7 dual-boot. Since grub will have gone to that great bit-heaven in the sky, does the Win7 installer set up a Windows dual-boot menu if one is needed? I don't know the answer to this.

---

### Post by Rlad78 on 2009-11-08
> **coffeecat said:**
> Let's make it simple - you say you want to "remove all partitions" in your first post. If you want to install Windows 7 to the whole of the hard drive, simply boot up an Ubuntu live CD, go to System > Administration > Partition editor (or System > Administration > Gparted if you're using a Karmic live CD - the menu is slightly different) and mark all partitions for deletion. Don't forget to click on the "Apply" button otherwise they don't actually get deleted. Apart from removing the Linux partitions, this will effectively remove all of grub except for stage 1 on the mbr which will be overwritten anyway when you install Windows 7.

Now boot up with the Windows 7 install DVD and install.

When I boot up the disk, I get the installation screen. Should I hit "boot from first hard disk"?

EDIT: I tried this and there not a Partition Editor in System > Administration...

---

### Post by coffeecat on 2009-11-08
> **Rlad78 said:**
> EDIT: I tried this and there not a Partition Editor in System > Administration...

Oh dear, oh dear. If you are booting up from a live Ubuntu CD, **yes there is**. Depending on the version number of Ubuntu you are using, the menu entry will be called 'Gparted', 'Partition Editor' or, if memory serves correct, 'Gnome partition editor'.

But if you're booting up from a hard disc install of Ubuntu (which hardly seems likely in the circumstances), there won't be - not unless you've installed Gparted from the repositories.

---

### Post by Rlad78 on 2009-11-08
> **coffeecat said:**
> Oh dear, oh dear. If you are booting up from a live Ubuntu CD, **yes there is**. Depending on the version number of Ubuntu you are using, the menu entry will be called 'Gparted', 'Partition Editor' or, if memory serves correct, 'Gnome partition editor'.

But if you're booting up from a hard disc install of Ubuntu (which hardly seems likely in the circumstances), there won't be - not unless you've installed Gparted from the repositories.

Since I couldn't get this to work, I used the idea I had posted in one of my previous posts (I think...). Worked like a charm. Currently installing 7.

---

### Post by NFblaze on 2009-11-08
Although, this is now solved. 
There is also a LiveCD dedicated to partitioning and other hard disk manipulations called PartedMagic and it's only 40mbs. I use it all the time for most of my partitioning and hard disk recovery needs.

---

