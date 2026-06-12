---
title: "Replacing broken boot partition"
date: 2012-09-26
forum: General Help
---

### Post by paddyjoy on 2012-09-26
Hi,

Would appreciate any help with this issue, not sure how to proceed.

Today I physically smashed my boot partition (it was on a usb key). 

Some more info:

Primary hard drive is configured like this:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   215050239   107525088+   7  HPFS/NTFS/exFAT
/dev/sda2       215050240   625142447   205046104    5  Extended
/dev/sda5       215052288   625142447   205045080   83  Linux

inside /dev/sda5 I have an encrypted volume
Disk /dev/mapper/sda5_crypt: 210.0 GB, 209965109248 bytes

I installed the boot partition on a usb drive /dev/sdc1

Set up works like this.
If laptop is turned on without usb inserted it boots into windows.
If laptop is turned on with usb inserted, ubuntu boots, ask for passphrase then boots

I have been using this set up for months and haven't had any problems until today my laptop fell and the usb key snapped in half. The circuit board inside it is broken so there is no hope of recovery.

My laptop is currently on and running but as soon as I switch it off I won't be able to boot into ubuntu anymore.

Does anyone know if there is a way I can rebuild a boot partition on a new usb key so I will be able to get back into the system after a shutdown? I'm concerned that even though I know the passphrase for my encrypted partition that the actual 128bit key was on the usb key and now lost?

Thanks

---

### Post by oldfred on 2012-09-26
It does not sound like a boot partition but just grub installed to the MBR of the flash drive. But I do not know encryption so you may have had the full /boot partition on the USB partition.

You need your new flash drive.

If just grub you can reinstall grub to the flash drive:

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub


But if you have /boot on external flash then you also need the /boot & /boot/grub installed to flash also.

Post this before rebooting. If /boot is in a separate partition it probably was on flash.

cat /etc/fstab
ls -l /dev/disk/by-uuid/

[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)

---

### Post by paddyjoy on 2012-09-26
Thanks for the reply.

The full boot partition was on the usb stick, not just the mbr.

I have taken the following steps.

1) Insert new usb, format and mount as /boot
2) Reinstalled grub and check

New usb has /boot and /boot/grub now so I'm feeling semi confident about reboot.

The only issue I can see is that in the new grb.cfg there is no reference to the fact that the root partition is encrypted so I need to research this some more before I take the plunge. I thought there should be something in there that loads a crpyt module or similar.

```
menuentry 'Ubuntu, with Linux 3.2.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root e86700a3-0511-472f-9375-0d7a0ed4fd9e
    linux    /vmlinuz-3.2.0-30-generic root=/dev/mapper/vg-root ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-30-generic
}
```cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdc1 during installation
UUID=7e26d0f6-0c02-46e9-870a-873196e62436 /boot           ext2    defaults        0       2
/dev/mapper/vg-swap none            swap    sw              0       0
```ls -l /dev/disk/by-uuid/
```
lrwxrwxrwx 1 root root 10 Sep 25 10:39 186e249c-3546-4369-909b-d985a21f0e04 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Sep 26 19:10 6825-1DFE -> ../../sdc2
lrwxrwxrwx 1 root root 10 Sep 25 10:39 88A0836DA0836114 -> ../../sda1
lrwxrwxrwx 1 root root 10 Sep 25 10:39 d2ea4ac3-cb1e-4cb3-9008-cdc63893222e -> ../../dm-2
lrwxrwxrwx 1 root root 10 Sep 26 19:10 e86700a3-0511-472f-9375-0d7a0ed4fd9e -> ../../sdc1
lrwxrwxrwx 1 root root 10 Sep 25 10:39 f94a77f8-9223-4411-97b6-5884bed021f3 -> ../../sda5
```

---

### Post by oldfred on 2012-09-26
I do not use encryption.

The mapper shows something. I know when swap is mounted with the mapper gparted cannot see it and that is usually because swap is encrypted.

Is UUID for (hd1, 1) the new partition ? It looks like it is, but if you changed without rebooting it may not be?

set root='(hd1,msdos1)'     search --no-floppy --fs-uuid --set=root e86700a3-0511-472f-9375-0d7a0ed4fd9e

lrwxrwxrwx 1 root root 10 Sep 26 19:10 e86700a3-0511-472f-9375-0d7a0ed4fd9e -> ../../sdc1

# To clear cache and get new view:
sudo blkid -c /dev/null -o list

---

### Post by paddyjoy on 2012-09-27
Thanks yes /dev/sdc1 is the new boot partition.

```
device                                         fs_type         label            mount point                                        UUID
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                                      ntfs                             (not mounted)                                      88A0836DA0836114
/dev/sda5                                      crypto_LUKS                      (in use)                                           f94a77f8-9223-4411-97b6-5884bed021f3
/dev/mapper/sda5_crypt                         LVM2_member                      (in use)                                           yt5V1h-HUeU-2CAm-bal0-qZ92-R0Pr-uceh1H
/dev/mapper/vg-root                            ext4                             /                                                  186e249c-3546-4369-909b-d985a21f0e04
/dev/mapper/vg-swap                            swap                             <swap>                                             d2ea4ac3-cb1e-4cb3-9008-cdc63893222e
/dev/sdc1                                      ext4            boot             /boot                                              e86700a3-0511-472f-9375-0d7a0ed4fd9e
/dev/sdc2                                      vfat            files            (not mounted)                                      6825-1DFE                                    

```

---

### Post by paddyjoy on 2012-09-27
Thanks for the help oldfred, rebooted today and all is good. Had to modify the UUID in /etc/fstab as /boot failed to mount but that was an easy fix.

:D

---

### Post by oldfred on 2012-09-27
Glad you have it sorted out.

I thought I saw some mis-match on UUIDs, but missed it when I posted. It was the fstab /boot UUID was different as you found out.

---

