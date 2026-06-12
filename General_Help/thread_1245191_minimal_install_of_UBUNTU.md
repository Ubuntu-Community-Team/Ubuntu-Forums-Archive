---
title: "minimal install of UBUNTU"
date: 2009-08-20
forum: General Help
---

### Post by Kniste on 2009-08-20
Gddey Gents. 

I have been trying for a number of days trying to install UBUNTU on my Sony PGC505G. Unfortunately i have been hampered by my own stupidity and the habits of Sony to use proprietry hardware.  
The SONY is one of these tiny notebooks with external Floppy, external CDrom which does not work . 
The machine has 300mhz processer, 192mb ram and a 2gig HDD. the only input that I currently have to the Sony is Keyboard, Mouse, and the external floppy. there is a USB 1.1 slot but the operating system is DOS and I have not figured a way to get dos to recognise it. 

DOS
so far: i have tried a plethora of dos boot systems, dos 6.2, Dos WIN98 but am unable to find a (free) driver to load to recognise the USB. 

Now to linux: 
DSL: I loaded DSL onto a USB drive and then created a boot floppy. with this i was able to boot from the floppy and load a live DSL on the machine. 
why: this prooves that the USB slot works. 

I then installed DSL onto the HDD, everything looked good, came to the end, booted and nothing from the HDD. 

back to dos: fdisked the HDD into 2 portions, 1.8gig C and the rest D. Installed (copied) DOS programs onto the D and tried again with DSL, again was unable to bootDSL from the HDD. 

C is now in the ex2 format. booted from the DSL floppy, loaded live DSL, installed to the first partition HDD from the USB stick, came to the reboot and was unable to reboot from the HDD.

so with a floppy working, HDD working can anyone tell me if it is possible to 
1   boot from a floppy
2   point to a USB which has UBUNTU loaded 
3   and then install UBUNTU onto my HDD (to boot)
stage 4 would then be to get the PCMCIA slot working and i would then have a very clever very small machine. which was ultra portable. 

After all this Bla-Bla. the question i have is: 

is it possible to install UBUNTU to a HDD with a computer that only has a bootable floppy, keyboard and mousepad -- and a non bootable USB (from the BIOS) slot. 

the other handicap I have is my YOB, this is not an abbreviation for YOBBO, 

Thanks for any help

Steve

---

### Post by coldReactive on 2009-08-20
--- Delete Post ---

---

### Post by oldfred on 2009-08-20
With 2GB and 192mb memory Ubuntu will not work. Even Xubuntu will not be very fast.
I have an old Toshiba that had 128k of memory and I was able to install Ubuntu from a CD but I think it took over 8 hours to install and a similar time to update. It was a dog.
My only access to the internet was a USB port so I purchase a $5 USB to ethernet converter which worked for Ubuntu.
I installed DSL and it worked at reasonaly speeds, but would not use the ethernet adapter. Same with Puppy.  It turned out the adapter did not work with linux 2.4 and some versions of 2.6. Zenwalk had updated to the newest kernel (this was in 2008) and it ran reasonably well and worked on the Internet until they did another update.

Use a supergrub floppy to boot and choose a lightweight linux for the USB.
Some info:
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
[http://www.supergrubdisk.org/wiki/USB_Boot](http://www.supergrubdisk.org/wiki/USB_Boot)
[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

---

### Post by Kniste on 2009-08-21
thank you OldFred,

it looks like my options are DOS, win 98 or older, or one of the small footprints Linus, DSL has reported an install 3 times but refused to boot from the HDD,

do you have any suggestions for a linux which would work on the above config.

my hope is to leave this small PC as a small mobile browser!

thanks for any suggestions.

---

### Post by justleen on 2009-08-21
Im running Debian 5.0 + LXDE on a similar specced machine (HP Thinclient, 512mb disk, 256 mb RAM, some weird brand CPU running @400Mhz), that works fine. Though patience is needed, since its not fast. But it is workable. 
Another lightweight is Sidux (stripped down LXDE).

On this same machine I have had ubuntu running too. I started out with the Alternate CD to install a CMDline only system, and from there installed openbox.

Crunchbang linux might be a good alternative too, though i have tried that on my thin client.

Really light light weights:
Puppy is already been mentioned, which is very good in my opinion.
DSL is pretty good to. If your hardware is not fully supported with DSL, try Not Damn Small Linux (N-Dsl), which is still pretty small, but they added qite a lot of hardware support 
Slax is quite impressive looking too, and very lightweight (looks best imho)

---

