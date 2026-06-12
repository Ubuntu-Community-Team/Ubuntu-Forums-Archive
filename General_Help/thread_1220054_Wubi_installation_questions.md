---
title: "Wubi installation questions"
date: 2009-07-22
forum: General Help
---

### Post by Theory5 on 2009-07-22
hey, I am trying to get Ubuntu to work, I used UNetbootin to install it on an empty partition. Then I ran a file called Wubi and a ubuntu help thingy popped up. I had read up on wubi, and everyone says It can only be used to install ubuntu within windows. But when I ran that program it told me it can be used to separatly install ubuntu. Which one is it?

---

### Post by kogger on 2009-07-22
In response to your other post, no, Ubuntu cannot use NTFS. It uses the 'ext' filesystems, such as ext3 and ext4.

Wubi is a windows program that installs ubuntu. If you ran the program from inside windows, even if it says it can be installed separately, it's still a windows program.

---

### Post by aysiu on 2009-07-22
Wubi does both--it installs Ubuntu within Windows and runs Ubuntu separately from Windows. That's what's so great about Wubi: you can set up a dual-boot without bothering with repartitioning and replacing boot loaders.

*In a traditional dual-boot*, you use the Ubuntu installer to resize the Windows partition to make some free space, you create a new partition for Ubuntu in that free space, install Ubuntu in the new partition, and install Ubuntu's boot loader (Grub) to the Master Boot Record, replacing Windows' boot loader. 

The problem with this approach (for the new user, anyway) is... well, what if you decide you don't want Ubuntu any more? That becomes tricky. You have to use the *fixmbr* function from the Windows CD to replace Grub with Windows' boot loader. Then you have to use another CD to delete the Ubuntu partition and resize (grow) the Windows partition to fill the space.

**With a Wubi dual-boot**, you install Ubuntu on a virtual partition (basically a very large file) inside of Windows. Then you modify the Windows boot loader to include an entry for that virtual partition.

That's it.

And if you want to remove Ubuntu later, you just go to Start Menu > Control Panel > Add or Remove Programs and remove Ubuntu as you would Opera or Songbird. The virtual partition is deleted, and the boot menu is modified to go back to including only Windows as an option.

---

### Post by Theory5 on 2009-07-22
then idk what it is. When I ran it it was named wubi but it said I needed to restart the computer in order to run it. I dont want a virtual partition all I am trying to do is find a way to dual-boot it because the CD and the USB drives kept giving me an error, saying it couldnt locate parts of the installation, and it crashed to some shell thing, every single time. I used Unetbootin to put ubuntu on a usb drive, and it gave me the same error. I used unetbootin and put the installation on my secondary partitions and tried to run it but I couldnt figure out how to get it to ask me about which one I want to boot it from. I still have the USB drive with the installation on it, if anyone wants to help me run it. Does unetbootin always put wubi on it or is that just one of the things I can use it install it, or is the only one i can use through unetbootin?

---

### Post by aysiu on 2009-07-22
If you keep getting crashes and errors, regardless of whether you're using CD or USB, then it's very possible that your .iso image is corrupt (could have corrupted during download).

I would advise using BitTorrent to download the .iso.

---

### Post by Theory5 on 2009-07-22
> **aysiu said:**
> If you keep getting crashes and errors, regardless of whether you're using CD or USB, then it's very possible that your .iso image is corrupt (could have corrupted during download).

I would advise using BitTorrent to download the .iso.

I thought of that already, and thus I had Unetbootin download and install it. Many times.
The shell it drops to is called busybox, would it be possible to do some sort of manual install from there?

---

### Post by aysiu on 2009-07-22
> **Theory5 said:**
> I thought of that already, and thus I had Unetbootin download and install it. Many times.
The shell it drops to is called busybox, would it be possible to do some sort of manual install from there?
I don't think UNetBootIn uses BitTorrent to download the .iso.

---

### Post by philcamlin on 2009-07-22
> **aysiu said:**
> I don't think UNetBootIn uses BitTorrent to download the .iso.

it gets it from the mirrir site on ubuntu page

---

### Post by aysiu on 2009-07-22
> **philcamlin said:**
> it gets it from the mirrir site on ubuntu page
Exactly, so if Theory5 is having trouble getting intact images through a straight download, then UNetBootIn's download won't help.

---

### Post by Theory5 on 2009-07-22
> **aysiu said:**
> Exactly, so if Theory5 is having trouble getting intact images through a straight download, then UNetBootIn's download won't help.

yes today I will check the MD5 of a download. But I doubt that is the problem. The first time I downloaded from a US mirror and I dont know what mirror Unetbootin from. 
Here is the error I am getting.

ata1: softreset failed (device not ready)
ata2: softreset failed (device not ready)
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory
BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
(initramfs)

Thats most of the error, I didnt get a chance to write down all the paths that modprobe had trouble with.

---

### Post by aysiu on 2009-07-22
> **Theory5 said:**
> But I doubt that is the problem. I don't. ```
ata1: softreset failed (device not ready)
ata2: softreset failed (device not ready)
``` This could be a hardware problem. I don't know. ```
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory
BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
(initramfs)
``` Definitely a problem with the .iso here. You don't get that BusyBox prompt unless there's something wrong with your installation medium.

---

### Post by Theory5 on 2009-07-22
> **aysiu said:**
> ```

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
(initramfs)
``` Definitely a problem with the .iso here. You don't get that BusyBox prompt unless there's something wrong with your installation medium.

What mirror did you use to download Ubuntu 9.04 with then?

---

### Post by aysiu on 2009-07-22
> **Theory5 said:**
> What mirror did you use to download Ubuntu 9.04 with then?
I didn't.

I used BitTorrent to download it.

More details here:
[http://psychocats.net/ubuntu/getting#download](http://psychocats.net/ubuntu/getting#download)

---

### Post by Theory5 on 2009-07-22
ok I used a mirror to download it again, and this time I verified it with  the md5 checksum. It should work now.

son of a B**** it works now. I downloaded from the USA MIT media lab mirror, which was 1.19MB/s.

---

