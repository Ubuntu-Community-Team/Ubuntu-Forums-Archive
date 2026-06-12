---
title: "Does Ubuntu like laptops?"
date: 2006-01-30
forum: General Help
---

### Post by Knight on 2006-01-30
I was recently thinking of getting a laptop (first one) and was wondering about Ubuntu compatibility. But when I was googling around, I couldn't find any info on any Linux being tried on this laptop. I was wondering if anyone has tried, or if anyone knows some good links where I might be able to check compatibility with Ubuntu. The laptop in question is an HP  PC Portable Pavilion dv5017EA, with a Sempron 3000+, doesn't say if it's 32 or 64bit, I'm betting 32. Heres a link to it:
[http://www.surcouf.com/catalogue/ficheproduit.aspx?idproduct=9607023](http://www.surcouf.com/catalogue/ficheproduit.aspx?idproduct=9607023)
Sorry for it being in french, I can't find an english site for this pc. Any info would be much appreciated. Thanks in advance.

---

### Post by Scotland on 2006-01-30
Have a look here :-

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)


Dougie

---

### Post by earobinson on 2006-01-30
you could always test your laptop with a live cd.

---

### Post by bloodborne on 2006-01-30
I'm running Ubuntu exclusively on a laptop at the moment, so yes, Ubuntu does like laptops, but it does depend on your hardware. The biggest problems most people seem to have with Ubuntu on laptops is wifi. I worked for me out of the box, but others have to mess around with ndiswrapper (I think that's what it's called) to get their internet up and running. 

Like earobinson said, just try it out with a Live CD, it's your best bet to test out your hardware.

---

### Post by Knight on 2006-01-30
wow thanks for the timely replies! On the ubuntu site, this model isn't listed, and haven't actualy bought it yet but was thinking of picking it up today. Was thinking of bringing a live cd with me and seeing if they would let me test it on the demo machine they have out, but they might not, and I wouldn't blame them. Thanks again for the quick replies.

---

### Post by earobinson on 2006-01-30
Confirm: ndiswrapper

EDIT 01: If its a newer laptop chances of it working are usualy less since the programers havent had a chance to fiddle with it yet, But if you put in the time you should be able to get ubuntu working.
EDIT 02: If you do test it and the only problem is the wireless card then chances are you should be able to get it working with ndiswrapper like bloodborne said.

---

### Post by hw-tph on 2006-01-30
I run only Ubuntu on my HP nx9105 laptop. According to the specs of your laptop it could be similar (or pretty much identical) to the HP/Compaq R3000z series. If that's the case it should be pretty Linux friendly. We (from the Linux-R3000 mailing list) have a [wiki](http://prinsig.se/weekee) for the R3000z and similar laptops as well.


Håkan

---

### Post by wilem on 2006-01-30
I have an inspiron b130 from Dell and it works. I only have ubuntu on the machine. 

My only issue is a strange issue with sound coming from both headphone jack and the built in speakers.

---

### Post by m.musashi on 2006-01-30
I've installed Breezy on several Dell laptops at work (dual boot with windows) without problems. It's on Latitude D610s, an Inspiron m600 and an older D505 (I think). All of them work fine with Breezy and no install problems. Wifi was also recognized but it doesn't seem to like anything besides WEP encryption. There are some forum posts dealing with ways to use WAP but I never had any success with them. I've also had some trouble with switching between wireless and wired. The ethernet utility is not as good as it could be. Hopefully something that will get improved with time.

I'd bring the live CD to the store and get them to let you boot with it. The live CD won't mess anything up and you should be able to make sure something will work for you before you plop down a bunch of cash. If they have a return policy you could also buy it and try it and the return it if it doesn't work.

---

### Post by mdmarmer on 2006-01-30
Good idea is to buy at a store, take the live CD with you and try it out.  My experience is that Linux works very well on HP laptops, except maybe the Conexant winmodems, which can be made to work with Linuxant driver.  Other laptops such as Toshiba have more proprietary features and are slightly more difficult. Most problems are easily solved, but a few are not, and trying out the Live CD at the store may give you confidence when you buy.

Mike

---

### Post by Maggot on 2006-01-30
I have a Dell XPS Gen2 Laptop and have everything working great...sort of. I'm trying Kubuntu even though I'm not a huge fan of KDE. Its not working out too great....network interfaces don't seem to be wanting to go active, my sound buttons on the laptop don't work, the odd other glitch/bug occurred.

Running Ubuntu, I had no problems.  Wireless WPA2 worked without ndiswrapper, buttons for sound works.  Sure I had to fine tune/tweak the wireless and it was a bit of a pain but end result, it works! :-)

---

### Post by DarkKnight70 on 2006-01-30
I tried five  different distro and ubuntu was the only one that worked out of the box even the wifi. The only problem I have is I can't set the Encyption which really isn't a problem for me. My laptop is a little older but I thought I would put the information out there. It's a Dell inspiron 4000 with an Intel PRO/Wireless 2200BG wireless card. I hope this helps someone. I too am not running ndiswrapper.

---

### Post by RavenndudE on 2006-01-30
I'm running ubuntu on a Gateway MX6030 and most things work great. I did have to use ndiswrapper for wifi and some of the hot key on the laptop don't work (but that doens't matter, i'm using synergy to share mouse / keybopard with my windows machine)

---

### Post by pbailey on 2006-01-30
Works great on my old Dell Inspiron 8000 :)

---

### Post by ronmarley1 on 2006-01-30
I'm running it on an IBM R51 and it runs great.  No hardware problems; worked great on first install.

---

### Post by IYY on 2006-01-30
Works very well on my NEC laptop. It's a 333 MHz Celeron, circa 1998. 

Touchpad, D-Link NIC (DWL G650, Atheros based), 800x600 resolution, and everything else worked right after the installation. 

Gnome was too slow, but Fluxbox Dillo and Konqueror as browsers works just fine. 

Most Linux and BSD distros I tried on it required some configuration to get these stuff to work. I'm impressed.

---

### Post by RikoW on 2006-01-31
Hi,

just want to add briefly my experience with Ubuntu on Laptop! Works like a charm on Dell Latitute D600 with ATI Radeon 9000 Mobility Graphics (I use the xorg drivers so that suspend/hibernate works),  Intel Pro 2100 wifi card and broadcom Netxtreme BCM5702X gigabit lan card. It's a dual boot with XP but I hardly boot it up under XP anymore only to update windows and virus signatures ... just in case :)

I work in a typical office enviroment and do some programming on the side. In my office the laptop sits in a port replicator with external keyboard, mouse and TFT screen. works great, just for undocking and docking you should shut the machine down. not a big drawback.

for other resources on Linux on Laptops for plenty of models/distros, check also these sites:

[http://www.linux-on-laptops.com/]("http://www.linux-on-laptops.com/")
[http://tuxmobil.org/]("http://tuxmobil.org/")

I converted from SUSE to Ubuntu and never regretted. And I encourage you to try you laptopof choice with the Ubuntu Live CD. Easy way and quick way to test what works out of the box and what doesn't.  

Good luck,

                Riko

---

### Post by Burgundavia on 2006-01-31
Ubuntu loves laptops. I encourage all laptop owners to report all bugs that they find, including minor things like SD card readers and the like. The hardware should work as well as in Windows or OS X (I make no claims about the quality of the original OS).

If you have more time, you can join the laptop testing team. It can be found at:

[https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

Corey

---

### Post by thoffland on 2006-02-01
I'm running Breezy on an old Dell CPx. I've loaded the Ubuntu Server base and I'm using fluxbox as a Window Manager. Ubuntu recognized my wireless pcmcia card (Airlink) during the install and allowed me to download the rest of what I needed from the net.

I have tried, however to run the live Hoary cd on my HP Pavilion 5500 without any luck getting the built in wireless adapter to work. Maybe it's the difference between Breezy and Hoary or the hardware... I dont know.

---

### Post by thoffland on 2006-02-01
I'm running Breezy on an old Dell CPx. I've loaded the Ubuntu Server base and I'm using fluxbox as a Window Manager. Ubuntu recognized my wireless pcmcia card (Airlink) during the install and allowed me to download the rest of what I needed from the net.

I have tried, however to run the live Hoary cd on my HP Pavilion 5500 without any luck getting the built in wireless adapter to work. Maybe it's the difference between Breezy and Hoary or the hardware... I dont know.

---

### Post by polo_step on 2006-02-01
[FONT="Fixedsys"]Lots of problems with mine, a new ECS 536S (AKA GQ ZX-5360).  The usual stuff:  Modem, WiFi and video are flat not supported from install, so I didn't even bother to go beyond that, figuring I was flogging a dead horse.  Timely hardware support is the weakest link with Linux.  

Linux driver development has forked for at least two of these devices, too.:cry:

Maybe in the next release?[/FONT]

---

### Post by sunny_nwho on 2006-02-01
Actually even I run Ubuntu from my Laptop and it is gr8 working on Ubuntu...my laptop is an ACER FLCi 290 Travelmate and i can do every thing I can in Windows at more ease and without the hassel of installing new drivers and no spyware or adware or virii on my system.....I wish whole of my university uses ubuntu....

---

### Post by alamba on 2006-02-01
Working great on both my laptops - HP dv1350ea and Thinkpad T41.

Akshay

---

### Post by ps2gimp on 2006-02-01
Works great on my 6 year old Tosh Satellite :)

---

### Post by nikosft on 2006-02-01
It works great for me in my Fujitsu Siemens Amilo A. Except from the wifi card. I wuld suggest also to not by an 64bit processor laptop. I had big difficulties with 64bit version and I had to use 32 bit. What I like most,and other distributions couldn't achieve, is that informs me correcty about the status of my battery.

---

### Post by bigken on 2006-03-17
Works well on my dell Inspiron 9200 had do some cofiguring to get touch pad to work properly and the ati graphics no support for the built in sd reader not a big 
issue in windows xp i have to install at least 10 different drivers so id say ubuntu is a easier install and a lot more fun \\:D/

---

### Post by earobinson on 2006-03-17
I seem to have installed it without any problems.

bigken, any idea where I an get one of those stickers for my laptop (just got it) I know there was a thread on it some place but I cant seem to find it.

---

### Post by OMRebel on 2006-03-17
Works perfectly on my HP Pavilion n5150.  Even the little volume buttons on the front of the laptop case works!  I didn't have to manually configure anything, as everything worked 100% out of the box.  Granted, it's a bit of an older laptop, but it runs extremely quick with Ubuntu.

---

### Post by crxyem on 2006-03-17
Works well on my Dell Inspiron 6000, only thing I can't get it to work with is the internal SD card reader. I had to use ndiswrapper to get my wifi working. had to configure the touch pad a bit , other than that works seemlessly.

---

### Post by dasunst3r on 2006-03-17
I have a Dell Inspiron 6000, and my experience of Ubuntu (or Kubuntu, rather) on laptops was not as pleasant (in terms of hardware).  For some reason, processor usage drove the processor temperature up to an insane 70 C compared to the 40 C I would see normally, and the fan would be on full blast, which makes the computer real noisy.  Hope your experience will be better than mine.

---

### Post by bigken on 2006-03-17
[QUOTE=earobinson]I seem to have installed it without any problems.

bigken, any idea where I an get one of those stickers for my laptop (just got it) I know there was a thread on it some place but I cant seem to find it.[/QUOTE]
Sorry mate I dont I got the image from the thread in this forum you could try ebay hears some links in the forum

[http://www.ubuntuforums.org/showthread.php?t=113001&highlight=laptop+stickers](http://www.ubuntuforums.org/showthread.php?t=113001&highlight=laptop+stickers)

[http://www.ubuntuforums.org/showthread.php?t=71614&highlight=laptop+stickers](http://www.ubuntuforums.org/showthread.php?t=71614&highlight=laptop+stickers)

---

### Post by Strike&gt;&gt; on 2006-03-17
I installed ubuntu on my freinds laptop, and everything worked just fine. His was an acer with an amd chip. Though he had some problem with his wireless card.

---

### Post by lordofkhemenu on 2006-03-17
I'm running Ubuntu (first Breezy, now Dapper) on my [Gateway 450ROG]("http://support.gateway.com/s/Mobile/Gateway/450ROG/3501353sp66.shtml") (similar to the 450X w/ minor differences, i.e. LCD size).
Everything was detected and worked "out of the box" - 
The integrated Centrino wifi
The LCD res was automagically at the max (1400x1050), when other distros failed and set it to anything between 640x480 and 1024x768.
The *ONLY* real change I made was to my xorg.conf file. All did was change the video driver section from 'vesa' to 'ati', restarted X, and Voila! Direct Rendering.

---

### Post by killua_kd on 2006-03-17
well I currently run ubuntu (dapper drake) on a pavillion zt3260ea and it works like a charm. but I think there is always a chance of some strange behaivior so you better test with a live cd

---

### Post by ArizonaKid on 2006-03-17
I am running Ubuntu 5.1 on a HP Compaq NC6220, and overall I am very pleased with the performance.  I have tried Gentoo, SUSE, and Fedora Core 4 on this notebook.  Ubuntu is by far the most friendly to this notebook, and I have heard the same results for many other notebooks in general.

I made a few minor tweaks to get the wireless LCD light to work (not really a significant issue), but most everything else just works.

Some problems I have not found resolution to:
+Sound usually stops working after "suspend" mode.  
+WPA access is not availible, but this could be because I am new to Linux (n00b) and have yet to find a solution.
+Notebook can hang after hibernation mode, and closing the lid doesn't always put it in the proper mode.

Like I said, solutions may exist to these problems, but I wouldn't consider them intuitive.  I continue to dual boot Windows and Ubuntu, but typically operate most of the time in Ubuntu.

---

### Post by ArizonaKid on 2006-03-17
One more thing to consider is that I don't believe Automatix is going to be availible until the official release of Dapper.

This keeps me off Dapper, since I rather not spend time getting all the little stuff that Automatix takes care of working.

---

### Post by otaviofcs on 2007-01-31
I have 2 notebooks with ubuntu installed. Now 1 is using 6.10 and the other 6.06. Both work well (one is a Toshiba and the other an Accer). The Accer notebook have a video chipset SYS (argh!!!!) and every time you start the machine it has a little bug loading X (the screen gets all black) Making  a ctrl+alt+f1 and then ctrl+alt+f7 it becomes working nicely. 

The toshiba, with everything Intel Inside :), works well. The only problem that I have is that it randomly have a suspend issue that makes me restart (sort of kernel panic). Images at attachment. I couldn't  fix it out and its hard to repeat the problem (at least for me). But it's been an year without a ctrl+alt+del stuff :D .

---

