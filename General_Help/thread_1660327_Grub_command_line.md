---
title: "Grub command line"
date: 2011-01-05
forum: General Help
---

### Post by arunthakurmanali on 2011-01-05
Does anyone know how to login through cmdline in grub.I tried some of codes but failed.codes were-grub>set root=(hd0,8)
                            grub> linux /vmlinuz root=/dev/(sda,8) ro
                              error;no such disk

---

### Post by matt_symes on 2011-01-05
Hi

Have a read of this

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Specifically this section: Command line and rescue mode.

> ls Display the drives/partitions known to GRUB 2.
ls (hdX,Y)/ Display the contents of the / directory of the designated drive/partition.
ls (hdX,Y)/boot Display the contents of the /boot directory. Example: ls (hd0,5)/boot
ls (hdX,Y)/boot/grub Display the contents of the /boot/grub directory. Example: ls(hd0,5)/boot/grub
ls (vg-lv)/ Display the contents of the logical volume /dev/mapper/vg-lv or /dev/vg/lv (same thing). Example (ubuntu-root used as /): ls (ubuntu-root)/

> set root=(hdX,Y)
linux /vmlinuz root=/dev/sdXY ro
initrd /initrd.img
boot

Kind regards

---

### Post by arunthakurmanali on 2011-01-05
> **matt_symes said:**
> Hi

Have a read of this

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Specifically this section: Command line and rescue mode.





Kind regards
I followed the same steps but in vain,i had the same source.

---

### Post by Rubi1200 on 2011-01-05
Are you seeing a grub prompt or a grub rescue prompt? There is a difference.

How did you install Ubuntu, which version, etc.?

We need more information please.

---

### Post by arunthakurmanali on 2011-01-05
> **Rubi1200 said:**
> Are you seeing a grub prompt or a grub rescue prompt? There is a difference.

How did you install Ubuntu, which version, etc.?

We need more information please.
I installed through cdrom ubuntu 10.04(dual boot with win7) with grub 1.98.  As the system boots, at menu list i just pressed c(as suggested)and entered grub prompt.thanks

---

### Post by matt_symes on 2011-01-05
Hi

Start of by typing 

ls

at the grub prompt. This will give you a list of the partitions grub can see.

then for each partition type

ls (hdX,Y)/ where X and Y are the drive and partition. This will help you discover the correct drive partition number to enter.

You are looking for something with vmlinuz and   initrd.img in it. These are symbolic links to your newest kernel and initrd file stored in your /boot directory.

```
matthew@matthew-laptop:~$ ls /
bin    etc             lib         opt   selinux  tools    vmlinuz.old
boot   home            lost+found  proc  srv      usr
cdrom  initrd.img      media       root  sys      var
dev    initrd.img.old  mnt         sbin  tmp      vmlinuz
matthew@matthew-laptop:~$
```

```
lrwxrwxrwx   1 root root    33 2011-01-04 12:50 initrd.img -> boot/initrd.img-2.6.32-27-generic
lrwxrwxrwx   1 root root    30 2011-01-04 12:50 vmlinuz -> boot/vmlinuz-2.6.32-27-generic
```


Rubi1200 is correct. There is a difference between Grub and grib rescue prompts. You were at the grub prompt.

Kind regards

---

### Post by arunthakurmanali on 2011-01-05
> **matt_symes said:**
> Hi

Start of by typing 

ls

at the grub prompt. This will give you a list of the partitions grub can see.

then for each partition type

ls (hdX,Y)/ where X and Y are the drive and partition. This will help you discover the correct drive partition number to enter.

You are looking for something with vmlinuz and   initrd.img in it. These are symbolic links to your newest kernel and initrd file stored in your /boot directory.

```
matthew@matthew-laptop:~$ ls /
bin    etc             lib         opt   selinux  tools    vmlinuz.old
boot   home            lost+found  proc  srv      usr
cdrom  initrd.img      media       root  sys      var
dev    initrd.img.old  mnt         sbin  tmp      vmlinuz
matthew@matthew-laptop:~$
``````
lrwxrwxrwx   1 root root    33 2011-01-04 12:50 initrd.img -> boot/initrd.img-2.6.32-27-generic
lrwxrwxrwx   1 root root    30 2011-01-04 12:50 vmlinuz -> boot/vmlinuz-2.6.32-27-generic
```
Rubi1200 is correct. There is a difference between Grub and grib rescue prompts. You were at the grub prompt.

Kind regards
Thank you Matt_symes for your support.I'll try the given commands.

---

