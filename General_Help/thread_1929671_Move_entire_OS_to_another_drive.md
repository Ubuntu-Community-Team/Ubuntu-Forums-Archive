---
title: "Move entire OS to another drive"
date: 2012-02-22
forum: General Help
---

### Post by Mike Loubet on 2012-02-22
Hi there. I'm aware that there are some guides out there about this but I want specific instructions to my issue since doing this wrong could be catastrophic.

Basically, I bought a new and bigger HDD to replace my existing one and want to make an exact copy (OS, files, GRUB, etc) onto my new one so I can just boot that one but have everything like before (except with more space). Some simple instructions would be appreciated :).

I have Mint LXDE 11 installed on that HDD, but I have Kubuntu 11.10 ready on a livecd since I assume it's needed.

Thanks

---

### Post by TheFu on 2012-02-22
Connect both HDDs to the same system.
Boot from any live CD ....
Get to a root shell.
Figure out exactly which HDD is which device.  Probably /dev/sda and /dev/sdb.  If you get this mixed up, it will be bad - REALLY bad.

**You must be booted into the live CD to move forward.**

$ sudo fdisk -l /dev/sda
should return an expected partition table.

$ sudo fdisk -l /dev/sdb
should return an empty partition table.
If this isn't what you see - STOP.

To clone
$ sudo dd if=/dev/sda of=/dev/sdb bs=102400
This will mirror all partitions, swap, everything bit for bit.  The 2nd HDD must be larger or it will be really bad.

Now take out the old HDD and boot.  The new HDD partitions will have the same UUID as the old one did, so nothing more should be necessary even if you don't swap the SATA cables.

These guys say the same things I did ... perhaps better.
[http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/) has pictures.
[http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/](http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/)

---

### Post by cptrohn on 2012-02-22
The easiest way is just to clone your old drive.  Clonezilla is a great OS cloning solution that is very simple and easy to use.  It's available in sourceforge.  Make a livecd follow the prompts and save your image to an external drive and you shouldn't have any problems.

---

### Post by Mike Loubet on 2012-02-22
I went with TheFu's method since I already had the livecd booted. It seems to be working but it looks like it will take a while. I'll let you know if it worked or if I just wiped my entire HDD :P

cptrohn: Clonezilla looks really interesting, I looked into it a bit. The multicasting cloning interests me a lot, I might need to clone a disk to multiple drives soon and had no idea how I would do it until now, so thanks!

---

### Post by dandnsmith on 2012-02-22
Once you have it working, using TheFu's method, you'll be wondering what happened to the rest of the space on the new HDD, as you'll have copied all the parameters (including sizes and limits) from the old.

I suggest that gparted (run from the LiveCD) can sort things out for you.

---

### Post by Mike Loubet on 2012-02-22
> **dandnsmith said:**
> Once you have it working, using TheFu's method, you'll be wondering what happened to the rest of the space on the new HDD, as you'll have copied all the parameters (including sizes and limits) from the old.

I suggest that gparted (run from the LiveCD) can sort things out for you.

Yup haha. I guess it's just a case of resizing the partition to make it take up the rest of the disk?

It worked great though, thanks TheFu :)

---

### Post by TheFu on 2012-02-22
No problem.

This method makes the most sense for that first time copy.  Going forward something like Clonezilla or **PartImage** are probably better.  I use PartImage myself for pure OS images. Under Linux, I haven't found that to be necessary ... for standard installs since a list of all the installed programs and my normal backups let's me reinstall from a normal distro DVD/CD install and re-apply everything for much less hassle.  

OTOH, Windows demands an image backup of the OS for every installation on non-identical hardware. PartImage is good at that.

---

### Post by dandnsmith on 2012-02-24
TheFu:
thanks for the comment about partimage and Windows - I've used partimage for saving states of Ubuntu/Mint, and for easy transfer to a system in another country where I don't have any internet connection (so cannot easily add the extra bits), but hadn't thought of it for Windows.

---

