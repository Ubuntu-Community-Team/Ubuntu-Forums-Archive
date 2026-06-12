---
title: "Did I just kill my hard drive?"
date: 2010-07-24
forum: General Help
---

### Post by dgw on 2010-07-24
Ok, so I guess there was a grub update (can someone confirm that? I didn't pay enough attention). Back when I upgraded to 10.04, the computer wouldn't boot and I reinstalled grub. A few times since then after installing updates, I've had the same issue all over again, again solved by reinstalling grub. I kept thinking I'd figure out how to actually fix it or just do a clean install sometime, but it wasn't really a big deal. Until now.

I started my computer today and had the grub message. I didn't have a live CD handy (which is what I used in the past) but I did have a flash drive that I happen to have 9.10 installed onto, so I figured that would work. I couldn't get it to boot from the flash drive, so I pulled out the hard drive from the laptop and it would then boot from the flash drive. Then I plugged the hard drive into a little device that's supposed to connect it to the computer via USB like it's an external drive. The computer didn't seem to recognize that I'd plugged in a drive. First time I did sudo fdisk -l it said that there was another drive with a messed up partition table (sorry, I don't have the exact phraising of it). Now...nothing.

I plugged the hard drive back into the computer and tried to start it. No longer do I see the grub message, now it's giving me a "no bootable devices" message when I start the computer without a live CD or the bootable USB. 

The hard drive was making a weird noise when I had it plugged into the adapter device. Did I kill it?

I'm kinda freaking out right now.

---

### Post by mr clark25 on 2010-07-24
:(

the noise you are hearing is probably "the click of death"...
the noise comes from the hard drive heads.

do you have a backup of your data anywhere?

somewhere, i read about a fix for this... it will probably take some time, but ill see if i can find it.

---

### Post by dgw on 2010-07-24
I do have a backup, but it's older than it should be so I'll lose some things. Nothing crucial though. I think you're right about the noise being the click of death. Well, thanks.

---

### Post by mr clark25 on 2010-07-24
if you really want to keep the stuff that isnt backed up, you can get another hard drive just like yours, and swap the circuit board. (this is not guaranteed to work, but it could)

here is a youtube video that might be worth watching:
[http://www.youtube.com/watch?v=PoVBHG4kajA&feature=related](http://www.youtube.com/watch?v=PoVBHG4kajA&feature=related)
(yes, he is a windows user, but it was the best one i could quickly find...)

if you watch all of the video, he should answer many questions...

---

### Post by VioletCent on 2010-08-25
I am in the same situation as Dgw is

Last week, I upgraded my ubuntu to 10.04 version (I haven't use ubuntu for long). My laptop was working absolutely perfect. After few days using ubuntu 10.04 (properly 2 days, I remembered), I restart my laptop, my laptop started making "clicking noise", then the hard drive was dead :( ... sadly

I took the hard drive out, and plugged it into the hard drive dock. it is detected but i can't access to it. it keeps  warning "format" it. Should I try? will it help? (I guess not) :(

the warranty of my laptop is over. I am planning buy a new hard drive and install ubuntu again
Just want to make sure that it is just coincident

---

