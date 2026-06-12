---
title: "New to this - need help"
date: 2009-07-17
forum: General Help
---

### Post by cb2410 on 2009-07-17
Hello,

How can I uninstall ubuntu ?

I installed the amd64 version next to my WindowsXP. 

Thx

---

### Post by nothingspecial on 2009-07-17
What`s the problem?

---

### Post by vinutux on 2009-07-17
> **cb2410 said:**
> Hello,

How can I uninstall ubuntu ?

I installed the amd64 version next to my WindowsXP. 

Thx

Whats matter....reasons for uninstalling....explain more where is you installed it inside windows or as a duel boot with xp

.

---

### Post by cb2410 on 2009-07-17
> **vinutux said:**
> Whats matter....reasons for uninstalling....explain more where is you installed it inside windows or as a duel boot with xp

.


Hi, its a dual boot where I can select the OS from the boot menue. I just want to know hoe to uninstall it again. thx

---

### Post by howefield on 2009-07-17
> **cb2410 said:**
> Hi, its a dual boot where I can select the OS from the boot menue. I just want to know hoe to uninstall it again. thx

Did you install it via Wubi ? in which case you can uninstall via windows add/remove programs or did you install on a seperate partition/disk to windows in which case you can delete the Ubuntu partition and fix your windows bootloader.

---

### Post by cb2410 on 2009-07-20
> **howefield said:**
> Did you install it via Wubi ? in which case you can uninstall via windows add/remove programs or did you install on a seperate partition/disk to windows in which case you can delete the Ubuntu partition and fix your windows bootloader.


Its a Dual Boot installation with a separate partition plus swap partition. Thx

---

### Post by nikhilk on 2009-07-20
> **cb2410 said:**
> How can I uninstall ubuntu ?

Technically, it is not possible to un-install Ubuntu (or any other OS for that matter), if you have installed it onto a separate partition. You can simply re-format the corresponding partition(s) and reclaim the disk space.

---

### Post by MikeSD on 2009-07-20
> **cb2410 said:**
> Its a Dual Boot installation with a separate partition plus swap partition. Thx

If you will just remove linux partitions, recreate partition and format it with NTFS, won't it be a solution to uninstall ubuntu? :)

---

### Post by 3rdalbum on 2009-07-20
> **MikeSD said:**
> If you will just remove linux partitions, recreate partition and format it with NTFS, won't it be a solution to uninstall ubuntu? :)

True, but Windows won't boot because the MBR will still want to find GRUB, which will no longer exist because it's been wiped.

You will need to use the "fixmbr" command in recovery mode on your Windows install disc after wiping Ubuntu. Alternately, if you don't have a Windows install disc, you can use the "ms-sys" program that is ready-to-compile here: [http://ms-sys.sourceforge.net/]("http://ms-sys.sourceforge.net/") from a live CD. Some "system rescue"-type Linux live CDs have this program on them. It creates valid master boot records and it is a lifesaver.

---

### Post by cb2410 on 2009-07-20
> **3rdalbum said:**
> True, but Windows won't boot because the MBR will still want to find GRUB, which will no longer exist because it's been wiped.

You will need to use the "fixmbr" command in recovery mode on your Windows install disc after wiping Ubuntu. Alternately, if you don't have a Windows install disc, you can use the "ms-sys" program that is ready-to-compile here: [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/) from a live CD. Some "system rescue"-type Linux live CDs have this program on them. It creates valid master boot records and it is a lifesaver.

Oh mate, thx for this info ! That is what I was thinking.

---

