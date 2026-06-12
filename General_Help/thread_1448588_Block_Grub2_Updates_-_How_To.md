---
title: "Block Grub2 Updates - How To?"
date: 2010-04-06
forum: General Help
---

### Post by Doctor Mike on 2010-04-06
Just went through monkey hoops again with the updated version of grub2. Just finished restoring 9.10 after testing the lucid beta (not going to work with my older system). So easy 'right', nope. Restored complete image of 9.10 including MBR... and grub error... grub error...

Had to boot from live cd and repair grub. Got my dual booting system back to where I want it including being able to boot 9.10 after removing the other drive. Couldn't do that with the way the updated version works. The updated grub2 had also trashed my XP install while I was testing Lucid, but I was able to restore from image. So you can see why I don't want any more grub updates...

Now all I want to do is arrest the development of grub2 etc. on my system. Any ideas (outside of having to hunt for it on every update)? I'll have a shload of updates on this restore because it was sitting in cold storage for about a month.

---

### Post by djoxyk on 2010-04-06
by default grub does not damage partitions. When new version installed it looks for all available OSes and add it to your boot list. I have 3 OSes to boot and my grub has been damaged only once (i helped it manually :)).

---

### Post by Doctor Mike on 2010-04-06
> **djoxyk said:**
> by default grub does not damage partitions. When new version installed it looks for all available OSes and add it to your boot list. I have 3 OSes to boot and my grub has been damaged only once (i helped it manually :)).Sorry, but I wasn't the only person who ended up with more than one copy of grub on drives (HDD's) where I didn't want them. And the copy that got installed on sda was corrupt and could not be fully removed by super grub and was not repairable using the Windows Cd MBR repair utility. In short... restore image. Most of the people having this problem were going from 9.10 to Lucid beta. Check the bug reports.

To be sure, I didn't say the partition was damaged (file system was intact), but there was no way that I could find to restore the MBR of my Windows drive (HDD), short of maybe a repair install, but image restore was a much better option.

Note I have two physical HDD's, grub2 is on the Ubuntu drive (sdb) (they are not just partitions of the same drive).

I was informed that there was a toggle option on update, but I missed it like several others. Now there's a pop up confirmation dialogue on update (at least in Lucid Beta), but I don't want my current version of grub2 to change at all because it is working exactly as I wish it too. The updated grub2 version in Lucid would fail if I removed a drive, i.e., sda (which would be the same as what would happen if sda just died) leaving me no immediate access to a working OS...

---

### Post by louieb on 2010-04-06
You can lock any software package to a version.  - open Synaptic and look under the Package menu.

---

### Post by Doctor Mike on 2010-04-06
> **louieb said:**
> You can lock any software package to a version.  - open Synaptic and look under the Package menu.
Thank you. That will be very useful to me considering my dated hardware etc.

---

### Post by Doctor Mike on 2010-04-06
grub-pc and grub common pinned... cool...

---

### Post by oldfred on 2010-04-07
I copied this from someone with an external drive where grub kept installing to the internal:

reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/debconf/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep stage1 install in sync.

---

