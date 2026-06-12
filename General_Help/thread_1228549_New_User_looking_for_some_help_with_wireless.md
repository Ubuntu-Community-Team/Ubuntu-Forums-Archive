---
title: "New User looking for some help with wireless"
date: 2009-08-01
forum: General Help
---

### Post by chriscorbin on 2009-08-01
Let me start out by saying that this is my first post(of many hopefully) in these forums.

I am a first time linux user as of yesterday but a long time Mac OS and Windows user, so take it easy.

I installed Ubuntu 9.04 on my HP Mini 1000 netbook yesterday. I must say that so far i am very impressed and intend to make Ubuntu the main OS on this laptop, however:

While wireless worked great out of the box on the live version, mounted via USB drive and worked for a while on the installed version it no longer is able to connect to my wireless router and as if that wasnt bad enough it seems to have done something to break the wireless connection in Windows as well(i made a seperate partition for Ubuntu so i can still get to a few windows programs)

The computer sees my router and attempts to connect to it but all i get is a little blue dot circling around the two green ones in the top of my wifi menu.

I have tried:

[LIST]
[*]restarting the computer and booting back into Ubuntu
[*]Restarting my computer and booting into Windows
[*]Restarting my router 
[*]Restarting my Cable box
[*]Removing my battery, taking out the power cable and restarting into both OSs
[*]Connecting another computer to the router(i tried 2 other computers and both connect fine)
[/LIST]

Frankly i am at a loss.

Normally i would think "no, Ubuntu and Windows are completely diffrent, even if something was wrong with a driver or something in Ubuntu, Windows would be able to connect to WiFi" but installing linux was the last thing i did, i havent moved the computer at all so i dont think i could have damaged the hardware.

Any help would be much appreciated, if i would have known installing Ubuntu would make my laptop worthless i would have never done it, but its SOOOOO much better than windows(at least when it was working)

In peril

Chris

---

### Post by Tclarkie on 2009-08-01
what exactly did u do when connected, what brand is the router

---

### Post by chriscorbin on 2009-08-01
the router is a Linksys 

when i connected just logged onto facebook for about 5min, got Pidgin set up with all my info, installed skype(and it doesnt seem to work, but thats the least of my problems now!) and i  installed breakout from the app catalog(or whatever its called)

I wasnt randomly typing into terminal or anything

---

### Post by Tclarkie on 2009-08-01
check status of router by typing the ip address into firefox, it should start something like 169.

---

### Post by Tclarkie on 2009-08-01
how have u secured your network

---

### Post by chriscorbin on 2009-08-01
> **Tclarkie said:**
> check status of router by typing the ip address into firefox, it should start something like 169.


I was not able to access it on the Ubuntu laptop but when checking from another computer it appears to be working just fine. I am not using any kind of encryption or security and the SSID is being broadcast publicly(we live in the middle of nowhere so we dont have to worry about wifi thieves)

---

### Post by Tclarkie on 2009-08-01
in the router menu in firefox, can u check current users or history

---

### Post by chriscorbin on 2009-08-01
> **Tclarkie said:**
> in the router menu in firefox, can u check current users or history

I think what you mean by this is: can i see who or what computer(by IP address) has accessed the router, if that is the case then no, i cant or rather havent found a way to in the years ive owned this router.

is that what you meant?

---

### Post by zkriesse on 2009-08-01
It sounds like you have either a hardware issue or a driver issue...did you do the automatic update...? Even though it's the latest version of Ubuntu it still needs to get updates on your pc...If not try a full load of Ubuntu as an OS...

---

### Post by Tclarkie on 2009-08-01
yes it was. the only other thing i can think of is that you've changed some important settings. Do you have a static ip address?

This may destroy the point of wireless, but try connect either:
straight to router (through LAN)
straight to modem (through LAN)

I would much appreciate hearing if this works, so keep posting

---

### Post by zkriesse on 2009-08-01
> **Tclarkie said:**
> yes it was. the only other thing i can think of is that you've changed some important settings. Do you have a static ip address?

This may destroy the point of wireless, but try connect either:
straight to router (through LAN)
straight to modem (through LAN)

I would much appreciate hearing if this works, so keep posting
He's got a problem don't he? I put Ubuntu on a laptop once before and the wireless worked fine....

---

### Post by chriscorbin on 2009-08-01
> **Zachk18 said:**
> It sounds like you have either a hardware issue or a driver issue...did you do the automatic update...? Even though it's the latest version of Ubuntu it still needs to get updates on your pc...If not try a full load of Ubuntu as an OS...


When the Ubuntu install to my hard drive completed it ran update and installed the updates, there where a lot of them.

What do you mean by a full load: Erase the windows partition and just put Ubuntu on there???

---

### Post by Tclarkie on 2009-08-01
i aggree with Zach, but be careful, my cous install securety updates and completely stuffed his grub

---

### Post by zkriesse on 2009-08-01
You're gonna have to re-load the Ubuntu OS full partition...:( sorry man

---

### Post by chriscorbin on 2009-08-01
> **Tclarkie said:**
> yes it was. the only other thing i can think of is that you've changed some important settings. Do you have a static ip address?

This may destroy the point of wireless, but try connect either:
straight to router (through LAN)
straight to modem (through LAN)

I would much appreciate hearing if this works, so keep posting


I actually have no idea weather the IP is static or dynamic, how does one find this out?

I tried connecting it via ethernet to the router with no success, although i just plugged it in and assumed it would work, thats how mac os and windows does it, is there something else i should be doing?

what settings could i have changed and how do i restore them back to when i first started???

---

### Post by zkriesse on 2009-08-01
At this point man it sounds like you really f****d up the OS....

---

### Post by chriscorbin on 2009-08-01
> **Zachk18 said:**
> You're gonna have to re-load the Ubuntu OS full partition...:( sorry man

I dont consider myself to be the master IT guy or anything but that sounds like a REALLY BAD IDEA, i have no windows backup and no way to re-install if this doesnt pan out. This computer has no CD or DVD drive of any kind and i dont exactly have the cash around to purchase one.

and correct me if im wrong here, doesnt installing Linux totally void your warranty? at least when i had a windows partation i could just delete the linux partition if i needed to get it repaired but this seems like a point of no return?

is there any other way?

and how could doing something in a diffrent OS mess up the connection in Windows anyway?

UPDATE:::

Just for kicks i tried booting the live version from my USB drive again, it has the same problem now i might be wrong, and tell me if i am:

The live version on the flash drive is a un-touched version devoid of anything i may have done(and i still cant figure out what stupid move i made) to screw up my install

and it still has the same problem, it cant connect, so wouldnt this dictate a hardware issue?

---

### Post by PrivatePickle on 2009-08-01
Sorry to hear you're having problems, I am not sure if I can help but I have a few simple suggestions of some things I had to do with my mini after installing Ubuntu.  I know these are pretty basic but sometimes I find I spend a long time trying to solve a big problem when it was something simple I didn't check.

First, did your mini come with an xp reinstall disk?  Mine did but I guess some models didn't.  You can reinstall windows using winsetup from usb 

[http://www.msfn.org/board/install-USB-WinSetupF-t120444.html]("http://www.msfn.org/board/install-USB-WinSetupF-t120444.html")

All you need is access to a windows machine with a cd drive and at least a 1gb thumbdrive to make a winXP installation thumbdrive.

For your Ethernet connection, I remember mine wouldn't work at first until I rebooted with the cable plugged into the mini but worked normally after that.  

If that gets you internet access I would make sure ubuntu is up to date then go to system->administration->hardware drivers and make sure the broadcom wireless driver is activated and currently in use. Then right click on the networking icon at the top right and make sure networking and wireless are both enabled (checked) they should be but I always check anyway.  Then left click the networking icon and see if your network is listed, if it is select it and see if it connects.  If it won't connect or is not listed then if no one else has any suggestions I would consider reinstalling.

If you decide to reinstall I would leave winXP alone for now and continue dual booting.  Also the mini has some issues with sound as you may have noticed when Skype did not work. There are some fixes for this but if you don't wish to mess with it right now I recommend doing what I did and install a custom remix from the following site.

[http://psychocats.net/hpminiremix/](http://psychocats.net/hpminiremix/)

It is the standard Ubuntu 9.04 with sound fixes for the mini and some minor tweaks.  Been working great for me so far.  I only had to change a couple settings after that to get the external mic working.

---

