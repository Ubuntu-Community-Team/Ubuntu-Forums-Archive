---
title: "Really need help!"
date: 2009-09-02
forum: General Help
---

### Post by xxshifterxx on 2009-09-02
So i recently installed ubuntu 9.04 on my pc..i was wondering how do i access my vista files without booting?

---

### Post by Vaphell on 2009-09-02
ubuntu should let you mount vista partitions, usually it puts shortcuts in Places menu by default
if somehow they are not there then you will need some manual tweaking of fstab file

---

### Post by nikhilbhardwaj on 2009-09-02
post the output of
sudo fdisk -l

you need to add an entry for that partition in your fstab
you can find great tutorials at these forums
search for something like mounting ntfs partition

---

### Post by xxshifterxx on 2009-09-02
ok ill try.
can you plz post a link to a good guide.

---

### Post by TheNessus on 2009-09-02
> **xxshifterxx said:**
> So i recently installed ubuntu 9.04 on my pc..i was wondering how do i access my vista files without booting?

it's usually at /media/home. you of course need to mount it as just explained. you can also install some program that makes it mounted on every boot instead of handling it every time again.

---

### Post by xxshifterxx on 2009-09-02
HEre's the output you told me to post.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8         399     3148740    7  HPFS/NTFS
/dev/sda3   *         400       38662   307347547+   7  HPFS/NTFS
/dev/sda4           38663       38913     2016157+   5  Extended
/dev/sda5           38663       38913     2016126   82  Linux swap / Solaris

---

### Post by xxshifterxx on 2009-09-02
so what do i do next?

---

### Post by egalvan on 2009-09-02
> **xxshifterxx said:**
> I installed ubuntu 9.04 on my pc..
i was wondering how do i access my vista files without booting?

Err, without booting?

Without booting Ubuntu?

Without booting Vista?

Without booting the laptop?

:) :)

Seriously, Linux has excellent NTFS support, so accessing them from Ubuntu is no big problem.
maybe setting permissions, at most.

---

### Post by xxshifterxx on 2009-09-02
..with out booting ubuntu.

---

### Post by fluffman86 on 2009-09-02
Yeah it really should just show up under the Places menu, usually as 40.0 GB Media, or whatever the size of your partition is. 

Places is on the top panel, next to applications.

---

### Post by xxshifterxx on 2009-09-02
Mine says 3.2 gb media,here's what is inside the folder.
[http://img210.imageshack.us/img210/1147/screenshotcze.png](http://img210.imageshack.us/img210/1147/screenshotcze.png)

---

### Post by Vaphell on 2009-09-02
it's some kind of usb stick?
either way your windows partitions were not detected automatically because they should be right there, next to that 3.2 drive.

you will need to edit fstab file - it tells the system which partitions are to be mounted on startup.

---

### Post by xxshifterxx on 2009-09-02
And how do i do that?sorry im a big nub to ubuntu.

---

### Post by Vaphell on 2009-09-02
in terminal sudo gedit /etc/fstab

you will need to add a line for each of your partitions

mine looks like that:
# /dev/sda1
UUID=4848E3B648E3A0C4 /media/WinXP ntfs defaults,umask=007,gid=46 0 1 

here you declare where these drives should show up - everything is mounted as a directory and mounted drives generally are to be found in /media

according to your fdisk output NTFS partitions are sda2 and sda3
create dirs for them in another terminal window - let's say
sudo mkdir /media/Win1
sudo mkdir /media/Win2
these will be mount points for your NTFS partitions

find proper UUID values for them by running 'sudo blkid' in terminal and put them in proper places
UUIDs are not mandatory to identify partitions, but they are more reliable because they always point in the same place, unlike other methods.

---

### Post by egalvan on 2009-09-02
Open Synaptic and search for ntfs-3g.

If not found, install it.

---

### Post by xxshifterxx on 2009-09-02
Here are results for "sudo blkid. I really dont know the proper place :(
/dev/loop0: UUID="bfbbe266-75ce-4ae1-a6e7-88c8193909f5" TYPE="ext3" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D9-050B" TYPE="vfat" 
/dev/sda2: UUID="56B40082B4006739" TYPE="ntfs" 
/dev/sda3: UUID="1C0355DB52BD03FA" TYPE="ntfs" 
/dev/sda5: UUID="9cca911c-77c4-433d-bc72-616e4b79c8f2" TYPE="swap"

---

### Post by Vaphell on 2009-09-02
#dev/sda2
UUID=56B40082B4006739 /media/WindowsPartition1 ntfs defaults,umask=007,gid=46 0 1
#/dev/sda3
UUID=1C0355DB52BD03FA /media/WindowsPartition2 ntfs defaults,umask=007,gid=46 0 1

WindowsPartition1/2 are whatever names you want - they just have to be present in /media directory

---

### Post by xxshifterxx on 2009-09-02
> **egalvan said:**
> Open Synaptic and search for ntfs-3g.

If not found, install it.
It was not found so i installed it.So what do i do next please ?

---

### Post by Vaphell on 2009-09-02
chances are these drives will show up after reboot :)
and this whole fstab file excercise will make them mount by default at startup

---

### Post by nikhilbhardwaj on 2009-09-02
> **xxshifterxx said:**
> It was not found so i installed it.So what do i do next please ?

sudo mkdir /media/WindowsPartition{1,2}

gksu gedit /etc/fstab
#dev/sda2
UUID=56B40082B4006739 /media/WindowsPartition1 ntfs defaults,umask=007,gid=46 0 1
#/dev/sda3
UUID=1C0355DB52BD03FA /media/WindowsPartition2 ntfs defaults,umask=007,gid=46 0 1

then sudo mount
that should do the trick

---

### Post by xxshifterxx on 2009-09-02
> **nikhilbhardwaj said:**
> sudo mkdir /media/WindowsPartition{1,2}

gksu gedit /etc/fstab
#dev/sda2
UUID=56B40082B4006739 /media/WindowsPartition1 ntfs defaults,umask=007,gid=46 0 1
#/dev/sda3
UUID=1C0355DB52BD03FA /media/WindowsPartition2 ntfs defaults,umask=007,gid=46 0 1

then sudo mount
that should do the trick
lol it WORKED!!!!!!!!!!!
Thanks everyone who helped,appreciated very much:):D

---

