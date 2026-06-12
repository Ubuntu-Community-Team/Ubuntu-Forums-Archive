---
title: "having trouble mounting and chrooting ..  help?"
date: 2010-11-24
forum: General Help
---

### Post by Søren on 2010-11-24
hi im having trouble mounting and chrooting. what i want to do is mount the partition highlighted red and chroot into it so that i can have terminal access to it. is this possible and if so what are the commands? i googled for a while but none of the examples helped me 

*edit: the one in blue is my current partition, the one i am in now. 


```
sudo fdisk -l 

Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cd86c

   Device Boot      Start         End      Blocks   Id  System
[COLOR=Red]/dev/sda1               1        1216     9767488+  83  Linux[/COLOR]
/dev/sda2   *        1217        1229      102400    7  HPFS/NTFS
/dev/sda3            1229       22915   174187254    7  HPFS/NTFS
/dev/sda4           22915       43778   167581697    5  Extended
[COLOR=Cyan]/dev/sda5           22915       43075   161933312   83  Linux[/COLOR]
/dev/sda6           43075       43778     5647360   82  Linux swap / Solaris

```

---

### Post by Quackers on 2010-11-24
Try this from a live cd after selecting "try ubuntu" and after checking your internet connection opening a terminal and running

```
sudo mkdir /mnt/temp 
sudo mount /dev/sda1 /mnt/temp 
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```

If those commands ran correctly your terminal prompt should be "root@ubuntu"

You now should have terminal access to install/remove packages etc......I think :-) You could at this point run ```
sudo apt-get update
``` both to check you have internet and that you are in your installation.

Don't forget to unmount these files when you have finished with 

```
for i in /dev/pts /dev /proc /sys / ; do sudo umount /mnt/temp$i ; done
```

---

### Post by Søren on 2010-11-24
thanks, how come i have to do it from a live cd? can i do it from my other linux partition? 
the one i have access to now is dev/ sda5. i dont have access to a live cd atm but i can download on if i need to.

---

### Post by Quackers on 2010-11-24
I just said that because that's how I've used it before :-)
I honestly don't know if it will work from within another system!
You could try it out and let me know :-)
Maybe it would be an idea to wait for somebody else's confirmation first.

---

### Post by Søren on 2010-11-24
ahh ok cheers. well i tried it and i got an error  after 


" for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done "

```
xxx@xxx-desktop:~$ sudo mkdir /mnt/temp 
xxx@xxx-desktop:~$ sudo mount /dev/sda1 /mnt/temp 
xxx@xxx-desktop:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
mount: mount point /mnt/temp/dev does not exist
mount: mount point /mnt/temp/dev/pts does not exist
mount: mount point /mnt/temp/proc does not exist
mount: mount point /mnt/temp/sys does not exist
```

also keep in mind that there are no files in sda1. its just an empty linux partition. no operating systme on it. i want to use the partition for building a linux from scratch.

---

### Post by Quackers on 2010-11-24
I'm not sure enough to offer advice on that I'm afraid. I only know that it's worked for me from the live cd environment.
Maybe somebody else could offer you better advice.
If you choose to end what you've already entered don't forget to unmount /dev/sda1 with ```
sudo umount /dev/sda1 /mnt/temp
```

---

### Post by Søren on 2010-11-24
ahh ok will do. 

thanks a lot for trying to help! :)

---

### Post by Quackers on 2010-11-24
You're welcome.
I allowed an update to delete a program and my system wouldn't boot, so I booted the live cd and chrooted with those commands and re-installed the missing program and fixed things. So I know it works, but I can only vouch for it in those circumstances.
There may well be different commands to do what you want to do from another booted system. I just don't know them :-(
Good luck in your quest :-)

---

### Post by Søren on 2010-11-24
hmmm. yeah i cant think of any reason why the commands would be different from a live cd / vs installed system. if i cant work it out by tomorrow ill download a live cd and try.

---

### Post by Quackers on 2010-11-24
There's still chance somebody will come along with answers for you. It's only a normal sort of time for some people, depending on where they live :-)
Not 2am like it is here :-)

BTW a live usb will do too if you have one.

---

### Post by Søren on 2010-11-24
I got it worked out :D 


```
root@xxx-desktop:/home/xxx/Desktop# mkdir llffss
root@xxx-desktop:/home/xxx/Desktop# mount /dev/sda1 llffss/
root@xxx-desktop:/home/xxx/Desktop# cd llffss/
root@xxx-desktop:/home/xxx/Desktop/llffss# ls 
lfs-sources  lost+found [COLOR="Red"]<- im in ^^[/COLOR]

```

---

### Post by Quackers on 2010-11-24
Nice one, well done sir :-)

---

### Post by Søren on 2010-11-24
thank you sir. now get to sleep!

---

### Post by Quackers on 2010-11-24
Very soon now. I'm watching The Ashes at the moment :-)

---

### Post by Søren on 2010-11-24
mwahahaha. i though us noble aussies were doing well when it was 1 / 8 but is seems you poms have decided to fight :p:popcorn:

---

### Post by Quackers on 2010-11-24
You Judas! We just lost two wickets! :-)

---

### Post by Søren on 2010-11-24
hahaha!

---

### Post by Quackers on 2010-11-24
Anyway, you're the pohms not us! :-)

---

### Post by ezsit on 2010-11-24
> also keep in mind that there are no files in sda1. its just an empty linux partition. no operating systme on it.

Just so you know, chroot is to access an installed system. You merely wanted to mount a partition. You successful mounted the partition. That is why it worked. When you asked to chroot, everybody got a bit confused why the chroot commands did not work.

---

