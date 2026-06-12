---
title: "Help me I am new to Ubuntu"
date: 2009-12-21
forum: General Help
---

### Post by bibincherianv on 2009-12-21
Dear friends,

My Name is Bibin and I am new to Ubundu (Linux) I am using 9.10 of Ubuntu.
I got dual boot on my Laptop Linux and Windows XP. My Xp got corrupted and I want to reinstall it, but if I reinstall it then I may have to reinstall my Ubuntu also and all my ubundu data will be lost. Is there any way out so thet I can retain my Ubuntu and at the same time I can reinstall my XP?

Its bcoz XP will change the boot and after reinstallation only XP will be shown, as windows will not load Linux.

Somebody please help me......

Regards

Bibin.

---

### Post by DeMus on 2009-12-21
> **bibincherianv said:**
> Dear friends,

My Name is Bibin and I am new to Ubundu (Linux) I am using 9.10 of Ubuntu.
I got dual boot on my Laptop Linux and Windows XP. My Xp got corrupted and I want to reinstall it, but if I reinstall it then I may have to reinstall my Ubuntu also and all my ubundu data will be lost. Is there any way out so thet I can retain my Ubuntu and at the same time I can reinstall my XP?

Its bcoz XP will change the boot and after reinstallation only XP will be shown, as windows will not load Linux.

Somebody please help me......

Regards

Bibin.

Yes, Windows will destroy your grub. But have a look [_here_]("http://ubuntuforums.org/showthread.php?t=224351") and perform the actions (write them down first) after you re-installed that terrible OS.

---

### Post by omskates on 2009-12-21
You'll have to re-install the Grub bootloader as DeMus says with that link. Your dual boot should be on 2 separate partitions, you can see this with Gparted.  Reinstalling XP to the Windows partition won't effect your Ubuntu as long as you choose that correct partition for install and NOT entire HDD.  Its always good to backup your /home directory in oUbuntu before doing anything like that as well.  Check with GParted also called "Partition Editor" to re-assure yourself on what partition you are re-installing to. Ask yourself why you need your Windows so badly ;)

---

### Post by DeMus on 2009-12-21
> **omskates said:**
> Your dual boot should be on 2 separate partitions, you can see this with Gparted.  Reinstalling XP to the Windows partition won't effect your Ubuntu as long as you choose that correct partition for install and NOT entire HDD.  Its always good to backup your /home directory in oUbuntu before doing anything like that as well.  Check with GParted also called "Partition Editor" to re-assure yourself on what partition you are re-installing to.

Erased

---

### Post by zvacet on 2009-12-21
If you are using  Ubuntu 9.10 then you are using grub2 so look [here]("https://help.ubuntu.com/community/Grub2") to see how to reinstall grub.

---

### Post by omskates on 2009-12-21
> **DeMus said:**
> Erased

:confused::confused:

---

