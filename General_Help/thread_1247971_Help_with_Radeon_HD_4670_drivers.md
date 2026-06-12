---
title: "Help with Radeon HD 4670 drivers"
date: 2009-08-23
forum: General Help
---

### Post by Raeannmac on 2009-08-23
Hey everyone!
I've been using Ubuntu/Kubuntu for over 2 years now, but never had an issue with graphics (oddly enough, with intel graphics), but I've recently bought a new computer and have had 2 graphics cards: an onboard NVIDIA which worked fine, and now a Radeon HD 4670 which has given me a LOT of trouble :(
I've had to re-format over and over again, as after I first boot it up (in safe graphics mode) and install the drivers (either through envy or the hardware app) it seems to work so I restart as prompted.  Upon startup I put in my password (everything seems to have worked thus far...proper resolution and everything) and then the black/grey bubble splash thing starts to flash and after a while I can see bits of my desktop but it still keeps flashing.  There is always a notification that pops up, such as kwallet or the network security thing except they're all distorted and it always goes back to the splash.  I've waited as long as half an hour one time and still couldn't use my desktop.
I've tried updating through the terminal in safe mode but it does nothing and I have nooooo idea what to do now (and I Definitely don't want to have to use windows 7 as my primary os!)

Specs:
HP a6700f
AMD Phenom 9150e x4 1.8
500 gigs
4 gigs ram
...

Does anyone have any idea as to what's going on?

Thanks for any help!!

-Rae

---

### Post by Raeannmac on 2009-08-23
Does anyone know if it would be possible for me to switch between my two graphics cards, using my onboard Nvidia for linux and my ATI for Windows 7? I did try plugging in my monitor to the Nvidia but the screen came up black... is there anything special I should be doing to force the computer to use the onboard card? Any help will be greatly appreciated... Thanks!

---

### Post by markbuntu on 2009-08-23
You can use one or the other with ubuntu, but not both since the drivers are mutually incompatible. You need to disable the nvidia in the bios  and completely remove any nvivia driver and its kernel modules before you can get the ati driver installed and working properly. 

And do not use Envy or the driver from hardware manager but get the latest one from ati and run the installer.

---

### Post by Raeannmac on 2009-08-23
Well that definitely worked! Thanks for giving me the courage to give up on envy lol...I never would have tried the manual install before your post, and yet it seems to have worked! I followed the guide from the wiki and am currently viewing my screen at 1680x1050 once again :)

---

