---
title: "teething problems on 10.04LTS"
date: 2011-05-23
forum: General Help
---

### Post by tonyuk123 on 2011-05-23
Hi
ok i got bored with windows 7 as it now has got slow and started changing things randomly after a year
so i have installed 10.04 LTS and done all the updates

i was surprised to find the kernel fix(?) that means the ZTE (three broadband) modem worked straight off, great !
anyway a quick question, how and where do i turn off the double click on the mouse pad, as i hate it !

also seem to have a problem that on startup sometimes it doesn't see the USB Dongle/modem for three broadband and wont no matter what use it, but other times will just start and be fine from the off?????
anyone got any ideas on this, the only cure i have found is to restart until it does work, not ideal :P

Any help much appreciated, Tony

---

### Post by dragonfly41 on 2011-05-23
Re: USB dongle .. guessing that you might need to "safely remove" or "eject" rather than just yanking it out and sticking it back in?   That routine (right click and eject) applies to USB flash so it might apply also to your USB dongle .. that's the guess since it is intermittent.

---

### Post by tonyuk123 on 2011-05-23
thanks, good suggestion, i will try that tonight after work although i see it as more of a short term solution rather than a long term one.
No ideas why mostly it doesn't see it or start up working with it?

Tony

---

### Post by dragonfly41 on 2011-05-23
I think you'll have to search for "auto mount devices" in the forum.

My several USB devices are all mounted in /media

Here is one example thread ..

[http://ubuntuforums.org/showthread.php?t=1660241&highlight=auto+mount+devices](http://ubuntuforums.org/showthread.php?t=1660241&highlight=auto+mount+devices)

---

### Post by nerdy_kid on 2011-05-23
I think he is talking about a usb "Dongle/modem"  not a flash drive.

---

### Post by barrieluv on 2011-05-23
> **tonyuk123 said:**
> Hi
anyway a quick question, how and where do i turn off the double click on the mouse pad, as i hate it 

Any help much appreciated, Tony

Open Nautilus>Edit>Preferences>Behaviour>Single click to open items

---

### Post by tonyuk123 on 2011-05-23
thanks for the fix for the double click but not sure it is what i want from the description (at work so can't try  it)
what i want is to disable the double tap to launch things on the touch pad, and let it only do it when i use the left mouse button (but this is a laptop)
i find i usually touch the pad so lightly it often thinks i have tapped it and does something i haven't intended
Tony

---

### Post by barrieluv on 2011-05-25
Ah, in that case fiddle with the settings under System>Preferences>Mouse>General>Double Click Time-Out

---

### Post by yetiman64 on 2011-05-25
> **tonyuk123 said:**
> thanks for the fix for the double click but not sure it is what i want from the description (at work so can't try  it)
what i want is to disable the double tap to launch things on the touch pad, and let it only do it when i use the left mouse button (but this is a laptop)
i find i usually touch the pad so lightly it often thinks i have tapped it and does something i haven't intended
Tony
Usually a laptop will have a function key combination to disable/enable the touchpad. My Acer laptop used the combination Fn (function key) + F7 (there should be a pictorial representation of a touchpad on one of your F<number> keys).

I was always triggering a double click or changing the window focus as the palm of hand brushed over the touchpad while typing, most annoying when you have a mouse available as well.

I think it is a hardware feature, not a software setting you're looking for, check your laptop manual if you have one available.

What make/model is your laptop?

---

### Post by tonyuk123 on 2011-05-25
hi, well i dont want the touch pad to stop working, just the double click on it as i prefer to use the left button

anyway thats really a minor problem, seems since i updated everything, the modem doesn't work atall, sometimes is present but wont connect, othertimes it isnt seen as a zte modem and shows not 'three' connection to connect to
any ideas?

from fresh cd install of 10.04lts it work straight off, which was great ! seems the updates stopped it 

presently back on win7 hellllllppppp

---

### Post by tonyuk123 on 2011-05-30
well still not getting very far here

decided as it worked from new install to go back to that stage
did that (10.04 LTS btw) when complete could not even get it to work
found that it recognised the device but not exactly what it was
after much looking and wondering i restarted and for some reason this time it knows what the USB modem is and works !
anyone any ideas on this ?????

here is the the terminal output for no USB modem attached (obv.not working)
USB Modem attached but not working
& USB modem attached and working

anthony@anthony-laptop:~$ lsusb
Bus 002 Device 004: ID 1004:6000 LG Electronics, Inc. VX4400/VX6000 Cellphone
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 064e:a219 Suyin Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

anthony@anthony-laptop:~$ lsusb
Bus 002 Device 006: ID 19d2:0103 ONDA Communication S.p.A. 
Bus 002 Device 004: ID 1004:6000 LG Electronics, Inc. VX4400/VX6000 Cellphone
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 064e:a219 Suyin Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

anthony@anthony-laptop:~$ lsusb
Bus 002 Device 004: ID 1004:6000 LG Electronics, Inc. VX4400/VX6000 Cellphone
Bus 002 Device 003: ID 19d2:0031 ONDA Communication S.p.A. ZTE MF636
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:a219 Suyin Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


if that helps atall

but i'm guessing if i restart again it will probably dissapear......

can i force it to 'know' the modem is a ZTE MF636?????


Tony

---

### Post by gandaran on 2011-05-30
I had the same problem with a mobile dongle in ubuntu 10.04, what I did was just to remove the modem then plug it again and it would connect no need to reboot, never had the problem on ubuntu 10.10.
check that you have usb-modeswitch installed from package manager as in 10.04 its not installed by default.

---

### Post by tonyuk123 on 2011-05-30
> **gandaran said:**
> I had the same problem with a mobile dongle in ubuntu 10.04, what I did was just to remove the modem then plug it again and it would connect no need to reboot, never had the problem on ubuntu 10.10.
check that you have usb-modeswitch installed from package manager as in 10.04 its not installed by default.

thanks Gandaran, seems this has fixed the problem
rebooted a few times and still works fine
otherwise all seems ok, apart from not being able to switch off the double click on the mouse pad, but i guess i will get use to that after a time

Tony

---

### Post by tonyuk123 on 2011-07-02
Hi,
well the Usb Modem fixed seemed to work for a few days, then stopped and so far never worked again
it does however work in win7 still so i know its not faulty
any more ideas on this, i did think about an upgrade to 10.10 but so far it hasn't connected for me to do this
i have found that if i start the laptop with it unplugged and wait then plug it in, it does appear in the connections list but it wont connect (anymore) 
basically these days without the internet you can hardly do anything
as you will appreciate
i think this modem fix should be much higher priority in future versions, as fixing anything requires a connection
i have also seen 10.10 is great with usb modems (or so it seems) but 11.? isn't ! how can they get that so wrong again !
Anyway, i appreciate getting everything to work is almost impossible, and am prepared to try whatever i can, but a connection by any means at the moment would be good or i am stuck on Win7 as i am now !!!!

---

### Post by tpprynn on 2011-07-02
Have you tried this?



SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="0103", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"



This is some contents for a file called

zte_eject.rules

which you should dump in

etc/udev/rules.d

Those are pre-existing folders and zte_eject.rules is a file you create.

My 3 dongle works fine with 11.04 by the way, and without zte_eject.rules, though it is slower to show up than when I had 10.04.

From another Tony in the UK...

The dongles work better with OpenDNS (208.67.222.222, 208.67.220.220) or GoogleDNS (8.8.8.8, 8.8.4.4) too.

If this doesn't work i'd think the only possible change needed would be for that number 0103 to be different, it shouldn't be hard to find out what though. Let us know how you do.

---

### Post by tonyuk123 on 2011-07-02
hi, well i tried that and no need to change that code, its working now, in fact i'm using it now
thanks for that
haven't tried a restart yet, hopefully be ok as i assume it loads that rule every time it starts?
thanks Tony from Tony

---

### Post by tpprynn on 2011-07-02
Yep that file if you put it where described will kick in each boot, as hopefully you've already found. I'm assuming there's something about 11.04's kernel that effectively includes that bit of code.

---

### Post by tonyuk123 on 2011-07-02
well guess not exactly, as restarted and it has no three connection
device is once again listed but not the exact one
so basically same as before, so back on Win7 again !
tony

---

### Post by tpprynn on 2011-07-02
Maybe it should have been this:

SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2",
  RUN+="/usr/local/sbin/usb_modeswitch"

in that file, judging by this page

[http://forums.whirlpool.net.au/archive/1130260](http://forums.whirlpool.net.au/archive/1130260)

I expect you've possibly had enough for now but next time you get the itch maybe give that a try.

My dongle is 3's current one, mf612 or mf112 or something, (£14 with 1gb on in some shops right now, Tesco I think), but I'd thought I'd deduced the lines would be the same.

Do you get the 3 Connect icon pop up on your screen? and if so did you right click on it and manually eject it, seeing if the modem shows up in Network Manager soon after shows this?

Whenever I've fluffed this sort of thing I always delete the connection in NM and reboot to make it anew until it works, although I could just be being superstitious.

There is also Saki3g, which is a bit of a pain to use but works.

[http://www.sakis3g.org/](http://www.sakis3g.org/)

---

### Post by tonyuk123 on 2011-07-04
well tried that too, as always, worked when i did it
but not after a restart
kind of hoping for a permanent fix as i am once again back on Win7!

i have an Acer apire 5742
the usb modem dongle is ZTE MF112 on 'Three' mobile broadband network

does anyone have any further ideas about this?
Tony

---

### Post by tonyuk123 on 2011-07-09
oh well i'll stick with win 7 until the next LTS version then
maybe usb modems will be higher priority by then 
thanks everyone for trying

---

