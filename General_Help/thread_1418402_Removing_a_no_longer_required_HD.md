---
title: "Removing a no longer required HD"
date: 2010-02-28
forum: General Help
---

### Post by valvegrid on 2010-02-28
I'm running Ubuntu 9.10 on a 250GB drive and have Windows 2K on a 40GB drive. I have noticed that the 40GB drive has got quite a few bad sectors appearing on it, so it looks like it's going to give up the ghost soon.

I have decided to do away with the 40GB drive and Win 2K because I never use it, the question is if I just remove the drive what are the consequences if I do that? Apart from still seeing Windows 2000 in the bootup list. I've never tried this hence the reason for the question.

I have backed up the files with Déjà Dup in case disaster strikes. 

Thanks.

Paul.

---

### Post by oldfred on 2010-02-28
If you did a clean install of Karmic and have grub2 running sudo update-grub will rewrite the menu without the windows entry. May also work with grub legacy but usually have to edit menu.lst. 
If you are mounting any partitions in fstab you need to edit those out or it may not let you boot as it will not be able to find that partition. Otherwise I do not think you should have any issues.

---

### Post by rahilm on 2010-02-28
What consequences you'll have depends on many things. While no consequence i can think of can mess with your data. There is no need for a backup.

Just try and see. Post any problems you are having.

---

### Post by valvegrid on 2010-02-28
> **oldfred said:**
> If you did a clean install of Karmic and have grub2 running sudo update-grub will rewrite the menu without the windows entry. May also work with grub legacy but usually have to edit menu.lst. 
If you are mounting any partitions in fstab you need to edit those out or it may not let you boot as it will not be able to find that partition. Otherwise I do not think you should have any issues.

Thanks oldfred, yes it was a clean install of Ubuntu, so it would have grub2 on it so I'll have to sudo update-grub.

> **rahilm said:**
> What consequences you'll have depends on many things. While no consequence i can think of can mess with your data. There is no need for a backup.

Just try and see. Post any problems you are having.

I do backups as a matter of course anyway, so it's not really a problem. I agree it shouldn't effect my data, it's just a habit backing up data and it's saved me on a couple of occasions in the past when I've been messing around, being a veritable twiddler :)

---

### Post by valvegrid on 2010-03-01
Thanks all, the drive has been removed and grub updated without problems.

I think the drive was on it's last legs, it's much quieter, I think the bearing must have been failing.

---

