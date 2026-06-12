---
title: "How to change sda2 to sda1 using fdisk?"
date: 2010-12-01
forum: General Help
---

### Post by darkhorse9000 on 2010-12-01
I'll avoid the details of what got me here and get right to the point.
 
I have two primary partitions on 1 hard drive. sda1 is my fat32 recovery partition and sda2 is my ntfs windows xp partition. I need to know how to change the order around so xp is sda1 by using the terminal in the ubuntu live cd.

---

### Post by CharlesA on 2010-12-01
What exactly are you trying to do? Fix fstab?

---

### Post by dcstar on 2010-12-01
> **darkhorse9000 said:**
> I'll avoid the details of what got me here and get right to the point.
 
I have two primary partitions on 1 hard drive. sda1 is my fat32 recovery partition and sda2 is my ntfs windows xp partition. I need to know how to change the order around so xp is sda1 by using the terminal in the ubuntu live cd.

[LIST=1]
[*]It cannot be done.
[*]It is pointless anyway. Nothing is dependant on the order - nothing.
[/LIST]

---

### Post by CharlesA on 2010-12-01
> **dcstar said:**
> [LIST=1]
[*]It cannot be done.
[*]It is pointless anyway. Nothing is dependant on the order - nothing.
[/LIST]
Indeed. That's why it would help to know what they are trying to accomplish.

---

### Post by darkhorse9000 on 2010-12-01
Sorry about the rushed post. It's almost one in the morning for me and I've had a really bad day.

I successfully installed and dual booted ubuntu 10.10 over the weekend and was customizing it yesterday. During the process I decided to find a way to make windows xp the default os and hide the grub menu on startup, which I accomplished by setting the menu's timeout values to 0 (as was mentioned in several threads in these forums).

Unfortunately, I soon found out that I could no longer access the grub menu and by extension ubuntu. One thing led to another and I deleted and reformatted the linux partitions in disk management in xp and then used a third party partition tool to give all of the unused space back to my C:/ drive. 

I then used the ubuntu live cd and ms-sys to repair the mbr so I could just revert back to a normal single boot windows xp install. The repair worked, but my computer began booting immediately to my recovery partition (drive D:/) instead of the windows xp partition.

The ubuntu live cd revealed that the fat 32 recovery partition was set as sda1 and was first in line to boot (the * next to it when doing fdisk -l). I would like to avoid reformatting the hard drive and reinstalling everything if possible, and from what I've read the best chance I have would be to use the live cd to change the order of the partition table so my computer starts booting from my actual ntfs windows xp installation. 

These are the only two partitions (both are primary) that are on my one hard drive and they are the only two that come up when I perform the fdisk -l command. 

Any help would be much appreciated.

---

### Post by CharlesA on 2010-12-01
Are you able to boot into WinXP?

If you can't boot into XP, you'd probably have to boot off an XP disc and fix the MBR from there.

---

### Post by darkhorse9000 on 2010-12-01
I was not able to boot to my windows xp partition at all. My emachine has a factory recovery partition (the "powered by pc angel" kind) that it kept booting to.
 
OVernight I realized that stupid gateway never supplied a real xp installation cd and all I had was their version that works together with the recovery partition (only two recovery options are full reformat and partial reformat). 
 
I decided to run a full destructive reformat overnight and see if that in the process fixes the master boot record (I would assume it would) because I really need this computer working again. When I woke up this morning it looks like it booted to the actualy windows partition because the recovery partition had finished the reformat, restarted, and begun loading factory defaults. 
 
I'll wait for the process to finish before I try restarting to see if the mbr was really fixed or not.

---

### Post by WorMzy on 2010-12-01
Just a note: If you decide to try dual booting again, after you've set the timeout to 0, grub should still appear if you hold shift down immediately after POST. If shift doesn't work, then ESC should. If neither of them work, then you can still boot a LiveCD, chroot to your partition, make the necessary changes and then run update-grub.

---

### Post by darkhorse9000 on 2010-12-01
> **WorMzy said:**
> Just a note: If you decide to try dual booting again, after you've set the timeout to 0, grub should still appear if you hold shift down immediately after POST. If shift doesn't work, then ESC should. If neither of them work, then you can still boot a LiveCD, chroot to your partition, make the necessary changes and then run update-grub.
 
That is pretty much what happened to me. I set the timeout value to 0 and the menu was successfully hidden and I assumed shift or esc would work. However, on startup esc wouldn't do anything and holding down shift would only bring up a line saying "grub loading" and then immediately proceed to booting windows xp. 
 
Just one question. I am relatively new to linux and ubuntu. What do you mean by "chroot to your partition"?

---

### Post by WorMzy on 2010-12-01
chroot = change root (filesystem)
The normal root is just / and everything branches off from there, but chroot lets you temporarily use (for example) /media/Maverick as the root, so the shell you run chroot in will temporarily think that /media/Maverick/bin is /bin, /media/Maverick/boot is /boot, etc. That lets you run applications on the partition as though you are booted into it. It's best to use mount --bind to bind specific directories to the partition before chrooting though, otherwise the shell won't be able to do certain things.

e.g. going on the assumption that your partition is mounted as /media/Maverick:
Open a terminal and then run:
```
sudo mount --bind /dev /media/Maverick/dev
sudo mount --bind /proc /media/Maverick/proc
sudo mount --bind /sys /media/Maverick/sys
sudo chroot /media/Maverick
sudo update-grub
```

That string of commands will update grub's files on the partition.
/dev holds information about devices, so mount --binding that will allow the chroot to access this information, ditto for /proc (processes) and /sys (system information (e.g. drivers)).

I dunno what file you have to edit to change grub's config (/etc/grub/default, possibly?), but you can do that in the chroot too. It may be easier to use a CLI editor, like nano or vim to edit it, as Xorg apps (like gedit, kate, gvim, etc) may not be able to launch. You could always edit the file from outside the chroot (e.g. Alt+F2, gksu gedit /media/Maverick/etc/grub/default, run) if you're not keen on the CLI.

I hope this explanation isn't too confusing. :)

---

### Post by CharlesA on 2010-12-01
For grub2 the file you edit is /etc/default/grub

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by darkhorse9000 on 2010-12-01
Thanks for all the help guys! 
 
I unfortunately ended up having to reformat everything and start over because of how my computer's recovery partition is set up, but at least everything is now working again.
 
I'll definitely keep the chroot idea in mind if I decide to try and dual boot a linux distro again.

---

