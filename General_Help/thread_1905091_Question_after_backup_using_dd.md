---
title: "Question after backup using dd"
date: 2012-01-06
forum: General Help
---

### Post by aaronLund on 2012-01-06
Hi all.

I followed the instructions here regarding making a clone of one's boot drive:  [http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/](http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/)

My bootdrive (sda1) is 16GB.

I cloned it onto a 40GB partition on sdb1

I did exactly this:
```
sudo dd if=/dev/sda1 of=/dev/sdb1
```

All seemed to go well.

However when I do a df -h, I only get this:
```
aaron@aaron-ringo:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              16G  3.5G   11G  25% /
none                  242M  644K  241M   1% /dev
none                  248M  188K  248M   1% /dev/shm
none                  248M  104K  248M   1% /var/run
none                  248M     0  248M   0% /var/lock

```

I don't see any mention of sdb1^^.  Is that something to do with the df command then?

Because if I do a 'fdisk -l', I get this:
```
Disk /dev/sda: 16.9 GB, 16907304960 bytes
255 heads, 63 sectors/track, 2055 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007f40f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1991    15987712   83  Linux
/dev/sda2            1991        2056      521217    5  Extended
/dev/sda5            1991        2056      521216   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b20b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4826    38758400   83  Linux
/dev/sdb2            4826       38914   273811456    5  Extended
/dev/sdb5            4826       38914   273810432   83  Linux

```

But here's where it gets weird.

At my GRUB screen, I see this:
[IMG]http://i204.photobucket.com/albums/bb78/Pure_L/grub-issue.jpg[/IMG]

(Crappy pic.  My apologies.)

But notice that there is the 'default' kernel listing on top and then at the very bottom there is another kernel listed with "(on dev/sda1)"?

If that last entry is referencing the kernel "on dev/sda1" then what kernel is the default (top) one from?  Seems to me that since my boot disk is /dev/sda1 then the default listing (top) would also be /dev/sda1, correct?

I only noticed the second "on dev/sda1" entry after doing the dd backup.

Thanks for any advice.

[COLOR="Red"]**Secondary question:**[/COLOR]  Is the only way to get GRUB onto sdb1 via a LiveCD?  That's the way suggested [here]("http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/").  Is there NO other way to get GRUB on this disk.  I ask only because I'm having a hard time getting the Live CD to behave when it's hooked up to a non-bootable disk (at least I think that's what my problem is).

---

### Post by mastablasta on 2012-01-06
never used the dd command in CLI. I use ubuntu based GUI frontends (example see in my sig).
 
regarding liveCD - live CD should "behave" even if there is no hard disk in the computer. it botos all to ram. I am not sure what problem it gives you but yes, the easiest way to install grub is form liveCD. i guess you could also install it withouth liveCD since you are trying to install it to a different disk. but you won't be able to do it on same disk. i believe the reason to use live disk is because the hard disk needs to be unmountet or not in use when you install the bootloader. or at least it's MBR. not really completely sure. I know for exampel if you want to fix windows MBR you also need to boot from install disk first (or floppy :-) )

---

### Post by aaronLund on 2012-01-06
Thanks, mastablasta.

So regarding GRUB installation, I'd have to physically disconnect my current bootdisk (sda1) and make sure that sdb2 is now the first hd and insert the Live CD and go from there?

That seems like such a hassle.

You mentioned a link in your sig.  Does the link in question do an 'auto grub install' of some sort?

How does that work GUI style?

I guess I'm trying to figure out the most brain-dead way of making a 100% bootable clone of my current boot drive.  I've configured the living hell out of this disk and I'd rather not start from scratch if at all possible.

But to do that, I need to physically unhook my current boot disk?

Seems weird.

Thanks again.

---

