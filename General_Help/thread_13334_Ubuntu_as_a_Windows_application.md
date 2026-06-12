---
title: "Ubuntu as a Windows application"
date: 2005-01-30
forum: General Help
---

### Post by chris-uk on 2005-01-30
If you set up 'qemu' [http://www.h7.dion.ne.jp/~qemu-win/](http://www.h7.dion.ne.jp/~qemu-win/) , you can 'boot' Ubuntu under Windows. Warty worked fine, but if you try it with Hoary then you get as far as starting up an Xserver; then the XServer falls over with inability to load device support for Cirrus Alpine.

Poor Windows user is then faced with a command-line login, instead of a Gnome, which is a shame.
Here is what things look like
[IMG]http://home.btconnect.com/chrisandcarolyn/ubuntu-hoary/no-alpine.png[/IMG] 
[IMG]http://home.btconnect.com/chrisandcarolyn/ubuntu-hoary/no-alpine-1.png[/IMG] 
[IMG]http://home.btconnect.com/chrisandcarolyn/ubuntu-hoary/no-alpine-2.png[/IMG] 

So a few things to be done ...
1) Put support for QEMU's virtual graphics adapter into Hoary. (Or enhance QEMU)
2) Figure how to include QEMU on the live CD, so it will 'autorun'. I can do this with Warty (QEMU wants to boot a virtual diskette, I can make a warty one, but the hoary initrd is too large to fit). Ideally this would be done by figuring how to get QEMU to boot the files from an ISO that had been mounted with 'mount -o loop'. Alternatively could be done by setting up a virtual boot disk, rather than a virtual boot diskette. I will have a play, but help is appreciated.

---

### Post by chris-uk on 2005-01-30
Here's the way to launch QEMU on  an autorunning CD with a cooked boot diskette; i.e. you can set up warty so the bit about being able to try Linux without altering your PC's configuration is really true. 

@echo off
REM KNOPPIX on Windows File System
REM Written by Japanese KNOPPIX TEAM 2004.08.17
REM Contact: [email]knoppix@m.aist.go.jp[/email]
REM License GPL

REM check CD-ROM Drinve 
REM This script assume CD-RM has \qemu-0.6.1-windows-2\qemu-knoppix.bat
if EXIST h:\qemu-0.6.1-windows-2\qemu-knoppix.bat set BOOTDRIVE=\\.\h:
if EXIST g:\qemu-0.6.1-windows-2\qemu-knoppix.bat set BOOTDRIVE=\\.\g:
if EXIST f:\qemu-0.6.1-windows-2\qemu-knoppix.bat set BOOTDRIVE=\\.\f:
if EXIST e:\qemu-0.6.1-windows-2\qemu-knoppix.bat set BOOTDRIVE=\\.\e:
if EXIST d:\qemu-0.6.1-windows-2\qemu-knoppix.bat set BOOTDRIVE=\\.\d:
if EXIST c:\qemu-0.6.1-windows-2\qemu-knoppix.bat set BOOTDRIVE=\\.\c:

REM Start qemu on windows.
qemu.exe -L . -m 1024 -boot a -fda %BOOTDRIVE%/qemu-0.6.1-windows-2/boot.img -hda %BOOTDRIVE% -hdachs 14070,16,63 -user-net -enable-audio -localtime


REM If you get iso image of KNOPPIX, please use the following options.
REM     qemu.exe -L . -m 128 -boot d -cdrom knoppix.iso -user-net -enable-audio -localtime
REM                          ^^^^^^^^^^^^^^^^^^^^^^^^^^
exit

---

### Post by chris-uk on 2005-01-30
Ubuntu is very slow to start 'virtual'. I suspect this is to do with the 1000Hz timer tick that 2.6 kernels get built with. 100Hz ticks and 2.4 kernels are faster to start.
Fixable, I hope. 

Maybe speed does not matter. The point is to make Ubuntu accessible to those who for watever reason want to or need to keep running Windows.

***** Recommends Microsoft(tm) Windows(tm) XP Professional. Makes a wonderful NAT-router-firewall !

---

### Post by chris-uk on 2005-01-30
Here's 'virtual warty' autorunning from my hacked CD under an unmodified Windows
[IMG]http://home.btconnect.com/chrisandcarolyn/ubuntu-hoary/virtual-warty.png[/IMG]

---

### Post by BWF89 on 2005-01-30
You have huge resolution.

---

### Post by TravisNewman on 2005-01-30
While I can't advocate the use of Windows, that's pretty sweet! I may venture a guess that quemu and xorg aren't getting along well? I haven't used qemu in a loooong time, so I dunno. That's a nifty idea though. Maybe incorporate that into the menu, so you can install Open Source software, or run a demo of Ubuntu in qemu

---

### Post by chris-uk on 2005-01-31
You don't need an option; just do it. If you know how to make a Windows screensaver, a virtual Ubuntu would be a good one... copy the ISO to disk, a real CD is just for effect.

My LCD panel is 1400x1050. Isn't everyone's ?
I also have a DVD player. I'd like a 4GB 'Live' ISO (because I'm cheap,I can't write the 9GB dual layer ones). I'll think about a BluRay recorder if you can make me a 50GB ISO, though  :D

---

### Post by chris-uk on 2005-02-01
Here is the 'qemu' kit for the above effect (with warty). The idea is, you get a CD; mount it and copy the files; unzip the kit into the root directory; and re-do the final 'mkisofs' to rebuild the CD. 
You can run 'qemu' from disk against an un-hacked Warty if you want; unpack the zipfile and look for '.bat' files in the qemu* directory.
If you need to rebuild with newer versions, or if you need to verify things, the sources of the files are ...
qemu 0.6.1-2 as above
virtual boot diskette from morphix-combined-game 0.4-1, on sourceforge
contents of virtual boot diskette partly from the real CD (vmlinuz and initrd), and some logos from morphix and text from gamesKnoppix 3.7-0.2 . 'mount -o loop' the virtual boot diskette to poke around it.

Sorry about lack of source code. I never saw any ! But I hope the description above would be sufficient for someone to find all they need.
[http://home.btconnect.com/chrisandcarolyn/warty-qemukit.zip](http://home.btconnect.com/chrisandcarolyn/warty-qemukit.zip) 

I may not be able to keep the zip file on line for long; please host elsewhere if you would like to. Plenty of bandwidth, very short on space. The ubuntuforums don't allow appending a zip larger than about 1MB, otherwise I'd copy it here.

---

