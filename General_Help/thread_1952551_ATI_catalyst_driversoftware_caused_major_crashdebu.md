---
title: "ATI catalyst driver/software caused major crash/debug issue"
date: 2012-04-04
forum: General Help
---

### Post by patw on 2012-04-04
Can't believe there was not a single reply to this thread
[http://ubuntuforums.org/showthread.php?t=1952205](http://ubuntuforums.org/showthread.php?t=1952205)

I spent all night debugging this nightmare, which turned out (IMO) to be an incompatibility issue.
with ATI catalyst driver/software for ATI radeon XXXX and ubuntu 11.10 64bit -- AKA amdccle.  My comments to those who run into this.

1) Don't install amdccle as pointed out on many threads, because you want dual monitor working right.
Because it will cause AMD weathermark unsupported hardware logo on screen for starters.
2) Having catalyst driver change the xorg.conf file can cause horrendous debugging nightmares with no more booting into OS and multiple text filled black screen of death.
3) See above for my nightmare journal.

For those who have been through it, please let me know if you tried ATI catalyst newest release (12?) 
and if it solved the watermark. I might try this route to get the dual monitors again ... gulp.
With the default driver xorg.conf menu, I'm stuck with no selection for 1920X1080, no monitor detect, and subpar resolution with a stretched screen at 1280X1024 max.


Also, since I didn't seem to get any help in my darkest hour and posting detailed text and screenshots, maybe someone can give
me some advice on whether my captions are not good or body too verbose or something? I really could have used some ubuntu guru help on this and
figured this is the best forum to do so.

---

### Post by QIII on 2012-04-04
I have used AMD/ATI grahics for years without problems with multiple monitors.  Some use NVIDIA without problems.  Users of each come here from time to time with problems.

In fact, ATI's Eyefinity is now supported in the Linux driver I believe.

Exactly what model of card are you using?

My first question with AMD/ATI is always this:

Did you do

```
sudo aticonfig --initial
```

In the terminal after installing the driver and BEFORE rebooting?

That will create a new xorg.conf, which is actually necessary.

---

### Post by patw on 2012-04-04
> **QIII said:**
> I have used AMD/ATI grahics for years without problems with multiple monitors.  Some use NVIDIA without problems.  Users of each come here from time to time with problems.

In fact, ATI's Eyefinity is now supported in the Linux driver I believe.

Exactly what model of card are you using?

My first question with AMD/ATI is always this:

Did you do

```
sudo aticonfig --initial
```In the terminal after installing the driver and BEFORE rebooting?


Thanks for the reply! Although I've seen several threads now with similar issues.
I don't recall doing that..although I keep pushing to fix dual-monitor detect/setup I got back the AMD unsupported hardware logo in bottom right corner again.

Here are the steps I've been logging:

1)installed fglrx

sudo apt-get install fglrx-updates
*result: AMD unsupported hardware logo bottom right of screen(s) &
*issues with not supporting full space of
*multi-monitors

2) fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7500 Series
OpenGL version string: 4.1.11251 Compatibility Profile Context

3) Identify card type
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Device 675d


Should I try your command line now? Unfortunately I rebooted just after fglrx update.  Or any other suggestions to get out of this now recurring nightmare?  Far as I know (beyond the specs identified above) it's an AMD radeon HD 7570 driving 
DVI and HDMI ideally.

If I get rid of catalyst and or fglrx and go back to old default drivers, it doesn't detect monitor and I get sub-par resolution options. If I install again (as I did) the
fglrx stuff, I get all these other headaches.
P.S. It does work in mirror mode w/reduced resolution to dvi port now, but continuous multi-mode has issues with fitting both into display allocation...
I'm going back 180 degrees in circles to modifying xorg.conf file again for this.  Trying to avoid all that.  My folders are also looking like they defaulted to some
ugly yellow archaic design now as well.

---

### Post by QIII on 2012-04-04
You should be able to run the command now.

However, you will still need to use Catalyst in admin mode to configure your monitors.  Unless you know what you are doing, I would recommend against editing your xorg.conf manually.

It is tempting sometimes to find "several" threads and jump to the conclusion that a problem is universal.  The problem with that is known as a referral bias.  Only people with problems create threads asking for help with problems.  People don't often start threads asking for help because things are working.

Edit, Note:  the 7xxx series may require the 12.x Linux driver, which is Beta.  I use it on my Precise machine and it works flawlessly.

---

### Post by patw on 2012-04-04
> **QIII said:**
> You should be able to run the command now.

However, you will still need to use Catalyst in admin mode to configure your monitors.  Unless you know what you are doing, I would recommend against editing your xorg.conf manually.

It is tempting sometimes to find "several" threads and jump to the conclusion that a problem is universal.  The problem with that is known as a referral bias.  Only people with problems create threads asking for help with problems.  People don't often start threads asking for help because things are working.

Ill run it. Should I reinstall ATI catalyst from software center? Any ideas on how to get rid of AMD Unsupported Hardware logo? (Last time i got rid of it by reinstalling and removing all ATI stuff).
The xorg.conf was altered by installing ATI catalyst. The only thing I modified before even installing that 
was to try to size up the virtual display space per the error not enough room command (after reading several other threads on that).

I can capture anything else you'd want to guide me. If you look back I was pleading for help all yesterday (on 1st link) and no one was around ... so yeah, I ended up following threads here and there to try to patch something I'm definitely not familiar with (but did find several other notable compatibility complaints... mostly unresolved).

That 12.x driver was what I was also referring to from another thread. Any ideas on how to do a clean install and clean up the old one in one step?

----------------------------------------------
results from your suggestion so far.
 sudo aticonfig --initial

aticonfig: No supported adapters detected

---------------------------------------------------
found this driver and downloaded to /home/downloads.
I'll wait to get instructions on how to properly run it.

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)
amd-driver-installer-12-3-x86.x86_64.run

---

### Post by QIII on 2012-04-04
I would attempt to start clean.  If you have it installed from the software center, uninstall it.  If you installed it from AMD/ATI's website, uninstall it following their instructions.  (There will be an ininstall.sh somewhere probably). If you installed it from both and have something cobbled together, you may need to do both things.

I'm going to check to see if the latest driver in Oneiric (if that is what you are using) will drive the 7xxx series.  I can't guarantee that will happen right away because my regression testing is nearly done and I'm about done choking down a sandwich.

---

### Post by patw on 2012-04-04
> **QIII said:**
> I would attempt to start clean.  If you have it installed from the software center, uninstall it.  If you installed it from AMD/ATI's website, uninstall it following their instructions.  (There will be an ininstall.sh somewhere probably). If you installed it from both and have something cobbled together, you may need to do both things.

I'm going to check to see if the latest driver in Oneiric (if that is what you are using) will drive the 7xxx series.  I can't guarantee that will happen right away because my regression testing is nearly done and I'm about done choking down a sandwich.


This was exactly how I reinstalled after de-installing:
1)installed fglrx

sudo apt-get install fglrx-updates
*result: AMD unsupported hardware logo bottom right of screen(s) &
*issues with not supporting full space of
*multi-monitors

yesterday I was able to uninstall with sudo sh ./fglrx -uninstall.sh
but maybe I should use ubuntu rec 
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

ran from terminal -- results below
----------------------------------------------------------------------------------------
sudo apt-get remove --purge xorg-driver-fglrx fglrx*


Reading package lists... Done

Building dependency tree       
Reading state information... Done
Virtual packages like 'xorg-driver-fglrx' can't be removed
Note, selecting 'fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx*'
Note, selecting 'fglrx-driver' for regex 'fglrx*'
Note, selecting 'fglrx-kernel-source' for regex 'fglrx*'
Note, selecting 'fglrx-modaliases' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-updates' for regex 'fglrx*'
Note, selecting 'fglrx-control' for regex 'fglrx*'
Note, selecting 'fglrx-control-qt2' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle-updates' for regex 'fglrx*'
Note, selecting 'fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-driver-dev' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-updates-dev' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-glx' for regex 'fglrx*'
Package fglrx-amdcccle is not installed, so not removed
Package fglrx-dev is not installed, so not removed
Package fglrx-updates-dev is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libc6-i386 lib32gcc1 dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  fglrx* fglrx-amdcccle-updates* fglrx-updates*
0 upgraded, 0 newly installed, 3 to remove and 2 not upgraded.
After this operation, 182 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 170826 files and directories currently installed.)
Removing fglrx ...
Purging configuration files for fglrx ...
update-initramfs: deferring update (trigger activated)
update-rc.d: /etc/init.d/atieventsd exists during rc.d purge (use -f to force)
dpkg: error processing fglrx (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing fglrx-amdcccle-updates ...
Removing fglrx-updates ...
Removing all DKMS Modules
Done.
update-alternatives: warning: alternative /usr/lib/fglrx/ld.so.conf (part of link group x86_64-linux-gnu_gl_conf) doesn't exist. Removing from list of alternatives.
update-alternatives: warning: alternative /usr/lib/pxpress/ld.so.conf (part of link group x86_64-linux-gnu_gl_conf) doesn't exist. Removing from list of alternatives.
update-alternatives: warning: /etc/alternatives/x86_64-linux-gnu_gl_conf is dangling, it will be updated with best choice.
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: warning: alternative /usr/lib/fglrx/alt_ld.so.conf (part of link group i386-linux-gnu_gl_conf) doesn't exist. Removing from list of alternatives.
update-alternatives: warning: alternative /usr/lib/pxpress/alt_ld.so.conf (part of link group i386-linux-gnu_gl_conf) doesn't exist. Removing from list of alternatives.
update-alternatives: warning: /etc/alternatives/i386-linux-gnu_gl_conf is dangling, it will be updated with best choice.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-initramfs: deferring update (trigger activated)
Purging configuration files for fglrx-updates ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-17-generic
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

----------------------------------------------------------------------
well, I seemingly couldn't wait ... so...results of above suggestion from ubuntu wiki:
I will now reboot.

does that seem reasonable?




Thanks again for your help!  If I was there I'd buy you a lunch.... 

Unfortunately, my keys are also now screwed up in software center ... 'requires installation from untrusted package.'  Geez, I only got dual-boot up and running on brand new computer less than a week ago. I'll deal with that next I suppose.

-------------------------

---

### Post by QIII on 2012-04-04
According to a Phoronix review conducted on an Ubuntu machine, the watermark and "no supported adapters" issues persist even with the 12.2 driver.

Hence:  continued watermark and limited Catalyst setup.

I've generally supported AMD/ATI.  Buggering the pooch like this may make me reconsider.

I'll see what I can find on screen resolution.

Uninstall the third party drivers.  But AMD/ATI also buggered the neighbor's pooch by not releasing the open source bits necessary for the open source developers!

Edit:  Just read your previous post.  No.  Not reasonable.  I'm wondering if you had one installed from repos and one and installed from web leaving bits and pieces in odd places.

---

### Post by patw on 2012-04-04
Well at least on reboot, the AMD watermark crap is gone.
But folders still have that ugly beige archaic look.

I followed the other ubuntu wiki suggestion...
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
... to look for remaining ATI traces using :
dpkg -l '*fglrx*'
locate fglrx

results:
-----------------------------------------
$ locate fglrx

/usr/share/app-install/desktop/fglrx-driver.desktop
/usr/share/apport/package-hooks/source_fglrx-installer.py
/usr/share/jockey/handlers/fglrx.py



$ dpkg -l '*fglrx*'

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
pc  fglrx          2:8.881-0ubunt Video driver for the AMD graphics accelerato
un  fglrx-amdcccle <none>         (no description available)
un  fglrx-amdcccle <none>         (no description available)
un  fglrx-control  <none>         (no description available)
un  fglrx-control- <none>         (no description available)
un  fglrx-driver   <none>         (no description available)
un  fglrx-kernel-s <none>         (no description available)
un  fglrx-modalias <none>         (no description available)
un  fglrx-updates  <none>         (no description available)
un  xfree86-driver <none>         (no description available)
un  xorg-driver-fg <none>         (no description available)

-----------------
even though system display tools cannot detect monitors or put in multi mode, they still look decent in 1920X1080 mirror mode.
Too bad I guess I'll be able to only code in one window or go back to windows. Not sure of the lesser of two evils.

---

### Post by QIII on 2012-04-04
Sorry this has been such a PITA.

For a member of the Linux Foundation, this is entirely unacceptable.

---

### Post by patw on 2012-04-04
> **QIII said:**
> Sorry this has been such a PITA.

For a member of the Linux Foundation, this is entirely unacceptable.

Thanks for your support. For the record I'm a virtual IT idiot.  I've only used ubuntu on an older machine
(ver 10, I think) without fancy graphics and wrote over the XP that was on it. I loved it from day one (about 2 yrs now). I never had to debug any OS issues there and barely understand terminal commands.

But I was so excited to setup a dual boot win7/ubuntu11.1 on a brand new HPE i7 quad core w/ a secondary SSD S3 so i could start running parallel apps and stuff not supported on windows.  
Unfortunately, a week in and I have been plagued by debug nightmares left and right (including having to solve non booting ubuntu for hours with no help on prior thread).

Glad to know I'm not creating this fubar condition entirely on my own.
P.S. I tend to get impatient about waiting around and move forward by gathering bits on other threads (as you pointed out), but I'm going to wait on any further instructions to clear up this mess for a few hours (or until I see further suggestions). I don't want to do any more damage at this point.

---

### Post by QIII on 2012-04-04
What I meant, by the way, is that AMD is a member of the Linux foundation.

---

