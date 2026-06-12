---
title: "suspend to memory does not work after upgrade"
date: 2006-06-22
forum: General Help
---

### Post by nanotube on 2006-06-22
Hey all
so i finally upgraded from breezy to dapper. wee. :)
have one problem that i have so far not been able to resolve. suspend to memory stopped working!

i have edited my /etc/default/acpi-support to uncomment ACPI_SLEEP=true (since it reverted during upgrade), rebooted, but the suspend option still does not show up in the new "quit" dialog.

also, in breezy, it was possible to set a shortcut for suspend in the keyboard shortcuts panel, but that line item is no longer present there.

also, i tried running 
"sudo /etc/acpi/sleep.sh force"
and it suspended properly, but failed to wake up.

there is one other thing - i have switched from using the oss "ati" video driver to using fglrx (in the hopes that it gives better performance - and it does), that may have something to do with it, possibly? but it should not affect whether suspend option even shows up in the first place, though..

so, i would appreciate any help and suggestions in this regard.

using dell inspiron 5150, if it makes any difference. 

please share your ideas with me. :)

---

### Post by nanotube on 2006-06-22
update:
well, i enabled the suspend to memory to actually show up by going through the system>preferences>power management panel (on the last tab, i chose "suspend" as action for when sleep button is pressed, and it asked me if i am sure i want to enable suspend, and i said yes, and now it shows up )

but: it still does not resume properly (screen remains blank). i tried this now with both the stock "ati" driver as well as with the "fglrx" driver, and both produce the same result, resume from suspend "does stuff" but the screen remains totally blank. ctl-alt-f2 does not help, ctl-alt-backspace does not help, and ctl-alt-delete does restart the computer :)

so, anyone have any clues, things to try, etc? i will note that suspend worked perfectly under breezy, so it's not the hardware's fault, it's gotta be something new in one of them acpi scripts that screwing it up...

---

### Post by nanotube on 2006-06-22
ok, so i looked around, and played around with my /etc/default/acpi-support file, and have some encouraging results. 

here are the changes i made:

```
20c20
< MODULES_WHITELIST=""
---
> MODULES_WHITELIST="fglrx"
32c32
< # SAVE_VIDEO_PCI_STATE=true
---
> SAVE_VIDEO_PCI_STATE=true

```

so, after i did this, and suspended, and resumed - it resumed properly, but then froze like 30 seconds after it came up. but at least this is encouraging, because i was able to start using the system, etc.

next thing i tried (since i started suspecting network-manager as the culprit, since it failed to connect to the net between resume and the freeze, even though usually it connects pretty quick). so i disabled the wireless device (there is a kb shortcut for wifi to turn it on/off), and /then/ suspended, and then resumed, and then turned on the wireless device. and it worked, and so far no crashing. 

i will have to test it some more i guess, but looks like i am making progress.

but don't let that stop you, please, if you have some ideas/suggestions, i'd appreciate them. i am kinda poking around in the dark here.

---

### Post by nanotube on 2006-06-22
and so, i am replying to my own thread yet again. :)

it appears that the resume from suspend issue is still not solved. after some time i started seeing graphical artifacts on the screen (like pieces of screen becoming wrong color, or not updating, etc), and then after some more time, the comp froze, just the mouse moving, and not responding to any clicks or any keyboard commands. so i had to hard boot it.

so i am back where i started - suspend is still inoperable.

can anyone help me out here please? :)

---

### Post by nanotube on 2006-06-23
ok, yet another self-reply, but this time i think with good news. i made the following changes to /etc/default/acpi-support:

```
23c25
< SAVE_VBE_STATE=true
---
> SAVE_VBE_STATE=false
29c32
< POST_VIDEO=true
---
> POST_VIDEO=false
35c40
< USE_DPMS=true
---
> USE_DPMS=false
42c48
< # DOUBLE_CONSOLE_SWITCH=true
---
> DOUBLE_CONSOLE_SWITCH=true

```
(and of course, ACPI_SLEEP=true is uncommented)

then i also made a change to /etc/acpi/wireless.sh (because i have ipw2200 wifi - not needed if you don't have it, i guess)
```
9c9
<           echo -n 2 > $DEVICE/device/power/state;
---
>           echo -n 3 > $DEVICE/device/power/state;
```

and now everything appears to work right for going into and out of suspend.

now, i am not sure which one of these did the trick, but the trick was done, and i'm happy enough for now not to go mucking around with this anymore. :)

---

### Post by caldevil on 2006-06-23
See
[https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/46181](https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/46181)

I guess changing vbe_state to flase did the trick. That worked for me when I was using fglrx. But with fglrx breaking down with every other ubdate I switched back to open source Radeon. On my system the difference is just  marginal and I can live with that.

---

### Post by francisco_athens on 2006-06-23
[QUOTE=nanotube]ok, yet another self-reply, but this time i think with good news. i made the following changes to /etc/default/acpi-support:

```
23c25
< SAVE_VBE_STATE=true
---
> SAVE_VBE_STATE=false
29c32
< POST_VIDEO=true
---
> POST_VIDEO=false
35c40
< USE_DPMS=true
---
> USE_DPMS=false
42c48
< # DOUBLE_CONSOLE_SWITCH=true
---
> DOUBLE_CONSOLE_SWITCH=true

```
(and of course, ACPI_SLEEP=true is uncommented)

then i also made a change to /etc/acpi/wireless.sh (because i have ipw2200 wifi - not needed if you don't have it, i guess)
```
9c9
<           echo -n 2 > $DEVICE/device/power/state;
---
>           echo -n 3 > $DEVICE/device/power/state;
```

and now everything appears to work right for going into and out of suspend.

now, i am not sure which one of these did the trick, but the trick was done, and i'm happy enough for now not to go mucking around with this anymore. :)[/QUOTE]

These changes seem to work well with my notebook too! Thank you!
Medion Akoya EX, Centrino - Intel 855 video, ipw2200 wifi

---

### Post by nanotube on 2006-06-23
[QUOTE=caldevil]See
[https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/46181](https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/46181)

I guess changing vbe_state to flase did the trick. That worked for me when I was using fglrx. But with fglrx breaking down with every other ubdate I switched back to open source Radeon. On my system the difference is just  marginal and I can live with that.[/QUOTE]

yea, i considered that, but my system really does feel snappier with fglrx. also, with oss radeon, i get
6722 frames in 5.0 seconds = 1344.386 FPS
and with fglrx i get
9137 frames in 5.0 seconds = 1827.332 FPS
a 50% difference. 

but anyway, thanks for liking that launchpad page, i suppose maybe it was the vbestate thing. but i am not gonna be playing with it anymore, since it works so well for me now. :)

---

### Post by nanotube on 2006-06-23
[QUOTE=francisco_athens]These changes seem to work well with my notebook too! Thank you!
Medion Akoya EX, Centrino - Intel 855 video, ipw2200 wifi[/QUOTE]
excellent. ;)

---

### Post by dread on 2006-06-24
Thanks this fixed my suspend to memory issues on my dell d600.

---

### Post by cbudden on 2006-06-24
Hi.  I have made the changes suggested above but my laptop still doesn't resume from suspend.  The laptop turns on but the screen stays black, and I have to hard reboot.

I have a Acer 4501 Travelmate.  I'm using fglrx and XGL.

Here is my acpi-support file 
```


# Uncomment the next line to enable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="fglrx"

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

```

Thanks.

---

### Post by nanotube on 2006-06-25
try the following:

1. remove fglrx from modules_whitelist
2. comment out the "save_video_pci_state=true" line.

just for extra reference, here is my complete /etc/default/acpi-support file:

```
# Uncomment the next line to enable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES=""

##
# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

##
# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

##
# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

##
# Save and restore video state?
#SAVE_VIDEO_PCI_STATE=true

##
# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

##
# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

```

---

### Post by cbudden on 2006-06-25
[QUOTE=nanotube]try the following:

1. remove fglrx from modules_whitelist
2. comment out the "save_video_pci_state=true" line.

just for extra reference, here is my complete /etc/default/acpi-support file:

```
# Uncomment the next line to enable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES=""

##
# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

##
# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

##
# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

##
# Save and restore video state?
#SAVE_VIDEO_PCI_STATE=true

##
# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

##
# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

```[/QUOTE]


Thanks for the tip, but it didn't work.  Still hanging on startup.

---

### Post by nanotube on 2006-06-25
well, at this point all i can suggest is try playing with the various items in acpi-support, and see if anything works. you could make post_video=true, or use_dpms=true...
or search around google and/or these forums for fglrx and your video card model, maybe something will come up..

---

### Post by cbudden on 2006-06-25
Ok then, ill give that a go.  I use a mobility 9700 pro.

---

### Post by naked on 2006-07-01
[QUOTE=nanotube]
then i also made a change to /etc/acpi/wireless.sh (because i have ipw2200 wifi - not needed if you don't have it, i guess)
```
9c9
<           echo -n 2 > $DEVICE/device/power/state;
---
>           echo -n 3 > $DEVICE/device/power/state;
```
[/QUOTE]

This did the trick for me.  I'm using a dell 700m, and my NetworkManager would say that there is no networking card after a suspend.

What does this do exactly?

L

---

### Post by nanotube on 2006-07-01
[QUOTE=naked]This did the trick for me.  I'm using a dell 700m, and my NetworkManager would say that there is no networking card after a suspend.

What does this do exactly?

L[/QUOTE]
well, that file puts the network card to sleep too, but apparently our wireless card does not support "suspend level 2" but does ok with "suspend level 3". so, that's as specific as i can get on what exactly that does :)

---

### Post by morgengenuss on 2006-07-01
hi, i tried the changes suggested (my etc/default/acpi-support is exactly the same as nanotube's) and actually my laptop seems to come back, but the graphics are somehow... hum... strange. you can't recognize a thing, just strange pixels.
since i know i have to unlock the screen first i can login. and then i will even see some desktop symbols, but e.g. the background is gone and if i open a terminal only the window frame will show up.

(up to now i "resolve" this by logging out and in again. but this is not a real solution.) any suggestions? (i use fglrx too)

---

### Post by nanotube on 2006-07-02
[QUOTE=morgengenuss]hi, i tried the changes suggested (my etc/default/acpi-support is exactly the same as nanotube's) and actually my laptop seems to come back, but the graphics are somehow... hum... strange. you can't recognize a thing, just strange pixels.
since i know i have to unlock the screen first i can login. and then i will even see some desktop symbols, but e.g. the background is gone and if i open a terminal only the window frame will show up.

(up to now i "resolve" this by logging out and in again. but this is not a real solution.) any suggestions? (i use fglrx too)[/QUOTE]

hmm, well, try uncommenting the SAVE_VIDEO_PCI_STATE=true line. (try playing around with other parameters, too, if this one doesn't work). what vid card do you have, btw?

---

### Post by morgengenuss on 2006-07-02
i have the ati x1400 (as it says in my signature ;) )

i'll try to fiddle around with the parameters in the evening and get back to you.

---

### Post by nanotube on 2006-07-02
[QUOTE=morgengenuss]i have the ati x1400 (as it says in my signature ;) )[/QUOTE]
oh right, hehe :)

---

### Post by naked on 2006-07-02
Does anyone have the problem of having the laptop suspend when removing the power cord?  This is extremely annoying!

L

---

### Post by nanotube on 2006-07-02
[QUOTE=naked]Does anyone have the problem of having the laptop suspend when removing the power cord?  This is extremely annoying!

L[/QUOTE]
not me. but can you look in your /etc/default/acpi-support, and make sure that you have
```
ENABLE_LAPTOP_MODE=false
```
at the end there?

another thing (if that is indeed false, or if setting it to false does not solve it), is to go rooting around in your /etc/acpi/power.sh script. look there and see if it tries to suspend when power is out...

---

### Post by naked on 2006-07-02
[QUOTE=nanotube]
another thing (if that is indeed false, or if setting it to false does not solve it), is to go rooting around in your /etc/acpi/power.sh script. look there and see if it tries to suspend when power is out...[/QUOTE]

I don't know if I understand the file enough to tell that.  But you can gander if you like!:
```
#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

function laptop_mode_enable {
    $LAPTOP_MODE start
    
    for x in /sys/bus/ide/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 12 /dev/$drive 2>/dev/null
	$HDPARM -B 1 /dev/$drive 2>/dev/null
    done
    
    for x in /sys/bus/scsi/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 12 /dev/$drive 2>/dev/null
	$HDPARM -B 1 /dev/$drive 2>/dev/null
    done
}

function laptop_mode_disable {
    for x in /sys/bus/ide/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 0 /dev/$drive 2>/dev/null
	$HDPARM -B 255 /dev/$drive 2>/dev/null
    done
    for x in /sys/bus/scsi/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 0 /dev/$drive 2>/dev/null
	$HDPARM -B 255 /dev/$drive 2>/dev/null
    done
    $LAPTOP_MODE stop
}

getState;

checkStateChanged;

shopt -s nullglob

for x in /proc/acpi/ac_adapter/*; do
    grep -q off-line $x/state

    if [ $? = 0 ] && [ x$1 != xstop ]; then	
	for SCRIPT in /etc/acpi/battery.d/*.sh; do
	    . $SCRIPT
	done
	if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
	    (sleep 5 && laptop_mode_enable)&
	fi
    else
	for SCRIPT in /etc/acpi/ac.d/*.sh; do
	    . $SCRIPT
	done
	if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
	    (sleep 5 && laptop_mode_disable)&
	fi
    fi
done
```

---

### Post by nanotube on 2006-07-03
hmm, your power.sh looks normal, and doesnt seem to be calling sleep... so i don't know what's up. i'd suggest starting another thread with your issue, and see if anyone picks up on it. (or just wait and see if anyone picks up on this one here)

edit: actually, check out this link, seems to be talking about your kind of problem:
[http://cvs.gnome.org/viewcvs/*checkout*/gnome-power-manager/docs/faq.html#faq-lid-state-confused](http://cvs.gnome.org/viewcvs/*checkout*/gnome-power-manager/docs/faq.html#faq-lid-state-confused)

---

### Post by nanotube on 2006-07-03
by the way, for those of you still having problems, here is an informative link about suspend and video:
[http://www.kernel.org/git/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;hb=HEAD;f=Documentation/power/video.txt](http://www.kernel.org/git/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;hb=HEAD;f=Documentation/power/video.txt)

and here is another potentially useful link:
[http://cvs.gnome.org/viewcvs/*checkout*/gnome-power-manager/docs/faq.html](http://cvs.gnome.org/viewcvs/*checkout*/gnome-power-manager/docs/faq.html)

---

### Post by bosjee on 2006-08-12
Follow post #12 in apci-support line-by-line for my Notebook-- Gateway ARC200 and it works perfect. My notebook used Intel graphic card and I upgraded from the default Intel Wireless 2100 (a 11b card) to Broadcom 54G (BCM4306) mini-pci card, now running ndiswrapper at 54Mbps. I don't need to change any other file and it just works! The great thing is wireless come back on automatically after suspend to ram! And no graphics artifacts like some people have reported. Thank you so much nanotube.

I have been struggling for a long time without any success using FC4 6 months ago. Don't know whether FC5 would do it, but hey, I got it working with Ubuntu the first time installing it. Thanks Ubuntu team and thank you again Nanotube!

---

### Post by Cartwheels4amile on 2006-08-13
Alright, this is a complete n00b question... but every time I attempt to save my changes in /etc/default/acpi-support I get the message "cannot open file to write."

What in the world is going on?

---

### Post by patrickfromspain on 2006-08-13
sudo gedit /etc/default/acpi-support ;)

---

### Post by woifi on 2006-08-13
Hi!

I have a Samsung X20 with ATI X600, suspend to ram worked with breezy and fglrx - unfortunately not with dapper - the screen remains black after wakeup.

I read this thread an the bugreport in launchpad but nothing helped. Here is my /etc/default/acpi-support
```
# Uncomment the next line to enable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES="usbhid hiddev ehci_hcd uhci_hcd"

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true
# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false
```

The last change I did was uncommenting SAVE_VIDEO_PCI_STATE=true.

Any help would be much appreciated.

bye

woifi

---

### Post by nanotube on 2006-08-14
try using the exact copy of the acpi-support file as i posted in post #12, and see if that works. i see that your acpi-support differs from mine in a number of lines...

---

### Post by geckomind on 2006-08-16
Wow. Instructions in post #12 worked perfectly for my Dell XPS Gen2. Standby and Hibernate both now work as they should. Thank you! :KS :KS :KS

---

### Post by kleedrac on 2006-08-17
I'm not having an issue with video but my wireless settings get severely messed upon resume.  I can still see the card but I'm no longer connected to a network and the only two ways to get it back are to disable/reenable both LAN and WiFi devices then reconnect the WiFi device.  The other way is to reboot.  By disabling/reenabling the network devices I connect and reconnect to the network to the point I need to reboot my router!  I know I'm venturing a little off topic but hopefully someone has had the same issue.  Should I add the module into acpi-support?  Which module is it?

---

### Post by morgengenuss on 2006-08-20
@kleedrac: have you tried using wifi-radar to save your wireless profile and autoconnect at startup? (you can get it by: "sudo apt-get install wifi-radar" or via synaptic)

---

### Post by AndrewLZ on 2006-08-25
Hello everyone,

This fixed my Suspend (haven't tried hibernate, I can't reboot right now because I'm using automatix :)) but now there's no shutdown option in the Exit icon screen (don't know what to call it?).

I've been forcing it by just running sudo shutdown -r now but i'd like it to be there still!


If anyone could help me that'd be great! (I'm using the settings in Post #12 and the wifi edit).


Thanks in advance,

Andrew

---

### Post by louaym on 2006-08-27
thanks this worked for me
HP-Pavilon DV5002

> ACPI_SLEEP=true

> SAVE_VBE_STATE=false


> POST_VIDEO=false

> USE_DPMS=false


I do not know which one made the trick

---

### Post by bgg71 on 2006-09-05
great job! thanks. Now it works on my dell latitude d600 even with teh fglrx drivers. Hibernate was working even before but suspend stopped working after installing fglrx. After I changed those instructions in acpi_support suspend works again. very cool!

---

### Post by bgg71 on 2006-09-05
great job! thanks. Now it works on my dell latitude d600 even with teh fglrx drivers. Hibernate was working even before but suspend stopped working after installing fglrx. After I changed those instructions in acpi_support suspend works again. very cool!

---

### Post by trubblemaker on 2006-09-06
ok tried the suggested steps in post #12 still no love ... I don't crash,  it looks like it hibernates, but when I turn on the power it boots like normal, and event says that it's clearing suspend 2 signature.  I can suspend but I lose my touchpab after resume. any ideas? Here's my current config slightly different from 12 as it didn't work and I tried others
```
# Uncomment the next line to enable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true
# SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
# POST_VIDEO=true
POST_VIDEO=false

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true
# USE_DPMS=false


# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=false

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=true

```

---

### Post by An3Azz on 2006-09-14
Hello, 

I tried the things posted in this tread and like magic, the suspend now works. But I have another problem, my computer does´nt shutdown anymore. It shuts down ubuntu just fine and I get a message similar to "it is now safe to power off your computer" And have to shut it down with the power button.

Any ideas, anyone :o

---

### Post by trubblemaker on 2006-09-25
Suspend works with my mouse messed up. It's having an issue with shared memory.  but in my efforts to work on suspend i used the command
```
 Hibernate -v3 
```
basically hibernate in verbose mode, and it turns out the error message said:
```
Your kernel does not appear to have Software Suspend 2 support compiled in.
Please follow the HOWTO linked from http://www.suspend2.net/ for instructions
on how to compile Software Suspend into your kernel.

```
great... so all this time and false leads and it turns out I never installed the necessary software. Thanks for the help. Ya'll wierd thing is that with my splash screen turned off at boot it says
"Clearing suspend2 Signature."  
Shouldn't that mean that I have suspend2 in my kernel? anyone know how to find out if Ubuntu has that included in the kernel?

---

### Post by cfischer on 2006-09-25
Hi -

In tracking down my problem with my dell inspiron 5150, these links offered me some insight. 

> **nanotube said:**
> by the way, for those of you still having problems, here is an informative link about suspend and video:
[http://www.kernel.org/git/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;hb=HEAD;f=Documentation/power/video.txt](http://www.kernel.org/git/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;hb=HEAD;f=Documentation/power/video.txt)

and here is another potentially useful link:
[http://cvs.gnome.org/viewcvs/*checkout*/gnome-power-manager/docs/Tjfaq.html](http://cvs.gnome.org/viewcvs/*checkout*/gnome-power-manager/docs/Tjfaq.html)

I had both suspend and hibernate working this summer on my dapper installation. Everything was great until an upgrade of xorg, I think - or maybe (probably) gnome-power-manager. Anyway, I think the problem is with the nvidia driver. The first link says this:
> 
 60 (6) other radeon systems, where vbetool is enough to bring system back
61 to life. It needs text console to be working. Do vbetool vbestate
62 save > /tmp/delme; echo 3 > /proc/acpi/sleep; vbetool post; vbetool
63 vbestate restore < /tmp/delme; setfont <whatever>, and your video
64 should work.
But I don't know where to put it. Can anyone help?

Thanks!
Charlotte

---

### Post by trubblemaker on 2006-10-25
Update. After messing with  aiglx, i decided to go for a clean install. (/home is on a different partition so it wasn't a data loss issue), and now hibernate works.

My mouse still fails to work after suspend so I think I'm good to bug report it if it's not already filed.  I'll update with link to bug after it's filed.

**FYI hibernating after suspend has broken my mouse fixes the mouse!**

---

### Post by frankob on 2008-01-10
Unfortunately, all this stuff doesn't work on my HP Compaq nx 6125... :-(

But, my computer fails at shut down, not at resume, both when suspending and hibernating. I use fglrx driver, too.

---

### Post by trubblemaker on 2008-01-12
If you laptop fails at shutdown it might be because your swap file isn't being properly detected/got into an invalid state.

```
free -m
``` would tell you if your swap is being detected or not.

---

