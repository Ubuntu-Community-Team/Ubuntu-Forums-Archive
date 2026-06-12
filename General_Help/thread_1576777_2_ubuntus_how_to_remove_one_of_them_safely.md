---
title: "2 ubuntus how to remove one of them safely"
date: 2010-09-17
forum: General Help
---

### Post by wwe9112 on 2010-09-17
So I have ubuntu installed to a external hard drive, and i have it installed to a internal -- main -- hard drive.  How do I safely remove one of them (external hard drive) from my computer safely?  They are set as a duel boot. 

thank you.

---

### Post by drs305 on 2010-09-17
Do you know which one your Grub is installed on?  If not, run:
```
mount
```
Your working partition should look something like this:
> /dev/sda1 on /mnt/lucid type ext4 (rw,nosuid,nodev,commit=0)

Look for the one with **/**

If the device is your main system (for example, sda1 or sda5 is /), then you just have to make sure grub is installed in the sda MBR. You can run this to make sure:
```
sudo grub-install /dev/sda
sudo update-grub
```

You will also want to remove any references to the external drive which you've placed in fstab:
```
gksudo gedit /etc/fstab
```
Place a # symbol at any partition on the external drive. If you aren't sure what the UUIDs are you can run:
```
sudo blkid
```
Save the file. 

You can check to see if things in fstab are correct by running these commands after closing your apps, unmounting and disconnecting your external drive:
```
sudo umount -a  # Note you will get "busy" messages for your system partition.
sudo mount -a
```
After the second command, you should get no errors, which means fstab doesn't contain any automatic mounting instructions for your external.

That should be all you need to do, as Grub2 will be installed on sda and it should boot with the external disconnected.

If you still aren't sure how your Grub is set up, run this script and post the results:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by wwe9112 on 2010-09-17
after i run mount i get this 

> brandon@brandon-desktop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/brandon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=brandon)
/dev/sdb1 on /media/a6088f09-b00c-45d0-94ad-677d8d0de11b type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd1 on /media/New Volume type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
brandon@brandon-desktop:~$ 



I dont see the one you had told me.

---

### Post by drs305 on 2010-09-17
> **wwe9112 said:**
> after i run mount i get this 

> **/dev/sda1 on / **type ext4 (rw,errors=remount-ro)

I dont see the one you had told me.

That's the one.  It says your current Ubuntu is running on sda1, which is your main system.

This one is your external drive:
> /dev/sdb1 on /media/a6088f09-b00c-45d0-94ad-677d8d0de11b type ext4 (rw,nosuid,nodev,uhelper=udisks)

You can unmount the external (/media/a6088...) and your system should still work normally.

---

### Post by wwe9112 on 2010-09-17
im mixed up at

[HTML]gksudo gedit /etc/fstab[/HTML]

sorry thanx

---

### Post by drs305 on 2010-09-17
> **wwe9112 said:**
> im mixed up at

[HTML]gksudo gedit /etc/fstab[/HTML]

sorry thanx

Open a terminal (Applications, Accessories, Terminal).

Running that command will ask you for your password. As you type, you won't see it but that's ok. Just type it and ENTER.

It will open your fstab file, where you are looking to make sure no partitions from "/dev/sdb" are listed. Instead of "/dev/sdb", they may be listed by their UUIDs. If you have any entries that start with:
> UUID=a6088f09-b00c-45d0-94ad-677d8d0de11b . . .
Then place a comment in front of it like this:
> # UUID=a6088f09-b00c-45d0-94ad-677d8d0de11b ...
You do this so Ubuntu doesn't try to automatically mount a device/partition that may not be connected, which would give you an error.

---

### Post by wwe9112 on 2010-09-17
[HTML]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=8182ac44-ab82-4c95-a8bf-54c3e70cbed0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d816fabd-4289-4ecf-af06-20689057b6d0 none            swap    sw              0       0[/HTML]

which one would i place it on?  Where would I save it at.

---

### Post by wwe9112 on 2010-09-17
I did what you said I figured it out but when I reboot i still get that menu to pick between the linuxes.

---

### Post by drs305 on 2010-09-17
> **wwe9112 said:**
> which one would i place it on?  Where would I save it at.

It only references your current partitions, so it is good. You can close it without any changes.

---

### Post by drs305 on 2010-09-17
> **drs305 said:**
> It only references your current partitions, so it is good. You can close it without any changes.

With the external disconnected, run:
```
sudo update-grub
```
You can then run this command to see what items you will have in your menu when you reboot:
```

grep 'menuentry' /boot/grub/grub.cfg

```

You may see recovery modes or different kernels but should not see any Ubuntu installs from the other partition.

---

### Post by wwe9112 on 2010-09-17
[HTML]menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb1)" {
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb1)" {
[/HTML]

This is what I get with that last command.

---

### Post by drs305 on 2010-09-17
Did you disconnect the external drive and run "update-grub"? It still shows your sdb install. The system will boot fine with your current configuration assuming your default OS setting in /etc/default/grub is:
> GRUB_DEFAULT=0

Since you don't have any other installs, you can eliminate the search for other partitions by adding a line to one of the grub configuration files or make the searcher not run by deactivating the os-prober script. To do this, run the following command, then update grub. The first command will remove the executable bit from os-prober so it won't add any extra installations.
```
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
grep 'menuentry' /boot/grub/grub.cfg

```

---

### Post by wwe9112 on 2010-09-17
Yeah I disconnected it but it wont stop showing it and i ran what you said...   IDK, maybe ill just leave it how it is

---

