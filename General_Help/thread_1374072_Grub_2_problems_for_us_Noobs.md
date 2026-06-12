---
title: "Grub 2 problems for us Noobs"
date: 2010-01-06
forum: General Help
---

### Post by Syirrus on 2010-01-06
I recently upgrade my computer to a Core i7 1366.  Excited, I installed Ubuntu 9.10 AMD64 all to reboot and find that it wouldn't boot. I was using one 500gb drive SATA only for Ubuntu.  I tried configuring my CMOS for ACHI IDE and RAID without success :(.  I search and search until I found a solution that worked for me:

Source: [Fixing grub]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html")

STEPS copied from the above source with some extras:

1. Boot off of your Ubuntu or Kubuntu CD and while booting select "Try Ubuntu without any change to your computer."

2. Install Ubuntu or Kubuntu as normal.  At the end (last step) make sure you have Ubuntu install Grub.

3. When the installation is complete, DO NOT REBOOT.  Instead select, "Continue to try or use Ubuntu Live" (can't remember the exact message).

4. Perform the steps listed below:

```

sudo fdisk -l

```

This will show your partition table.Here is my table to understand it better :

/dev/sda1 29 8369 66999082+ 83 Linux
/dev/sda2 * 8370 13995 45190845 7 HPFS/NTFS
/dev/sda3 13996 14593 4803435 5 Extended
/dev/sda5 13996 14593 4803403+ 82 Linux swap / Solaris

Now i will mount Linux (sda1 here), i have no external boot partition as you can see.(IF YOU HAVE external one, do not forget to mount it! )

```

sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc

```

The following command is optional (it copies resolv.conf)

```

sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

```

Now chroot into the environment we made :

```

sudo chroot /mnt

```

After chrooting, you do not need to add sudo before your commands because from now, you will run commands as root.

OPTIONAL: You may want to edit /etc/default/grub file to fit your system (timeout options etc)

```

nano -w /etc/default/grub

```

Play with the options if you want.(But do not forget to give grub-update command if you saved it ;) )

Now install/recover Grub2 via :

```

grub-install /dev/sda

```

command.However you may get errors with that code like me.If so please use this command :

```

grub-install --recheck /dev/sda

```

Now you can exit the chroot, umount the system and reboot your box :

```

exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
sudo reboot

```

---

