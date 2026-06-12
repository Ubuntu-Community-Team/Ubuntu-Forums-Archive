---
title: "creating Hiren's BootCD 15.1 in ubuntu 12.04"
date: 2012-10-01
forum: General Help
---

### Post by ame82 on 2012-10-01
i was trying to create hbcd using terminal commands in ubuntu 12.04 iam including the steps may be it would be usfull for any one , i got stuck at installing the bootloader mbr 
ubuntu 12.04 doesn't allow this command 
dd if=/usr/share/syslinux/mbr.bin of=/dev/sdx  
so anyone know how to finish this botable drive?
i also used unetbootin which let creat bootable drive of an iso  and the drive didnt boot 
 the method  steps
==============================================================
Linux Method
&#8226; Insert Hiren&#8217;s Restored BootCD, boot the computer from it and select Parted Magic Linux
(the Linux option of the main menu).
&#8226; Insert a 2 Gb (or larger) USB stick.1 Warning: All data on the USB stick will be erased.
&#8226; Open a console window (e.g. LXTerminal) and type the following commands exactly as they appear in the list bellow after you replace the xx&#8217;s with what is appropriate for your USB flash drive e.g. sdb1 or sdc1.2 Warning: If you get xx wrong you may erase your hard disk.

umount /dev/sdxx                            unount it first.
mkfs.vfat -F32 -n HBCD /dev/sdxx            Format the stick.
mkdir /mnt/cdrom                      Create a CD mountpoint.
mount /dev/sdxx /mnt/usb              Mount the stick.
mount /dev/sr0 /mnt/cdrom             Mount the CD.
cp -Rfv /mnt/cdrom/* /mnt/usb/        Copy files to the stick,
                                      and wait for some time...
syslinux -i -d isolinux /dev/sdxx     Install the bootloader.
dd if=/usr/share/syslinux/mbr.bin of=/dev/sdx                                        Install the bootloader&#8217;s MBR.  
parted /dev/sdx set 1 boot on Make the stick active, i.e. bootable.
sync Flush any pending buffered data.
&#8226; Note: In the last two commands before sync, sdx must be a device e.g., sdb or sdc, and
not a partition sdb1 or sdc1.
&#8226; Reboot the computer and test the stick for booting.
================================================================

---

### Post by Stonecold1995 on 2012-10-01
This:
```
dd if=/usr/share/syslinux/mbr.bin of=/dev/sdx 
```
Is just a sample command.  By "sdx" it means the location of your USB drive, for example it may be /dev/sdb or /dev/sdc (but be very careful, because if you specify the wrong drive you can render your OS unbootable.  For example, /dev/sda probably contains your main OS).

You'll also probably have to run that command as root.  To do that, you put "sudo" before the command, for example (if your external drive is /dev/sdb), you'd do this:
```
sudo dd if=/usr/share/syslinux/mbr.bin of=/dev/sdb
```

---

### Post by ame82 on 2012-10-02
> **Stonecold1995 said:**
> This:
```
dd if=/usr/share/syslinux/mbr.bin of=/dev/sdx 
```
Is just a sample command.  By "sdx" it means the location of your USB drive, for example it may be /dev/sdb or /dev/sdc (but be very careful, because if you specify the wrong drive you can render your OS unbootable.  For example, /dev/sda probably contains your main OS).

You'll also probably have to run that command as root.  To do that, you put "sudo" before the command, for example (if your external drive is /dev/sdb), you'd do this:
```
sudo dd if=/usr/share/syslinux/mbr.bin of=/dev/sdb
```

thanks for responding, but with my respect everything u mentioned is what i know but what i dont u didnt talk about, why that command doesnt work on ubuntu 12.04 and how can i make it work or any alternative to get my hbcd boots and works????

---

### Post by Stonecold1995 on 2012-10-02
> **ame82 said:**
> thanks for responding, but with my respect everything u mentioned is what i know but what i dont u didnt talk about, why that command doesnt work on ubuntu 12.04 and how can i make it work or any alternative to get my hbcd boots and works????

What is the output of this?
```
file /usr/share/syslinux/mbr.bin
```

And what do you mean the command didn't work?  Did it give you any error messages?

---

### Post by ame82 on 2012-10-02
> **Stonecold1995 said:**
> What is the output of this?
```
file /usr/share/syslinux/mbr.bin
```

And what do you mean the command didn't work?  Did it give you any error messages?
here is the output 
ahmed@N411Z:~$ sudo parted /dev/sdc1 set 1 boot on 
[sudo] password for ahmed: 
Error: The flag 'boot' is not available for loop disk labels.             
ahmed@N411Z:~$ file /usr/share/syslinux/mbr.bin
/usr/share/syslinux/mbr.bin: ERROR: cannot open `/usr/share/syslinux/mbr.bin' (No such file or directory)



as i said systemlinux is installed in my computer and its ok, but it works diffrent than it used to be in other versions
still have my hbcd not booting

---

### Post by Stonecold1995 on 2012-10-02
> **ame82 said:**
> here is the output 
ahmed@N411Z:~$ sudo parted /dev/sdc1 set 1 boot on 
[sudo] password for ahmed: 
Error: The flag 'boot' is not available for loop disk labels.             
ahmed@N411Z:~$ file /usr/share/syslinux/mbr.bin
/usr/share/syslinux/mbr.bin: ERROR: cannot open `/usr/share/syslinux/mbr.bin' (No such file or directory)



as i said systemlinux is installed in my computer and its ok, but it works diffrent than it used to be in other versions
still have my hbcd not booting

You don't have "/usr/share/syslinux/mbr.bin", which means using dd won't work.  Do you have the file anywhere, because you'll need syslinux.

Look under "/usr/lib/syslinux/mbr.bin".  Is mbr.bin there?

Tip: If you know something's installed but you don't know where, you can use the "locate" command:
```
alex@kubuntu:~$ locate mbr.bin
/usr/lib/syslinux/altmbr.bin
/usr/lib/syslinux/gptmbr.bin
/usr/lib/syslinux/mbr.bin
/usr/lib/syslinux-legacy/mbr.bin
```

---

### Post by ame82 on 2012-10-03
> **Stonecold1995 said:**
> You don't have "/usr/share/syslinux/mbr.bin", which means using dd won't work.  Do you have the file anywhere, because you'll need syslinux.

Look under "/usr/lib/syslinux/mbr.bin".  Is mbr.bin there?

Tip: If you know something's installed but you don't know where, you can use the "locate" command:
```
alex@kubuntu:~$ locate mbr.bin
/usr/lib/syslinux/altmbr.bin
/usr/lib/syslinux/gptmbr.bin
/usr/lib/syslinux/mbr.bin
/usr/lib/syslinux-legacy/mbr.bin
```

yes i do same like ur layout exactly , so what next should i copy it to where it should be?

---

### Post by Stonecold1995 on 2012-10-03
I suppose you'd do this:
```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdx
```

---

### Post by ame82 on 2012-10-03
thanks alot , i will try it today , to i did it using multisystem , 1st time didnt work but i think after i reboot and reformat my pendrive it worked , it loaded grub2dos and the hbcd was one of the choises , i will try this which is the original way and see the diffrent then i will post it here , thanks alot

---

