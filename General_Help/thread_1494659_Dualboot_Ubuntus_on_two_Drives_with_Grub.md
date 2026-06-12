---
title: "Dualboot Ubuntus on two Drives with Grub"
date: 2010-05-27
forum: General Help
---

### Post by PhilippAlder on 2010-05-27
Hello Forum,

I have a question regarding Ubuntu Server and the Grub bootloader. My home server has two drives and I have Ubuntu Server 10.04 installed on both drives and a data partition on each drive as well. One of the Ubuntu Server installations is just to have a working configuration in case things go wrong and the second data partition will be mirrored with rsync so that I won't lose data in case of a disk failure.

sda1 --> Default Ubuntu (10.04)
sda3 --> Data

sdb1 --> Backup Ubuntu (10.04)
sdb3 --> Data Backup


Now to my question. Do I need a Grub bootloader on each hard drive? When Ubuntu forces me to install Grub while I install Ubuntu on sdb and I chose to install Grub on sda, then Grub uses the configuration files on sdb! Can I change it back so that it'll use the original Grub configuration files on sda?

I really haven't found any answer yet and I'm a bit stuck. I'd be most grateful for any help.

Thanks

---

### Post by dcstar on 2010-05-27
> **PhilippAlder said:**
> Hello Forum,

I have a question regarding Ubuntu Server and the Grub bootloader. My home server has two drives and I have Ubuntu Server 10.04 installed on both drives and a data partition on each drive as well. One of the Ubuntu Server installations is just to have a working configuration in case things go wrong and the second data partition will be mirrored with rsync so that I won't lose data in case of a disk failure.

sda1 --> Default Ubuntu (10.04)
sda3 --> Data

sdb1 --> Backup Ubuntu (10.04)
sdb3 --> Data Backup


Now to my question. Do I need a Grub bootloader on each hard drive? When Ubuntu forces me to install Grub while I install Ubuntu on sdb and I chose to install Grub on sda, then Grub uses the configuration files on sdb! Can I change it back so that it'll use the original Grub configuration files on sda?

I really haven't found any answer yet and I'm a bit stuck. I'd be most grateful for any help.

Thanks

Various Grub2 HOWTOs spell out how to reinstall on specific locations, search them out.

---

### Post by philinux on 2010-05-27
My set up is the similar.

sda1 --> Ubuntu (10.04)
sda3 --> Home

sdb1 --> Ubuntu (10.10)
sdb3 --> Home

I have grub installed to sda mbr and grub installed to sdb1 pbr.

I then chainload from sda to sdb1 if I want to. It does complain about blocklists when you install to a partition. 

When new kernels arrive grub on sda gets updated but it is blocked from probing sdb1 since the os-prober is disabled (GRUB_DISABLE_OS_PROBER=true in /etc/default/grub). On sdb when a kernel updates I let it operate as normal so it shows kernel entries from both installs.

I have this in /etc/grub.d/40_custom
           menuentry "Grub on sdb1" {

            set root=(hd1,1)

            chainloader +1

            }

This way my sda grub is neat, with only kernel entries for sda. I could do the same for the sdb1 grub but I cant be bothered as it's only a development install which gets borked now and then.

See the grub2 link in my sig.

---

### Post by PhilippAlder on 2010-05-27
Thank you so much philinux. It looks really neat, that's exactly what I was looking for.

---

### Post by PhilippAlder on 2010-05-27
Why are you installing Grub on a partition on sdb and not to the MBR?

---

### Post by philinux on 2010-05-28
> **PhilippAlder said:**
> Why are you installing Grub on a partition on sdb and not to the MBR?

I was pretty sure that installing grub2 to sdb mbr would take over the whole machines booting, so I went with sdb1. This has happened in the past with legacy grub when testing out other distro's on sdb.

Try installing to sdb mbr and see. Let me know how it goes. I was tempted to do this when I installed lucid alpha2 but didn't.

---

