---
title: "Failing to boot ANY distro- AsRock P43DE3 board- is it just incompatible?"
date: 2011-01-19
forum: General Help
---

### Post by dave.kts on 2011-01-19
Anyone have any experience with this board?
I'm having trouble getting any distro of linux to boot properly. Fedora KDE seems to be the only one that would work installed but even the live CD was giving me occasional trouble. I need .deb support tho for my android tethering, so I prefer a debian based distro.
I'm not really too much of a newbie when it comes to linux, but when it comes to this new motherboard I'm stumped. I've had pretty good luck with my old setup, and was able to get ubuntu working good on my old gateway laptop, but everything I try on this setup just leads to hanging boots about 2/3rds of the time.

I've tried ubuntu 10.10 + 10.4, recent Kubuntu, Mint 9 and 10 (never booted once after instal), Debian 5.5, Knoppix, AV linux, Artist X (wont even boot live cd) and a couple others, and all of these refuse to boot, just a blinking cursor and a blank screen, no keyboard lights or anything, no drive activity. Once in a while it boots fine and the whole system is working nicely, some distro's are nicer than others. Some of these the live CD's wouldnt boot right either.
Knoppix seemed to work the best off the live cd, so i installed that one, and again, the 3rd time I try to boot it, i get nothing. 
Ive tried booting with no usb devices pluged in, same result.
Ive tried installing different variations of filesystems, no result. 
Only thing in my system that might not be getting along is a M Audio Delta 1010lt audio card. Using it in my Windows XP Audio workstation, booting fine and working as good as XP can.

Again, grub is working, but most of these distros i get nothing but a blinking cursor after i select it in grub. Windows boots perfectly.

3 new hard drives, WD black (640), Spinpoint F3 (500), Seagate single platter (500)

4 gigs of New and Memtested Gskill DDR3, selected out of my motherboard's Ram support list

Nvidia quadro fx550- drivers installed in ubuntu and worked great, was playing Open Arena

New ASRock P43DE3 board, squeezing some life out of a P4 prescott 3.2... I am overclocked (thru BIOS) to 3.67, been running it in windows and pushing it hard mixing music, never had any trouble.

***M-Audio Delta 1010lt PCI card***
For some reason, between messing around bouncing back and forth, installing windows and trying out Linux and the 100's of reboots in all this, (I even had huge trouble attempting to clone XP after I got all my software installed)... I had to pull the card and RESET CMOS at one point, it was taking 2 minutes to pass POST. onci I did this it was fine.

I'm pretty sure that audio card isn't showing up in any distro (when it boots into it) so I'm wondering if its giving it trouble at boot.

-OR-
Am I having a problem with SATA drivers or something? It was a pain getting the SATA drivers (asci drivers or whatever) loaded right in my XP install. (had to bust out the FLOPPY drive haha) but i think thats just XP for ya.

I did get a " failed to mount on dev\ something something error on one of the live CD'd that i tried. and then it just stopped. Im afraid i have no more usefull information for you tho.

Right now I have Fedora KDE 14 installed ant it boots about 75% of the time, the best of any.

---

### Post by tredegar on 2011-01-19
Not much from the search engines about linux with this MoBo, what there is is not helpful.

Some things to try:
> I am overclocked (thru BIOS) to 3.67
I'd undo this for a start. 

Try booting again.

Check your BIOS for SATA options ("legacy", and similar adjustments)

Try booting again.

> I'm pretty sure that audio card isn't showing up in any distro (when it boots into it) so I'm wondering if its giving it trouble at boot.
Try removing the card, you can always fix the audio later.

Try booting again.

Be logical about your approach, change one thing at a time, keep notes.

---

### Post by sum1nil on 2011-01-19
Would seem that if you can boot the livecd then your board is fine.

So if the board is fine and you can get to grub - try to find a way to pass options to grub so it boots in text only so you can see all the nice info linux produces. There has to be a kernel panic or more (hopefully) your X server can't start.

If there is no runtime option for grub and you can peruse and alter your files from  some live cd then there is a way to force it (if you want)
***Warning the file says dont alter me (but I have done so w/o a problem)***
Browse to /boot/grub/grub.cfg (hopefully it exists on your install - this is grub2.0)
at the line 'set default="0"' change that number to 3 and you can change it back to 0 if need be. 

This avoids grub altogether (at the little red menu I would select 'continue booting normally), goes to text mode, allows you to see the nice info running up your screen, and you log in normally.

I have no idea if this will help, but sounds like it can't hurt.

---

### Post by b0b138 on 2011-01-19
Sounds like a hardware problem, not software. Especially if you're having issues with live cd's

Strip it down to almost nothing. Leave only video, ram, cd drive, and the processor. Also reseat all of that.

"IF" it will boot up a live cd ok, especialy one that wasn't working before, start adding back things one at a time. You've got a new board and new drives, theres always the chance something might be bad.

If its still being flaky stripped down, pull the mem and try one stick at a time. I know you said they passed the memtest, but try anyway.

And as said before, don't overclock. AFAIK, the memory is also being overclocked and that mem might not be able to handle it. Some mem just can't be overclocked.

And don't worry about the maudio for know. It wont work out of the box, but will with some help, which I can point you to later (at least with ubuntu)

---

### Post by dave.kts on 2011-01-20
did some testing, still no closer to an answer, other than "forcevesa" seems to help

first thing to mention, the M Audio card is showing up when it boots, but isnt working in any the Ubuntu related distro's... but my USB "guitar gig session" interface works... M audio card works in the AV Linux distro... BUT
---No distro picks up my built in VIA audio on the Asrock board.
The M audio is showing up as Envy24 multi channel.

Other than that, it is NOT hardware or overclocking related, i took it to stock speed and Vcore, and had pulled all drives, and pulled the M audio card, all USB attachments. Even changed CD drive from master to slave and back (only device using IDE ribbon)
From what I saw spitting out at me in debug mode, all HD's are properly detected at 3 Gbps with NCQ'ing and all that.

This MB has no built in video, so pulling the card isnt an option.

As for the RAM handling the overclocking, I spent awhile selecting this board to accept my old P4 prescott and be upgradeable to 1333 FSB core 2 duo or quad, and it has 1600mhz DDR3 in it, so the RAM is actually running way underrated at 4*FSB (I'm running FSB at 229) running at 916. I didnt understand the whole FSB-RAM relation when i bought the board and memory a couple months ago, but i lucked out that it can work like this. But like I  said ive been running completely stable with this setup for a couple months now in XP, working on my super-demanding, over-produced, mega-VST demo for my band. Deffinately testing the stability of it. I've had to OC the old P4 just to give it a little breathing room for these audio projects. Been working great.

Sorry for getting sidetracked, here's some live CD results:

**Fedora 14 64bit** 
--normal boot= hang at first loading image (blue screen with progress bubble-sometimes buble is empty, sometimes it loads until bubble is almost full)
--sometimes will just show flashing video garbage with 1982 nintendo colors, on one or both screens, never getting anyplace.
--safe graphics mode-deleted "quiet" option= string of info as its detecting hardware, HUNG ON OR AFTER DETECTING CD DRIVE- seen my HD's ok, and USB's, couldnt catch anything else...last line:
[4.298486] scsi 6:0:1:0: CD-ROM      HP DVD writer 1040d   EH25 PQ:0 ANSI:5
and then a blinking cursor forever and ever.

**PC Linux OS Enlightenment**
--normal boot= hangs on a really really sluggish, animated splash screen
--forcevesa mode= still has slow spash logo, but boots. splash screen is snappy and pretty when shutting down.
--boots in safe kernal mode

**Artist-X** (prefer to get this one working)
--normal boot= never boots. get two output lines: Loading /casper/vmlinuz...................Loading /casper/initrd.gz....................
(then).......ready.
And then it freezes, the blinking cursor in the upper LH corner, with those lines displayed still.
--text only= same result as above
--another normal boot= loads a lot more, but never get any video, just a few random pixels along the very top of screen2 and nothing on screen1
--forcevesa mode= seems to boot good this way, from what i recall it hasn't failed yet i tried a few times
--debug mode= stops detecting hardware when it got to the CD drive again, same results as Fedora, just stopped right there.
--debug mode again= booted this time, couldnt catch what it spit out after the CD rom, it goes too fast at that point. Boots into crappy unusable garbled video again tho. just random blinking blocks with the 1982 nintendo colors.

hope this helps, ill keep booting ArtistX in forcevesa and make sure it keeps booting smooth

---

### Post by dave.kts on 2011-01-20
sorry- internet lag. trigger happy

---

### Post by dave.kts on 2011-01-20
3

---

### Post by dave.kts on 2011-01-20
sorry!

---

### Post by dave.kts on 2011-01-20
Oh yeah, Bob138 about that M audio... ArtistX is ubuntu based (right?) so if you could help me get it to work. like i said, it shows up, but no output. The USB interface I have does work however.

The M audio works in AV linux

---

### Post by b0b138 on 2011-01-20
I had to double check some stuff online, but it looks like the 1010 is a bit easier than the 2496 (which is what I have)

But supposedly, run run alsamixer in a terminal and turn up/unmute all the channels. You can also install alsa-tools-gui and access it that way.

I got that info from here [http://www.ardour.org/node/3673](http://www.ardour.org/node/3673)

---

### Post by dave.kts on 2011-01-21
Thanks Bob ill check that but pretty sure it was all unmuted.
So for this booting problem- pretty sure it works good using the xforcevesa mode booting from a live CD, but what do i do when i install it?
I think i'm sticking with ArtistX

---

### Post by dave.kts on 2011-01-22
still need a solution... not to fond of switching anything in BIOS unless i can get some confirmation. I mean, if I had to switch the hard drives to legacy mode, wouldn't it just not boot, ever? Dont wanna mess with that cause windows needs it set the way it is to support the sata drivers.

---

### Post by tredegar on 2011-01-23
> So for this booting problem- pretty sure it works good using the xforcevesa mode booting from a live CD, but what do i do when i install it?
If **xforcevesa** is what the distro needs to boot then after you have made the installation, add that to the kernel boot line by editing **/etc/default/grub** and then **sudo update-grub**

---

### Post by dave.kts on 2011-01-23
AAAHHHHRRRRGG!
Xforcevesa does not work. in any disk I try. 50/50 chance if it boots or not, guess i was just having better luck before. Completely random. I'm talkin live CD's, DVD's, or install-only disks like UbuntuStudio. 64 Studio I get a Kernal panic and loads even less. 
I tried BIOS options for usb legacy, sata compat. mode, etc.
I tried a new CD drive
I tried 2 CD drives
I tried a new IDE cable
I tried switching to master/slave mode on CD drives
I checked the winshield washer fluid

all ubuntu based distro's stop on or after detecting CD drives.

---

### Post by dave.kts on 2011-01-23
Jan 23 15:55:23 cdrom-detect: Searching for Ubuntu installation media...
Jan 23 15:55:46 cdrom-detect: CDROM-detect failed; unmounting CD just to be sure
Jan 23 15:55:46 main-menu[3720]: WARNING **: Configuring 'cdrom-detect' failed with error code 1 


This is what I'm getting from a log using Hardy alternate installer. Fails to find/mount CD ROM.
It's asking me if I have a driver on a floppy. I tried my board's floppy driver disk made for windows. "iastor.sys" Not it apparently.

---

### Post by dave.kts on 2011-01-25
bump?
Really disappointing me. Hope we don't have to chalk this motherboard up on the incompatible list. I want my linux :(
Especially now since I demo'd Open Arena and it plays great on this. 
Considering RMAing this board back to Newegg. but this was about my only choice to slip my old P4 into and be able to upgrade when i can afford a core2. Twice now in windows the USB's failed on me coming out of sleep. kept flagging me over and over that "usb not recognized" even after i unplugged all USB devices. I think this board is just flaky.
Hoping that someone else out there has tried this board out with Linux. wether you had any luck or not, i just want confirmation

---

### Post by dave.kts on 2011-01-27
Sooooo... some improvement, but not solved.

I switched my video card, last thing i could think of. Had one sitting around. Its a piece of crap MSI radeon, can cook an egg on it. Ubuntu installed thru alt. disk boots up nearly perfect. Cant locate drivers for this card and the video is unstable even with xforcevesa. (random black lines, screen blackouts, then i change resolution and its fine)
 AVlinux boots about 60 to 75% of the time now, seems a little better, but still not 100%. Other distro's still fail to boot.
Should I just give up? throw this board in the microwave and watch the fireworks?

---

### Post by dave.kts on 2011-02-01
Looks like this is SOLVED if I disable the IDE controller in BIOS!!! too bad its the last thing I thought of. Of course I couldn't do that using the CD installers.
running KXstudio 64 like butter dripping off a hot biscut. booting every time, knock on wood. 
Picked up a q8300 quad core and let my P4 cool down for once. Wierd, the P4 was supposed to support 64 bit, but didnt.

Glad to say the ASrock P43DE3 supports Linux, 64 bit, realtime kernel, 8.1 HDA audio- BUT the IDE controller must be disabled (after install). Maybe there is a workaround? I dont care. 20 bucks for a SATA DVD drive.

Still need some help with that delta 1010lt card tho

---

### Post by cascade9 on 2011-02-01
> **dave.kts said:**
> Wierd, the P4 was supposed to support 64 bit, but didnt.

IIRC at least some of the P4s are missing an instruction used in x86-64 distros. So 64bit linux will not run.

You could try the xorg-edgers PPA for the ATI card, the newer drivers might help.

---

### Post by dave.kts on 2011-02-01
Ehh no need for the ATI drivers, I threw my Nvidia card back in and with the core2 it works great now. 3D, desktop effects and all.

---

### Post by dave.kts on 2011-02-01
> **cascade9 said:**
> IIRC at least some of the P4s are missing an instruction used in x86-64 distros. So 64bit linux will not run.

Hey that would be a great thing to know when you go to download the 64 bit distros huh? lol

---

### Post by cascade9 on 2011-02-02
> **dave.kts said:**
> Hey that would be a great thing to know when you go to download the 64 bit distros huh? lol

I'd guess that most people dont know that some P4s have 64bit extensions. If somebody tried 64bit and it failed, they would be most likely to think they had the 'wrong' CPU and/or chipset.

---

### Post by dave.kts on 2011-02-05
Still working great! 64 and 32 bit installed (KXstudio, and Ubuntu)
one more note, as well as disabling the IDE controller, the onboard audio and FP audio must be set to ENABLED, not AUTO in BIOS to get the onboard sound working

---

### Post by b0b138 on 2011-02-05
Oh I saw something the other day that made me think of this thread.

Someone had issues with getting any linux distro to work, but windows was fine.  He changed the BIOS (downgraded it a version) and everything worked after that.

---

