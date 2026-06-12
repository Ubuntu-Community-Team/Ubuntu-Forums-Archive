---
title: "Grub OS boot problem"
date: 2012-03-04
forum: General Help
---

### Post by Rahul Jain on 2012-03-04
Hi,
I have UBUNTU 11.04 and windows7 in my lappy
yesterday i installed Redhat 5.1
Now the grub menu i have is of REDHAT and therefore it only allows me to boot either from RHEL or windows. I have two questions :

1) How can I edit the grub.conf file so that it will allow me to boot UBUNTU as well

2) What should I do to get the UBUNTU grub back ? 

I checked that all my partitions are where they should be:
/dev/sda1 NTFS
/dev/sda2 NTFS
/dev/sda3 swap
/dev/sda5 Ubuntu
/dev/sda6 Redhat
/dev/sda7 /boot for redhat

i tried editing grub.conf file in RHEL-5 but that won't work... can anyone help me please...

---

### Post by oldfred on 2012-03-04
Is Redhat using grub or grub2.

You could manually install the grub2 boot loader for Ubuntu. But you may want to keep the Redhat boot loader if you are using it more.

If you want to reinstall the grub2 boot loader:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

The boot stanza for Ubuntu will be different if grub or grub2.

This is a typical grub2 boot stanza that you can add to 40_custom.

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. You wuold have to change to your partition.

```
menuentry "Ubuntu on sda5" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}

```If old grub the partitions are counted from 0, so the partition is hd0,4 for sda5 in grub legacy.

```
title    Most Current Ubuntu on sda5
root    (hd0,4)
kernel   /vmlinuz root=/dev/sda5 ro quiet splash
initrd  /initrd.img

```

---

### Post by Rahul Jain on 2012-03-04
Hey thanks a lot...Link # 1 worked fine for me...

I am still wondering how can I boot into Ubuntu using redhat grub.

I don't wanna re-install Ubuntu grub and flush the redhat grub.
I tried editing the redhat's grub.conf file but everytime it gave me this error:

Error2 : bad file or directory name

i edited it like

root (hd0,4)
kernel /vmlinuz<my version> ro root=UUID=**** quiet splash
initrd /initrd.img.****

i also tried root=/dev/sda5 as well as root=LABEL=/ and many other combinations but none seemed to work... can you kindly elaborate what I am doing wrong here ?

---

### Post by oldfred on 2012-03-04
You do not need versions and would have to update manually on every kernel update. Ubuntu keeps a link to the newest kernel in / and the version I gave you is to that link. If you include the version, then you have to look in /boot/vmlin.... not just /. If you browse the / and the /boot folders in Ubuntu you will see the links in / and all the kernels in /boot.

As long as partitions do not change you do not have to use UUID. It just is that UUID is now the standard since many drives are portable or some systems do not boot in the same order every time and UUIDs do not (normally) change. You can use labels, but you have to add the label to the partition, a root partition is not in Ubuntu automatically labeled "/". A few systems do label that way, but then multiple installs can get confusing.

---

