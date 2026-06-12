---
title: "Inadequate Hardware (11.04)"
date: 2011-05-30
forum: General Help
---

### Post by ddjolley on 2011-05-30
I just installed 11.04 on a vintage laptop (Thinkpad - T-41).  At the conclusion of the install I received a warning that my hardware was inadequate and that I would be banished to Classic.  Unfortunately, no clue was given as to the exact nature of the hardware inadequacy.  My first thought was memory.  I have 1.5 GB.  Upon checking the hardware requirements it seems to me that that should be usable although (naturally) more would be better.

Does anyone have any insight as to what my problem might be?  Will I be able to overcome it; or, am I just out of luck.  (I want Unity so as far as I'm concerned running Classic is the same thing as being out of luck.)

Thanks for any input.

          ... doug

---

### Post by ChrisKu on 2011-05-30
I am pretty sure it has nothing to do with your hardware being insufficient. I have got the same effect when installing Ubuntu 11.04 on my T410. I haven't bothered solving the problem yet but if I remember correctly you need to install a prop. driver for your graphic card. I'll see whether I find that post...

---

### Post by linuxinstalledfromhdd on 2011-05-30
Try rolling back to 10.10.

Here is a nice walk through on getting yourself set up with 10.10:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

It shouldn't take long at all to have that completely installed and ready to go. :)

---

### Post by keithpeter on 2011-05-30
Hello ddjolley

More likely to be the graphics card specification than the RAM. Unity will run on my T42 which has only 1 Gb. I take it you can boot into classic and that programs run OK and so on?

What is the 'Type' number of your T41? My T42 has Type 2373 next to the IBM logo on the bottom. That number will enable you to find the exact specification for the graphics.

---

### Post by ddjolley on 2011-05-30
> What is the 'Type' number of your T41?

2373

Also, I'm not sure that I understood the suggestion about rolling back to 10.10.  I can easily get it to work with 10.10.  In fact, 10.10 is what I rolled forward from. :)  11.04 works fine in Classic mode.  It's just that I want the Unity UI.  So, I don't understand how rolling back to 10.10 is going to help me.

Thanks for all the input.

          ... doug

---

### Post by keithpeter on 2011-05-30
Hello ddjolley and all

Well, that is really strange, my early vintage T42 has the same graphics card:

```
Display Type 14.1 in TFT active matrix
Max Resolution 1400 x 1050 ( SXGA+ )
Widescreen Display No
Color Support 24-bit (16.7 million colors)
Video
Graphics Processor / Vendor AGP 4x - ATI Mobility Radeon 9000
Video Memory 32.0 MB DDR SDRAM 

```
and processor (1.7 Ghz centrino) but runs (well, jogs) with Unity ok

Any video gurus out there have any suggestions?

---

### Post by 3Miro on 2011-05-30
> **linuxinstalledfromhdd said:**
> Try rolling back to 10.10.

Here is a nice walk through on getting yourself set up with 10.10:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

It shouldn't take long at all to have that completely installed and ready to go. :)

The OP is stuck in classic mode and wants to run Unity. Your suggestion is to go back to 10.10 where only classic mode was available without Unity ... what kind of nonsense suggestion is that?

---

### Post by 3Miro on 2011-05-30
> **ddjolley said:**
> I just installed 11.04 on a vintage laptop (Thinkpad - T-41).  At the conclusion of the install I received a warning that my hardware was inadequate and that I would be banished to Classic.  Unfortunately, no clue was given as to the exact nature of the hardware inadequacy.  My first thought was memory.  I have 1.5 GB.  Upon checking the hardware requirements it seems to me that that should be usable although (naturally) more would be better.

Does anyone have any insight as to what my problem might be?  Will I be able to overcome it; or, am I just out of luck.  (I want Unity so as far as I'm concerned running Classic is the same thing as being out of luck.)

Thanks for any input.

          ... doug

If Ubuntu reverts you to classic mode, this is usually due to graphics. Unfortunately the older ATI graphics cards have very poor Linux support (ATI didn't have any Linux support for years and only after AMD took over, did things start to improve).

Were you able to run compiz (desktop effects on Normal or higher) on Ubuntu 10.10?

Have you checked the "Additional Drivers" section (System -> Admin -> Additional Drivers)? Are there any extra drivers available?

---

### Post by linuxinstalledfromhdd on 2011-05-30
> **3Miro said:**
> If Ubuntu reverts you to classic mode, this is usually due to graphics. Unfortunately the older ATI graphics cards have very poor Linux support (ATI didn't have any Linux support for years and only after AMD took over, did things start to improve).

Were you able to run compiz (desktop effects on Normal or higher) on Ubuntu 10.10?

Have you checked the "Additional Drivers" section (System -> Admin -> Additional Drivers)? Are there any extra drivers available?

If the user wants Unity, it can be install on 10.10. All the user would need to do after installing 10.10 would be to naturally add the corresponding PPA for Unity. You can even do it in Ubuntu-Tweak in the source center.  That's how I installed it. Works better than in 11.04 in my humble opinion.  11.04 isn't the only way to have a Unity environment:P. Why force them into only using 11.04 if they don't absolutely need it yet? I would wait until they get all the bugs out of 11.04 anyways or if the user doesn't really want to be part of the development team.  Just sayin.

---

### Post by ddjolley on 2011-05-30
> Were you able to run compiz (desktop effects on Normal or higher) on Ubuntu 10.10?

Sorry.  I don't know and (obviously) it's too late for me to check now.

> Have you checked the "Additional Drivers" section (System -> Admin  -> Additional Drivers)?
> Are there any extra drivers available?

I just checked that; and, no, there are not.  It says, "No proprietary drivers are in use on this system."

It also sounds like one commentator was suggesting that I roll back to 10.10 and then try to run Unity from there.  I feel that is too far off the beaten path and I want the other features of 11.04.  IOW, I want both 11.04 and Unity!  I'm spoiled! :)

Thanks for all the help.

           ... doug

---

### Post by linuxinstalledfromhdd on 2011-05-30
Well that's fine too, as long as you are happy to be part of the development of 11.04. Some of us just want a more stable system, and something tested out before we make it our daily use and bread and butter :)

---

### Post by 3Miro on 2011-05-30
> **linuxinstalledfromhdd said:**
> If the user wants Unity, it can be install on 10.10. All the user would need to do after installing 10.10 would be to naturally add the corresponding PPA for Unity. You can even do it in Ubuntu-Tweak in the source center.  That's how I installed it. Works better than in 11.04 in my humble opinion.  11.04 isn't the only way to have a Unity environment:P. Why force them into only using 11.04 if they don't absolutely need it yet? I would wait until they get all the bugs out of 11.04 anyways or if the user doesn't really want to be part of the development team.  Just sayin.

Wow, I did not realize this was a viable option. My apologies.

---

### Post by linuxinstalledfromhdd on 2011-05-30
Hey hey it's totally A-OK. :)  Whatever it takes to get the job done. :)

---

### Post by 3Miro on 2011-05-30
> **ddjolley said:**
> > Were you able to run compiz (desktop effects on Normal or higher) on Ubuntu 10.10?

Sorry.  I don't know and (obviously) it's too late for me to check now.

> Have you checked the "Additional Drivers" section (System -> Admin  -> Additional Drivers)?
> Are there any extra drivers available?

I just checked that; and, no, there are not.  It says, "No proprietary drivers are in use on this system."

It also sounds like one commentator was suggesting that I roll back to 10.10 and then try to run Unity from there.  I feel that is too far off the beaten path and I want the other features of 11.04.  IOW, I want both 11.04 and Unity!  I'm spoiled! :)

Thanks for all the help.

           ... doug

It may be that 10.10 is the only option (if 10.10 comes with a proper driver). AMD recently stopped supporting some of the old cards.

Can you run the following in the terminal:
```
glxinfo | grep direct
glxinfo | grep OpneGL
```
you may have to install mesa-utils to use glxinfo (gives information about OpenGL capabilities of your system).

If you cannot run Unity 3D, you can try Unity 2D. Go to Synaptic Package Manager (System -> Admin -> Synaptic) and search for Unity 2D. It has all the functionality of Unity 3D, minus some of the effects. It is still in a beta stage, but Ubuntu 11.10 will come with Unity 2D as a lighter alternative of Unity 3D.

---

### Post by tgalati4 on 2011-05-30
I was under the impression that you needed at least a Radeon 9600 or better to run Compiz.  I have a T43p with an ATI FireGL card.  It runs Compiz effects OK.  Not great, but OK.  I'm using the open driver under Jaunty.  It's probably possible to get Compiz running on the older cards, you just need to set the appropriate switches in /etc/X11/xorg.conf and it might be too slow to be practical.

---

### Post by 3Miro on 2011-05-30
> **tgalati4 said:**
> I was under the impression that you needed at least a Radeon 9600 or better to run Compiz.  I have a T43p with an ATI FireGL card.  It runs Compiz effects OK.  Not great, but OK.  I'm using the open driver under Jaunty.  It's probably possible to get Compiz running on the older cards, you just need to set the appropriate switches in /etc/X11/xorg.conf and it might be too slow to be practical.

I am not sure what the minimum requirements are, but Unity 3D is more needy then pure Compiz. If Compiz barely runs, then downgrading to 10.10 will not solve the issue, only Unity 2D may work.

---

### Post by mitso on 2011-05-31
I installed 11.04 on a minimum computer with  an  Atom motherboard. The classic 11.04 works fine but Unity 3D doesn't. I installed Unity 2D
and that works fine - good enough to check Unity. There are some
glitches and hangs once in awhile. I don't think its ready for 
production yet - but again - more than good enough to check out Unity.
I am impressed with Unity !

---

### Post by ddjolley on 2011-05-31
> Can you run the following in the terminal:
 	Code:
 	glxinfo | grep direct glxinfo | grep OpneGL 
No.  Neither command is available.  There is a command, 'directg'.

The thing that baffles me is this:

How is it that keithpeter is running the exact same graphics card as me on a machine that is extremely similar to mine and he reports that Unity "jogs" just fine on his machine?

Thanks.

         ... doug

---

### Post by DeadlyOats on 2011-05-31
This [COLOR="Red"]_[link]("https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements")_[/COLOR] is to a web page with really good details for how to figure out if your hardware will be supported by the Unity Desktop.

I installed 11.04, and I too got the message that Unity was not supported, but after I activated the proprietary drivers for my nVidia Geforce 7800 GS graphics card, Unity was indeed supported.

So, you may need to use the proprietary drivers to get the 3D 2D features of your card to work before you can get Unity to work on your machine.

Go to System>Administration>Additional Drivers from your panel (kicker bar? task bar?)  After it scans, it may provide you with choices for proprietary drivers for your video card.

I hope this helps.

By the way, using the proprietary drivers of my graphics card also gets compiz to work, as well as a bunch of 2D and 3D games.


> **ddjolley said:**
> 
> Have you checked the "Additional Drivers" section (System -> Admin  -> Additional Drivers)?
> Are there any extra drivers available?

I just checked that; and, no, there are not.  It says, "No proprietary drivers are in use on this system."

           ... doug

Check again, it says that until you "ACTIVATE" the proprietary drivers for a graphics card.  Select the "Recommended" driver, and then click on the Activate button.

I hope that helps.

---

### Post by ddjolley on 2011-05-31
> Go to System>Administration>Additional Drivers from your panel  (kicker bar? task bar?)
> After it scans, it may provide you with choices  for proprietary drivers for your video card.

Great suggestion.  Unfortunately, I have already tried that.  I get, "No proprietary drivers are in use on this system".

Maybe I need a proprietary driver?

Thanks.

         ... doug

---

### Post by ddjolley on 2011-05-31
> Check again, it says that until you "ACTIVATE" the proprietary drivers
> for a graphics card.  Select the "Recommended" driver, and then
> click on  the Activate button.

Sorry.  I don't see anything like that.  I'm attaching a screenshot.  Thanks.

       ... doug

---

### Post by zippytex on 2011-05-31
I did install the 2D Unity, but was under impressed.  I hope that it is not the only direction that Ubuntu will be traveling in the future.

I have a intel 850xx adapter with a Toshiba M35X-S311, 1.8ghz, 1.5 GB RAM.

The 11.04 works great!  I have had no troubles at all.  Gramps is happy on this system!

Thanks.

---

### Post by ddjolley on 2011-06-01
One more piece of info..  My wife has a Thinkpad Model T-42 (type 2373) with 2.0 GB of RAM.  I commandeered it and installed Ubuntu 11.04.  I got identical results to those I obtained with my T-41.  I am at a loss to explain how keithpeter got the identical laptop (except that it has only 1.0 GB of RAM) to run Unity.

I realize that I could likely get either of these laptops to run Unity in 2d.  I'm not really interested in doing that.  I think that I'm going to give up for now and probably get a new laptop in the near future.

Thanks to all for all of the thoughtful input.

          ... doug

---

### Post by keithpeter on 2011-06-01
> **ddjolley said:**
> One more piece of info..  My wife has a Thinkpad Model T-42 (type 2373) with 2.0 GB of RAM.  I commandeered it and installed Ubuntu 11.04.  I got identical results to those I obtained with my T-41.  I am at a loss to explain how keithpeter got the identical laptop (except that it has only 1.0 GB of RAM) to run Unity.

Hello ddjolley and  all

I put the live CD in and booted from it. Unity appeared and appeared to work fine for a half hour live session.

I'll try a full install in a bit and let you know what happens.

Well, well, I tried installing from the live cd triple booting with Xubuntu and with Windows XP. Everything went fine until near the end of the 'slide show' when I was dumped into console with the warning 'stopping runlevel V compatibility' and had to log back into the live session. Rebooting led to the grub screen with just xubuntu and XP. Running update-grub showed the Ubuntu installation but did not add it to the boot menu. The Ubuntu installation is on /dev/sda7 and this is a logical partition. Any ideas?

Back on topic, the output from lshw from this reconditioned laptop is at

[http://dhost.info/devnull/hw.txt](http://dhost.info/devnull/hw.txt)

---

### Post by ddjolley on 2011-06-01
> I put the live CD in and booted from it. Unity appeared and
> appeared to work fine for a half hour live session.

> I'll try a full install in a bit and let you know what happens.

Ah!  That's a revelation.  I didn't know that you didn't have Ubuntu installed.  So, I tried the same thing (i.e., run a sample session from the live CD) just to see what would happen.  Unfortunately, it silently pushed me right to Classic.  So, I'm not seeing any substantive difference between the installed version and the live CD.

FWIW.  Thanks.

            ... doug

---

### Post by keithpeter on 2011-06-01
> **ddjolley said:**
> > I put the live CD in and booted from it. Unity appeared and
> appeared to work fine for a half hour live session.

> I'll try a full install in a bit and let you know what happens.

Ah!  That's a revelation.  I didn't know that you didn't have Ubuntu installed.  So, I tried the same thing (i.e., run a sample session from the live CD) just to see what would happen.  Unfortunately, it silently pushed me right to Classic.  So, I'm not seeing any substantive difference between the installed version and the live CD.

I had Xubuntu installed (see signature) but I'm posting this from Ubuntu 11.04 complete with Unity now installed on the T42.

The video section of the output of the sudo lshw command is below: check if it is the same as your T42. This laptop has been refurbished and could have had parts swapped or jumper settings changed I suppose.

```
     *-pci
          description: Host bridge
          product: 82855PM Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:d0000000-dfffffff
        *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:3000(size=4096) memory:c0100000-c01fffff memory:e0000000-e7ffffff
           *-display
                description: VGA compatible controller
                product: RV350 [Mobility Radeon 9600 M10]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:11 memory:e0000000-e7ffffff ioport:3000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff
```

I have yet to update this installation so it could break yet

---

### Post by ddjolley on 2011-06-01
> check if it is the same as your T42.

The only material difference that I see is in the display product which, for me, is "Radeon Mobility M7 LW [Radeon Mobility 7500]".  The configuration is the same including the driver.  I would think that if the driver were the same, the products should be equivalent.

At this point, I don't know what to say; or, how to explain why yours works and mine doesn't.  However, unless someone has some further ideas, I think that I'm just going to have to accept that fact and move on.

Thanks to everyone for all the help that I have received.  I'm sorry that we weren't able to get to the bottom of this; but, again thanks for all the help.

             ... doug

---

### Post by DeadlyOats on 2011-06-01
> **ddjolley said:**
> > check if it is the same as your T42.

The only material difference that I see is in the display product which, for me, is "Radeon Mobility M7 LW [Radeon Mobility 7500]".  The configuration is the same including the driver.  I would think that if the driver were the same, the products should be equivalent... 


Actually, ATI (at the time, nowadays known as AMD), and nVidia began making consolidated drivers.  That is, one driver download supporting a range of video graphics cards of a particular model series.  So, the same downloaded driver is actually a compilation of many drivers, and the software picks the right one for you.

So, the same driver download does not necessarily mean it was also the same GPU chip.

But I see your disappointment nevertheless.

---

### Post by Dustin2128 on 2011-06-01
lspci to provide us with video info, and you probably need to download proprietary drivers if you do not have an intel card (all of those are open source- but weak cards).

---

### Post by ddjolley on 2011-06-02
> lspci to provide us with video info,

See below.  It would be really great if from the below information you could tell me what proprietary driver I need to download, where to download it from, and what I need to do to install it.  I mean that would be REALLY GREAT!! :)

> all of those are  open source- but weak cards

Understood.  I will be replacing this laptop soon.  However, this has become a personal challenge for me so I would really like to get it to work.

Thanks.

        ... doug

doug@t42:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b
doug@t42:~$

---

