---
title: "Boot/login seems to be too slow for the hardware"
date: 2009-09-28
forum: General Help
---

### Post by a1ek5ant3ri on 2009-09-28
My computer seems to be very slow during booting and when loading after login.
It is a newish install, maybe August 18th, of 9.04 x64 on a self-made PC
This is my first time posting on the forums. Normally I search until I find an answer, but I feel that this is too specific.

The system specs are:
Asus P5n-D mobo
Intel E8500 Core 2 Duo 3.16 GHz
8 GiB of 800MHz DDR2 g.skill ram
500 GiB Western Digital SATA HDD
XFX 9800gt 512GiB graphics card

OS:
9.04 jaunty
2.6.28-15-generic
GNOME 2.26.1

Not really necessary specs: 
500 watt PSU
Gigabyte wlan card

Boot to the login screen takes around 30 seconds and after login it takes ~15 seconds more to load everything (mostly the gnome panel at the top)
I do not have too many unnecessary programs loading on startup: pidgin, gnome-do

In comparison with a 1.8 GHz, 512? GiB ram, onboard video, 30 GiB IDE hdd, system with xubuntu and a boot time in the 20s, this seems slow. . . 

awaiting any help or suggestions, 
al

---

### Post by doas777 on 2009-09-28
> **a1ek5ant3ri said:**
> My computer seems to be very slow during booting and when loading after login.
It is a newish install, maybe August 18th, of 9.04 x64 on a self-made PC
This is my first time posting on the forums. Normally I search until I find an answer, but I feel that this is too specific.

The system specs are:
Asus P5n-D mobo
Intel E8500 Core 2 Duo 3.16 GHz
8 GiB of 800MHz DDR2 g.skill ram
500 GiB Western Digital SATA HDDit just allows us to be lazy,  
XFX 9800gt 512GiB graphics card

OS:
9.04 jaunty
2.6.28-15-generic
GNOME 2.26.1

Not really necessary specs: 
500 watt PSU
Gigabyte wlan card

Boot to the login screen takes around 30 seconds and after login it takes ~15 seconds more to load everything (mostly the gnome panel at the top)
I do not have too many unnecessary programs loading on startup: pidgin, gnome-do

In comparison with a 1.8 GHz, 512? GiB ram, onboard video, 30 GiB IDE hdd, system with xubuntu and a boot time in the 20s, this seems slow. . . 

awaiting any help or suggestions, 
al

I've built many high-perf systems over the years, and they never boot much faster than a mid-perf in their classs. your HDD is the bottleneck.

the fact of the matter is, that you get less and less bang for the buck the more you spend. if you need the 400$ vidcard to play your game, get it, but it won't add anything to the mix except the ability to play your game.

---

### Post by P4man on 2009-09-28
sounds about normal to me. especially if you have installed stuff like compiz or virtualbox, both of which seriously increase boot time.

Like the above poster said, bottleneck in booting is not cpu or ram, its harddisk. If you want uber fast boot times with gnome, then break the bank and buy an ultrafast SSD. here you see a youtube clip of a computer with similar specs to yours, but using an SSD:

[http://www.youtube.com/watch?v=bqefSHEx7kE&feature=related](http://www.youtube.com/watch?v=bqefSHEx7kE&feature=related)

Ubuntu booting in 13s..

---

### Post by a1ek5ant3ri on 2009-09-28
thanks for the insanely fast reply(s, by the time i had written this, there was a second reply. . . i love the forums)

i don't really use it for anything too intensive, but when i was building it i was planning with the future in mind. i hope to get 5 or six years out of it, hopefully through college.  i can always get a new (or used) laptop if i need something faster.  it's only the boot that is slow. i opened 100 5MP pictures with the gimp and that took some time, but didn't use more than 3 GiB of memory. . .

---

