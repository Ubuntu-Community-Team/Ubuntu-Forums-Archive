---
title: "Installed Windows 7, messed up ubuntu"
date: 2011-03-19
forum: General Help
---

### Post by koekjestrommel on 2011-03-19
Hey guys,

I deleted my old windows 7 partition. Then I re-installed windows 7 in the empty partition I created. And now my ubuntu partition suddenly became unallocated :s.

I setted the bootflag on the empty ubuntu partition and it only showed a flashing white stripe when booting up. Had to try something...

Anyways, i don't mind re-installing ubuntu, but is there any way i can get my documents on ubuntu back, or to make sure ubuntu boots again?

Here is a picture

[img]http://img339.imageshack.us/img339/5272/kaaso.png[/img]
130 gb was my ubuntu partition, i didn't even touch it nor make windows install into it.. 90 gb was my windows partition. 

Anyways I hope you can help :)

---

### Post by wyliecoyoteuk on 2011-03-19
EDIT: looking at the picture, the partition table may well be messed up, as the Linux partition is not visible.
[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

[video tutorial here]("http://computerharddrivedatarecovery.net/recover-deleted-partitions-using-testdisk-in-ubuntu-11.html")


Best bet is to use a Ubuntu LiveCD to copy your /home folder to an external drive  first, if you have one, that should serve as a backup of your personal files and settings.
Then either reinstall totally, or try to reinstall grub.

I don't dual boot these days, so can't really help with that, but I am sure someone here can, and the link below will help.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by blueridgedog on 2011-03-19
> **wyliecoyoteuk said:**
> 
Best bet is to use a Ubuntu LiveCD to copy your /home folder to an external drive

I think the partition that contains his /home folder is gone.  I recommend testdisk to recover the partition if possible then a re-install of Ubuntu to the same partition if not.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=site%3Aubuntuforums.org+testdisk](http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=site%3Aubuntuforums.org+testdisk)

What are you booted on to take the screen shot?

---

### Post by wyliecoyoteuk on 2011-03-19
I did suggest links which show how to use testdisk.
The partition is probably still there, just the Partition table is messed up

looks like he's got puppy booted to me.

---

### Post by blueridgedog on 2011-03-19
Testdisk is such an interesting product that I am reluctant to give a step by step outline and hope that a user of testdisk will read up a bit before jumping in.  If a step by step is wanted, the first link has a link to a process:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I too would wager that the partition is there and can be restored.

---

### Post by koekjestrommel on 2011-03-19
Ran testdisk in ubuntu live CD, this is where I'm at now... :(


[img]http://img534.imageshack.us/img534/3155/44885983.png[/img]

Everything's gone now lol :l

suggestions?

Thank god I backed up my music (A), but still my ubuntu was running great and I prefer not to reinstall.

I have no clue what happened to the partitions, but windows 7 partition also seems to be gone...

---

### Post by blueridgedog on 2011-03-19
Ouch.  Were there partitions to restore with testdisk?  Is there anything on the sda1 ext partition?  You should be able to mount it from the puppy boot disk.

sudo mkdir /mnt/drive
sudo mount /dev/sda1 /mnt/drive

---

### Post by koekjestrommel on 2011-03-19
Second try with Testdisk, found my windows partition again; yay :p

I just dint need that one, i really need the ubuntu one. 

[[IMG]http://img4.imageshack.us/img4/2420/20561075.png[/IMG]](http://img4.imageshack.us/i/20561075.png/)


This is how it looks now, weird is how my ubuntu partition used to be 130 gig and now slit up in A LOT of different parts.

How should I name the different partitions on testdisk?

---

### Post by koekjestrommel on 2011-03-19
[[IMG]http://img28.imageshack.us/img28/3126/screenshot2xg.png[/IMG]](http://img28.imageshack.us/i/screenshot2xg.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

How to name them?

---

### Post by koekjestrommel on 2011-03-19
Thank god, found back my files :D

New problem; when booting I get the error operating system missing, I know i've had this before, i should reinstall grub right?

Made a new grub, new error: error 15, file missing

---

### Post by blueridgedog on 2011-03-19
> **koekjestrommel said:**
> Made a new grub, new error: error 15, file missing

How did you re-install grub?  The steps for the current grub are:

Boot off of a LiveCD (Ubuntu), then open a terminal:

```
sudo -i
blkid
```

Find the partition you installed ubuntu on

```
mount /dev/sdax /mnt
```

Where x is partion # containing ubuntu and 'a' assumes this is your first hard drive (if have > 1).  Based on your image, you have two partitions, sda1 and sda2 that could be your install, or it could be shot and neither represents a complete install.

```
mount --bind /sys /mnt/sys
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
chroot /mnt
update-grub 
grub-install /dev/sda
``` 

This assumes the you want grub to be installed on your first hard drive ('a')

---

### Post by koekjestrommel on 2011-03-20
I tried installing grub using puppy linux. Didn't work.

By using your directions and a 9.04 live CD it all worked fine!


Thanks man! =D>=D>=D>8-)8-)8-)8-)

All i got is one partition now :p, but I guess thats all I need.

---

### Post by Savio2010 on 2011-03-20
Try Ubuntu Rescue Remix, if you are good a the Linux command line. It has many useful utilities like Testdisk, Photorec, Foremost, Gnu ddrescue, etc.

It is a live-cd fully command line.

Don't forget to read some of the forum topics in under Data Recovery on that site.

[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

---

### Post by koekjestrommel on 2011-03-20
Nah, I really hate using command line :p

---

### Post by wyliecoyoteuk on 2011-03-20
deleted

---

