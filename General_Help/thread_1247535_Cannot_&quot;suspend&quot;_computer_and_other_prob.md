---
title: "Cannot &quot;suspend&quot; computer and other problems"
date: 2009-08-23
forum: General Help
---

### Post by HolyMythos on 2009-08-23
When I try to suspend Ubuntu, it goes down fine. However, when I try to wake it up I get a LOT of error messages, so many that it reads too quickly for me to catch any of it down. Ubuntu never comes up and I'm forced to shut down. Hybernate, restart and shut down all work perfectly fine. I'm running on an HP dv5 laptop if that helps.

My volume buttons also stopped working. I have a touch volume bar at the top of my keyboard which used to work. However, I noticed that my highest volume wasn't high as it was on Vista, so I tried to change the volume on the master volume. I changed the PCM volume and it changed the volume, but stopped my volume keys from working. When I turn up/down the volume with my volume buttons it shows the volume bar in the top right changing, but the volume does not. The only way for me to change it is through the master volume.

Also, my touchpad is really, really sensitive, and i'm not sure how to change it's sensitivity. I also notice that sometimes my touchpad will click when I haven't touched it, but i'm not sure if it's just my hand grazing over it while typing. It happens about once every half a minute to a minute and a half.

Anyone have any solutions? Thanks in advance guys!

---

### Post by staf0048 on 2009-08-23
What version of Ubuntu are you using?

Your suspend issue typically (though not always) has to do with your graphics card.  Have you tried installing the proper drivers for your card?  From a quick Google search it looks like you have an Nvidia 9200.  Try enabling the driver through System/Administration/Hardware Drivers to see if that helps your suspend problem.

Not sure about the volume issue . . .

You can change your mouse settings in system/preference/mouse.  See if you can slow it down or otherwise change it's sensitivity there.

---

### Post by HolyMythos on 2009-08-23
> **staf0048 said:**
> What version of Ubuntu are you using?

Your suspend issue typically (though not always) has to do with your graphics card.  Have you tried installing the proper drivers for your card?  From a quick Google search it looks like you have an Nvidia 9200.  Try enabling the driver through System/Administration/Hardware Drivers to see if that helps your suspend problem.

Not sure about the volume issue . . .

You can change your mouse settings in system/preference/mouse.  See if you can slow it down or otherwise change it's sensitivity there.

I tried changing the settings for the mouse, there were none about touchpad sensitivity.

As for the graphic drivers, I have the most current one installed. My Ubuntu is the 9.0.4 one

---

### Post by P4man on 2009-08-23
> **HolyMythos said:**
> When I try to suspend Ubuntu, it goes down fine. However, when I try to wake it up I get a LOT of error messages, so many that it reads too quickly for me to catch any of it down. Ubuntu never comes up and I'm forced to shut down. Hybernate, restart and shut down all work perfectly fine. I'm running on an HP dv5 laptop if that helps.

you can check those error messages on the next boot, go to system > administration > log files. Check out "dmesg" and copy/paste the relevant parts here. Can you also give the exact laptop type ? DV5 covers a whole range of very different laptops.

> 
My volume buttons also stopped working. I have a touch volume bar at the top of my keyboard which used to work.  However, I noticed that my highest volume wasn't high as it was on Vista, so I tried to change the volume on the master volume. I changed the PCM volume and it changed the volume, but stopped my volume keys from working. When I turn up/down the volume with my volume buttons it shows the volume bar in the top right changing, but the volume does not. The only way for me to change it is through the master volume.

They made that pretty confusing didnt they :)
try this: system > prefences > sound 
default mixer tracks, set it to playback (yourcard) pulseaudio mixer.
> 
Also, my touchpad is really, really sensitive, and i'm not sure how to change it's sensitivity. I also notice that sometimes my touchpad will click when I haven't touched it, but i'm not sure if it's just my hand grazing over it while typing. It happens about once every half a minute to a minute and a half.


A (far too) common problem :s
See if this helps:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

(assuming you have a synaptics touchpad, not an alps one).

Disabling while typing is a workable workaround.

---

### Post by HolyMythos on 2009-08-25
> **P4man said:**
> you can check those error messages on the next boot, go to system > administration > log files. Check out "dmesg" and copy/paste the relevant parts here. Can you also give the exact laptop type ? DV5 covers a whole range of very different laptops.

I went to the dmesg after it happened and had nothing about the error. I have to force shutdown during the errors because I cannot do anything and the computer never boots up afterwards.

This is the error I keep getting over and over. Note the numbers at the beginning of the text constantly change higher and higher. The computer never recovers. Also, the number that I began with isn't the exact number, it's around where I think it started:

[ 720.000000] ata1: irq_stat 0x00000040, connection status changed
[ 720.000000] ata1: SError: { DexExch }
[ 720.000000] ata2: exception EMask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen

Then it loops, sometimes exchanging ata1 with ata2.

---

### Post by P4man on 2009-08-26
looks like a similar problem as these guys:

[http://ubuntuforums.org/showthread.php?t=1037819](http://ubuntuforums.org/showthread.php?t=1037819)

In their case, its related to the nvidia drivers apparently, or a conflict between the nvidia card and ahci. Can you check if there is a newer BIOS for you machine?

If not, just taking some shots in the dark here, perhaps you can try to boot with these kernel parameters:

```
irqpoll
```

and/or

```
acpi=noirq
```

This link explains how to add those options temporarily (for one boot):

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

---

