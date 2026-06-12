---
title: "How to fsck or e2fsck my full disk LUKS installation?"
date: 2012-01-31
forum: General Help
---

### Post by tehowe on 2012-01-31
I've noticed that a few bad things have happened to my alternate-CD LUKS encrypted installation of Ubuntu like


[LIST]
[*]gconf directory and settings disappeared
[*]Evolution sent mail from the past decade now has 36 items
[/LIST]
Also, when I ssh in from my netbook I notice that in the welcome message there's a persistent notification that 

> *** /dev/mapper/udisks-luks-uuidetcetctec will be checked for errors at next reboot ***I'm not sure it's doing that however. So how do I use my trusty LiveCD to perform this check myself? I've gone in with it and sudo fdisk -l returns

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953523711   976510977    5  Extended
/dev/sda5          501760  1953523711   976510976   83  Linux

```I've read elsewhere that simply running fsck on an encrypted partition will hose the entire thing so my next step was

```
sudo cryptsetup luksOpen /dev/sda5 foo
```However, now at the end of fdisk -l a message is printed

> Disk /dev/mapper/foo doesn't contain a valid partition tableIs it safe to proceed with 

```
sudo e2fsck -v /dev/mapper/foo
```in this case, or what should I do? Please provide the commands to use, as I'm still finding my way around.

Thanks!

---

### Post by Khayyam on 2012-02-01
tehowe ..

Instructions can be found [here]("http://ubuntuforums.org/showpost.php?p=4524774&postcount=9")

HTH ..

---

### Post by tehowe on 2012-02-07
> **Khayyam said:**
> tehowe ..

Instructions can be found [here]("http://ubuntuforums.org/showpost.php?p=4524774&postcount=9")

HTH ..

Thank you!

---

