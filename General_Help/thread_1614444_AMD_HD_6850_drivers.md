---
title: "AMD HD 6850 drivers"
date: 2010-11-05
forum: General Help
---

### Post by Bölvaður on 2010-11-05
I am looking for two new graphic cards that will be quite good for the next few years without having driver problems and such.

I am not sure what the status of the AMD and Nivida drivers are. The ones I've settled down on are AMD HD 6850 and GeForce GTX 460, but discouraged by my personal experience with them few years ago. I dont see any drivers for the AMD HD 6850 on their website but I do see the nvidia card drivers on their site... but it's both more expensive and not as powerful as the AMD one.

Drivers matter a lot when it comes to graphics and a good card with a lacking driver can be worse than a mediocre card with proper drivers.

Not sure what to do:confused:

---

### Post by alexan on 2010-11-05
When we talk about tech stuff, the "latest thing" is not existing... everything is and/or will be obsolete in a bunch of months.
you should look more for something that satisfy your need, and if the step (in comparision with what you already have) worth the $$$ spend.


My advice is to wait and see: you already have a firm choice (AMD HD 6850) then only thing you want is proper driver. When driver for linux come, wait for user's experiences (if they are worthy) and buy it.

Avoid the "wishful thinkings" in buy "hoping" that the driver will come.. eventually your money wouldn't come back.

---

### Post by del_diablo on 2010-11-05
But 6850 got a driver?
Install the latest Ubuntu along with the latest bleeding driver that AMD provided, and it is supported.

---

### Post by Bölvaður on 2010-11-05
> **del_diablo said:**
> But 6850 got a driver?
Install the latest Ubuntu along with the latest bleeding driver that AMD provided, and it is supported.
Where can I find the driver?

---

### Post by alexan on 2010-11-05
the HD 6xxx series still hadn't proprietary linux driver. (5 november 2010)
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)


Not experienced with opensource's one, but don't expect performance with them

---

### Post by Dawei87 on 2010-11-05
there probably arent any proprietary drivers out for ATI 6850 atm, but i think the open source drivers will give it 2d support. since you are looking at powerful cards, i am assuming you will be doing gaming in windows? if thats the case, i would go with ati (cause its cheaper) and just not use compositing in linux until the proprietary drivers are released from amd, which will probably be sometime this month. although the support wont be great in the beginning, it will only get better. right now im running an ati 5850 and other 5000 series since spring with no problems at all, so id imagine the 6000 series will have support real soon.

---

### Post by del_diablo on 2010-11-05
> **Bölvaður said:**
> Where can I find the driver?

What version of the Windows driver is needed if you ran Windows?
Use the same driver version, or higher.
And BTW: Ubuntu restriced drivers much?

---

### Post by Lucradia on 2010-11-06
> **del_diablo said:**
> What version of the Windows driver is needed if you ran Windows?
Use the same driver version, or higher.

No. One thing to note, is that your model, needs to be on [the release notes](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_1010_linux.pdf) (under Desktop Family.)

Sadly, any 6xxx series is not listed, in fact, when you go to the ATI main page, and select Radeon HS, and select 6xxx series, Linux is not selectable at all, which means, you guessed it, it doesn't work properly.

----

As for restricted drivers, if the open source (fglrx) doesn't support Radeon HD 6xxx, then you will just have 2D Effects.

---

### Post by del_diablo on 2010-11-06
The newest Ubuntu ALWAYS runs beta drivers shipped from ATI.....
Do i have to repeat myself?

---

### Post by ArcherB on 2010-11-07
> **del_diablo said:**
> The newest Ubuntu ALWAYS runs beta drivers shipped from ATI.....
Do i have to repeat myself?

I dont' care how many times you say it, there are currently no drivers for Linux for the AMD 6800 series.

I have the HD 6850.  It works fine for 2D.  You try to enable the "restricted drivers" and the system locks up on reboot.

So, you can say it as much as you like, but as of today, there are NO 3D drivers for the AMD 6800 series.

However, this may change any day now.  (hoping)

---

### Post by MooPi on 2010-11-07
Are the 5000 series supported with 3D enabled yet ?

---

### Post by Dawei87 on 2010-11-07
> **MooPi said:**
> Are the 5000 series supported with 3D enabled yet ?

ive used an ati 5750 and 5850 and they work just fine with 3D desktop effects. i cant remember for sure, but i might have played a few games through wine with the 5750.

---

### Post by Lucradia on 2010-11-08
> **Dawei87 said:**
> ive used an ati 5750 and 5850 and they work just fine with 3D desktop effects. i cant remember for sure, but i might have played a few games through wine with the 5750.

Mobility HD 5750 locked up during composition of desktop when using binary drivers from ATI itself. *shrug* Whatever works though.

---

### Post by Dawei87 on 2010-11-08
> **Lucradia said:**
> Mobility HD 5750 locked up during composition of desktop when using binary drivers from ATI itself. *shrug* Whatever works though.

hmmm. thats a shame. the cards i was using were on a desktop, i guess the drivers are different from the mobility version to the desktop. but hopefully that means they will be running better soon. im still using the 5850 right now, and just to test it out i installed nexuiz last night. i know its not a very demanding game, but it played perfectly fine with no tearing at all.

---

### Post by Lucradia on 2010-11-09
> **Dawei87 said:**
> hmmm. thats a shame. the cards i was using were on a desktop, i guess the drivers are different from the mobility version to the desktop. but hopefully that means they will be running better soon. im still using the 5850 right now, and just to test it out i installed nexuiz last night. i know its not a very demanding game, but it played perfectly fine with no tearing at all.

No, the supported hardware list in the drivers (That PDF List they publish with each version of the linux binaries on their site) specifically stated that my mobility Radeon HD would, in fact, work with their binary drivers. It's ok though, I have an NVIDIA GTX 470 desktop now, and it works like a champ with the open source / jockey drivers.

---

### Post by birtuma on 2010-11-12
You can activate fglrx with 6800 series (over xorg.conf) but you will get a watermark on the screen ("unsupported hardware") which you can disable.

[http://www.phoronix.com/forums/showthread.php?t=26542&page=6](http://www.phoronix.com/forums/showthread.php?t=26542&page=6)

[IMG]http://www.abload.de/img/nazisiguk9c.jpg[/IMG]
[Waffen-SS]("http://www.brigade2010.de/")

**Don't tolerate nazis and nazi symbolism in respect to all killed people by them. Or you can be ignorant...**

---

### Post by Lucradia on 2010-11-13
> **birtuma said:**
> You can activate fglrx with 6800 series (over xorg.conf) but you will get a watermark on the screen ("unsupported hardware") which you can disable.

[http://www.phoronix.com/forums/showthread.php?t=26542&page=6](http://www.phoronix.com/forums/showthread.php?t=26542&page=6)

That watermark is an OSD thing though, it won't appear on screenshots nor screencasts. I should know, I had it once on another machine.

---

### Post by olof_ on 2010-11-14
ATM I am using one 4850 and one 6850 with fglrx.
I do successfully have two screens attached to each card.
But I can not set the fan speed on my 6850, as it is not even recognized by 
```
aticonfig --list-adapters 
```
I think that is the reason why I sometimes get video disortions - it's too hot.
in short the only way for me to even see it's alive is through amdcccle

edit: Discovered today that the command which I use to raise my GPU fanspeed only seems to work on my 6850, but not on the other 4850 which it is supposed to do. So the temperature issue is due to my old 4850.

```
aticonfig --pplib-cmd "set fanspeed 0 80"
```

I know the possibility to choose different gpus with the command, but I have tried with numbers up to at least 20, and it does not seem to work.

someone knows anything more about this?

---

### Post by Lklklk on 2010-11-17
Well, I just got my amd hd 6850 and after installing it found out it doesn't work in linux because there are no drivers. Can I get a refund? Why does Amd sell product that isn't complete?

---

### Post by del_diablo on 2010-11-17
Because there exists beta drivers... somewhere, and their next catalyst supports it.
More or less AMD/ATi status for quite some time: "Soon, quite soon"

---

### Post by JDShu on 2010-11-17
> **Lklklk said:**
> Well, I just got my amd hd 6850 and after installing it found out it doesn't work in linux because there are no drivers. Can I get a refund? Why does Amd sell product that isn't complete?

Does this work? According to the 10.10 release notes, the 6800 series is supported, so 10.11 should have that support too.

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

---

### Post by olof_ on 2010-11-17
> **Lklklk said:**
> Well, I just got my amd hd 6850 and after installing it found out it doesn't work in linux because there are no drivers. Can I get a refund? Why does Amd sell product that isn't complete?

actually I can get it working, try adding [[COLOR="Red"]some[/COLOR]]("https://launchpad.net/~xorg-edgers/+archive/ppa") [[COLOR="Red"]ppa:s[/COLOR]]("https://launchpad.net/~ubuntu-x-swat/+archive/x-update"), I think that was what made it work out for me.

Yesterday I found out I get two clearly different values when using this two different commands, and my only conclusion is that they read from different graphic cards (as I have two, one 4850 and one 6850).
this one only reads from my 6850:
```
aticonfig --pplib "get temperature *"
Temperature for thermal controller 0 is 43.500000
```
and this one only reads from my 4850:
```
aticonfig --od-gettemperature
Default Adapter - ATI Radeon HD 4800 Series        
                  Sensor 0: Temperature - 74.00 C
```

hope maybe adding the ppa:s will help some.

someone else having this strange sensor-reading "errors"?

---

### Post by Lklklk on 2010-11-18
I installed Catalyst 10.10 and it works. I'm not sure about 10.11.. maybe I'll try it later. Also after installing it's necessary to manually edit xorg.conf.

---

### Post by Lklklk on 2010-11-18
> **olof_ said:**
> 

Yesterday I found out I get two clearly different values when using this two different commands, and my only conclusion is that they read from different graphic cards (as I have two, one 4850 and one 6850).
this one only reads from my 6850:
```
aticonfig --pplib "get temperature *"
Temperature for thermal controller 0 is 43.500000
```

All I get is 
```
aticonfig --pplib "get temperature *"
aticonfig: No supported adapters detected

```

---

### Post by olof_ on 2010-11-18
> **Lklklk said:**
> All I get is 
```
aticonfig --pplib "get temperature *"
aticonfig: No supported adapters detected

```

maybe try with 
```
aticonfig --pplib "get temperature [COLOR="Red"]0[/COLOR]"

```

I just checked and I am using catalyst 10.10.

Anyone more than me who got this "AMD Unsupported hardware" thing in the bottom right corner?

Another thing too, just searched in the aticonfig --help, and it does not even mention --pplib, is not that strange?

---

### Post by olof_ on 2010-11-18
Is not this thread in the complete wrong section?

> [SIZE="3"]The Community Cafe[/SIZE]
The Community Chat area is for lighthearted and enjoyable discussions, like you might find around a water cooler at work.

Almost any non-tech-support topic may be discussed here. Discussions on religion and politics are not allowed, except for politics directly related to free and open source issues. Any topic or discussion that causes problems or drama will be closed. This area is intended for fun and community building, not arguments. Please take those elsewhere. Thanks!

Maybe someone "admin" want to move this thread to a more suitable place?

---

### Post by cariboo on 2010-11-18
Moved to General Help

---

### Post by olof_ on 2010-11-18
Another update, I started into MS Windows just to see how things looked there, and the fan on the 4850 were at 25%, the lowest possible setting. Raising it to about 50% made no additional noise and I had a stable computer again (when using Windows).

Now, please ATI/AMD, release your next linux driver!

---

### Post by olof_ on 2010-11-21
Just to update the thread a little have I made a "script" which displays both my graphic cards temperatures and sends it to notify-osd. It is almost perfect, but to me that is enough.(it shows a little misplaced Ra in the first line, coming from Radeon)
I am using it togheter with [xbindkeys]("http://www.nongnu.org/xbindkeys/xbindkeys.html") and have assigned it a keyboard shoutcut. Maybe someone will find it as useful as I find it.

```

notify-send -i jockey "GPU temps" "`aticonfig --od-gettemperature | awk '{print substr($5,0,2)}' && aticonfig --pplib-cmd "get temperature 0" | awk '{print substr($7,0,2)}' `"

```

it must be on the same line, and therefore it looks quite long above.

---

### Post by Heuamöbe on 2010-12-07
Hi
I have a HD 6950 in my new Coumputer and the Driver in the repository is not working, I get a black screen when I boot. The last thing that could be seen is "Too many conections."

Without the fglrx-Driver the resolution is 1280*980 or something like that, what is not accaptable for a FullHD monitor... ;( Catalyst 10.11 creates only errors, too.

Have you any ideas how to get a proper resolution (maybe with some desktop effects *sigh*)?

Thank you very much, I hope everythings understandable... (I'm german)

---

### Post by Kir_B on 2010-12-08
> **Heuamöbe said:**
> Hi
I have a HD 6950 in my new Coumputer and the Driver in the repository is not working, I get a black screen when I boot. The last thing that could be seen is "Too many conections."

Without the fglrx-Driver the resolution is 1280*980 or something like that, what is not accaptable for a FullHD monitor... ;( Catalyst 10.11 creates only errors, too.

Have you any ideas how to get a proper resolution (maybe with some desktop effects *sigh*)?

Thank you very much, I hope everythings understandable... (I'm german)

According to [this article]("http://www.phoronix.com/scan.php?page=news_item&px=ODc5NQ") on the [phoronix site]("http://www.phoronix.com/scan.php?page=news_item&px=ODc5NQ"), you can [download]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English") the [drivers from here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English").

As to how to install them, I can be of no help, but google should be useful.

Good luck and please, please come back and let us know how it goes. I know there are more than a few of us that are more than a little curious.

Kirby =D>

---

### Post by olof_ on 2010-12-08
for a IMHO good tutorial for installation check [here]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide").

---

### Post by Heuamöbe on 2010-12-08
> **olof_ said:**
> for a IMHO good tutorial for installation check [here]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide").

I used this site to get rid of the fgrlx-driver, worked very well.

I installed Catalyst, too, but the ATI Control Center craches when I try to start it. The are not more options in the grafic options,too ;(. I made the .run executable, the site above suggests to make a deb. Could this be a problem?

Recording to this site: [http://support.amd.com/de/gpudownload/Pages/index.aspx](http://support.amd.com/de/gpudownload/Pages/index.aspx) the HD 6XXX-carts simply are not implemented yet...

---

### Post by Kir_B on 2010-12-08
> **Heuamöbe said:**
> I used this site to get rid of the fgrlx-driver, worked very well.

I installed Catalyst, too, but the ATI Control Center craches when I try to start it. The are not more options in the grafic options,too ;(. I made the .run executable, the site above suggests to make a deb. Could this be a problem?

Recording to this site: [http://support.amd.com/de/gpudownload/Pages/index.aspx](http://support.amd.com/de/gpudownload/Pages/index.aspx) the HD 6XXX-carts simply are not implemented yet...

Yes, you are right , in that they aren't available there.

That is why I posted the link to the bleeding edge drivers:

> According to [this article]("http://www.phoronix.com/scan.php?page=news_item&px=ODc5NQ") on the [phoronix site]("http://www.phoronix.com/scan.php?page=news_item&px=ODc5NQ"), you can [download]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English") the [drivers from here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English").


Good luck. Kirby

---

### Post by Heuamöbe on 2010-12-09
No chance. I still only get errors.

Hopefully it will be implemented in 10.12...

---

### Post by olof_ on 2010-12-09
> **Heuamöbe said:**
> No chance. I still only get errors.

Hopefully it will be implemented in 10.12...

well, you dont have to feel alone waiting, but I have found some very [cool]("http://emergedesktop.org/") [software]("http://explorerplusplus.com/") to windows during my waiting, but that clearly does not belong in this thread.

---

### Post by olof_ on 2010-12-13
seems that the catalyst 10.12 is [on]("http://www.hexus.net/content/item.php?item=27952") [its]("http://208.65.201.194/article.php?aid=1050") way

Also found that you could download the 10.12 drivers to windows [here]("http://forums.guru3d.com/showthread.php?p=3808342").
edit: also found the 10.12 to linux [here]("http://www.planet3dnow.de/cgi-bin/newspub/viewnews.cgi?id=1292260101")!!

ill try it as fast as i can, will post back results.

I am not shure if i did it correctly as catalyst control center says it has version 10.10...
will retry.

well, seems somethig failed (me or the driver.) Upon startup, after grub, I only get this error:
"Error during acpi methods call"...

seems like this needs googling

well, reinstalling now and i got the bright idea to post my gpu specs:
one 6850 and one 4850. no crossfire.

---

### Post by olof_ on 2010-12-13
actually got it working now.
no fancy menus here, nothing new at all *dissapointed*
screenshot:
[IMG]http://ubuntuone.com/p/TVr/[/IMG]

edit: someone who knows how to change or set the default screen?
there is no setting for it in Catalyst Control Center

and, forgot to mention, i have still got the watermark "unsupported hardware" in every screen. (will try to fix that later)

---

### Post by olof_ on 2010-12-13
also now found out that the fan issue is persistent.
i do not know how to change the fanspeed on my second gpu, and its default settings are at its absolutley minimum. This renders my computer unstable when using ubuntu/linux.

i really had hope in 10.12, let´s hope it will be better in the sharp version later on.

---

### Post by BigWhale on 2010-12-14
It seems that 10.12 will still display "Unsupported Hardware" watermark and aticonfig is still reporting "No supported adapters detected".

"Multi display desktop" is still available only if your monitors have the same resolution.

Switching to "Single display desktop (multi desktop)" and turning on Xinerama helps. But if you try to run amdcccle Xorg will crash.

Documentation is outdated and almost non-existent and manually writing xorg.conf without amdcccle is close to impossible for a little more advanced configuration.

Is there an 'official link' to 10.12 drivers?

---

### Post by olof_ on 2010-12-14
> **BigWhale said:**
> It seems that 10.12 will still display "Unsupported Hardware" watermark and aticonfig is still reporting "No supported adapters detected".


according to [this]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Unsupported_Hardware_Watermark") article is it possible to remove it.
though I have not tried it yet. If I should try I have to be fast as my computer freezes after a while...

---

### Post by olof_ on 2010-12-14
> **BigWhale said:**
> 
Is there an 'official link' to 10.12 drivers?


i tried 
```
wget http://www2.ati.com/drivers/linux/ati-driver-installer-10-12-x86.x86_64.run
```
and for me it worked. for more info, see my previous posts.

---

### Post by TweFoju on 2010-12-21
Olof, is that really the official website though? shouldn't it be on amd.com?

---

### Post by olof_ on 2010-12-21
I posted the link just days before it was updated  [here]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide") which is the unofficial fglrx wiki - I think the download link is correct.

---

### Post by Heuamöbe on 2010-12-25
Did I understand it right that you got a HD 6850 to work? Because I tried it several times now, even with a fresh intalation, and I can't even start amdcccle and aticonfig says there is no device detected.
Can you please explain how you did it? I mean, i'm working with ubuntu for quite a while now, but i'm not very into this "system"-stuff... Thank you very much.

---

### Post by Rhodan on 2010-12-26
Please let us know how you got this working?

I have an AMD 6870 GPU, and a clean installation of Ubuntu 10.10.

I followed the instructions from this site to install the AMD 10.12 drivers:

[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)

What I did:

1)
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0

2)
sudo apt-get install ia32-libs

3)
sudo apt-get remove --purge xserver-xorg-video-radeon

4)
sh ati-driver-installer-10-12-x86.x86_64.run --buildpkg Ubuntu/maverick

5)
sudo dpkg -i fglrx*.deb

That all worked fine.

6)
Now when I try this, I am told the file does not exist:
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

7)
If I try this,
sudo aticonfig --initial -f

It says:
aticonfig: No supported adaptaters detected

What is the problem?

---

### Post by olof_ on 2010-12-27
> **Rhodan said:**
> 
6)
Now when I try this, I am told the file does not exist:
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak


that is because on a fresh install of ubuntu the xorg.conf does not exist.
it is made with the below command (i think)

from the wiki:
> 
Before you do this, back up your current xorg.conf if you have one *(Lucid does not have an xorg.conf by default) *


> **Rhodan said:**
> 
7)
If I try this,
sudo aticonfig --initial -f

It says:
aticonfig: No supported adaptaters detected

What is the problem?

try to configure it manually:

if you have a gui: 
```
sudo gedit /etc/X11/xorg.conf
```

and paste this, from the same wiki mentioned in your reply (the title says Minimal Config):

> 
Section "Device"
Identifier "ATI radeon 6870"
Driver "fglrx"
EndSection


if no gui:
```
sudo nano /etc/X11/xorg.conf
```
and then copy the same text.

then time to reboot. (of course you do save the document first)

---

### Post by olof_ on 2010-12-27
> **Heuamöbe said:**
> Did I understand it right that you got a HD 6850 to work? Because I tried it several times now, even with a fresh intalation, and I can't even start amdcccle and aticonfig says there is no device detected.
Can you please explain how you did it? I mean, i'm working with ubuntu for quite a while now, but i'm not very into this "system"-stuff... Thank you very much.

I followed the wiki to the letter, and then rebooted, and it worked...
I think I used the --initial setup, and then I loaded amdccle and disabled mirroring, rebooted, enabled one screen on my second gpu, rebooted, increased the resolution, rebooted, enabled my fourth screen, rebooted, and then after like 10 reboots I had it set up like I wanted.

Although I still have this "AMD Unsupported hardware" watermark in the right bottom corner on every screen. And stability issues because of the lack of control of my 4850 fanspeed (its practically still). But you cant get everything, can you?

What is your hardware, in detail? We could compare and see what is the difference.

my computer:
[LIST]
[*]intel E8400 (OC 3,6Ghz)
[*]Asus striker II formula
[*]8 GB ram
[*]one Sapphire 4850 (in the second pci-e slot)
[*]one Gigabyte 6850 (in the first pci-e slot)
[*]four monitors: three 1024*1280, one 1920*1080
[*]no crossfire
[/LIST]
I think that is what hardware which matters.

---

### Post by YPwn on 2010-12-30
I have the same problem as olof_,
1. It displays AMD Unsupported Hardware watermark.
2. I cannot render any videos, I just get a black screen when playing videos in Totem.

[http://i55.tinypic.com/2ywiybc.jpg](http://i55.tinypic.com/2ywiybc.jpg)

This script didn't help:
```
#!/bin/sh
DRIVER=/usr/lib/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
 sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done
```

Any solution? Thanks.

---

### Post by olof_ on 2010-12-30
YPwn, I assume that you are using fglrx version 10.12?
regarding the watermark, have you tried the solution explained under "Unsupported Hardware Watermark " on [the ccchtml wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide")?

---

### Post by YPwn on 2010-12-30
> **olof_ said:**
> YPwn, I assume that you are using fglrx version 10.12?
regarding the watermark, have you tried the solution explained under "Unsupported Hardware Watermark " on [the ccchtml wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide")?

Yes, I'm using 10.12, because this version was in the guide.
I don't think replacing /etc/ati/control from the same version I have will work.

---

### Post by Yellow Pasque on 2010-12-30
As some of you have noted, the watermark trick only works if you have a newer control file than the one included with the Catalyst version you're running. I'll update the guide to explain it better.

> And stability issues because of the lack of control of my 4850 fanspeed (its practically still).
If your GPU is making your system unstable because of overheating, you need to get more airflow to the heatsink (e.g. somehow attach or aim another fan that plugs into the PSU). Your other option is doing nothing and increasing probability of permanent GPU artifacting or outright failure.

> 2. I cannot render any videos, I just get a black screen when playing videos in Totem.
Is this limited to Totem, or do you have issues with other video players? What gstreamer video plugin are you using and do any others work? Test them in:
```
gstreamer-properties
```

---

### Post by Rezn on 2011-01-01
Many thanks to all the people who have posted in this thread. I've got my 6870 running now, thanks to the guide that was posted.

I first used the suggested driver using additional drivers but that just caused Ubuntu to not boot properly on reboot.

Still can't get rid of the unsupported Hardware logo though.

---

### Post by staphylo on 2011-01-02
I'm with the same problem. I have a  RADEON 6870 and catalyst 10.12 wich does'nt recognize this videocard as supported. However, video performance is good and it works as a recognized hardware.  I tried a lot of ways to make this watermark disappear. However, it still remains in the right side of my screen. It is ugly and boring.

This problem was already explained in some WIKI online but there was no solution. The problem is that catalyst software does'nt recognize the PCID of the hardware.

If anyone know how to solve this problem, give us a solution. I know that many Radeon HD 6XXX users are experiencing this trouble.

---

### Post by martunes13 on 2011-01-03
To install:
sh whatever_directory_you_put_it/ati-driver-installer-10-12-x86.x86_64.run

Manually configure /etc/X11/xorg.conf
Here's a sample 
> 
Section "Module"
   Load "GLcore"
   Load "glx"
   Load "dri"
EndSection

Section "Device"
   Identifier "Default Device"
   Driver     "fglrx"
EndSection


To get rid of the AMD watermark. Create a script file in /etc/init.d/

Put the script:
> 
#!/bin/sh
DRIVER=/usr/lib/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
 sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done


Let's say we name the script file as ATI.sh
Make the script executable
$chmod +x ATI.sh

To make it run at reboot
$ sudo update-rc.d -f ATI.sh start 1 0 6 .

Don't forget the period at the end.
Restart your computer.

You can't use an old control file as the hardware is new and unsupported.

To check if you have the ATI drivers issue the command fglrxinfo or open the catalyst control center.

---

### Post by olof_ on 2011-01-04
thank you for the post, but it did not work for me.
what I did (in this order):

```

cd /etc/init.d/
sudo gedit ati.sh

```
pasted your code
```

sudo chmod +x ati.sh
sudo update-rc.d -f ati.sh start 1 0 6 .

```
reboot.

Do you think it have something to do with me using Xinerama?

---

### Post by martunes13 on 2011-01-04
It might have something to do with that but try this instead.

sudo nautilus, go to /etc/init.d, right click on ati.sh, properties and check if it's executable in the permissions tab.

sudo update-rc.d ati.sh defaults 

To easily check startup scripts

sudo apt-get install rcconf
sudo rcconf

This will come up with an interface which shows all the scripts which are loaded when it starts. Check if the switch for ati.sh is marked. Reboot.

---

### Post by kulturloseramerikaner on 2011-01-05
I was stoked to finally get the driver working, but now I've been through all the tricks on this thread and the wiki. Still have the watermark. And yes, I made sure the script was checked in rcconf... Is there something else we should be looking at? Everything else works great; video renders well, Compiz does its thing, and it detected the new monitor without any issues at all.

---

### Post by darmok47 on 2011-01-05
Hi, 
first thanks so much for this very useful help.

Now i have the same problem with amd watermark; tried your solution, but doesn't work!

Someone has other solutions?

---

### Post by mrintegrity on 2011-01-05
It works perfectly here with an 6870, Installed from the official ATI fglrx 10.12, manually updated Xorg.conf and added the suggested init script. The watermark is gone also.

Thanks to those who suggested the solution.

/mr

---

### Post by martunes13 on 2011-01-05
If you are using 64-bit, use the script below:

#!/bin/sh

DRIVER=/usr/lib64/xorg/modules/drivers/fglrx_drv.so

for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done

---

### Post by olof_ on 2011-01-06
> **Heuamöbe said:**
> Did I understand it right that you got a HD 6850 to work? Because I tried it several times now, even with a fresh intalation, and I can't even start amdcccle and aticonfig says there is no device detected.
Can you please explain how you did it? I mean, i'm working with ubuntu for quite a while now, but i'm not very into this "system"-stuff... Thank you very much.

I just came up with this idea that I aways use to add these two ppa:s when I install ubuntu:
[URL="https://launchpad.net/~ubuntu-x-swat/+archive/x-update"]
ubuntu-x-swat/x-updates[/URL]
and 
[xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa")

maybe it have something to do with my success, but probably not. Anyways, now you have everyhing I use(d) to successfully get it working.

---

### Post by jniklast on 2011-01-06
> **martunes13 said:**
> If you are using 64-bit, use the script below:

#!/bin/sh

DRIVER=/usr/lib64/xorg/modules/drivers/fglrx_drv.so

for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done

That didn't work for me either (I'm on 64-bit), what did the trick though was using DRIVER=/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so 

Hope that helps others too.

---

### Post by olof_ on 2011-01-06
THANK YOU!

> 
#!/bin/sh

DRIVER=/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so 

for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done

That is IT!
THANK YOU so much!

edit: I am using Ubuntu 10.10 x64.

---

### Post by mrintegrity on 2011-01-06
Can someone else who has this driver working please confirm if flash videos are unwatchable and nearly lock up the system on youtube?

[http://www.youtube.com/watch?v=-zvCUmeoHpw](http://www.youtube.com/watch?v=-zvCUmeoHpw)

That's a 720p example but it also happens with SD content try changing that video to lowest res, same problem in full screen - wth!?

---

### Post by mrintegrity on 2011-01-06
The slowness and lockups occur with standard def content in Full screen I would like to clarify.. :|

---

### Post by olof_ on 2011-01-06
When I watch it in fullscreen in 720p is my cpu approximatly using up to 80% load, using flash 10.1 r102 and a 3.6 Ghz intel c2d dualcore with 8 GB ram.

but no lag or other artifacts. 

Maybe you should try with [flash 10.2]("http://www.ubuntugeek.com/how-to-install-adobe-flash-10-2-preview-in-ubuntu-10-10-maverick-using-ppa.html")?

---

### Post by mrintegrity on 2011-01-06
> **olof_ said:**
> When I watch it in fullscreen in 720p is my cpu approximatly using up to 80% load, using flash 10.1 r102 and a 3.6 Ghz intel c2d dualcore with 8 GB ram.

but no lag or other artifacts. 

Maybe you should try with [flash 10.2]("http://www.ubuntugeek.com/how-to-install-adobe-flash-10-2-preview-in-ubuntu-10-10-maverick-using-ppa.html")?

Thanks I tried 10.1 and 10.2 from the repo's and a ppa, same on both. Just to be sure, are you using a radeon 6000 series?

---

### Post by olof_ on 2011-01-06
I added the new info on the [cchtml wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide"), but can anyone confirm which version of the script which did work on Ubuntu 10.10 x86?

---

### Post by olof_ on 2011-01-06
> **mrintegrity said:**
> Thanks I tried 10.1 and 10.2 from the repo's and a ppa, same on both. Just to be sure, are you using a radeon 6000 series?

yes and no, I am using one 6850 and one 4850, with two monitors attached to each gpu. What is your hardware specs?

---

### Post by mrintegrity on 2011-01-06
> **olof_ said:**
> yes and no, I am using one 6850 and one 4850, with two monitors attached to each gpu. What is your hardware specs?

:o Nice setup! I have a single 6870 with 24" Dell U2410 and normal videos play excellently full screen, including 1080p.. just flash is completely broken.

Have you tried putting the flash on each of your GPU's?

---

### Post by olof_ on 2011-01-06
> **mrintegrity said:**
> :o Nice setup! I have a single 6870 with 24" Dell U2410 and normal videos play excellently full screen, including 1080p.. just flash is completely broken.

Have you tried putting the flash on each of your GPU's?

how should I do that, I am using Xinerama. 
Maybe you should give [ Gnash]("http://savannah.gnu.org/projects/gnash/") or [Swfdec]("http://swfdec.freedesktop.org/wiki/") a try?

---

### Post by mrintegrity on 2011-01-06
I have not used gnash etc yet, they are not really feature complete enough for me to not care about fixing this issue with proprietary flash. 

Interestingly, the issue seems to dissapere when i "pop out" the youtube flash video into it's own window, I can then resize the window to whatever I want (bigger than full screen) and it playes pretty much OK (720p or lower). The issue only happens when it's embedded in the main firefox window.. I will try to make a video to show the issue and upload it.

/mr

EDIT: This is fixed now :D. The issue was actually compiz and enabling "workarounds > legacy fullscreen support" in compizconfig-settings-manager fixed it perfectly!

Thanks for your help though olof_!

---

### Post by Flipflops4life on 2011-01-06
I'm following the cchtml tutorial to get my Radeon 6850 working, and I'm stuck on generating the new xorg.conf file. When I enter the command:

*sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak*

I get this:

*mv: cannot stat `/etc/X11/xorg.conf': No such file or directory*

Any thoughts? Do I need to manually create a config in the X11 folder? There is a xorg.conf.failsafe I'm guessing this was the backup I created? I dunno, I'm stumped :p

---

### Post by mrintegrity on 2011-01-06
> **Flipflops4life said:**
> I'm following the cchtml tutorial to get my Radeon 6850 working, and I'm stuck on generating the new xorg.conf file. When I enter the command:

*sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak*

I get this:

*mv: cannot stat `/etc/X11/xorg.conf': No such file or directory*

Any thoughts? Do I need to manually create a config in the X11 folder? There is a xorg.conf.failsafe I'm guessing this was the backup I created? I dunno, I'm stumped :p

Ubuntu generally does not create an xorg.conf file anymore. This message is just telling you that the file does not exist so you can ignore that step in the instructions.. Instead you just need to create the file manually.

/mr

---

### Post by olof_ on 2011-01-06
> **Flipflops4life said:**
> I'm following the cchtml tutorial to get my Radeon 6850 working, and I'm stuck on generating the new xorg.conf file. When I enter the command:

*sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak*

I get this:

*mv: cannot stat `/etc/X11/xorg.conf': No such file or directory*

Any thoughts? Do I need to manually create a config in the X11 folder? There is a xorg.conf.failsafe I'm guessing this was the backup I created? I dunno, I'm stumped :p

copied from the cchtml wiki:
> 
Before you do this, back up your current xorg.conf if you have one (Ubuntu Lucid/10.04 and later does not have an xorg.conf by default) 


---

### Post by jniklast on 2011-01-06
> **olof_ said:**
> THANK YOU!


That is IT!
THANK YOU so much!

edit: I am using Ubuntu 10.10 x64.

You're welcome! ;)

I'd like to add that executing that script on startup isn't really necessary. Just do it everytime the module gets updated (driver updates and kernel updates?). Of course it doesn't hurt at boot either, but it takes a few seconds at least on my system.

> **mrintegrity said:**
> Can someone else who has this driver working please confirm if flash videos are unwatchable and nearly lock up the system on youtube?

[http://www.youtube.com/watch?v=-zvCUmeoHpw](http://www.youtube.com/watch?v=-zvCUmeoHpw)

That's a 720p example but it also happens with SD content try changing that video to lowest res, same problem in full screen - wth!?

I can't confirm that with a 6850 using Flash 10.1 r102. Just like the olof I have roughly 80% CPU in FS, but everything is smooth and no lockups.

---

### Post by olof_ on 2011-01-06
> **jniklast said:**
> 

I'd like to add that executing that script on startup isn't really necessary. Just do it everytime the module gets updated (driver updates and kernel updates?). Of course it doesn't hurt at boot either, but it takes a few seconds at least on my system.

thank you for the information. I feel like I can wait that additional second just to never have to see the watermark again. (I have had it there for more than a month now!)

---

### Post by Flipflops4life on 2011-01-06
@ Olof_ Oooook got it. I read the disclaimer as "10**.14** and later" - I've been working on this so long I'm beginning to see imaginary numbers.

I'd like to say I've made progress but it seems I've worked myself into more trouble. At first, I rebooted after installing all the packages/debs whatnot and went to test the installation with the "fglrxinfo" command. It came back as "command not found"

I did some poking around and found fglrx and the rest of the downloaded package and they are installed according to software manager.... then comes my newest issue. I was poking around some more - I can't remember exactly what I was doing - but I think I went into >Additional Drivers where I found ATI/AMD: FGLRX or something to that effect and it was not active. Since activating the driver and rebooting I am unable to boot back into my GUI. 

First - I have to get back into my GUI - how?:confused:
Second - assuming I don't have to restart the entire Catalyst installation process what is my next step considering fglrxinfo returns no results?

Thanks for the continued help folks ):P

---

### Post by jniklast on 2011-01-06
> **olof_ said:**
> thank you for the information. I feel like I can  wait that additional second just to never have to see the watermark  again. (I have had it there for more than a month now!)

Wow I feel bad for you, glad that I could help you. I was already getting mad at it even though I just got my video card today and had to bear it for only half an hour or so.

> **Flipflops4life said:**
> @ Olof_ Oooook got it. I read the disclaimer as "10**.14** and later" - I've been working on this so long I'm beginning to see imaginary numbers.

I'd like to say I've made progress but it seems I've worked myself into more trouble. At first, I rebooted after installing all the packages/debs whatnot and went to test the installation with the "fglrxinfo" command. It came back as "command not found"

I did some poking around and found fglrx and the rest of the downloaded package and they are installed according to software manager.... then comes my newest issue. I was poking around some more - I can't remember exactly what I was doing - but I think I went into >Additional Drivers where I found ATI/AMD: FGLRX or something to that effect and it was not active. Since activating the driver and rebooting I am unable to boot back into my GUI. 

First - I have to get back into my GUI - how?:confused:
Second - assuming I don't have to restart the entire Catalyst installation process what is my next step considering fglrxinfo returns no results?

Thanks for the continued help folks ):P

Well, I guess I used a rather opportunistic approach, but it worked pretty fast for me:

After installing the video card itself I couldn't start X anymore, so I chose recovery mode at boot and chose the root shell. There I simply started X by starting kdm (I'm on Kubuntu, probably simply gdm for ubuntu) adn I was greeted by a dialog saying that my graphic card isn't working as expected (surprise, surprise). I then chose the standard settings that the dialog was offering me, rebooted, and I was able to start X with the vesa drivers. There I first installed fglrx via the additional drivers dialog. Of course those were the old catalyst drivers, so I manually downloaded the newest and installed those. That got everything working except for the watermark, but I removed that with the script like I said.

I don't know if this helps you at all, but I would recommend you to use the recovery mode boot option when you can't start X anymore anyway.

---

### Post by Yellow Pasque on 2011-01-06
> **Flipflops4life said:**
> @ Olof_ Oooook got it. I read the disclaimer as "10**.14** and later" - I've been working on this so long I'm beginning to see imaginary numbers.

I'd like to say I've made progress but it seems I've worked myself into more trouble. At first, I rebooted after installing all the packages/debs whatnot and went to test the installation with the "fglrxinfo" command. It came back as "command not found"

I did some poking around and found fglrx and the rest of the downloaded package and they are installed according to software manager.... then comes my newest issue. I was poking around some more - I can't remember exactly what I was doing - but I think I went into >Additional Drivers where I found ATI/AMD: FGLRX or something to that effect and it was not active. Since activating the driver and rebooting I am unable to boot back into my GUI. 

First - I have to get back into my GUI - how?:confused:
Second - assuming I don't have to restart the entire Catalyst installation process what is my next step considering fglrxinfo returns no results?

Thanks for the continued help folks ):P
You probably typed fglrxinfo wrong and then borked your system by installing the (older) Ubuntu version of fglrx over your Catalyst 10-12. That's exactly what the instructions told you to do, right? ;)

---

### Post by Flipflops4life on 2011-01-06
>  There I first installed fglrx via the additional drivers dialog. 

Where is "there"? lol sorry I'm not sure I follow. You installed fglrx from the additional drivers window? And not through the command promt?

>  ... so I manually downloaded the newest and installed those 

Where did you find these catalyst drivers? I can't seem to find anything that I can use.

> That's exactly what the instructions told you to do, right? :wink:

haha you got me, I'm always trying to figure things out through trial/error - which is why this is probably so hard right now. In my defence there is no possibility of misspelling fglrxinfo because I copied it straight from the wiki. I'm guessing at this point I'll need to backup and reinstall the whole mess hoping that I don't leave behind any remnants of this last fiasco.

Did anyone else have the "command not found" after entering fglrxinfo?

---

### Post by Flipflops4life on 2011-01-06
Alright, I think I did a pretty good wipe and reinstalled everything. I still get the "command not found" error when I run fglrxinfo. Not sure what to do here, this is the same dead end I keep ending up at.

Also when I go to System>Administration>Additional Drivers I see that there is an ATI/AMD proprietary FGLRX graphics driver, but it is not activated. The wiki does mention something about activating this driver but it is at the beginning. I dunno it just seems out of order - I activated this the last time and got locked out of the GUI. I'm just going to sit tight at this step until some good advice surfaces ;)

As always thanks for the help guys!

---

### Post by martunes13 on 2011-01-07
@ Flipflops4life

Download the linux driver from the AMD website at [www.amd.com](www.amd.com) . Currently, the package is not available for the HD6XXX series so download the linux package for the HD5XXX series. Just go a couple of pages back to find out how to install it manually. You also have to make your own xorg.conf file.

---

### Post by Flipflops4life on 2011-01-07
@martunes13 THANK YOU THANK YOU! I knew I had to go back and create the xconfig, I found the command line I was looking for. All I have to do now is apply the water mark fix and I'm done CHEERS!:p

---

### Post by martunes13 on 2011-01-07
For the watermark, the portion of the script "DRIVER=/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so" depends on where fglrx_drv.so is located. 

Mine is at "/usr/lib64/xorg/modules/drivers/". I don't have this folder "/usr/lib/fglrx/xorg/modules/drivers/".  

It could also be at "/usr/lib/xorg/modules/drivers/".  

So locate fglrx_drv.so first using nautilus or whichever way suits you before saving the script. It probably depends upon how the driver was installed.

---

### Post by Yellow Pasque on 2011-01-07
> It probably depends upon how the driver was installed.
You installed directly (i.e. not using .deb packages). I hope that doesn't come back to haunt you eventually :( (yes, I've seen it happen too many times).

---

### Post by martunes13 on 2011-01-07
@Temüjin,

No problems whatsoever. First used Catalyst 10.11 and now using Catalyst 10.12. No slowdown when watching flash videos maximized. CPU usage is still low. :D

---

### Post by YPwn on 2011-01-09
> **martunes13 said:**
> For the watermark, the portion of the script "DRIVER=/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so" depends on where fglrx_drv.so is located. 

Mine is at "/usr/lib64/xorg/modules/drivers/". I don't have this folder "/usr/lib/fglrx/xorg/modules/drivers/".  

It could also be at "/usr/lib/xorg/modules/drivers/".  

So locate fglrx_drv.so first using nautilus or whichever way suits you before saving the script. It probably depends upon how the driver was installed.

Thanks. That helped me when I changed the folder in the script.

But I still have the problem with Totem: [http://s003.radikal.ru/i202/1101/67/a0fbc979dfe4.png](http://s003.radikal.ru/i202/1101/67/a0fbc979dfe4.png)

---

### Post by Heuamöbe on 2011-01-12
Hi
After the holidays I'm now trying to get full resolution...

The good thing is, I made it two days ago with a fresh installation (driver and xorg.conf).
The bad thing is that after installing some updates (about 200 ;)) I have the same problem as before (page 5). Of course i could install new again, install the updates and then set up the driver, but then I will be scarred at any new update :(. Have any one of you problems with updates? What would you advice me?

---

### Post by Yellow Pasque on 2011-01-12
> **Heuamöbe said:**
> Hi
After the holidays I'm now trying to get full resolution...

The good thing is, I made it two days ago with a fresh installation (driver and xorg.conf).
The bad thing is that after installing some updates (about 200 ;)) I have the same problem as before (page 5). Of course i could install new again, install the updates and then set up the driver, but then I will be scarred at any new update :(. Have any one of you problems with updates? What would you advice me?
How did you install the driver? If you update your kernel and the driver doesn't work right, that probably means something went wrong with building the new kernel module using dkms (or you didn't have dkms set up properly).

---

### Post by Krya on 2011-01-13
Hi there !
Im running 6870 on 10.10 and scrolling in browser killing my CPU :(
fglrx installed but
$ glxinfo | grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
3d works fine and glxgears is running smooth
$glxgears
31326 frames in 5.0 seconds = 6265.198 FPS
31509 frames in 5.0 seconds = 6299.018 FPS

Any ideas?

---

### Post by Heuamöbe on 2011-01-14
> **Temüjin said:**
> How did you install the driver? If you update your kernel and the driver doesn't work right, that probably means something went wrong with building the new kernel module using dkms (or you didn't have dkms set up properly).

Hey
I only made the .sh executable and double-clicked it^^
Is there something else to do?

---

### Post by Yellow Pasque on 2011-01-15
> **Heuamöbe said:**
> Hey
I only made the .sh executable and double-clicked it^^
Is there something else to do?
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)
This method builds packages and ensures dkms is enabled so that kernel updates automatically transfer the fglrx kernel module from the old kernel.

---

### Post by Yellow Pasque on 2011-01-15
EDIT: Double post. Forums are really touchy right now.

---

### Post by Heuamöbe on 2011-01-16
OK, thank you
I will try it tomorrow.

---

### Post by Heuamöbe on 2011-02-03
Hey,
I have one last problem. This evening I was short before to write a thankyou-note here because, everything was Ok in Linux Mint Debian Edition 32bit (Ubuntu always crashed the instalation), except the watermark. And because 
```
#!/bin/sh
DRIVER=/usr/lib/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
 sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done 			 		
```

didt'work, I tried

```
#!/bin/sh
DRIVER=/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so 
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
 sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done 			 		
```

And now I always end up in the shell after booting. :(

Is there any way to get this undone? Thank you very much :).

---

### Post by Yellow Pasque on 2011-02-03
Yes, you can reinstall the .debs you built:

```
cd ~/catalyst11.1 ; or whatever directory you put them in
sudo apt-get install --reinstall fglrx*
```

The hack was specific to Catalyst 10-12, so I removed it from the wiki. Sorry about the inconvenience.

---

### Post by Heuamöbe on 2011-02-05
Ok, thank you.

Is it possible to get rid of the watermark with Catalyst 11.1?

---

### Post by Heuamöbe on 2011-02-08
Is it?

---

### Post by Lucradia on 2011-02-10
> **Heuamöbe said:**
> Is it?

home-built Catalyst drivers that usually are built because older and stable drivers don't support your video card will have this watermark until you downgrade to your OS-distributed driver package that supports your card.

It's unavoidable. Just a note: The Watermark is an OSD. Turning your brightness / contrast all the way down will show as such. Hence, when taking screenshots or recording video on screen, the water mark will not appear.

---

### Post by Heuamöbe on 2011-02-10
> **Lucradia said:**
> Hence, when taking screenshots or recording video on screen, the water mark will not appear.

That doesn't help me, when I am looking at it all the time... 

Other question: Is it easily possible to downgrade to 10.12? Because with this version it is possible to remove the watermark, as you can read some posts before.

---

### Post by Heuamöbe on 2011-02-15
I updated to the new Catalyst 11.2 and the watermark is gone. Thanks to AMD and all the nice people in this forum!

---

### Post by Nilsb7 on 2011-02-19
Ok, I'm new to ubuntu, just done installing the basics but I'm stuck at installing the graphic drivers for my 6850 to.

Following this guide
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)
to manually install the drivers should work?

I've tried installing by going to system > administration > additional drivers which didn't work (black screen at startup) and I've tried installing by downloading the .run file directly from amd website (same result)

---

