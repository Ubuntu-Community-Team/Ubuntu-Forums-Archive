---
title: "stuck at grub rescue prompt after partition resize"
date: 2009-10-29
forum: General Help
---

### Post by sdowney717 on 2009-10-29
it shows 
grub-rescue >

so what do i type in?

---

### Post by ImaginaryPixel on 2009-10-29
I have the same problem as you, but mine says
error: no such partition

---

### Post by sdowney717 on 2009-10-29
from a live cd  i try this and get

ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

---

### Post by ImaginaryPixel on 2009-10-29
I had that happen too, I just uninstalled GRUB2 and tried to install GRUB but for some reason GRUB2 still exists and keeps giving me that error message.
I am just going to reinstall my OSs

---

### Post by drs305 on 2009-10-29
Go to the GRUB 2 Community docs. There is a section on booting from the Grub menu (by editing the contents) and another on booting from the GRUB 2 rescue mode. If you have questions, use this thread.

[https://help.ubuntu.com/community/Grub2#Command Line & Rescue Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

---

### Post by sdowney717 on 2009-10-29
[http://74.125.95.132/search?q=cache:SyoWSBzgQ4gJ:ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7+fix+grub2&cd=2&hl=en&ct=clnk&gl=us&client=firefox-a](http://74.125.95.132/search?q=cache:SyoWSBzgQ4gJ:ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7+fix+grub2&cd=2&hl=en&ct=clnk&gl=us&client=firefox-a)

for me sda5 is my ext4 partition, sda1 is my windows ntfs partition
try this, i may have gotten it

ubuntu@ubuntu:~$ sudo -i

root@ubuntu:~# mount /dev/sda5 /mnt

root@ubuntu:~# mount /dev/sda1 /mnt/boot

root@ubuntu:~# grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
root@ubuntu:~#

---

### Post by VMC on 2009-10-29
> **sdowney717 said:**
> it shows 
grub-rescue >

so what do i type in?

This is not a lot to go on. What did you install, and how. Also did you have Windows on that first partition, and what linux is sitting on sda5?

Have you tried just tying help or tab from the grub prompt?

---

### Post by sdowney717 on 2009-10-29
now it shows
sh:grub>

help scrolls a huge unseeable list
tab says unknown command

how do i restore grub2??

I have an ntfs on sda1 vista
i have an ext4 on sda5 with karmic

grub2 is an improvement?

---

### Post by drs305 on 2009-10-29
> **sdowney717 said:**
> now it shows
sh:grub>

help scrolls a huge unseeable list
tab says unknown command

how do i restore grub2??

I have an ntfs on sda1 vista
i have an ext4 on sda5 with karmic

grub2 is an improvement?

To stop the scrolling, at the grub prompt type: 
```

set pager=1

```
The infomation will now scroll with the ENTER key.

Did you use the GRUB 2 community doc and follow the instructions there?

---

### Post by VMC on 2009-10-29
> **sdowney717 said:**
> [url]...for me sda5 is my ext4 partition, sda1 is my windows ntfs partition
try this, i may have gotten it

ubuntu@ubuntu:~$ sudo -i

root@ubuntu:~# mount /dev/sda5 /mnt

[B]root@ubuntu:~# mount /dev/sda1 /mnt/boot
[/B]
root@ubuntu:~# grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
root@ubuntu:~#

That "/boot" you tried to mount is your Vista partition.

That link you posted is showing Grub4Dos. Try to follow this [link]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") instead.

---

### Post by sdowney717 on 2009-10-30
thanks, VMC, i got it with that link you posted.
grub2 is not easier than grub, imo.
i had to pull my original drive out of the system. leaving it in even though gparted was showing sda as the bigger drive, updating grub on sda made it load sdb?
also, in gparted when i changed to sdb it showed sdb 200gb drive as unallocated space?

so i pulled it out and reupdated grub and now it is booting off sda the big 750 gb drive

i would like to keep my 200gb drive in the system. 
i dont wish to reformat it, and i thought updating grub would show both drives with the option to boot off either.

---

### Post by pirog on 2010-01-16
> **sdowney717 said:**
> [http://74.125.95.132/search?q=cache:SyoWSBzgQ4gJ:ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7+fix+grub2&cd=2&hl=en&ct=clnk&gl=us&client=firefox-a](http://74.125.95.132/search?q=cache:SyoWSBzgQ4gJ:ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7+fix+grub2&cd=2&hl=en&ct=clnk&gl=us&client=firefox-a)

for me sda5 is my ext4 partition, sda1 is my windows ntfs partition
try this, i may have gotten it

ubuntu@ubuntu:~$ sudo -i

root@ubuntu:~# mount /dev/sda5 /mnt

root@ubuntu:~# mount /dev/sda1 /mnt/boot

root@ubuntu:~# grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
root@ubuntu:~#

thanks mate! the same thing was given in the official guide, but they confused me with a note that /dev/sda should be location of your GRUB installation (in my case grub installed separately on /dev/sda1). Of course when i put sda1, it does not work. I tried your solution (without 1) and it worked.

> 
root@ubuntu:~# grub-install --root-directory=/mnt/ /dev/sda


cheers.

---

### Post by Egreto on 2010-02-13
Have exactly the same problem
Tried to install  ubuntu 9.1 64 on laptop with W7 64
After getting black screen during installation of Linux, i tried to get rid of Linux. 

Now all I get from brand new laptop is grub rescue. 
I tried recovery disks from gateway, after 1 hour of "recovery" I still get 
grub rescue>

other than ls no other usual commands work with 
grub rescue>

I understand that mbr is messed up, it might be looking for linux that is no longer there as I deleted linux partion. 

Tried to use win xp cd, and i am getting blue screen after some initial file copying, and i never get to rescue screen

Ubuntu 9.1 32 or server give me black screen

What's next?
Any ideas?
Would clean sweep of hdd, low level formatting and recovery dvd work?

From previous attempts I am getting idea that recovery disk from Gateway might be worthless.

---

### Post by Brian34 on 2010-02-26
> **sdowney717 said:**
> it shows 
grub-rescue >

so what do i type in?

I have the same problem,
some days ago my linux Netbook Remix 9.10 crashed and I turned the computer off keeping pushed the start button.
Since then when I try to boot the system appears:

```

GRUB loading.
error: biosdisk read error
grub rescue>

```if I type the ls command it returns:

```

grub rescue> ls
(hd0) (hd0,5) (hd0,1) (hd1) (hd1,1)

```end if I try to read the (hd0,1) it returns:

```

grub rescue> ls (hd0,1)/
error: biosdisk read error

```any idea?
Thanks

---

### Post by fenderr357 on 2010-11-04
> **sdowney717 said:**
> [http://74.125.95.132/search?q=cache:SyoWSBzgQ4gJ:ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7+fix+grub2&cd=2&hl=en&ct=clnk&gl=us&client=firefox-a](http://74.125.95.132/search?q=cache:SyoWSBzgQ4gJ:ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7+fix+grub2&cd=2&hl=en&ct=clnk&gl=us&client=firefox-a)

for me sda5 is my ext4 partition, sda1 is my windows ntfs partition
try this, i may have gotten it

ubuntu@ubuntu:~$ sudo -i

root@ubuntu:~# mount /dev/sda5 /mnt

root@ubuntu:~# mount /dev/sda1 /mnt/boot

root@ubuntu:~# grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
root@ubuntu:~#

I just wanted to post and say that this worked excellently for me. I had installed Kubuntu alongside Ubuntu and Windows 7.. I then got tired of Kubuntu and removed it, and it apparently took grub with it. I loaded up the live CD and ran this and it worked.
 
Thanks

---

### Post by Rausan on 2011-05-19
root@ubuntu:~# mount /dev/sda6 /mnt
root@ubuntu:~# mount /dev/sda1 /mnt/boot
root@ubuntu:~# grub-install --root-directory=/mnt/ /dev/sda
/usr/sbin/grub-setup: warn: no signature.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
root@ubuntu:~# 


I am getting this. Any solution?

---

