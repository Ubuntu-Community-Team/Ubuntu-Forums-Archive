---
title: "Stuck in Grub prompt AGAIN. (Ubuntu 9.1, newest kernel)"
date: 2009-12-18
forum: General Help
---

### Post by ChattaBenji on 2009-12-18
This is kinda the last stand for me.

I am running an Ubuntu9.1/XP dual-boot and I am on my 4th Wubi installation.
The first three had crashed within a day of use after updating to 2.6.31-15.

The 4th time I updated from -14 to -16, updated grub, and everything worked perfect, even my ATI Wonder TV Card =]
It has been working great for about 2 weeks, with restarts almost every day.
Last night, though, I came home and noticed that my system was completely frozen and I ended up having to hard reboot.

When I booted back up and chose Ubuntu it went strait to the dreaded Grub Prompt (1.97 Beta4). This happened on -15 too when I had to hard reboot. Last time I was able to boot using:
```

linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single
initrd /boot/initrd.img-2.6.31-14-generic
boot

```Now, when I try either -14 or -16 it reads "File not found".
I have checked for misspellings and ran these multiple times getting the same response. I am positive my installation is on sda1, too.

I have also tried running the live CD and mounting the filesystem then updating grub.
I get this far:
```

sudo fdisk -l
sudo mount /dev/sda1 /mnt
**sudo mount --bind /dev /mnt/dev**

```After that last command I get "Mount point not found /mnt/dev"

It seems to me as if the installation isn't even there?
Is this possible even when all the ubuntu folders are still intact on my drive?

This is the last shot I am going to give to Ubuntu, I love it, but after a re-install it takes over a day just to get it back to how it was, and I lose a lot of work in the process :(

---

### Post by ChattaBenji on 2009-12-18
bump

---

### Post by drs305 on 2009-12-18
> **ChattaBenji said:**
> 
I get this far:
```

sudo fdisk -l
sudo mount /dev/sda1 /mnt
**sudo mount --bind /dev /mnt/dev**

```After that last command I get "Mount point not found /mnt/dev"



You will have to make the /mnt/dev mountpoint and then mount it (sudo mkdir /mnt/dev).

---

### Post by ChattaBenji on 2009-12-18
> **drs305 said:**
> You will have to make the /mnt/dev mountpoint and then mount it (sudo mkdir /mnt/dev).

Wow, I'm an idiot.
That did work, but the next thing it says is to do sudo update-grub
and I get:
"grub-probe: error: cannot find a device for /."

I'm really new at this as you can tell. I printed out these directions from XP before I booted in Live CD so I don't know the exact thread but it was on this forum.

The fact that I can't even boot from Grub and get "file not found" is just really weird to me.

---

### Post by drs305 on 2009-12-19
> **ChattaBenji said:**
> I'm really new at this as you can tell. I printed out these directions from XP before I booted in Live CD so I don't know the exact thread but it was on this forum.

The thread could have been the Grub2-Basics link below. That and the community doc link (GRUB2) both cover booting from the Grub 2 (rescue) prompt and reinstalling Grub 2.

---

### Post by Leppie on 2009-12-19
Try this at the grub rescue prompt:
```
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro		
initrd /initrd.img		
boot
```

---

### Post by wethecom on 2009-12-27
Soulution set your primary graphics adapter in bios

this is some commands you might want to note.


ls
ls (hd0)
ls /(hd0)
ls /(loop0)
ls (loop0)
/ls boot
root(loop0)
root(hd0,1)
root(hd0,0)

this next combination will boot up linux..but it wont solve your problem .your problem is bois setting so you end up at a command prompt
i spent 24 hours strait trying to get past the same grub prompt that you had..and this is what i learned
/ls boot  "this will list the data you need to put into the commands 
you dont need the version in the command line 
```



 linux /vmlinuz 
 initrd /initrd.img 
 boot
 
```

---

### Post by wethecom on 2009-12-27
Soulution for me
problem was a mix of a few thing but easly fixed
restore bios to optimal settings...why because after installing gerforce proprietary drivers you get dumped a grub next boot
i had messed around with the settings for on-board video card  /or geforce agp card in the past ...windows will boot but ..ubunt wont
other wise dont install geforce binary driver..my problem was with nivida driver v 185 i think

---

