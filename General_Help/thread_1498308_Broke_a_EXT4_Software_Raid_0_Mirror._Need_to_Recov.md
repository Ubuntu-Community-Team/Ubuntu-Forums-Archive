---
title: "Broke a EXT4 Software Raid 0 Mirror. Need to Recover Files."
date: 2010-05-31
forum: General Help
---

### Post by Cloaky8x on 2010-05-31
I have a MSI Board that had this hard drive configuration.

200GB x Single EXT4 Ubuntu

320GB x Raid Mirror NTFS
320GB x Raid Mirror NTFS

750GB x Raid Mirror NTFS
750GB x Raid Mirror NTFS

I moved all files off the 320GB Raid 1 Mirror. Then I deleted the Hardware Raid 0 for the 320GB Drives via the BIOS Controller Interface.

Then I formatted the 320GB Drive as EXT4 to try it out over NTFS.

Although the Hardware Raid Mirror was removed, Ubuntu for some reason decided to format the 320GB as a Software Raid Mirror.

I moved my Important Files from the NTFS 750GB to Ubuntu's EXT4 320GB Software  Raid Mirror.

Then I realized that somehow the system was still using Raid as the other drive wasn't showing up. I needed another 320GB of space to Empty the 750GB and format it EXT4 Raid 1 Mirror.

I turned off the PC, unplugged one of the 320GB Raid Mirror Drives, turned it back on and Formatted the one 320GB to NTFS.

In windows, with a hardware Raid Mirror this would merely manually break the mirror, but in Ubuntu, it made my other Drive inaccessible like a Raid Striping or something. So now my pictures, and 10 years of Websites, and Documents are trapped on a Half Broken Raid Mirror.

Ubuntu starts up and informs me that 3/4 of the Drives meta data is accessable, however, I'm not sure if that means I need to perform some kind of "Repair", or use a Command Line Recovery program? or DD? Do I need to use DiskPatch to rebuild the MBR or Partition Tables or something?

I know EXT4 is new, but there's no way It's impossible to recover, otherwise why would people use any Linux for File Servers or Web Servers.

Can anyone offer any Ideas, Solutions or Help please?

---

### Post by Jeroensum on 2010-06-01
First things first, raid 0 is **NOT** a mirror, raid 0 is striping and raid 1 is mirroring. 
[http://en.wikipedia.org/wiki/Standard_RAID_levels](http://en.wikipedia.org/wiki/Standard_RAID_levels)

If you made a mistake in your post and not your config, try this:
When you break a mirror the default action is to repair it and the only way to do that would be to add a drive and let mdadm rebuild the mirror.

However since you don't want a raid rebuild, you could try this:
edit /etc/mdadm.conf so the current array is commented out. Restart mdadm. 

Assuming md0 can be used (if not make it md1) and the drive you want is /dev/sdb try this:
```

mdadm --create /dev/md0 --raid-devices=1 /dev/sdb --level=1

```

However, if you have made a mistake in your config and not your post then you've got a problem. Breaking a stripe-set is effectivly destroying data, on the disk you have allready overwritten, getting data back is nearly impossible. On the disk you have left alone you could take a look here to try and recover documents:
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by dcstar on 2010-06-01
> **Jeroensum said:**
> First things first, raid 0 is **NOT** a mirror, raid 0 is striping and raid 1 is mirroring. 
[http://en.wikipedia.org/wiki/Standard_RAID_levels](http://en.wikipedia.org/wiki/Standard_RAID_levels)
.........

Yep, "RAID 0" is **the exact opposite** of "Redundancy", you double the chances of losing your data because you make it dependant on two devices.

"RAID 0" is anti-RAID and anyone who uses it for critical data is just fooling themselves.

---

### Post by Cloaky8x on 2010-06-01
Ah, Yes I don't know why I confuse Raid 0 & Raid 1, but I do sometimes.

Yes it is a Raid 1 Mirror as the Drive size was only 320GB instead of 640GB. I'll try editing the config now or rebuilding.

Edit:

Here's more details on the two disks.
[http://img710.imageshack.us/img710/192/screenshot320gbharddisk.png](http://img710.imageshack.us/img710/192/screenshot320gbharddisk.png)
[http://img175.imageshack.us/img175/192/screenshot320gbharddisk.png](http://img175.imageshack.us/img175/192/screenshot320gbharddisk.png)

I tried "gedit /etc/mdadm.conf" although the configuration file is empty, also the /etc/fstab also only has one entry.

---

### Post by Cloaky8x on 2010-06-01
I tried setting up the single drive as a mdadm RAID array

```
sudo mdadm --create /dev/md0 --raid-devices=1 /dev/sda --level=1 --force
```

It created the RAID 1 Array, and found the Filesystem as EXT4 and volume label.

however, I cant mount it.
[http://img52.imageshack.us/img52/6568/screenshot2hj.png](http://img52.imageshack.us/img52/6568/screenshot2hj.png)

```

loren@loren-desktop:~$dmesg | tail
[   79.822938] EXT4-fs (md0): group descriptors corrupted!
[  192.642565] md: requested-resync of RAID array md0
[  192.642569] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[  192.642573] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for requested-resync.
[  192.642578] md: using 128k window, over a total of 312571136 blocks.
[  192.642789] md: md0: requested-resync done.
[  203.657182] EXT4-fs (md0): ext4_check_descriptors: Block bitmap for group 880 not in group (block 268482810)!
[  203.657189] EXT4-fs (md0): group descriptors corrupted!
[  462.244840] EXT4-fs (md0): ext4_check_descriptors: Block bitmap for group 880 not in group (block 268482810)!
[  462.244847] EXT4-fs (md0): group descriptors corrupted!

```

---

### Post by Cloaky8x on 2010-06-02
The final thing I did was run 

```
fsck /dev/md0
```It scanned for corruption for user group and file counts I believe and I hit y a couple hundred times.

I was really nervous, but the ext4 partition has now mounted after being offline for the last month. I recommend extreme caution and a dd image if anyone has a similar problem to minimize the risk.

Thank you for your 1st step Jeroensum. I am now copying Photos...etc to an External Drive. :)

---

### Post by Jeroensum on 2010-06-04
Np yw :)

---

