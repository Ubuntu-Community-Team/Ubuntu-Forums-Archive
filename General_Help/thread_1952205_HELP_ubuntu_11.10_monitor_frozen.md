---
title: "HELP ubuntu 11.10 monitor frozen"
date: 2012-04-03
forum: General Help
---

### Post by patw on 2012-04-03
So I had everything working great on ubuntu 11.10 w/ATI Radeon 6570 Hdmi to an ASUS VW246H 1920X1080 LCD monitor.  Then I tried adding 2nd acer X221W(1680X1050 max) monitor to the DVI port.
I ran into issues without being able to display continuous multi (non-mirror mode) and followed advice here...
[http://askubuntu.com/questions/71457/how-can-i-set-up-dual-monitor-display-with-ati-driver](http://askubuntu.com/questions/71457/how-can-i-set-up-dual-monitor-display-with-ati-driver)

I toyed around with increasing virtual memory in /etc/X11/xorg.conf
and modifying gksudo amdccle

I then kept trying to adjust the independent monitor settings on the ubuntu display configure window and reset the 1st to something like 1600X1280. Both screens shutdown.

I had to hard reboot into bizarre screen, like it's missing 1/2 display. Only one monitor works. Removed Acer DVI connection on card. I can't even get to dual-boot back to win; it just goes right to my quasi ubuntu screen ; allows login and can barely type anything , with screen trailing all over the place.

HELP!

edit: 
whew got one working again (Acer).
Acer X221W (1680X1050)
ASUS VW246H (1280X1080)

Here is /etc/X11/xorg.conf file:Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "0-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "1680 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP3"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP2" "0-DFP2"
    Option        "Monitor-DFP3" "0-DFP3"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Default Video Device"
    DefaultDepth     24
    SubSection "Display"
        Virtual   3360 1680
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3360 1680
        Depth     24
    EndSubSection
EndSection


In Display setup,
I try 1680X1050 on Acer
and 1900X1080 on ASUS
and it just shuts off the ASUS 

I can mirror with a very low res, but can't get both at continous multi display and max.
Any thoughts are greatly appreciated.

edit 2:
still complaining about virtual size, but I'm forcing to desired size:
I'm also getting this annoying, AMD unsupported hardware icon on the bottom right.
[IMG]http://i43.tinypic.com/wtmjk.png[/IMG]

---

### Post by patw on 2012-04-03
I was able to switch monitors, so that both are 1920X1080 and went back to AMD catalyst settings and re-applied. Appears to work ok. Maybe the issue was with mixing 1920X1080 and 1600X1050 as the 
vertical dimensions are completely different (but I'd think it could somehow adjust).

I still can't get rid of the AMD Unsupported hardware Icon on bottom right though.:confused:

---

### Post by patw on 2012-04-04
Crimeney, I followed some thread on commands to reinstall drivers and now ubuntu starts with crash failures everywhere and black screen of death.
ex 
Stopping automatic crash report generation [fail]
etc etc..

At least the win7 boot still works.
Can anyone guide me back to a working ubuntu 11.10 dual boot 
plextor 128G SSD S3
HP HPE Win7
i7 2600
Ubuntu 11.1 64bit AMD


This is just driving me nuts.
I had finally installed most of my programs and thought I was solid until the multi display issues.
----
some of the errors ..
1st it just hangs on black screen of nothing for a while..
after repeatedly hitting power on/off

acpid exiting 
checking for running unattended updates
asking all processes to terminate
blah blah
will now unmount

and dies

---------
try recovery mode

I tried recovery mode w/recovery options:
Recovery Menu (limited read-only menu)
2.749320 usb 2-1.2 new low speed USB ddeevice
fsck check all file systems (will exit read-only mode)
root Drop to root shell prompt

I have to shut off power to get out of that menu.

I'm too afraid to hose windows too now and I booted off the live CD ISO...

---

### Post by patw on 2012-04-04
Any help or guidance would be GREATLY appreciated here...tearing more hair out.
P.S. It's 64bit ubuntu 11.10 in case I haven't mentioned prior.
I found other nightmare threads seemingly related to ATI radeon drivers.

I thought this guys post was a godsend and followed everything on the LiveCD.

[http://zeeis.me/ubuntu-error-gave-up-waiting-for-root-device/](http://zeeis.me/ubuntu-error-gave-up-waiting-for-root-device/)

even after upgrades I still have errors though, and upon rebooting same black screen of exit death.

I have attached screens of the major steps and associated complaints.
Apologies if it is too large of a file, I can shrink just let me know (I wanted 300 dpi so someone can read the text).

[IMG]http://i44.tinypic.com/16hvo87.jpg[/IMG]

One other observation by looking at the path failure...  which is:
[http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/)
there is no oneiric sub-directory there (at least that I can see)...
Could that be a bug in the update or clue?


I'm willing to try suggestions, but I'm far from an It guy, so please try to make suggestions a simpleton could just cut and paste
to terminal. Thanks.

---

### Post by patw on 2012-04-04
sorry if I'm not adding evidence properly, but I'm trying to add as much as I can before going off to bed.  I tried to capture as much of the boot sequence (pre crash) as I could by typing what I see on screen and rebooting several times. I also notice the speech error:
when I was running the monitor setups mentioned previously, I somehow enabled this text to speech program (with a whale icon) that ran me through all these steps regarding language and was spitting out the synthesized speech.

anyways.. on to screen capture(s) on boot up death:
these occur upon selecting ubuntu as OS, win still boots fine.


1) dual boot select to solid black screen ... hangs there
sometimes it starts to try to boot into purple ubuntu screen but mostly... I get black hange 

and...
2) press HP power on/off soft boot.
[ok]
1st most common sequence before monitor put to sleep)

acpid : exiting
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
Checking for running unattended-upgrades
*Stopping Bluetooth
*Asking all remaining proceesing to terminate...
*Killing all remaining processes

modem manager 910: 
nm-dispatchter.action: caught signal 15 shutting down...



2nd bootup sequence happened once)

Modem
''Starting bluetooth
*Pulseaudio configured for per-users sessions
                                                                   saned disabled: edit /etc/default/saned
                                                                                                           fsck from util-linux 2.19.1

[3.577976 phy0 -> rt2800pci_mcu_status: Error -MCU request failed no response from hardware
fsck from util-liunx 2.19.1
fsck from util-linux 2.19.1
/ddev/sda3: clean, 185692/10994440 files, 1146756/439240 blocks (check in 3 mounts)
/dev/sda5 has been mounted 30 times without being checked, check forced.
/dev/sda5: 2666/2744320 files (1/2 non contigous) .. blocks [ok]
Skipping profile in /etc/spparmor.d/disable: usr.bin.firefox
*Starting AppArmor profiles
speech-dispatcher diabled; edit /etc/default/speech-dispatcher
Checking for running unatteneded upgrades:
* Starting System V runlevel compaitibility
*Starting CPU interupts balancing demon
*Starting deferred exection scheuler
*Starting regular background processing daemon
*Starting LightDM Display Manager
*Starting ACPI daemon
*Starting anac(h)ronistic cron

All * above display [ok] then screen hangs or goes back to step 2.




Killing all remaining processes
------------------------------------
another tidbit I recall was that when I was trying to get multi-monitor earlier, I think I followed another suggestion to alter X11/xorg.cnfg file 
somewhere I edited so instead of just splash.. i think I added radeon.mode=1
this thread looks related
[http://ubuntuforums.org/showthread.php?t=1862478](http://ubuntuforums.org/showthread.php?t=1862478)
yes, i did alter to radeon.audio=1 (maybe because I couldn't get audio out of hdmi earlier and another thread/forum suggested it)..
I altered to radeon.mode=0 as in the linked suggestion, but no luck.

--------------------
more attempts.
Tried to uninstall ATI catalyst from LIVE CD using mount commands earlier mentioned:
root@ubuntu: /usr/share/ati# sh ./fglrx- uninstall.sh

got 
sh: can't open ./fglrx

BUT-- ati directory is now gone from /usr/share

also, if I look under ubuntu@ubuntu:/etc/X11$ there is no more xorg.conf or xorg.conf.bak (i created earlier today pre catalyst).
Maybe because I'm not still mounting the right drive somehow? or btw. I've been mounting SDA3 all this time but I set that up as root and SDA4 is /home.

---------------------
logged in again via Live CD: I can see the etc/Xll/xorg.conf files again... Tried to...
move old xorg.conf.bak to xorg.conf
so it is original (not ATI filled) xorg.conf.


WOOOHHOOOOOOOOOOOOOOO   Those last 2 steps got me back to booting into ubuntu again!!!!!!!!!!!!!!!!
I'm crossing my fingers and going to bed finally.
Any further thoughts are most appreciated as I'm not 100% out of the woods yet, but it's a good start.
Also, it brings me back to square one on the earlier problem of setting up 2 monitors  (that started it all).
No more ATI logo crap on bottom right either.

---

