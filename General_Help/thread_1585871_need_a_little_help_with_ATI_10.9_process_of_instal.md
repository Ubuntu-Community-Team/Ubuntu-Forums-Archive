---
title: "need a little help with ATI 10.9 process of installing"
date: 2010-10-01
forum: General Help
---

### Post by sendblink23 on 2010-10-01
Currently in the beginning/middle about to do the purging of the ATI "fglrx" drivers(I haven't done it yet)

Just incase... I'm using 10.04 LTS x64, crossfireX 5770's

well following the Catalyst 10.9 PDF provided by ati's website... it says something about the xorg...
> In order to restore the system to the previous state before the last installation, the original
configuration file needs to be restored manually. Without that, Xorg may fail to start
properly after uninstalling the driver and rebooting the system.

To restore the original Xorg configuration file:
1 Locate backup configuration files: ls /etc/X11/xorg.conf.original-*

2 Take the latest version with the highest number and copy it over the existing
xorg.conf file: cp /etc/X11/xorg.conf.original-<number> /etc/X11/xorg.conf

After that it is safe to reboot the system and it will start up using the open-source driver
that ships with the OS.


Well here is my concern...  my etc/X11/   has:
xorg.conf.dist-upgrade-201009261805
xorg.conf

both contain the exact same thing inside of them:
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

```

I assume they both look for the same thing "not the original ubuntu driver".. I'm guessing they both look for the fglrx driver

so.....  I am 100% certain my cards on a fresh install of 10.04 I get no display... so my way of fixing my own no display issue on 10.04 was doing an install of 9.10, installing the ati fglrx driver there(System > Administration > Hardware Drivers)... afterwards doing the 10.04 upgrade & then 10.04 would boot fine without the no display issue - plus they actually work perfectly fine for me... I just want to test out the 10.9's(since obviously they are way extremely newer than the outdated fglrx drivers)

Now since I don't have an original Xorg.conf file of 10.04.... How can i fix this now... hoping after reboot I do not get the no display issue?

-I haven't yet purged the current ati fglrx driver, I'm waiting for anybody here who is an ATI expert lol to help me with this.. so that I could continue on the process

in other words I haven't done anything yet.. just downloaded the *run file from ati's website... if you have a better process of how to install these 10.9 drivers please share your process, so that i can do it like it works for you.. including your process of purging these fglrx drivers.. hopefully it works for me too

thanks

---

### Post by pelle.k on 2010-10-06
I just happened to stumle over this post. I reckon i'm a bit late? Anyways, AFAIK, ubuntu 10.04 has no xorg.conf by default. The one that is there now is just to overrde the built in "free" driver.

---

### Post by sendblink23 on 2010-10-06
Thnx don't worry, I did solve my issue of getting to work the 10.9's

And yes you are right about the no need of xorg.conf ... no clue why i get the no display issue when installing fresh 10.04...   but wte... I decided to erase them and yes it booted fine afterwards

Managed to test the 10.9 catalyst drivers on 10.04 and honestly the performance was exactly the same as the regular FGLRX driver while using 10.04 LTS

I'm currently now using 10.10 RC (fresh install) which its working pretty good... using now FGLRX...  I'm still kinda getting the same performance as previously back on 10.04

Does anybody know how to fix the Jerky Video(vetical lines = as in like playing games on Windows with Vsync Off) on any movies or video files(avi, mkv) even on a Window or Full Screen on both it does the same thing - I've already tested with mplayer, vlc & movie player - and on all of them the same thing happens

The videos / movies play fine... its just that it creates the vertical lines randomly on any type of video file.. look at the example screen shot:

[[IMG]http://img819.imageshack.us/img819/2326/screenshotverticallinea.th.jpg[/IMG]](http://img819.imageshack.us/img819/2326/screenshotverticallinea.jpg)

fglrxinfo from 10.10 RC:
[[IMG]http://img541.imageshack.us/img541/8796/fglrx1010rc.th.jpg[/IMG]](http://img541.imageshack.us/img541/8796/fglrx1010rc.jpg)

---

### Post by pelle.k on 2010-10-08
> **sendblink23 said:**
> I'm currently now using 10.10 RC (fresh install) which its working pretty good... using now FGLRX...  I'm still kinda getting the same performance as previously back on 10.04

Does anybody know how to fix the Jerky Video(vetical lines = as in like playing games on Windows with Vsync Off) on any movies or video files(avi, mkv) even on a Window or Full Screen on both it does the same thing - I've already tested with mplayer, vlc & movie player - and on all of them the same thing happens

The videos / movies play fine... its just that it creates the vertical lines randomly on any type of video file.. look at the example screen shot:
Yeah, that's called screen tearing, and it's becuase the propreitary ATI driver cant use vsync (on most configurations) with videos while compositing (compiz, desktop effects) is activated. The free driver should do better in that respect, but i guess your 5770 isn't well supported with that one just yet. The situation is much better for nvidia owners, im afraid.

That said, catalyst10.9+xorg1.8 is reported to play videos without screen tearing, but catalyst10.10+xorg1.9 (the ones in ubuntu maverick) has yet to do that. catalyst10.10 isn't even official yet anyway, so maybe it'll be fixed in time for it's "real" release? If not, you can always hope for catalyst10.11. LOL. Or turn of desktop effects.

---

