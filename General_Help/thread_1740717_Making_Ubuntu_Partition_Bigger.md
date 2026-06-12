---
title: "Making Ubuntu Partition Bigger"
date: 2011-04-27
forum: General Help
---

### Post by ooboontwo on 2011-04-27
Hello everyone,

I installed ubuntu on my laptop as a rather small partition, just so I could try it out. (Running dual-boot with Windows Vista.)

I haven't used Windows for weeks now, and I want to migrate to using Ubuntu almost exclusively. However, there are a few programs that wine can't handle, and so I want to keep Windows on my laptop.

My question is, having Windows and Ubuntu already installed, how can I make my NTFS (Windows) partition smaller, and then tack the new free space on to my Ubuntu partition?

In other words, I don't want two separate Linux partitions, I want to merge them together after I've created them.

What open-source (read:free!) tools for partitioning are at my disposal on Ubuntu, and what do you recommend?

I'm so happy to be kicking my Windows habit. I am loving Linux!

Cheers,
Cody

---

### Post by Buntumatic on 2011-04-27
**parted** from CLI

**gparted** is parted with GTK frontend

Depending how your partitions are located on harddrive you may need to get creative when resizing and moving them, there are some restrictions.

---

### Post by Rubi1200 on 2011-04-27
First of all, before you start changing anything, make backups of all important data, whether in Windows or Linux.

With partitioning there is always a certain amount of risk involved.

Next, I recommend you use GParted on the Ubuntu CD in live mode to do the work. That way, all partitions are unmounted and you are less likely to run into difficulties. You may need to turn the swap partition off; right-click > Swapoff.

I also suggest you post a screenshot here of how GParted sees all your partitions so we can offer better advice on how to proceed.

I am no expert on Windows, but I have heard it is better to resize Windows partitions using the built-in tools in Disk Management. It is probably also a good idea to defragment your drives beforehand and to run chkdsk after resizing.

If you need more help, just ask.

---

### Post by trollger on 2011-04-27
If you are moving/resizong a partition that windows is in you MUST do it in windows disk utility if you don't you will ruin windows boot sector. You can repair this with the windows installation dvd if you have it handy.
Also do make sure to back things up first.

---

### Post by ooboontwo on 2011-04-27
OK, so what I am gathering is that I need to resize my NTFS partition IN WINDOWS, using the Windows tool first.

Next, I boot ubuntu using my install CD and somehow run parted from there?

I will be sure to back things up on external HDDs before I attempt any of this.

Cheers,
Cody

---

### Post by -kg- on 2011-04-27
> **ooboontwo said:**
> OK, so what I am gathering is that I need to resize my NTFS partition IN WINDOWS, using the Windows tool first.

Next, I boot ubuntu using my install CD and somehow run parted from there?

I will be sure to back things up on external HDDs before I attempt any of this.

Cheers,
Cody

That's correct.  I don't know about Windows 7, but Vista most certainly will have problems if you try to resize the partition with anything but it's own partitioning tool.

You might have a problem with a limit on how small you can make your Vista partition.  I've heard the way to solve this problem is to turn off paging under Vista, then reboot.  This deletes the paging file and enables you to shrink the partition further.  Of course, remember to turn paging back on next time you boot into Vista.

Then boot to the Live CD to the desktop, then launch GParted from "System/Administration/Gparted".  From there, you will be able to resize your Ubuntu partition to fill the space left when you shrank your Vista partition.  If your Ubuntu partition is a logical partition (i.e., inside an Extended partition...your Ubuntu partition would be listed as "sda5" or greater), then you will need to expand the Extended partition before you will be able to expand your Ubuntu partition.

You can read more about partitioning operations at the link in my signature block, if you need to.

---

### Post by ManyBeers on 2011-04-27
> **ooboontwo said:**
> OK, so what I am gathering is that I need to resize my NTFS partition IN WINDOWS, using the Windows tool first.

Next, I boot ubuntu using my install CD and somehow run parted from there?

I will be sure to back things up on external HDDs before I attempt any of this.

Cheers,
Cody

I have just shrunk my Vista partition 2 days ago from within Vista.
You need to turn off the pagefile,hibernation, and Systerm restore reboot then start the shrink process. If you cannot get
enough shrink using Vista's native tools download Raxco Perfect
Disk free trial edition and it should be able to move stubborn blocks that Vista puts 'way out there'. It will consolidate all data as close together as possible.

---

