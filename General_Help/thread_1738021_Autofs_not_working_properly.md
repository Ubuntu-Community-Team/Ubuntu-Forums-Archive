---
title: "Autofs not working properly"
date: 2011-04-24
forum: General Help
---

### Post by deckoff on 2011-04-24
Hi , I managed to configure autofs5 on my Kubuntu 10.10. I want to use autofs to mount my NAS drive, when I am home(most of the time ) and not bother me when I am away. I mount it in /etc/fstab, but suspend and hibernate does not work correctly, when I am not at home. Now I comment the line which mounts the NAS drive
I am still not at home, and decided to try to autofs my flash drive 
Here is my auto.master 
```

# directory    map
/-             /etc/auto.direct    --timeout=2 --ghost

```and my auto.direct

```
/mnt/data    -fstype=vfat,uid=1002,gid=1002,umask=002    :/dev/sdb1
```Problem is, when I connect and disconnect the usb flash, all of a sudden it stops working. I sto seeing my files in /mnt/data until restart. So, this worries me, I dont want to have to restart just to have to get my NAS back online.

---

### Post by ddd-222 on 2011-05-06
i have been playing with autofs recently for nfs and cifs/samba, but flash drives automount for me without autofs. udev automounts flash drives. if you want to create a specific link somewhere on your file system, you can either create a synmbolic link ( which is dead when nothing is mounted ) or you can create a file in /etc/udev/rules.d describing what you want.

---

### Post by deckoff on 2011-05-07
Well, I wanted to fix NFS/SAMBA automount in the first place. My problem is, that once NFS is disconnected, it never connects again

---

### Post by ddd-222 on 2011-05-07
if that's the case, check out my post about nfs automount:

[http://ubuntuforums.org/showthread.php?t=1750888](http://ubuntuforums.org/showthread.php?t=1750888)

concerning indirect auto mounting of samba shares, i had problems getting it working on ubuntu 10.10. It works fine on Linux Mint Debian Edition and Suse Enterprise Linux, however. I can get direct mounting of samba shares working with no problem however. 
Since you are using a slightly older version of ubuntu. it may just work. try exactly the same thing, just use the auto.smb instead of auto.net and apply it to a different directory ( like /smb ).

Mine had no problem connecting, disconnecting and re-connecting. that could possibly be a bug in that release.

---

### Post by deckoff on 2011-05-07
I should update my info. I am on Kubuntu 10.10. 
My general problem is that using a laptop with NFS drive and fstab , the laptop will hang forever if you are not at home and access it. That is why I wanted to use autofs.
It seems the best way( for my case) is to mount it with a script that checks the network you are connected to, and mount the drive if the desired network is connected.
I hoped that autofs will solve my problem, but it will just not work.

---

