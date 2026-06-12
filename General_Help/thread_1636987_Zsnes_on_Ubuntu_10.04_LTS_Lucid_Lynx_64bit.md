---
title: "Zsnes on Ubuntu 10.04 LTS Lucid Lynx 64bit"
date: 2010-12-03
forum: General Help
---

### Post by joelstitch on 2010-12-03
I've been trying to install Zsnes on my computer with Ubuntu 10.04 LTS Lucid Lynx 64bit (AMD64) with no success. I have read plenty of topics on this subject, follow the directions but still doesn't work for me. I don't know if is because of my system or what but I really want to get this to work. I can't install it from the Ubuntu Software Center, I get this message:

> Sorry, 'ZSNES Emulator' is not available for this type of computer (amd64).The last one I tried was on this topic:

[http://ubuntuforums.org/showthread.php?t=588744](http://ubuntuforums.org/showthread.php?t=588744)

and these are the directions given by [B]epsilon72:

[/B]> 1) Download the i386 maverick version of zsnes [here]("http://mirrors.kernel.org/ubuntu/pool/universe/z/zsnes/zsnes_1.510-2.2ubuntu4_i386.deb")
2) If they aren't installed already, install ia32-libs
     Code:
     sudo apt-get install ia32-libs 
3) Install the 32-bit zsnes package:
     Code:
     sudo dpkg -i --force-architecture zsnes_1.510-2.2ubuntu4_i386.deb 
4) Make a symbolic link to the 32-bit libao oss plugin so zsnes will run..
     Code:
     sudo ln -s /usrlib32/ao/plugins-4/liboss.so /usr/lib/ao/plugins-4/lib32oss.so 
5) Run zsnes with:
     Code:
     padsp zsnes -ad oss 
But I keep getting this error on step 3:

> sudo dpkg -i --force-architecture zsnes_1.510-2.2ubuntu4_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 215796 files and directories currently installed.)
Preparing to replace zsnes 1.510-2.2ubuntu4 (using zsnes_1.510-2.2ubuntu4_i386.deb) ...
Unpacking replacement zsnes ...
dpkg: dependency problems prevent configuration of zsnes:
 zsnes depends on libao4 (>= 1.0.0); however:
  Package libao4 is not installed.
dpkg: error processing zsnes (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_CA.utf8.cache...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for menu ...
Processing triggers for python-support ...
Errors were encountered while processing:
 zsnes                      

---

### Post by joelstitch on 2010-12-03
I was able to install it using the installer in this website:

[https://rohieb.wordpress.com/2010/10/06/zsnes-on-amd64-ubuntu/#comment-40](https://rohieb.wordpress.com/2010/10/06/zsnes-on-amd64-ubuntu/#comment-40)

but now if I try to open it it shows the terminal windows for a split second and then it closes immediately. This is what I get when I open it trough the terminal:

> pag@pag-laptop:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Segmentation fault


---

### Post by joelstitch on 2010-12-04
I was able to get it started by using this command ( I got it from [https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/346155):]("https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/346155%29:")

> zsnes -ad sdl

---

### Post by lebigouden on 2011-04-16
> **joelstitch said:**
> I was able to get it started by using this command ( I got it from [https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/346155):]("https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/346155%29:")
Hey Joel,

I also run 10.04 in amd 64, i tried first to install snes9X but the sound was choppy and unbearable. I looked for different solutions in a lot of places, none of it worked. Finally i decided to try zsnes and was able to make it work thanks to the command you found.. 
Thanks to you , i am now playing terragnima with flawless music :)

---

### Post by shandtacklann on 2011-06-16
I have installed snes9x successfully with no tearing or any errors or problems successfully.  I am also new to Ubuntu, and I'm still having trouble with some things, but I have figured out how this program works at least, so I'm going to share what I did to make it work for ya'll  =P

It was actually alot simpler than it looked.  

1) go to Applicatioins>ubuntu Software Center

2) Search in the Upper right hand box, Snes9x  (not zsnes for this tutorial, 9x works just as well as zsnes =D)

3) After it installs, it should automatically be under Applications>Games>snes9x

open it

4)  In snes9x go to Options>preferences

5) In Display (default top option) at the bottom under Hardware Acceleration, switch it to the third option "XVideo use hardware video blitter"

And your good to go.  No tearing, just smooth gaming.  

before step 5 I had it working but it didn't work in Fullscreen and I got alot of tearing. but after changing to xvideo, it worked like a charm!

Also you can change your hotkeys/buttons, turbo buttons etc in the preferences menu's

I hope this helps someone.  =)

---

### Post by kingofspades8 on 2011-07-16
My experience was the same as shandtacklann, the only thing I would add is to make sure to turn on multithreading to improve performance.

Go into Options -> Preferences -> check "Use _ threads for filtering and scaling"

I got best performance when I turned on 8 (which is the max).

---

### Post by fernandoc1 on 2011-07-16
:popcorn:

That worked for me.

I've created a tutorial to help people achieving the same results as I in Ubuntu 11.04 Natty 64 bit:
[https://docs.google.com/document/pub?id=1H_hkPoUXRN8CODj7fOPTgsjOFysib9FNZors83Cqq5g](https://docs.google.com/document/pub?id=1H_hkPoUXRN8CODj7fOPTgsjOFysib9FNZors83Cqq5g)

---

