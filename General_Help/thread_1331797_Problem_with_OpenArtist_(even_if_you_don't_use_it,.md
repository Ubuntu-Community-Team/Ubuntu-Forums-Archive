---
title: "Problem with OpenArtist (even if you don't use it, you could still be helpful)"
date: 2009-11-19
forum: General Help
---

### Post by razor180 on 2009-11-19
I know OpenArtist is different than normal Ubuntu, but it was based on ubuntu 8.04 hardy heron and had some of its kernels upgraded to 9.04 jaunty, but its core is still 8.04 and some of its kernels are still different, but because its core is still ubuntu, the same or similar methods to fix these problems should still work, and I'm posting here because I'm getting no reply on the OA forums

anyways, I have 3 main problems (problems I can't seem to fix on my own)

1. During the setup process when I installed OA, I set a user and pass, but it's still using the default tux/tux setup, I don't know if it's a bad install, but it seems to think it's still running off of a live disc even though I formatted it to my hard drive (all 500gb of it)

2. I'm having problems setting up my second screen (again), and whenever I try, one of a few things happen. A) it will stretch the desktop and maximized windows across both screens (not messing with the resolution, it just doubles the horizontal resolution). B) Instead of having access to both screens, it will just clone the screens, but there's nothing in my settings that allows it to do that. Now I may know partially what's causing this, while xserver may be recognizing both screens, this screen resolution program that's embedded into this OS is not, it's only recognizing one, could it be that xserver and this program are having a conflict? I didn't have this problem in ubuntu studio 9.04, but then again it didn't have this screen resolution program

3. I can't get my wacom bamboo fun tablet to work. It's being recognized by the OS, but whenever I bring the pen over or the wacom mouse, it will not work, the cursor isn't moving at all, presses, clicks, taps, and the keys on the tablet itself are not being recognized, I don't even have a remote idea of what's causing this

I'm thinking I may just reinstall the OS, I looked and the OA disc I used has some scratches, so I might get another dvd and just reburn the OS onto a brand new disc and reinstall the OS and see if that fixes my problem because as far as I know I'm the only one that's having this problem. but I want some guidance on this and the other 3 problems I'm having first

---

### Post by razor180 on 2009-11-19
I also can't edit my partition, I'm planning on reducing the partition from 500gb to 300 and load ubuntu karmic on it, but I can't get it to work (atleast not graphically)

---

### Post by razor180 on 2009-11-20
I know it's a triple post but I figured it might help to get someone to help me

if it helps with the user thing, I'm not getting the login screen when I choose my openartist OS, it just shows the linux shell, initializes everything, then the desktop pops up and all of the startup programs start, so no log in screen, and this is what it would do when I would run it as a live disc, so it's starting to bother me

---

### Post by P4man on 2009-11-20
Kinda hard to say if those are openartist specific problems or not. Since you can install all those apps on ubuntu anyway ( I imagine?), I would suggest trying that first.

You say you cant resize the partition from the livecd, can you post the output of

```
sudo fdisk -l 
```

Or if the partition you want to resize is inside a blue extended partition, then try right click on the swap partition and select "swapoff". Then try again.

---

### Post by lisati on 2009-11-20
> **razor180 said:**
> 

1. During the setup process when I installed OA, I set a user and pass, but it's still using the default tux/tux setup, I don't know if it's a bad install, but it seems to think it's still running off of a live disc even though I formatted it to my hard drive (all 500gb of it)


Apologies if you've checked this already: Do you still have the installation CD in your CD drive?

---

### Post by razor180 on 2009-11-20
> **lisati said:**
> Apologies if you've checked this already: Do you still have the installation CD in your CD drive?
no, that's the strange thing, no the disc is in the dvd case, not my disc drive

I'll try that for the partition, thanks

and I don't think I can edit it with teh disc because the disc doesn't act like it does on the normal ubuntu images, it acts like the grub bootloader

---

### Post by razor180 on 2009-11-21
okay, I tried installing the latest drivers from the linux wacom project, I got them installed and nothing happened, then I reinstalled the ubuntu drivers and nothing happened (although I'm thankful for the documentation on the ubuntu site)

so it's not the drivers

---

