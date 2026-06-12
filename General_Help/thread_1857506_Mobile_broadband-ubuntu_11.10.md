---
title: "Mobile broadband-ubuntu 11.10"
date: 2011-10-10
forum: General Help
---

### Post by Jomukuk on 2011-10-10
Mobile broadband-ubuntu.
A little help needed !
The system was upgraded from 11.04 to 11.10 recently (beta)
On 11.04 I had no problems, it would see the adaptor and display it.
In 11.10, it does not. Immediately.
I installed the work-around so that the device seen as a USB memory stick was disabled.
Not much use.
The adaptor is seen as cdrom-1, so still does not appear as a mobile connection (noticed because I was looking for the thing in system....and cdrom-1 only appears after I plug the device in)
Using the command line to query usb devices (lsusb) the huwei device is shown.
Hmmmm.
I'm going bald here.....

John

---

### Post by tpprynn on 2011-10-10
Every other edition of Ubuntu us Mobile Broadbanders are thrown...

Do you still have a live CD for 11.04 (Or 10.04/10 if it worked then too)? You could run it and inspect /lib/udev/rules.d/40-usb_modeswitch.rules and see if the lines with the numbers that tally up with your modem as seen in lsusb are missing from 11.10. If they are, put the lines on a pendrive and paste them back in in 11.10.

What dongle is it you've got, what model name and number and which provider are you with? I might be stumped for what to say next but I've got round this sort of thing a couple of times. And what does it say in lsusb about the Huawei?

Another workaround is to use Saki3G:

[http://www.sakis3g.org/](http://www.sakis3g.org/)

"Hello is that the Linux Foundation or whatever, yes, this is the managing director of Vodafone. I will sponsor your kernel if you help make our dongles obolete every eighteen months...." No, I'm sure this doesn't happen...

---

### Post by Jomukuk on 2011-10-10
What does lsusb respond with:
Bus 002 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270 HSDPA/HSUPA Modem
I still have a cd for 11.04 (have to, the system will not upgrade live.....) so I'll have a look...but the problem is not what it used to be a year ago (seeing the modem as removeable storage.....) this time "it" thinks the modem is a cdrom !
Mind you, I am so underimpressed with 11.10....the unity icons are so large, and not resizeable [yet]
I get so many warnings that everything is closing down that I feel like I'm back in windows ....
Compiz remains the same........and getting the desktop cube working needs a degree in extreme patience along with an ability to not throw a brick through the machine (acer aspire 5315)
Thanks for your help.....oh, and the report a program fault feature also crashes....so it cannot report itself...which is probably why so many faults are not corrected ?

John

---

### Post by gandaran on 2011-10-11
check if usb-modeswitch is installed, it should be but as 11.10 is still beta it could be missing.

---

### Post by Jomukuk on 2011-10-11
Usb-modeswitch 1.1.9-1 installed......about a week ago....the only difference is that it SOMETIMES recognises the adaptor.....after a period of time it will suddenly show 3internet in the taskbar...never immediately....usually after an hour or so...
And the device now shows as cdrom-1....oh well, it'll save me money on the data !!

---

### Post by tpprynn on 2011-10-11
Have you tried manually ejecting the cd-rom aspect of the dongle from the desktop as if it really were a cd-rom, with the right click on its icon and eject option? One or two dongles back I was having to do that for a while, it then showed up in Network Manager after a couple of seconds.

Annoying though, when I was with 3 earlier in the year that was the best Mobile Broadband speed-wise, often 6 meg down, 1 1/2 up, though they started dire. I have to go out right now but I'll make a suggestion when I get back if no one else has turned up with a solution, I don't want to rush it for the minute.

My T-Mobile (Huawei E167s) is working, but if I disconnect I have to reboot - not merely log out - before I can go online again. We never had that palaver about eighteen months ago.

---

### Post by Jomukuk on 2011-10-11
That's the first thing I looked for....I remember version 9....but i could not find removable storage on anything let alone the desktop.....then I installed the usb-modeswitch thinking that would solve it....well, it did, sort of.
It is now seen by lsusb...but still does not appear from boot....it's there as of this moment....but it takes a lot of time before the system sees the modem....
Very strange.

---

### Post by tpprynn on 2011-10-11
Okay this might be useless or you might have done this in the meantime or before.

Does your file /etc/udev/usb_modeswitch

read:

# Configuration for the usb_modeswitch package, a mode switching tool for
# USB devices providing multiple states or modes
#
# This file is evaluated by the wrapper script "usb_modeswitch_dispatcher"
# in /usr/sbin
# To enable an option, set it to "1", "yes" or "true" (case doesn't matter)
# Everything else counts as "disable"


# Disable automatic mode switching globally (e.g. to access the original
# install storage)

DisableSwitching=0


# Enable logging (results in a extensive report file in /var/log, named
# "usb_modeswitch_<interface-name>" (and probably others)

EnableLogging=0



...I think the DisableSwitching bit is the key bit...

And does /lib/udev/rules.d/40-usb_modeswitch.rules

have these lines:

# Huawei E220, E230, E270, E870
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1003", RUN+="usb_modeswitch '%b/%k'"

They've kept rejigging usb_modeswitch, where its files sit and all that - once it's working, why don't they leave it alone... Debian 6 is different again, and Fedora 15 got on with a dongle its contemporary edition of Ubuntu couldn't.

One last thing - you haven't changed any BIOS settings at all? I altered one setting regarding 'legacy usb' at one point, out of half-cocked curiosity, and didn't immediately suss out that this was why one dongle stopped behaving.

The issue with E220 modems has very recently been reported a couple of times on Launchpad by the way. Different laptops mentioned so I'm assuming it's not you.

---

### Post by Jomukuk on 2011-10-11
Thank you for the suggestions, I'll attempt to sort it once I have the laptop fired up....tomorrow !

---

### Post by Sergiu Bivol on 2011-10-12
Hi,
I think I have the same problem in Kubuntu 11.10 - the modem is detected, but by default Mobile Broadband is disabled in Network Manager.
If I chech „[x] Enable Mobile Broadband”, it works. After a restart, it's disabled again.
No matter how I change the settings, it will always be disabled after a reboot.

---

### Post by Jomukuk on 2011-10-13
Interesting.
in etc/usb_modeswitch.conf changing disable=1 to disable=0 and away it goes....albeit with a time-lag of a minute.
In the reply previous to this...have you saved the file after altering it ?
Thankyou for all the help....I'm still on a learning curve...which is getting more like a spiral....

---

### Post by alexfish on 2011-10-13
Hi

this seems to be a recurrence of problem in 10.04 , generally happens to devices which do not change the usb ID's after switching , think this device ID's have worked with Ubuntu without the modeswitch from 8.10. IE it is recognized by the kernel, had done a post some time ago . if the device does not require the usb_modeswitch  , best to leave the
> /etc/udev/usb_modeswitch and  usb_modeswitch.conf file as is,  the recommend change should be applied to "usb_modeswitch.conf" ( if any) . try edit the 

 /lib/udev/rules.d/40-usb_modeswitch.rules 

to disable the rule place a  #    at start  of the line , example

> # Huawei E220, E230, E270, E870
# ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1003", RUN+="usb_modeswitch '%b/%k'"this should allow the use of modems which require switching.

see what happens

regards

alexfish

---

### Post by tpprynn on 2011-10-13
So Jomukuk yours is working now then? Great. Not sure what the lag's about. Don't know if you notice any difference whether the dongle's plugged in before boot or after? My T-Mobile one won't work unless it's plugged in first with 11.04. Just about ot try Xubuntu 11.10 which I downloaded this afternoon, to see if it's any smoother. Lastly if your learning curve hasn't included Open DNS yet it's worth googling or telling us here so I or someone can add a crash course - did wonders for speed and connection stability with 3, Vodafone and T-Mobile alike.



...Mobile Broadband with KDE seems a bit of an enduring pain, except with Vodafone where you can use their own Linux software. Linux Mint 7 a couple of years back had the bright idea of using the Gnome Network Manager applet with KDE and it worked as well as in Gnome. Might be worth looking into, for example joining their forum and asking how it was done, or trying the iso out, which is of course out of date now but might tell you if the method is worth it.

At a guess you'd need to purge the KDE version of Network Manager while having access to wired internet and then reboot and install the Gnome applet.

---

