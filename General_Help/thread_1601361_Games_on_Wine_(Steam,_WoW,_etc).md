---
title: "Games on Wine (Steam, WoW, etc)"
date: 2010-10-20
forum: General Help
---

### Post by Daemn on 2010-10-20
Hi guys and gals,

My games either run incredibly slow or freeze my system. I'll start HL2 games, they will run the intro decently (some strange misplacement until it finishes loading), but after that it's either laggy or it completely freezes. It either does that repeated sound over and over, or I can hear my programs in the background but can't do anything to get my desktop back (I have System Monitor F12 keybound) - then computer reboots. It's also worth noting that when I start the game, my other monitor (dual) turns off then back on for a couple seconds - not sure why.. driver requirement to prevent something maybe - happens when I play a video too.

Specs: Ubuntu 10.10 x64, XFX 5850 Radeon HD, Core i7, Corsair 6GB triple channel, WD Black, OCZ 750w gold

Pretty much an above average rig. It runs most of my games 100-300 FPS on Faildows (zzzz :().

I'm using the latest drivers from "Additional Drivers" - ATI/AMD proprietary FGLRX.

I've tried quite a bit. Everything I could Google. I've updated wine to 1.3. I've checked all the settings - installed recommended d3d, .net. I am not using Compiz (no desktop effects at all) or have desktop composition enabled. My resources are 90% free. I disabled all sounds in the list (OSS, ALSA). I tried using the -dxlevel81 argument. I, ugh, tried smiling at my computer.

I only get 3000fps on glxgears which seems odd, even for a non-benchmark.

It seems hopelessssssss, and yet I see people running these games from back in 2007 perfectly fine. What gives!! Any help greatly appreciated!

---

### Post by garethfoxwilliams on 2010-10-20
I would be interested in any optimisation help too. Just about the only reason I keep a Windows partition on my home desktop is to run WoW.

Wait....that's the only reason!!


Seriously though, I have run the same install of WoW from my Linux partition and had a lower graphics performance than running from Windows - I am using an Nvidia card with the proprietory driver installed automatically by Ubuntu.

---

### Post by P4man on 2010-10-20
Windows games dont like Linux.
Linux doesnt like ATI. 
ATI doesnt like OpenGL. 

Its combination from hell.But even then it should work better than that.

FWIW, on my 4870 I get >6000 FPS in glxgears on a slower CPU. 

I suspect the problem is with the radeon 5x series which do not seem to be supported very well in the latest ati drivers under 10.10. You might actually consider using ubuntu 10.04 instead, or wait for the new catalyst drivers (interestingly, also called 10.10 lol).

---

### Post by Daemn on 2010-10-20
> **P4man said:**
> Windows games dont like Linux.
Linux doesnt like ATI. 
ATI doesnt like OpenGL. 

I don't know whether to cry, laugh or get mad. I feel like all three. This is not cool! (how can you not like OpenGL?)

Well that's too bad cause I'm not re-doing all my packages and settings.

Proprietary drivers ftl!

---

### Post by P4man on 2010-10-21
> **Daemn said:**
> I don't know whether to cry, laugh or get mad. I feel like all three. This is not cool! (how can you not like OpenGL?

Im not saying the company AMD doesnt like OpenGL, or even linux, maybe they do, but their drivers are quite horrible at it. Even on windows. I did extensive benchmarking with a openGL windows game called IL-2, and discovered that the ATI drivers put so much load on the CPU that even a 5 year old budget nVidia card outperformed my 4870 by as much as 30% - provided you reduce graphic settings to a minimum (so the CPU becomes the bottleneck). DId some profiling of the app with vtune and found with ATI it spent over 40% of its CPU time in the OpenGL driver where the load with nVidia drivers was minimal.

AMD just has limited resources and they arent spending a lot on opimizing for OpenGL.. or Linux. Their drivers are okay for windows and directx games though, but not much else. Its a shame, because the hardware is really good nowadays.

---

### Post by Chame_Wizard on 2010-10-21
Big game companies are to stupid to recognize Linux full potential.

AMD is a good company btw.:guitar:

---

### Post by bobwyajnr on 2010-10-21
After struggling to get a ATI 4870 (1Gb) running with Ubuntu 10.04 I went back to my Nvidia 8800 GTX (768Mb). It may not have VDPAU support (GPU just to old :-({|=:-) ) but I am having a lot success with getting DirectX games to run via WINE 1.3.5 (and at decent framerates) with the Nvidia blob drivers. Christ (with a bit of hacking - just following an online guide actually) I even got the Windows folding@home client running on my GPU (again it's fast @60-120 seconds/percentile) - running alongside an 8-threaded SMP CPU client that's not bad!!

So far I have all of the HL2.0 series (original, episodes 1 & 2), GTA: San Andreas, World in Conflict (inc. multiplayer - wow!!), Bioshock 1.0, working at a very playable (DirectX 9.0c) level. Launching all of these from my Steam client...

I have a pretty similar rig to yours. Core i7 920 @4Ghz, 6Gb RAM, Nividia 8800 GTX (768Mb), 6Gb OCZ 1600Mhz DDR3 RAM. I am afraid it might be time to Ebay the 5850 and get a GTS 250 or 460 card instead... (My plan is certainly to update to a newer Nvidia card when I have the cash - to get VDPAU support. I plan to Ebay my 4870 card ASAP...)

There is no sign of ATI fixing their HD decode acceleration technology and (in my experience) their fglrx OpenGL support tends to lag behind Nvidia. If you can hold on for about 4+ years (!!) then the Open Source ATI driver will probably have stable, working OpenGL acceleration by then...

Bob

---

### Post by Daemn on 2010-10-21
> **bobwyajnr said:**
> After struggling to get a ATI 4870 (1Gb) running with Ubuntu 10.04 I went back to my Nvidia 8800 GTX (768Mb). It may not have VDPAU support (GPU just to old :-({|=:-) ) but I am having a lot success with getting DirectX games to run via WINE 1.3.5 (and at decent framerates) with the Nvidia blob drivers. Christ (with a bit of hacking - just following an online guide actually) I even got the Windows folding@home client running on my GPU (again it's fast @60-120 seconds/percentile) - running alongside an 8-threaded SMP CPU client that's not bad!!

So far I have all of the HL2.0 series (original, episodes 1 & 2), GTA: San Andreas, World in Conflict (inc. multiplayer - wow!!), Bioshock 1.0, working at a very playable (DirectX 9.0c) level. Launching all of these from my Steam client...

I have a pretty similar rig to yours. Core i7 920 @4Ghz, 6Gb RAM, Nividia 8800 GTX (768Mb), 6Gb OCZ 1600Mhz DDR3 RAM. I am afraid it might be time to Ebay the 5850 and get a GTS 250 or 460 card instead... (My plan is certainly to update to a newer Nvidia card when I have the cash - to get VDPAU support. I plan to Ebay my 4870 card ASAP...)

There is no sign of ATI fixing their HD decode acceleration technology and (in my experience) their fglrx OpenGL support tends to lag behind Nvidia. If you can hold on for about 4+ years (!!) then the Open Source ATI driver will probably have stable, working OpenGL acceleration by then...

Bob

Thanks!!!! I might throw in my 9800gt and pray they work on 10.10. I guess I could install 10.04, copy the packages and settings over (home directory is on a separate partition woot!)

It sucks though, this card was suppose to run cooler and cheaper than the nVidia equivalent.

Does anybody know of somewhere you can view Ubuntu/linux benchmarks, or topics with people having success with 10.10 or even 10.04? Think I'll just buy the card that works best on Ubuntu.

---

### Post by P4man on 2010-10-22
> Think I'll just buy the card that works best on Ubuntu. 

On linux, nvidia works best, at least if you dont mind using proprietary drivers. Thats "common knowledge". Much more mature drivers,  support for video decode acceleration, vastly better opengl performance and generally much less headaches.

For people who prefer or insist on opensource drivers, the opposite is arguably true, radeon/radeonhd drivers still seem better than nouveau, at least for 1+ generation old cards, but neither can hold a candle to the proprietary drivers yet.

---

### Post by Daemn on 2010-10-22
Yeah thanks P4man, I've been hearing people having issues with nvidia in 10.10 and ati getting better though. I wasn't looking for superb performance, but at least 40fps on a 5 year old game would be nice, with a brand new card. I wonder if 2x GTX 460's will work fine...

Nexuiz is running great.. not Wine though.

---

### Post by P4man on 2010-10-22
Since you apparently still have a 9800GT, give that a try. Im not sure how well, if at all, SLI works with wine games. To tell you the truth, if you are that much into gaming, just keep a windows partition.

---

### Post by bobwyajnr on 2010-10-22
> **Daemn said:**
> 
Does anybody know of somewhere you can view Ubuntu/linux benchmarks, or topics with people having success with 10.10 or even 10.04? Think I'll just buy the card that works best on Ubuntu.

I hang out quite a lot at: [Phoronix]("http://www.phoronix.com/scan.php?page=category&item=Graphics%20Cards") which has very good coverage of general GNU/Linux desktop issues/performance (for a change)!! :popcorn:

Bob

---

### Post by Daemn on 2010-10-26
Update:

Switched to the 9800GT.

Still exhibits the same problems/glitches as the ATI, except instead of failing completely (freezing), it just stalls, and/or the game or X crashes. I've had better success with wine 1.2.1, the dev wine 1.3.5 has more graphical glitches and freezes - but both still have issues and/or freezing so that comes down to the driver. 

With what actually runs, I get better FPS (something closer to what I got on Windows). glxgears gives me 10.5k on this older card.

Games run better in VirtualBox, but I didn't realize Guest Additions wasn't installing correctly (no notification) since I installed it before v3.1 which added D3D support - so I had to do it in safe mode. 

Now WoW runs in VBox. Some games run in Wine 1.3.5, some in 1.2.1. Actually, I originally tried fullscreen but those often fail in all Wine - started using windowed which seems to work overall unless it freezes X server. Also exhibits graphical glitches in newer Wine (so does VBox, but old Wine does not). The Steam client runs better in VBox, it's laggy in all Wine's, and all Source Engine games on Wine have issue with text font, either really squished together or doesn't show up (server list). Some Steam games crash VBox completely. Some Wine games freeze X server.

In the process tried PlayOnLinux and CrossOver Games.

Some progress, definitely going to need that GTX 460. I assume it won't make things any worse than 9800GT - just more FPS.

---

### Post by bobwyajnr on 2010-10-26
> **Daemn said:**
> Update:

Switched to the 9800GT.


Hi Daemn,

My initial attempts at running the Steam client (yes!! just Steam!! - not any actual games) brought my Core i7 @4Ghz to a virtual stand-still. This appears to have been caused by the Nvidia binary drivers in the Ubuntu repository... I was all set to jack it all in and go back to Windows 7 at that point... :eek:
(That was using WINE 1.3.4 BTW)

Anyway I installed an up-to-date Nvidia binary driver (straight from the horse's mouth). All my Steam client issues went away and I actually found I could play some games!!

Certainly I have had a lot of success with quite demanding Steam titles through WINE. I have only got an 8800 GTX (768Mb) - which doesn't even support VDPAU (like yours). Games like World In Conflict, S.T.A.L.K.E.R. and Bioshock 1 appear to run OK (with some minor hacks).

Certainly I learnt (the hardway) to have the MetaCity Window Manager enabled when actually playing any games. Compiz doesn't play nice with games needing OpenGL in WINE. :)

The 9800 GT is a decent card - so I would make sure you've really tested it before ditching it. It took me at least 2-3 weeks of messing about before I started making any progress with WINE (and I've used it a fair bit in the past).

Bob

---

### Post by ROMOAS on 2010-12-06
please help anyone i have just installed UBUNTU i have been adding items that i believe i need i am new to linux all the way i went to a game site that i use STEAM and went to install the client when it was downloaded i got a window that opened asking to chose witch program to use to open it with  i tried wine i got a error stating that it was not reconized that the file extenchine was a .ISM and not able to opes ???? can some one point me to what packet i would need for running programs eather from on line or from a disk i guess a add on from the software center i have no idea what i need and have been looking through all the ones offered and cant find one that states that they are for installing a program please help if any one can i can't stand windows anymore and the sooner i can figure linux out the faster i can get away from them or does anyone know of a addon that will run windows baced programs with in linux.
please drop me a email at *snip* and thank you for any help

---

### Post by CharlesA on 2010-12-06
Are you sure it wasn't an MSI file?

---

### Post by ROMOAS on 2010-12-06
> **CharlesA said:**
> Are you sure it wasn't an MSI file?
 
yes sorry MSI

---

### Post by bobwyajnr on 2010-12-06
> **ROMOAS said:**
> yes sorry MSI

Hi

To avoid a lot of forum noise it's worth looking out Wine AppDB page for whatever software you are trying to install *first*:
[Valve Steam Client : AppDB Webpage]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444")

**winetricks** (in the Ubuntu repositories) can install the Steam client directly. All you need to do is click a checkbox by steam in the the **winetricks** GUI (which should be under your *Wine* entry in the main Gnome menu/application launcher).

Post here if you get any further problems... :popcorn:

Bob

---

### Post by ROMOAS on 2010-12-06
> **bobwyajnr said:**
> Hi

To avoid a lot of forum noise it's worth looking out Wine AppDB page for whatever software you are trying to install *first*:
[Valve Steam Client : AppDB Webpage]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444")

**winetricks** (in the Ubuntu repositories) can install the Steam client directly. All you need to do is click a checkbox by steam in the the **winetricks** GUI (which should be under your *Wine* entry in the main Gnome menu/application launcher).

Post here if you get any further problems... :popcorn:

Bob

a BIG thank you bob went off with out a hitch working fine now and no issues this is all a learning curve for me but i'm a fast learned thanks again

---

