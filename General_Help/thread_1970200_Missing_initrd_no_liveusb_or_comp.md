---
title: "Missing initrd no liveusb or comp"
date: 2012-04-30
forum: General Help
---

### Post by Alexcunn on 2012-04-30
Hi i have had a major problem. My entire boot folder is erased and i am stuck in initramfs is there commands that i can use to make a new initrd or can i act as the initrd file somehow. Remember I have limited commands i only have the basic such as mkdir cat mktemp cp pwd set du chroot chmod and a few others. 
I have very little access i bet i could use commands to open up programs. I dont know anything about these programs. I do know about the boot proccess as far as the kernel and grub but i do not know anything else like what initrd says to do. Please help.

---

### Post by bodhi.zazen on 2012-04-30
boot a live CD, mount your root file system and if necessary boot partition in a chroot, and re-install the kernel.

Assuming you are now running a live CD, and your ubuntu root partition is /dev/sda, and you do not have a separate boot partition ...

```
sudo mount /dev/sda1 /mnt
sudo cp /etc/resolv.conf /mnt/etc/
```

Depending on your configuration, you may also need to copy the hosts file

```
 sudo cp /etc/hosts /mnt/etc/

sudo mount --bind /dev/ /mnt/dev
sudo chroot /mnt
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devpts none /dev/pts
```

To avoid locale issues and in order to import GPG keys

```
export HOME=/root
export LC_ALL=C
```

Restore grub

```
grub-install /dev/sda
```

Reinstall the kernel

```
apt-get install --reinstall linux-gnereic
```

Should automatically update /boot and grub.

You should then be able to reboot.

---

