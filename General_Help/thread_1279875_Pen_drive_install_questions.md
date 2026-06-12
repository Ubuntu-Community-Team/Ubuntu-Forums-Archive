---
title: "Pen drive install questions"
date: 2009-10-01
forum: General Help
---

### Post by Flavian on 2009-10-01
Hi guys.
I have some questions regarding Ubuntu Pen drive installation
First of all, my goal is to have my Ubuntu OS always with me, to carry around and use at any pc I like.
I did a lot of reading on that subject and am a little confused as for now. So I hope you guys can help me out a little.

First of all I do NOT WANT a live installation!
I want all of the ubuntu system files on the pen drive.

Second, I am a little confused about the filesystem format
Must it be fat32 ? And why?? Wouldn't reiserFS be way better (that's what I read in one post) I tried installing ubuntu several times in different filesys formats on the pen drive, but ONLY ever succeded when using fat32! Why??! I can not find any answer on that matter. The USB pendrive installer that comes with the Ubuntu 9.04 iso also can only read fat32 disks.

Thirdly
I have a 16Gb pen drive.
I want to use 3Gb for ubuntu and the rest on another partition for data storage.
But there's a problem: Windows would only recognize the FIRST of the two partitions. What the heck?! why? - OSX and Linux perfectly reads both.
So would I have to install ubuntu in the FIRST partition or in the second for it to work propperly?
Or does that not matter at all, if GRUB is installed all well?



Which method for installing a FULL ubuntu install on my pendrive with 2 partitions on it, would you recommend for me, using which filesystem to install on? And, where would I have to put the GRUB bootloader? would it work if I'd install it into hd(0,0) or must it be in say /dev/sdb2? if i consider ubuntu being in the second partition?

AND:
If I'd have to use fat32 to install ubuntu on, would there be a way to encrypt the home folder? - I ask that because a fat32 partition could easily be mounted by anyone with a windows pc, who would steal my pen drive. And so have access to all my data. E.G. E-Mails.

Thanks for your kind help in advance.
Flo

---

### Post by Flavian on 2009-10-02
help, anyone?

---

### Post by Mighty_Joe on 2009-10-02
> **Flavian said:**
> I tried installing ubuntu several times in different filesys formats on the pen drive, but ONLY ever succeded when using fat32! 

You cannot, to my knowledge, install Ubuntu to a FAT32 filesystem.  The installer will not let you.  You must be using the [Live USB Creator]("http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator"), which *does *require FAT32.

> **Flavian said:**
> 
But there's a problem: Windows would only recognize the FIRST of the two partitions. What the heck?! why? 
Windows doesn't play well with others.  As far as they're concerned there's one OS (windows) and a handful of filesystems (FAT and NTFS).  
You'll probably want a bigger Ubuntu partition.  A full install weighs in at well over 2Gb and you'll need room for updates, installs and your data.  Flash drives are [cheap]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820326008").  Buy a handful.

> **Flavian said:**
> 
Which method for installing a FULL ubuntu install on my pendrive with 2 partitions on it, 

[Here's a post]("http://ubuntuforums.org/showpost.php?p=7497700&postcount=4") where I link to the procedure I used to install Ubuntu to a flash drive.  I put Grub on the MBR of the flash drive.  I've used both ext2 and ext3 on flash drives with success.  ext2 occasionally will not be cleanly shut down.  Haven't had that problem yet with ext3.  My latest install with ext3 *feels *faster, but that may be because I'm using a different drive with this install.

---

### Post by Meow27 on 2009-10-02
the persistance file which lets you store data in a live USB doesnt show your files smack off the bat, you need to know how to browse the huge file in order to browse it... so i wouldnt worry about it too much

---

### Post by sabre2th on 2009-10-02
I used to have Ubuntu on my flash drive.  I used it mostly for utility and recovery purposes, but it was a full (non-live) install. All I did was:

Using gparted, I broke my 8gb drive into three partitions: one for the system (~5gb), one for home (~2gb), and one fat32 (~1gb) so I could still use the drive to move files on Windows boxes.  The system and home partitions were ext2 to try to limit the wear and tear on the drive.

Also to limit wear and tear, I specifically avoided putting a swap partition on there and set swappiness to a very low number (maybe even 0, but I don't remember).

Works great, as long as the computer can boot from usb flash.

It'll bog down due to slow read speed on the drive, but it's tolerable.  I'd recommend Xubuntu or even a smaller distro if you can stand to switch, but Gnome/Ubuntu will work fine too.

---

### Post by Giblet5 on 2009-10-02
Windows can read ext2/ext3 if you install explore2fs or one of the e2fs drivers.

Just because Microsoft doesn't support anything newer than VMS doesn't mean the user community is stuck in the 70's too...

(All "new" windows products are based on NT, or more correctly, WNT. V+1 M+1 S+1 = WNT. Same guy. Same architecture. Same dumb. With none of the security.)


With a big 16G thumb drive, I'd partition it 3 ways:
FAT16 - 1G (for selinux boot and the live image)
FAT32 - 7G (to keep Windows files)
ext3 - 8G (with truecrypt, for full-on awesome goodness)

---

