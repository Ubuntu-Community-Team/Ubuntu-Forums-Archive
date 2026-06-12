---
title: "Xubuntu boot blues (it just hangs with a flashing &quot;_&quot;!)"
date: 2010-05-09
forum: General Help
---

### Post by d3drocks on 2010-05-09
im gunna sum up some stuff I posted in #ubuntu on freenode

> anyone know how to help me? I've got a fresh install of Xubuntu that hangs after grub. i am using the default kernel "2.6.32-21-generic" on xubuntu 10.04. when I select this option, all that appears is a flashing underscore, and it sits there untill I hard reboot. I know its doing nothing, because the hard disk spins down, and absolutely nothing happens.I havnt had this issue with with any other editions of ubuntu, and the system is not duel booted (xubuntu is the only one on there)
thats pretty much the issue. this happens with standard ubuntu 10.04 as well. I've tried from CDs, and Live USBs with the same result. tried different ISO mirrors with the same result. I have had a working install of 9.10 on that machine, but I wanted to move to an LTS edition so I could stay on it a while. I have no idea what I should do, because my ideas have run completely dry. I have reinstalled 8 or 9 times trying various things. I've redone the partition tables of the disk myself, the "recovery mode" kernel isnt working, and the only thing that sucessfully boots is the memory test.
I'de greatly appreciate any help or ideas, as I am completely dry of what to do.

EDIT: forgot to mention that live mode works perfictly.

---

### Post by d3drocks on 2010-05-10
bumping to avoid second page. I really need help here. my system will boot up the odd time, but should I reboot, its back to the usual. I've tried booting without "quiet splash"
the last line it puts out before completely hanging up on me is "[2.295266] ata4: DUMMY"

---

### Post by zach.detton on 2010-05-10
What you could try doing is booting off a Live CD and chrooting into your system. Once you're root on the HDD, you can run check for updates, there may be an update that will fix it.

---

### Post by d3drocks on 2010-05-10
> **zach.detton said:**
> What you could try doing is booting off a Live CD and chrooting into your system. Once you're root on the HDD, you can run check for updates, there may be an update that will fix it.

how would I go about doing this? ive never done something like that before.
thanks

---

### Post by d3drocks on 2010-05-10
bump

---

### Post by d3drocks on 2010-05-10
...no one has any idea? the system completely locks up when the flashing underscore happens. not even the capslock/scroll lock lights flash when I press their buttons.

---

### Post by zach.detton on 2010-05-10
Well you start by booting off a Live CD :-p. Once it's booted you would open a terminal and do:

```
sudo mount /dev/sdx /mnt
```

Replace "X" with the number of your root partition. Then you would do:

```
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
```

Now you are chrooted into your system and you don't need to use "sudo" here so next you'll just do:

```
apt-get update
apt-get upgrade
```

You may also want to re-update your GRUB config and run

```
update-grub2
grub-install /dev/sda
```

Once the updates are complete you'll do:

```
exit
sudo umount /mnt/dev
sudo umount /mnt
```

After exiting the root system and unmounting you can then try booting off your HDD.

---

### Post by d3drocks on 2010-05-10
> **zach.detton said:**
> Well you start by booting off a Live CD :-p. Once it's booted you would open a terminal and do:

```
sudo mount /dev/sdx /mnt
```

Replace "X" with the number of your root partition. Then you would do:

```
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
```

Now you are chrooted into your system and you don't need to use "sudo" here so next you'll just do:

```
apt-get update
apt-get upgrade
```

You may also want to re-update your GRUB config and run

```
update-grub2
grub-install /dev/sda
```

Once the updates are complete you'll do:

```
exit
sudo umount /mnt/dev
sudo umount /mnt
```

After exiting the root system and unmounting you can then try booting off your HDD.

thanks for the help, but I'm still in the same boat. its still not booting. I booted off of a live USB and did your suggestions with no effect

---

### Post by jkhiebert on 2010-05-24
Make sure that extra ram is out of the computer and only your HDD that you want the OS on is plugged in. This fixed it for me.

---

