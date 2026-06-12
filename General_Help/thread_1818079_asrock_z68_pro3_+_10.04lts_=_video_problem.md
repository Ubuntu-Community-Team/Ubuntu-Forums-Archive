---
title: "asrock z68 pro3 + 10.04lts = video problem"
date: 2011-08-04
forum: General Help
---

### Post by then_dude on 2011-08-04
hello everybody

i got myself a brand new pc,

it has an asrock z68 pro3 motherboard and an i2500k proc. 
the screen is a dell u2311h 

the problem is i cannot get the resolution higher then 1280*1024. 

with 10.10 the monitor works perfectly, but the system crashes. 

so i want to use 10.04, which seems quite stable on my hardware, but could somebody please point me out how to fix this problem. 

please elaborate a bit, i'm a beginner

thanks so much
friendly greetings

---

### Post by then_dude on 2011-08-04
this is what i found on phoronix website

As I've been saying, Ubuntu 10.10 will not work fully with the Sandy  Bridge CPU's graphics as its stack is too old. Intel has been working on  Sandy Bridge open-source Linux support going back a year now, and some  of the DRM and DDX bits have been living in mainline trees for months,  but it's not the polished and proper support. For the proper Sandy  Bridge experience you are left looking for the Linux 2.6.37 kernel, Mesa  7.10, the latest libdrm, and the xf86-video-intel 2.14.0 DDX that  should be released in the next week or so. If you are trying to use  MPEG2 / H.264 VA-API video acceleration, you will also need to be  pulling libva (the VA-API library) from Git as the Sandy Bridge support  upbringing is in no official release either. 

the problem is: i'm a newby, can anybody help me out on how to perform these tasks.
do i really need a 10.10 or can i stay with a 10.04. 

it is pretty frustrating, i wished i bought an amd system, at least that would be supported. regrets for buying intel

---

### Post by then_dude on 2011-08-06
i got everything working fine.

the small history aka: the solution
1)run ubuntu 10.10 or 11.04
2)update bios motherboard to latest driver (1.60 in my case)


my new system: 
asrock za68 pro3
i2500K
ssd crucial M4 60 ggb
screen: u2311H dell

the long history:

1)started out with ubuntu 10.10: everything worked out of the box. ssd, sound (i have a usb dac), 
even my 1920*1080 monitor was working great: but then all of a sudden: hard crashes. 

2)i switched back to the old and trusty 10.04: everything worked expect the screen: i could not get it over 1280*1024; so the driver of the intel was lacking; i looked for solution on the internet, and found the post above. but implementing those solutions was not that easy. also again the system sufferd hard crashes. 

3)i switched to opensuse 11.4. A lot of people like suse very much, it's very stable and very tweakable.  so i gave it a go. and indeed the live disc install was running stable. no craches (at least for the short time i had it tested). i decided to upgrade the suse: and i lost wifi....

4)i had the suse dvd not at hands, but got it via my other pc, installed suse and it was stable, but there were problems with the videodriver too.  and i was shocked by the slow speed of suse. (it was just an out of the box installation, so i guess it can be tweaked into something lighting fast)

5)by that time i had red that the hard crashes were the result of an old bios and energy saving settings. so i flashed the bios. 

6)i was willing to go back to ubuntu. and popped in 11.04 disc, while i actually wanted to run the 10.10
but i thought let's check it out. so after a few minuts everything was running smooth and the resolution was okee. 

but i really set back to classic view with no effects. Good god what a bad creation that is : the GUI of 11.04. Also i want the fastest and most snappy system and i'm not willing to give an resources to some effects. so now i'm running stable as a rock  and everyhting works great. (except my DVBT dongle: which was always a pain). 

i'm willing to investigate in suse kde, but i hate distro's that start to look like fisher and price. (and the latest suse and ubuntu really look like that).

anyway that's my story
byebye

---

