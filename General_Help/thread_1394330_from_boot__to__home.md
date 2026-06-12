---
title: "from /boot  to  /home"
date: 2010-01-30
forum: General Help
---

### Post by kazN on 2010-01-30
hi guys, i made 1 mistake while i was installing ubuntu9.10. I made 20gb partition for root  and 300gb partition with /boot, but this one partition must be /home (to keep files there).
So, how i can change mount point?

P.s. sorry for me crappy English language.

---

### Post by falconindy on 2010-01-30
Assuming that your disk looks something like this:
```
/dev/sda1        80gb        /
/dev/sda2        300gb       /boot
```
Then you'll need to do the following:

1) Boot off the liveCD, and mount both partitions, say at /mnt/root and /mnt/boot
2) mv /mnt/boot /mnt/root/ # (this puts the boot directory in the "proper" place)
3) mv /mnt/root/home/* /mnt/boot/ # (move folders within home to the "proper" place)
4) Update your /etc/fstab: change the line that mounts boot to mount home instead. You should just be able to change /boot to /home in the entry.

When this is all done, do the following:
```
umount /mnt/{boot,root}
mount /dev/sda1 /mnt
mount /dev/sda2 /mnt/home
```
And look around in boot and home to make sure that everything is in the right place.

At this point you need to reinstall grub -- this is the tricky part and probably better explained by someone more familiar with Grub2 than I am (I still use grub-legacy out of loathing for grub2). If it were me, I'd do something like this:
```
# Make a proper chroot and enter it
for tmpfs in dev sys proc; mount -o bind /$tmpfs /mnt/$tmpfs; done
cd /; chroot /mnt /bin/bash

# Reinstall Grub
grub-install --recheck /dev/sda

# Disassemble the chroot
logout
umount /mnt/{sys,proc,dev,home,}
```
This seems like a fair bit of work, and might be a little intimidating if you don't understand some of it. If you **just** finished installing, it might be easier to reinstall. Then again, you might take the opportunity to learn a bit...

---

### Post by Leppie on 2010-01-30
hi and welcome to the community,

- unmount the /boot parition
- create a folder /boot on your root partition:
```
sudo mkdir /boot
```
- mount the /boot partition temporarily:
```
sudo mount /dev/sdXY /mnt ##change sdXY to the boot partition/CODE]
- copy the contents of the /boot parition to your newly created /boot folder:
[CODE]sudo cp -R /mnt/* /boot/
```
- open your fstab and remove the /boot partition entry:
```
gksudo gedit /etc/fstab
```
- regenerate your grub.cfg to tell grub2 to not use the /boot parition anymore:
```
sudo update-grub
```
reboot to see your system boots properly (as at this point things can still be reverted).

- when back in the system, mount the old boot partition temporarily:
```
sudo mount /dev/sdXY /mnt  ##change sdXY to the boot partition
```
- delete contents of the old boot partition:
```
cd /mnt
sudo rm -rf ./
```
- copy contents of the /home folder to the new home partition:
```
sudo cp -r /home/* ./
```
- check the uuid for your new /home partition:
```
sudo blkid
```
- open your fstab:
```
gksudo gedit /etc/fstab
```
- create an entry for your /home partition, use the UUID found with blkid. it could look something like this:
```
UUID=04245038-d146-48cc-aee5-79be1bf32094 /home ext4 defaults 0 2
```
- move the contents of the old /home folder, just in case:
```
sudo mkdir /home/backup
sudo mv -rf /home/ /home/backup/
```
reboot and enjoy the system ;)

---

### Post by oldfred on 2010-01-30
When I was  converting from 9.04 to 9.10 and testing 9.04 64 bit and Karmic beta I added a new drive and created a new /boot. I then decided I did not want that and converted it to /grub only. As I remember (this is oldfred you are dealing with:)) I just copied files over and updated grub in the MBR. Then it was old grub but I am sure new grub should be similar in just reinstalling so it knows where to find the boot/grub files. I think I had to modify fstab also.

You should be able to do this all while in your system, but if you do not copy everything correctly or put grub into the MBR you then will not be able to boot. I would have a working liveCD handy just in case.

Make sure both /boot and /boot/grub are copied to root.

reinstall from working system - first find Ubuntu drive: 
sudo fdisk -l 
if it's "/dev/sda"  then just run: 
sudo grub-install /dev/sda 
If that returns any errors run: 
sudo grub-install --recheck /dev/sda 
Then: 
sudo update-grub

To move home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

But I still have several installs and want my data preserved on clean new installs. I also created a separate /home and /data for all my data. Now my home is only 1GB with 3 years of history in some files. All my data is linked into /home.

[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

It may be easier to link in data than move home. My home is now small enough to easily backup for a new install, although I have now gone to two partitions for installs and will alternate every 6 months and just copy /home over and relink data.

---

