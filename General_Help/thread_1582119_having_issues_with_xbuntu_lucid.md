---
title: "having issues with xbuntu lucid"
date: 2010-09-26
forum: General Help
---

### Post by niemann999 on 2010-09-26
i started off with xubuntu 9.1  worked amazing i loved it didnt miss windows at all. then i tried to upgrade it to xubuntu lucid or xubuntu 10.4 and now i get this  screen  i sign in typing in gdm when i looked up how to get out of this and this the error i get idk what to do 
**(gdm-binary:969): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.19 is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file
 
** (gdm-binary:1969): WARNING **: Could not acquire name: bailing out
 
if this helps my computer is a junk i wanna get it more up to date eventually when i get extra money but this what it has that i know of
 
intel pentium 3 processor
nvidia geforce fx 5200
352mb of RAM
 
i dont get why it says its not allowed to own the service when xubuntu 9.1 worked great and i updated it from update manager plz help i really dont wanna reformat my computer back to xubuntu 9.1

---

### Post by mrhhug on 2010-09-26
whoa whoa whoa, lets all calm down here and try to fix your problem? 

can yu be more specific? you seem to be on a rant right now, please repost (in this same thread) how you feel you go to this point... lets go from there

---

### Post by niemann999 on 2010-09-26
i just wanna get this fixed i dont what to do i dont get on how xbuntu 9.1 worked great no problems but soon i update to lucid i cant even get a display i just get a command line and stuck on here

---

### Post by niemann999 on 2010-09-26
bump

---

### Post by niemann999 on 2010-09-26
To clear up idk if you u can full understand what's wrong I when I start my computer after it loads up all I get is a command line login I login and and tells me my last login in blah blah I type gdm I get that error above

But when I type startx it does it thing but I still on command line no graphic nothing and. It saying this

Current version of pixman: 0.16.4 
  Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure you have the lastest version
Markers: (--) probed, (**) from config file, (==) default setting, (ww)warning, (ee) error, (ni) not implemented, (??) Unknown.
(==)log file: "/var/log/Xorg.0.log", Time: Sun Sep 26 02:16:38 2010
(==) using config file:"/etc/X11/xorg.conf"
(==) using config directory: "/usr/lib/X11/xorg.conf .d"
FATAL: module nvidia not found
(EE) nvidia: failed to load the nvidia kernel module. Please check your
(EE) nvidia:   system's kernel log for additional error messages.
(EE) failed to load mofule "nvidia" (module-specific error,0)
(EE) no drivers available.

Fatal server error:
No screens found

Please consult the the X.org Foundation support at [http://wiki.x.org](http://wiki.x.org) for help
Please also check log file at "/var/log/Xorg.0.log" for additional info

DdxSigGiveUp: closinf log
Giving up
Xinit: no such file or directory (errno 2): unable to connect to X server
Xinit: no such process (errno 3): server error. 

This what I can see comes up idk what else I can do to give more info

---

### Post by mrhhug on 2010-09-26
how olds your RAM and hdd? can you run some tests on them?

---

### Post by niemann999 on 2010-09-26
Idk what u mean on how to test them but the hdd and ram not sure how old they are but have to be atleast 7 yrs old maybe younger

---

### Post by mrhhug on 2010-09-26
im thinking you have failing hardware, when you insert an ubuntu live CD there is an option for memtest86+, run that for a few hours, see if you get any red errors, red = bad

your hard drive can be tested by downloading and burning - then booting into a "hard drive fitness test" [http://www.hitachigst.com/support/downloads/#DFT](http://www.hitachigst.com/support/downloads/#DFT)

if both your RAM and hdd pass these tests, there is something else wrong, if they either fail, you have flaky hardware. post results either way

---

### Post by clhsharky on 2010-09-26
niemann999

> (EE) no drivers available.
The nvidia driver not installed is problem or config.

Up grading Ubuntu from one release to another, the 3rd party drivers and ppa's get disabled.

I disable or uninstall proprietary drivers and get the Open Source driver or vesa driver working before upgrading.That way you will have a working desktop after upgrade.(Not necessary with fresh install) Then install the proprietary drivers.

Ubuntu doesn't use xorg.conf file for OSS drivers anymore but ATI/Nvidia proprietary drivers does.
Look at /etc/X11/xorg.conf , if you have xorg.conf file remove it
```
sudo rm -f /etc/X11/xorg.conf*
```
restart

Hopefully desktop will be able to start in safe graphics mode or OSS driver. Then install nvidia proprietary driver. The xorg.conf file will then be created, configured, installed for nvidia driver.

Drivers can be installed from command line.  I don't have info on correct driver or code at this time.

Search this forum or wait for someone able to help with command line.

Sharky

---

### Post by niemann999 on 2010-09-27
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by niemann999 on 2010-09-27
Okay right now I'm doing the memory check see how that goes ill post the results when it comes up idk how I can test my hard drive from command line and if memory test passes ill try to remove that file and see if that will work.

---

### Post by mrhhug on 2010-09-27
could you please post the output of ```
sudo lshw -c display
```?

---

### Post by niemann999 on 2010-09-27
I will after I get done with the memory test I'm at 30 mins and no errors and I can't do the hard drive test this the only computer I got I'm using the forums through my blackberry

---

### Post by niemann999 on 2010-09-27
It passed the memory test I had a friend of mine burn me a disc to install lucid I installed it this morning and it works. I'm letting it install its updates. But it loaded up no problem at all but its asking for updates to install a nvidia proprietary driver do I install it and see what happens or just don't install it

update after the updates are installed it is working great im having no issues at all guess it was the nvidia driver that was causing it to not work thank for all that try to help.

---

### Post by mrhhug on 2010-09-27
you can install the proprietary drivers if you need them, if you juse using this box as a server then i wouldn't worry about it 

[http://www.desktoplinux.com/news/NS7895189911.html](http://www.desktoplinux.com/news/NS7895189911.html)

---

