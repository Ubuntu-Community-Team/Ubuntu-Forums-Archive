---
title: "non linux iso on a usb drive"
date: 2009-08-19
forum: General Help
---

### Post by nw68868 on 2009-08-19
My only computer is a mini 10v with jaunty, i would like to put some video dvds on it and MOST IMPORTANTLY i want to install startcraft on it. the bike shop i run has an optiplex tower with a dvd player and intrepid. so i want to put cds and dvds into the work computer and put them on an 8gb thumbdrive and them fool my mini 10v that there is a disk and install startcraft.

soooooooooooooooo.......

..........how do i do that?

---

### Post by Bachstelze on 2009-08-19
Just mount the ISO

```
sudo mount -o loop /path/to/image.iso /path/to/mount/point
```

---

### Post by nw68868 on 2009-08-19
do i just copy it from the cd to the usb drive?

can i partition the drive to put multiple disks on same usb key?

sorry im kinda a newb

---

### Post by Slim Odds on 2009-08-19
> **nw68868 said:**
> do i just copy it from the cd to the usb drive?

can i partition the drive to put multiple disks on same usb key?

sorry im kinda a newb

You can mount an ISO image from anywhere.

---

### Post by nw68868 on 2009-08-19
how do i get ISO to thumbdrive? the mini has no optical drive, this is the basis of the problem

---

