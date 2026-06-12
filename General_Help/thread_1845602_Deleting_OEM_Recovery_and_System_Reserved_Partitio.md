---
title: "Deleting OEM Recovery and System Reserved Partitions"
date: 2011-09-17
forum: General Help
---

### Post by Consecrated on 2011-09-17
Hello,

I have some big questions here.

On my hard-drive I have two unknown partitions that I am curious about. These partitions are the first two listed. My goal is to install Windows 8 on the empty partition space as a new primary partition.

/dev/sda1 1.6 GB non-flagged NTFS "TOSHIBA System Volume" partition
/dev/sda2 105 MB bootable HPFS/NTFS(0x07) "System Reserved" partition
/dev/sda3 115 GB non-flagged NTFS "Filesystem" Windows 7 partition
62 GB of unallocated space << Where Windows 8 will go
/dev/sda4 21 GB Extended "Container for Logical Partitions"
---- /dev/sda6 20GB Ext4 "Filesystem" Ubuntu partition
---- /dev/sda5 1 GB Linux swap(0x82) "Swap Space" Partition

My questions for the first partition are (a) Can I delete this partition? (b) What is its purpose, given it only contains 1.6 GB, which may not be enough space to store the originally installed Windows Vista? (c) Does it still work as a recovery partition even though I have modified the harddisk with different partitions? (d) And if so, how do I access it, ie F3? (e) If I do delete it, can I burn it to a CD/DVD and it still function as a recovery disk? (f) If so, how do I do this?

My questions for the second partition are (a) Can I delete this partition? (b) What is its purpose?

Some background for the second partition: At one point in time, I had a BTRFS partition for my Ubuntu installation for which I believe I had to make a separate boot partition. I think I had made it approximately 100MB large. Could this possibly be that long-lost/forgotten partition? Since that time, I have re-installed Ubuntu as ext4 which doesn't require a separate boot partition. Some of the files found on that partition are Boot(folder), System Volume Information (folder), bootmgr, and BOOTSECT.BAK. 

If the second partition is not in use, I would like to delete it. I need another primary partition available for a Developer Preview Windows 8 install. (I am not a developer though and I only have very basic, though much enjoyed, Linux experience.) I don't mind re-installing Ubuntu, so long as my Windows 7 drive isn't messed up by deleting this second "System Reserved" partition.

Please aid!

Thanks

---

### Post by SeijiSensei on 2011-09-17
If it were me, I'd merge the unallocated space into the extended partition, then put Ubuntu and Win8 within that partition.  You'll have to back up your Ubuntu installation while you do this, as it probably won't survive the merge.  When you're finished Win8 should occupy /dev/sda7.

---

### Post by Consecrated on 2011-09-17
Would Windows 8 boot from a logical partition? I have heard that Windows needs a primary partition to boot correctly.

---

### Post by Consecrated on 2011-09-17
What are the chances the "System Reserved Partition" is used for Windows 7 or Toshiba? If it looks like it is just for Linux, then I'm willing to take the chance to delete and see if it affects Ubuntu.

---

### Post by howefield on 2011-09-17
> **Consecrated said:**
> What are the chances the "System Reserved Partition" is used for Windows 7 or Toshiba?

Very high, if I remember correctly that partition is likely to contains boot files for your Windows 7 install, I'd caution against removing it until you know for sure.

In any event, sounds like you want to make sure any data you wouldn't want to lose is safely backed up, if not already done :)

---

### Post by Mark Phelps on 2011-09-17
First of all, Win8 is just a Tech Preview -- basically the same maturity as an Alpha in Linux distro terms.  It's going to have MAJOR problems and LOTS of stuff is not going to work.  It's likely NOT to be upgradeable to the Beta, when that comes out, and the Beta is likely to require new activation codes -- which might not be publicly available.

Win8 is going to overwrite your MBR, meaning that you will have to then reinstall GRUB in order to regain access to Ubuntu.

Also, I never heard of ANY PC coming with BOTH Vista and Win7 preinsgtalled. So, did you buy this from someone else?

My guess, from the script output, is that the initial partition was once used as a boot partition for Windows, but that doesn't seem to be the case anymore ... so fixing this is going to be major work -- without adding Win8 to the mix.

---

### Post by Consecrated on 2011-09-17
Yes, I made a backup of all my data. I bought this computer new with just Vista and installed Ubuntu shortly after. Then I purchased a copy of Windows 7 with a student discount, and dual-booted Windows Vista, Windows 7, and Ubuntu. Later my computer crashed, so I had my university put an enterprise copy of Windows 7 during which they wiped the Vista partition.

Does windows need a separate boot-loader partition??? Is this normal?

It does look like Windows to me. I've found the file bootmgr.exe.mui inside the partition. If it normally doesn't create this partition, it may be high time for me to re-image my computer. Then I'll have one less primary partition, and one more available for Windows 8. I've made numbers of changes to my hdd over the years, so its likely that I separated out the boot loader for some reason connected to my btrfs experiment. Windows 7 could use a clean install as it is. Windows slows down with age. I think I'll delete these two partitions and re-install Windows 7, install windows 8 on 40 GB of space, and re-configure grub with a live CD.

I was thinking that the Developer Preview would allow me to boot into MS PowerPoint much faster to take notes for class. Windows 8 has an incredibly fast boot time. It also would be fun to try. Windows 7 is currently unstable on my system if it enters sleep or hibernate, so I was considering giving windows 8 a shot. Hopefully it will be as stable as Ubuntu, or at least more than Win7.

---

### Post by Consecrated on 2011-09-17
Is there any way to check in the GRUB configuration files if Grub is using this partition for me to boot into Windows 7? Perhaps what is mounting when I select Windows 7?

---

### Post by Consecrated on 2011-09-17
I found this in the grub.cfg. Looks like it does require this partition to boot into Windows 7.

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 684...
	chainloader +1

---

