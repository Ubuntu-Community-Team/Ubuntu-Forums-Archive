---
title: "After kernel update GRUB will not boot Windows 7"
date: 2012-09-20
forum: General Help
---

### Post by shiajun on 2012-09-20
I've been searching the forums but honestly I get a little confused with knowing if my problem is identical to those reported or not. To avoid confusion for me  I decided to make a new thread.

I've got a Dell XPS 17, and I'm dual booting 12.04 and Win 7 on two different hard drives. After a routine update from the software center it installed kernel 3.2.0.30 (before it was 3.2.0.29) and linux.firmware, along with another small 49 updates. I restarted. When it came to the grub menu to choose OS, Windows 7 was no longer on the list. 

I tried running update-grub from a terminal and get the following output:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
grub-probe: error: cannot find a GRUB drive for /dev/sda1.  Check your device.map.
done

```
Also, when checking device.map on /boot/grub/device.map, the file is empty.

A little history might help understand this.Originally the computer only had one hard drive with  Dell's Windows 7 installation on it, meaning some small 100 Mb partition (sda1), then the recovery paritition (sda2), then the windows proper (sda3). At one moment I decided to make a partition and install Ubuntu unto it (it as 11.04). Everything went fine but evidently GRUB nuked Dell's MBR on that disk and, because of my inexperience, I had not backed it up. 

Eventually I got a second hard drive and installed Ubuntu on that one and returned the original hard drive to factory state, but without Dell's MBR obviously. It didn't matter because I booted from the linux Hard drive. That worked out perfectly fine for a while.

I recently upgraded to Ubuntu 12.04 with a fresh install after reading that direct upgrades didn't work out quite well everytime. I had no problem at all and the dual boot still worked as usual. Now, after the recent update, GRUB no longer sees where to boot from on the WIndows 7 hard drive, apparently. I finally got a windows 7 professional legit copy (Dell only supplies its recovery image with the computer, for free) through an agreement with my university with Microsoft . I'm planning on formatting the windows 7 hard drive and doing a clean install of that OS, so I'll finally have two independent OS each on its own hard drive. Right now I only need to regain access to windows 7 to backup all the info I require before the format.

Any help on how to regain booting into windows 7 is greatly appreciated.

---

### Post by Bucky Ball on 2012-09-20
If you want to drag stuff off the Windows drive why not just mount it while booted into Ubuntu? Is Win drive not in the left pane of Nautilus (the file manager)? It may be called '150Gb' or something dumb. Click, it should mount.

If this is not the case, open a terminal (Applications>Accessories>Terminal) and copy/paste this:

```
sudo blkid
```... and post the output back here, please. We should then be able to mount it manually. ;)

PS: Code tags by editing the post then clicking 'Go Advanced' and using the # icon. Or you can type them in by using [code] tags. I generally put my code in [quote] tags by using the quotation icon then change 'quote' in the tags to 'code' or just type them in from scratch. Cumbersome ...

---

### Post by shiajun on 2012-09-20
I can easily copy files by mounting the Win7 hard drive. It's program configurations I want to backup as well (like Steam savefiles and game installations) and those I have to access directly from the applications, since sometimes they're stored in several folders that only the program knows how to handle.

---

### Post by Bucky Ball on 2012-09-20
Can you copy the folders containing the config files and  then drop them back into a Win install later?

---

### Post by oldfred on 2012-09-20
Grub remembers where to reinstall on major updates. Perhaps that was not correct & it updated to the Windows partition corrupting it? Then we may be able to repair the Windows partition.

To see where everything is at, but this will not fix Windows:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Do you have a Windows repairCD?

To see if grub is reinstalling to the wrong place:
#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

---

### Post by shiajun on 2012-09-20
I installed Boot Repair and got a summary, which is in this link:
[http://paste.ubuntu.com/1217204/](http://paste.ubuntu.com/1217204/)

I see that sda1 is set to boot but appears empty. This may be the problem.  I know that the boot files could be in that 100 Mb partition on sda1, but they don't seem to be working. There don't seem to be any boot files there anymore.

The windows 7 version currently installed is home premium. I don't have a repairCD as is for this version, only the recovery image by Dell that I saved to usb stick. The version i got through the university is win 7 professional, and I have burned that to a DVD, which could help in repairing the boot for win7.

I see boot repair has an option to repair windows files, but it states my OS windows Xp, which it is not.

debconf-show gives this output: 
```
grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices: /dev/disk/by-id/ata-ST9500420AS_5VJ380BL
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: true
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 10

```And grub-probe looks for grub in /dev/sdb1, where it should be, since it's the linux hard drive.

---

### Post by oldfred on 2012-09-20
Normally Windows 7 installs to a 100MB boot partition with the two boot files - /bootmgr /Boot/BCD. You have those in sda2. The sda1 is now FAT32 and script is not showing any of the standard boot files, but script only looks for standard files in standard locations. 

Boot flag is normally on the 100MB boot partition which is also hidden. Then the main install is in a large c: "drive" partition. But that partition should show /Windows/System32/winload.exe which script did not find. Is winload.exe some where on your system?

Sometimes all three boot files are in one partition, but that is usually an upgrade from Vista or XP where that was only one NTFS partition or manual installs where the user specified to only install in one partition. I think Boot-Repair now copies boot files from boot to main install just to have a copy.

Grub is set to reinstall to the MBR of this drive, so that is ok:
/dev/disk/by-id/ata-ST9500420AS_5VJ380BL

If totally reinstalling Windows be sure to set BIOS to boot from Windows drive first. Otherwise it may get confused on trying to install the 100MB boot partition on the BIOS boot drive.

Normally only UEFI systems have the first partition as FAT32, your system was not UEFI was it?

---

### Post by shiajun on 2012-09-20
> **oldfred said:**
> Normally Windows 7 installs to a 100MB boot partition with the two boot files - /bootmgr /Boot/BCD. You have those in sda2. The sda1 is now FAT32 and script is not showing any of the standard boot files, but script only looks for standard files in standard locations. 

Boot flag is normally on the 100MB boot partition which is also hidden. Then the main install is in a large c: "drive" partition. But that partition should show /Windows/System32/winload.exe which script did not find. Is winload.exe some where on your system?

Sometimes all three boot files are in one partition, but that is usually an upgrade from Vista or XP where that was only one NTFS partition or manual installs where the user specified to only install in one partition. I think Boot-Repair now copies boot files from boot to main install just to have a copy.

Grub is set to reinstall to the MBR of this drive, so that is ok:
/dev/disk/by-id/ata-ST9500420AS_5VJ380BL

If totally reinstalling Windows be sure to set BIOS to boot from Windows drive first. Otherwise it may get confused on trying to install the 100MB boot partition on the BIOS boot drive.

Normally only UEFI systems have the first partition as FAT32, your system was not UEFI was it?

I see the boot files in sda2. That is supposed to be the recovery partition dell ships with its machines. I don't know if I can access that partition and copy those files and put them on sda1 as well. Also, I don't know why sda1 being FAT32 would be a problem. If I remember right, it has always been FAT32. 

Mounting the win7 drive I get access to the sda3 partition in the file manager. I looked for winload.exe and it's there alright. Thing is, just before updating Ubuntu I was booting just fine into both operating systems so I wouldn't think it's a change in the windows OS, since it wasn't mounted at all at the time.

Also, when doing the complete reinstall of Windows I'll remove the ubuntu drive, just so there's no chance at all of the installation messing up the boot or MBR files there.

---

### Post by shiajun on 2012-09-20
OK...so I fixed it. It was much easier than I thought it would be. All I did was boot from my Gparted Live CD. After choosing several options of keymap and language I finally got to the program. I used the first menu option, selected to view sda hard drive and changed the flags on the sda3 partition to be able to boot. I exited Gaprted and booted back into Ubuntu. There, I ran sudo update-grub and now GRUB was able to find the windows loader, as it should, and all is back to working order.

I'm still going to do the full reinstall because it's just less messy that way. I still have no idea why suddenly the sda3 partition was no longer bootable. One chage I do see is that now the 100 Mb partition shows up in my windows manager and in nautilus, which I means that maybe, maybe, I could put the missing boot files where they belong.

Anyway, I hope this helps someone that stumbles across this.

---

