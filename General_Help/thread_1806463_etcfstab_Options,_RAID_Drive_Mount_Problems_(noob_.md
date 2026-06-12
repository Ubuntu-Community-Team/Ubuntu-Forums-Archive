---
title: "/etc/fstab Options, RAID Drive Mount Problems (noob question)"
date: 2011-07-17
forum: General Help
---

### Post by tokyo-joe on 2011-07-17
I have setup a 4TB raid10 drive on my Ubuntu 10.10 Maverick system and am trying to mount it. Now, I have two problems in doing this. How can I solve these problems?

1. The raid drive does not accept writing operations (I cannot create folders, files within the drive).

2. Most of times, the system fails to mount the raid10 drive at startup. After skipping automount at startup, manual mounting with the "mount" command works fine.

Here is my system information:

[RAID Configurations]
/dev/sda ----System SSD(120GB)
/dev/md2 ----RAID0(4TB)
  + /dev/md0 ---RAID1(2TB)
  |----/dev/sdb -----Data Storage HDD(2TB)
  |----/dev/sdc -----Data Storage HDD(2TB)
  + /dev/md1 ---RAID1(2TB)
  |----/dev/sdd -----Data Storage HDD(2TB)
  |----/dev/sde -----Data Storage HDD(2TB)

[RAID Stat with proc/mdstat]
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid0 md0[0] md1[1]
      3907028864 blocks 64k chunks
      
md1 : active raid1 sdd[0] sde[1]
      1953514496 blocks [2/2] [UU]
      
md0 : active raid1 sdc[1] sdb[0]
      1953514496 blocks [2/2] [UU]

[/etc/fstab Configuration]
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=11548d46-202e-4e47-87e6-1517dfeb6918 /               ext4    discard,errors=remount-ro 0       1
UUID=15b7045f-1237-4cf9-abcb-e2a6d5a4a81e none            swap    discard,sw              0       0
//192.168.0.11/share /media/terastation smbfs credentials=/root/.smbcredentials,iocharset=utf8,noperm 0 0
//192.168.0.12/share /media/linkstation smbfs credentials=/root/.smbcredentials,iocharset=utf8,noperm 0 0
/dev/md2 /media/raid ext4 defaults 0 0

[Error Log]
After rebooting the system, dmesg tells like this. 
hoobar@Ubuntu:~$ dmesg | tail
[   23.978751] Bluetooth: RFCOMM ver 1.11
[   24.569776] CIFS VFS: Error connecting to socket. Aborting operation
[   24.569781] CIFS VFS: cifs_mount failed w/return code = -101
[   24.625111] CIFS VFS: Error connecting to socket. Aborting operation
[   24.625116] CIFS VFS: cifs_mount failed w/return code = -101
[   24.929121] EXT4-fs (sda1): re-mounted. Opts: discard,errors=remount-ro,commit=0
[   26.248189] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[   26.248345] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   26.316563] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   74.797499] lo: Disabled Privacy Extensions

[Other Information]
-I have set drive types of four HDDs as fd (RAID drives) with the fdisk command.
-I have formatted md0, md1, md2 drives with ext4 file system.

Thanks in advance.

---

### Post by JaizEdelmann on 2011-07-17
-

---

### Post by tokyo-joe on 2011-07-17
Here is a follow-up. Adding the following option to /etc/fstab did not work.
  errors=remount-ro

---

### Post by tokyo-joe on 2011-07-19
I finally found a workaround.

After formatting the newly created raid10 drive, run this.
# sudo update-grub

And run this after setting up /etc/mdadm/mdadm.conf.
# sudo update-initramfs -u

I don't know much about the linux boot-up process, but it seems you need to include mdadm.conf information in initramfs.
[http://www.linuxquestions.org/questions/linux-hardware-18/sotware-raid-dont-forget-to-update-your-initramfs-757144/](http://www.linuxquestions.org/questions/linux-hardware-18/sotware-raid-dont-forget-to-update-your-initramfs-757144/)
[http://en.gentoo-wiki.com/wiki/Initramfs#Software_RAID](http://en.gentoo-wiki.com/wiki/Initramfs#Software_RAID)

I appreciate if any expert explain why and how this workaround worked.

---

