---
title: "Help me recover grub with an encrypted volume on sda5?"
date: 2012-02-11
forum: General Help
---

### Post by volkerbradley on 2012-02-11
I've read all the posts that I can find but cannot seem to reinstall grub. I have Ubuntu 11.10, 64-bit on my hard drive.
When I try to boot my system I see the following error: unknown filesystem, grub rescue.
I then booted with Ubuntu live CD and gave the following commands: Some of the important output is in parentheses.
sudo su
mkdir /mnt/system
apt-get install lvm2 cryptsetup
modprobe dm-crypt
cryptsetup luksOpen /dev/sda5 encrypted-volume
vgscan
vgchange -ay
(2 logical volume(s) in volume group "volker-laptop" now active)
sudo lvscan
  (ACTIVE            '/dev/volker-laptop/root' [140.82 GiB] inherit
  ACTIVE            '/dev/volker-laptop/swap_1' [7.99 GiB] inherit)
ls /dev/mapper
(control  encrypted-volume  volker--laptop-root  volker--laptop-swap_1)
sudo mount /dev/mapper/volker--laptop-root /mnt/system/
mount -o bind /dev/ /mnt/system/dev/
mount -o bind /proc/ /mnt/system/proc/
chroot /mnt/system
grub-install /dev/sda
(/usr/sbin/grub-probe: error: no such disk.
Auto-detection of a filesystem of /dev/mapper/volker--laptop-root failed.
If the problem persists please report this together with the output of "/usr/sbin/grub-probe --device-map="/boot/grub/device.map" --target=fs -v /boot/grub" to <bug-grub@gnu.org>)
/usr/sbin/grub-probe --device-map="/boot/grub/device.map" --target=fs -v /boot/grub
(/usr/sbin/grub-probe: info: changing current directory to /dev/mapper.
/usr/sbin/grub-probe: info: opening volker-laptop-root.
/usr/sbin/grub-probe: error: no such disk.)

Can you give me some suggestions?

---

### Post by volkerbradley on 2012-02-14
Solved my problem by doing the following:
While I had the encrypted sda5 on my hard drive which I could no longer visualize because the system would not boot, I used Clonezilla to make an image of this partition.
Then reinstalled an image of my entire hard drive contents that I had made in November. I could then boot the computer and see the contents of the encrypted sda5 as it was in November.
Using Clonezilla I then resinstalled the recent image of sda5.
Now the computer boots perfectly and the contents of sda5 as it was a few days ago is avaible to me again.

---

