---
title: "New ubuntu User, Help?"
date: 2010-11-07
forum: General Help
---

### Post by Nortesidin on 2010-11-07
Hey everyone.. Would like to say WOW..and thanks to the developers! ubuntu is absolutely amazing. i was given a free computer today, a 1.2ghz athlon with 512 ram, and a 16mb video card.. lol. was scrambling around the house going frantic looking for my spare XP cdkey and cd, and found an ubuntu CD a friend gave me. i LOVE it. and its free?! nice!
Anyways, heres the issues i am having, some advice would be greatly appreciated.

The videocard i have is a "NVD01.0" model number. It works, but its very choppy on internet sites and main screen. It has 16MB of memory and is AGP.
I cannot find a driver for linux for it.. Would i be better off using my onboard video?
Again this was a free computer so i dont need advice to buy new stuff lol. Using it strictly for internet use and c# programming. (as well as random filestorage)

Any advice? Thank you in advance.

-Ryan

---

### Post by Bucky Ball on 2010-11-07
Xubuntu would be faster again on your old machine. Have you opened a terminal and installed 'ubuntu-restricted-extras'? Your video choppiness may have nothing to do with the card but the fact  you haven't the right codecs and plug-ins for Firefox to handle Youtube,  etc. When you go to Youtube are you invited to download the latest  Flashplayer for Linux?

What release number of Ubuntu are you using? I would suggest getting onto one of the long term support releases (8.04 or 10.04 preferably). You might find better results.

A tip: 8.04 LTS=2008, April release. 10.04 LTS=2010, April release. If you are running 7.04 you are pretty much obsolete. No longer supported release. If it works and others won't stick with it but you will not receive updates. :)

---

### Post by Nortesidin on 2010-11-07
sorry but i havent ever used linux so i am very unfamilliar. I have ubuntu 9.10 I just installed the latest flash player plugin so flash is working,  its just every website i go to, graphically intensive or not, is horribly choppy and laggy.

---

### Post by Bucky Ball on 2010-11-07
Well, is a 16Mb card ...

You might try install 'Envy' which will choose an nvidia driver appropriate to your card for you. Beware though; it doesn't always choose the right one! Still, can always reinstall at this early stage.

Your first suggestion is not unfeasible; try swapping to the onboard graphics chip and see if you get an improvement. If so you can always chuck another RAM stick in there which will help with the RAM the onboard graphics sucks up. For a machine like that pretty cheap (unless you have a couple lying around).

---

### Post by Nortesidin on 2010-11-07
sorry but where can i get envy? i searched google for 20minutes on a download, but only got guides on how to install it..

---

### Post by Nortesidin on 2010-11-07
Im going to sleep, going to conquer this in the morning with fresh eyes. Could someone please point me to the "envy" download and how to get envy working? Much appreciated.

-Ryan

---

### Post by DeMus on 2010-11-07
> **Bucky Ball said:**
> Xubuntu would be faster again on your old machine. 

My experiences with Xubuntu are not that great. I used it on an old Dell Latitude 110L laptop and saw no differences in speed compared to Ubuntu.
Now I use Lubuntu, based on the LXDE desktop, and it turned the "Fiat" into a "Ferrari". So if it is speed you need, use Lubuntu.

---

### Post by kanishkdudeja on 2010-11-07
Download it from here..

[http://linux.softpedia.com/get/System/Software-Distribution/Envy-36960.shtml](http://linux.softpedia.com/get/System/Software-Distribution/Envy-36960.shtml)

---

### Post by kanishkdudeja on 2010-11-07
also check out..

[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Install_Latest_Nvidia.2FATI_drivers](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Install_Latest_Nvidia.2FATI_drivers)

---

### Post by Nortesidin on 2010-11-07
"Error: Dependency is not satisfiable: libstdc++5"

I get this error when its done downloading.
again sorry for my inexperience.. new to linux..

---

### Post by edward1978 on 2010-11-07
Wow, what is the card? Maybe put card name linux drivers in Google will help.

---

### Post by dino99 on 2010-11-07
whith your old hardware you might choose "light" config and use (if possible the builtin video chip on MB if it is stronger than the 16mb one.

from synaptic: (on top menu: system admin synaptic)

search for: ubuntu-desktop and install it
search for: lubuntu-desktop and install it

about video driver: if none nvidia work well, try xserver-xorg-video-vesa or xserver-xorg-video-nouveau

---

### Post by edward1978 on 2010-11-07
[FONT=ARIAL][SIZE=2]**Support Mail:**[/SIZE][/FONT]                                                                [EMAIL="webmaster@nvidia.com"]**[FONT=ARIAL][SIZE=2]webmaster@nvidia.com[/SIZE][/FONT]**[/EMAIL] might help, not sure if the address works.

---

### Post by dino99 on 2010-11-07
> **edward1978 said:**
> [FONT=ARIAL][SIZE=2]**Support Mail:**[/SIZE][/FONT]                                                                [EMAIL="webmaster@nvidia.com"]**[FONT=ARIAL][SIZE=2]webmaster@nvidia.com[/SIZE][/FONT]**[/EMAIL] might help, not sure if the address works.

nvd01 is from VisionTek (no more existing) with STB system chip

( so nothing related to nvidia)

---

### Post by Nortesidin on 2010-11-07
any ideas anyone? also an update, i went to youtube to try and watch a video, i was literally getting less the 1 frame per second..

---

### Post by Nortesidin on 2010-11-07
theres an nvidia sticker right on the video card. going to try your ideas, i will report back with results in a few.

---

### Post by dino99 on 2010-11-07
give the output related to video only:

sudo lshw

---

### Post by Nortesidin on 2010-11-07
okay i did the lubuntu desktop thing, it said i already had the ubuntu desktop package... so i installed it but dont see any performance increase

---

### Post by Nortesidin on 2010-11-07
If this helps:

 *-display UNCLAIMED
                description: VGA compatible controller
                product: NV4 [RIVA TNT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 04
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-1.0 bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5

---

### Post by Nortesidin on 2010-11-07
okay i applied the lubuntu desktop package and now my internet doesnt work, had to go over to my other computer.. any ideas?

---

### Post by Nortesidin on 2010-11-07
fixed internet, it disabled itself.

Tried swapping to my onboard.. when i booted up screen was all black. Do i have to switch devices from ubuntu some how?

---

### Post by goldshirt9 on 2010-11-07
sorry for just reading this thread but what  linux are you trying to install :confused:

with your old spec i'd try a specific netbook edition.
damn small linux / puppy linux .
a newer edition may just be too much / demanding

---

### Post by Jetso on 2010-11-07
I've never used envy, but try this: ```
sudo apt-get install envy
``` In the terminal. It might not be the right name to download, but if it is it will get all the dependencies. If not go to System>Administration>Synaptic and search for envy, that will get the dependencies too.

---

### Post by Nortesidin on 2010-11-07
what steps do i take after installing envy?

---

### Post by Nortesidin on 2010-11-07
well i have changed to onboard, and i dont even get into the login screen, it goes to a command line screen and my monitor blinks on and off, however at the bios menu it doesnt turn on and off.

---

### Post by Jetso on 2010-11-07
What does aforementioned command line say? Try ```
startx
``` that should start everything...

---

