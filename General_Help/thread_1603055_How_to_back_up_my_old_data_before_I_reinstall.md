---
title: "How to back up my old data before I reinstall"
date: 2010-10-22
forum: General Help
---

### Post by brianj.wagner on 2010-10-22
Okay so I made a mistake and I have to reinstall Linux (see: [http://ubuntuforums.org/showthread.php?t=1602329](http://ubuntuforums.org/showthread.php?t=1602329))

Since I can no longer boot to my existing installation (the graphical version OR the text version), I am having trouble saving off what I don't want to lose.

Can I boot from the CD and get to my stuff through there? I am in the CD version of Mint right now (posting this) and I cannot navigate to /home/myusername/ (obviously). So where would I find those files?

Do I have to mount that partition or something? It looks like a lot of my stuff is mounted already in this CD version... which worries me.

An alternative is that I still have Windows 7 installed that I can boot to if needed. If thats a way to extract my files I am all for it.

Thanks for the help.

---

### Post by nothingspecial on 2010-10-22
Should be in the places menu.

Plug in an external drive and drag and drop, should be that simple.

If you don`t have permission 
```

gksudo nautilus
```

---

### Post by brianj.wagner on 2010-10-22
In Places I do see my primary hard drive, but it looks like I can only see the Windows partition; I can't find any of the Linux filesystem on there.

Is there something I have to mount first?

---

### Post by nothingspecial on 2010-10-22
```
sudo fdisk -l
```

figure out which /dev/sd?? is your linux partition
```

sudo mkdir /media/buntu
sudo mount -t ext4 /dev/sd?? /media/buntu
```

---

### Post by brianj.wagner on 2010-10-22
Okay, so I figured it out and I hope it helps someone else in this situation.

I found my entire partition to be in root.disk form. I neglected to mention I installed this with wubi (I didn't think it mattered).

When I was browsing my linux partition in places, it looked relatively empty, then I saw this one file that was 30GB called "root.disk". I looked it up and was able to mount it with this:

sudo mkdir /media/vdisk
sudo mount -o loop /media/LINUX/linuxmint/disks/root.disk /media/vdisk

vdisk showed up in Places and I tossed my home directory and my other important stuff onto my drive. Now on with a clean install.

Thanks for your help everyone!

---

