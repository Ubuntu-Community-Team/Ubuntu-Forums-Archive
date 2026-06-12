---
title: "Natty &amp; FGLRX Not Working"
date: 2011-04-29
forum: General Help
---

### Post by cottfcfan on 2011-04-29
Looking at other threads i'm not the only one with this problem.
after installing the proprietary driver, graphics are slow & 3D appears not to be working.
fglrxinfo gives this:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 3.3.10666 Compatibility Profile Context

No mention of "glx" or "direct rendering" as in previous versions.

sudo aticonfig --initial -f   gives this:

Uninitialised file found, configuring.
Fail to link to fglrx-libglx.so, please check whether driver is installed correctly
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx

Apparently driver not installed correctly.

Also there's no fglrx-modialases (or something) in synaptic thats been needed before.

Any help would be much appreciated.

---

### Post by cottfcfan on 2011-04-29
So i reverted back to the OSS Drivers. Very slow & laggy, I then added the xorg-edgers ppa to my sources, still no improvement.
Whether I use propriety or open source, my desktop in Natty is awful.
 Help i'm screwed!!

ps. suppose i could go back to Lucid, all works well there.

---

### Post by ArcherB on 2011-04-30
> **cottfcfan said:**
> Looking at other threads i'm not the only one with this problem.
after installing the proprietary driver, graphics are slow & 3D appears not to be working.
fglrxinfo gives this:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 3.3.10666 Compatibility Profile Context

No mention of "glx" or "direct rendering" as in previous versions.

sudo aticonfig --initial -f   gives this:

Uninitialised file found, configuring.
Fail to link to fglrx-libglx.so, please check whether driver is installed correctly
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx

Apparently driver not installed correctly.

Also there's no fglrx-modialases (or something) in synaptic thats been needed before.

Any help would be much appreciated.

I had the same problem and here is how I fixed it:

First, boot into fall back mode and have Ubuntu reset your X config to default.
Once this is done, tell system to run X one time in safe mode (or whatever it's called)
Make sure you click the old gnome mode
Once in the old gnome, click Administrative and restricted drivers.  Remove the fglrx driver.
Open your trusty browser and go to [www.amd.com/ati](www.amd.com/ati) and go the drivers section.
Download the drivers for your version of linux.
Open a terminal and navigate to you Downloads folder.
Type "sudo su", press enter and type in your password.
Type chmod 777 ati... (whatever driver you downloaded.)
Type ./ati... (whatever driver again) and let it run, answering Y or 1 to all questions.
Reboot, and you should be good to go.

Yes, I am aware that my notes are bit... "fuzzy", but it's late, I'm tired, and if someone else wants to go into more detail, please, be my guest and thank you.

---

### Post by cottfcfan on 2011-04-30
thanx ArcherB,
That actually worked & got rid of the error message.
Performance however is abysmal. When I run glxgears or gtkperf, the graphics just stick, and opening any application causes the window to distort and wobble. (and no i dont have wobbly windows enabled).
Ive just drawn the conclusion that Natty & fglrx aren't compatible yet.
 Thanks for your help anyway.

---

### Post by 4x31 on 2011-05-04
Hi, 
I got same error when trying to re-enable dual monitors under natty 
> 
Fail to link to fglrx-libglx.so, please check whether driver is installed correctly

So I assume my drivers didn't install correctly, Natty isn't supported yet by ATI so which version did you use?
I tried to build and install ubuntu-source one but got

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.38-8-generic; make sure that the version is being
correctly set by --iscurrentdistro

I used this installer ati-driver-installer-9-3-x86.x86_64

any idea if an open source driver is a good alternative?

---

### Post by Lupajz on 2011-05-04
> **4x31 said:**
> Hi, 
I got same error when trying to re-enable dual monitors under natty 

So I assume my drivers didn't install correctly, Natty isn't supported yet by ATI so which version did you use?
I tried to build and install ubuntu-source one but got

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.38-8-generic; make sure that the version is being
correctly set by --iscurrentdistro

I used this installer ati-driver-installer-9-3-x86.x86_64

any idea if an open source driver is a good alternative?
Have you tried updating your fglrx to 11.4 ?

---

### Post by cottfcfan on 2011-05-04
Hi,
I'm using the latest 11.4 fglrx.
If you install according to the release notes on ATIs site, it installs correctly, but performance for me is still poor.
I think the problem may be compiz though.
If I turn compiz off & use metacity & enable metacity compositing, all works well, just no effects, but I can live with that.

---

### Post by Hanmac on 2011-05-04
i used the latest fglrx package and this are my found bugs:
vlc, tiled or other grafic things like games are draw not on the window, there are draw above all other things, even other windows over the drawing one

in windows games run with wine, there are run faster than open driver, but with many errors, as sample the characters are not renderd or renderd in wrong color

---

### Post by blimbo on 2011-05-04
Similar problems for me too.. installed fglrx with ATI's 11-4 driver and the module builds/loads ok but performance is terrible (it was ok with 10.10). fglrxinfo gives me this:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6450
OpenGL version string: 4.1.10666 Compatibility Profile Context

Should it mention of "glx" or "direct rendering"? Or do I need to configure my xorg.conf futher (it is rather minimal after an aticonfig --inital)

Edit: Just tried video and it barely works in VLC :-(

---

### Post by blimbo on 2011-05-04
I just found a solution that semi-fixes things for me. In 10.10 I had turned 'tear free' on and set 'wait for vertical refresh' to 'quality' (both these made things very nice) in Catalyst control centre. I guess the same settings for picked up on upgrade to 11.04. Anyway, I turned 'tear free' off and set vertical refresh' to 'performance' and my frame rate has jumped from about 60fps to 900fps :-) Video is working again too.

---

### Post by Hanmac on 2011-05-04
if i activate "tear free" (in my german it means "rissfrei")
video is totaly BROKEN and nothing is shown, only a black box

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3300 Graphics
OpenGL version string: 3.3.10665 Compatibility Profile Context

---

### Post by 4x31 on 2011-05-05
> **Lupajz said:**
> Have you tried updating your fglrx to 11.4 ?
Well, just now I''ve followed manual driver install from [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx)
but ended up with the same driver I had before
Package: fglrx                           
New: yes
State: installed
Automatically installed: no
Version: 2:8.841-0ubuntu1

So still no dual monitors (

Actually I've just tried running .run file and let it install fglrx driver , and it fixed the missing library problem... I'm going to try again

---

### Post by Lupajz on 2011-05-05
> **4x31 said:**
> Well, just now I''ve followed manual driver install from [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx)
but ended up with the same driver I had before
Package: fglrx                           
New: yes
State: installed
Automatically installed: no
Version: 2:8.841-0ubuntu1

So still no dual monitors (

Actually I've just tried running .run file and let it install fglrx driver , and it fixed the missing library problem... I'm going to try again
I read that fglrx was released too soon to be compatible with Natty :P So maybe running open-source driver will do the job, but I couldn't handle so laggy OS so I'm back to 10.10

See : [http://ubuntuforums.org/showpost.php?p=10766687&postcount=9](http://ubuntuforums.org/showpost.php?p=10766687&postcount=9)

---

### Post by sikander3786 on 2011-05-05
Did you try this simple fix with Proprietary Drivers.

[http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html)

---

### Post by Hanmac on 2011-05-05
thanks sikander3786 this solv the vlc "bug" but the bug of wine games like Torchlight are not gone

hm emerald does not work :/
and with akivated compiz the title from the windows does not change, but it change in the panel below

---

### Post by hardyn on 2011-05-07
PERFECT, thank you.


> **sikander3786 said:**
> Did you try this simple fix with Proprietary Drivers.

[http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html)

---

### Post by 4x31 on 2011-05-08
> **Lupajz said:**
> I read that fglrx was released too soon to be compatible with Natty :P So maybe running open-source driver will do the job, but I couldn't handle so laggy OS so I'm back to 10.10

See : [http://ubuntuforums.org/showpost.php?p=10766687&postcount=9](http://ubuntuforums.org/showpost.php?p=10766687&postcount=9)

Actually after a bit of tweaking around, I managed to get it working, using "Montors" and aticonfig didn't work for me so I used "ATI control center" and that go both monitors finally running! :)

---

### Post by cottfcfan on 2011-05-09
The link that sikander3786 has pointed to actually works quite well.
However graphics performance in Natty is nowhere near as good as in Lucid imo. Still time & updates may improve things.

---

### Post by Lupajz on 2011-05-10
Okay, but lets get back to laggs :/ Have any1 of you guys tried to install latest ATI Catalys 11.5 ?

---

### Post by Oleq on 2011-05-10
> **Lupajz said:**
> Okay, but lets get back to laggs :/ Have any1 of you guys tried to install latest ATI Catalys 11.5 ?
Yes I've already installed it. The problem still occurs.

---

### Post by Niels_D on 2011-05-14
I also have the same problems.
I updated from 10.10 to 11.04 and got graphics problems, especially with Compiz.

Now I completely re-installed my machine to 11.04, but the same problems are there.

When I switch to Compiz, the PC crashes with a bug report window. 
It happens every time I try so, so it is reproducable.
Can anyone confirm that this is related to the problems as described in this topic?

When I try aticonfig --initial, I also get the "fail to link to fglrx-libglx.so" error.

---

### Post by cottfcfan on 2011-05-14
This is the same problem, it appears that fglrx & compiz don't sit too well together at the moment.
I also got the same error message when running aticonfig --initial.
The way around that is to download the driver to your desktop, then:
```
cd Desktop
```
```
sudo su
```
```
sh ./ati-driver-installer*
```
Answer all the questions, then:
```
aticonfig --initial -f
```
Seems to install properly after that, although doesn't resolve the compiz issue.

---

### Post by menglim on 2011-05-19
I still have the problem of fglrx not installing.

I look at the ati control center and everything looks ok except for dual monitors.

when i do and aticonfig on the terminal it says "aticonfig:No supported adapters detected"

I also tried the .sh file ver 11.5 and still the same.

Is there a way to reinstall everything and maybe delete files or drivers and start all over? not sure if there are any residual setup that's causing the problem

---

### Post by nishant.singh28 on 2011-05-19
Why can't ATI make one decent driver??? Just ONE?
I can't enable sync to vblank...that makes the normal desktop lag horribly, almost like a frame a second. And with the thing disabled, videos tear badly.
Disabling the fglrx is not an option for me, the default drivers heat up the GPU, and the battery life goes down drastically.
I don't want to disable compiz. I use the desktop wall very frequently.
I've been using my notebook since Jaunty, and I have never ever had a time when the ATI driver has not been problematic. Too bad I am stuck with this machine for another year. But is there a solution in sight just yet, or will we have to bear with the rubbish ATI driver?

---

### Post by fianor on 2011-05-24
> **sikander3786 said:**
> Did you try this simple fix with Proprietary Drivers.

[http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html)

Thanks a lot! This fix worked for me, I'm using ATI Radeon 6950 on Natty, was wondering why video was choppy despite using proprietary drivers.

---

### Post by lakerssuperman on 2011-05-27
I don't think it's the drivers.  I have a system running a heavily updated 10.04.2 install with the Kernel Mainline PPA and the latest 11.5 AMD/ATI drivers and it is totally, perfectly smooth.  My 11.04 install with the same Kernel and drivers is noticeably laggy on several systems.  In addition I have a computer running a Core i7 and an NVIDIA GTX 560 and the drivers for that are currently terrible as well.  The system becomes wildly unstable and sometimes hard locks.  That seems to be an NVIDIA driver issue, but the on the ATI/AMD side it seems to have something to do with Compiz and Unity.

In my opinion, and I have been an avid Ubuntu user for pretty much it's entire lifetime, 11.04 is a total and unmitigated disaster.  The Unity desktop is nice, but can't be run on the two dominant video hardware vendors without serious issues.  VDPAU makes the whole system lag and VAAPI is totally broken.  Unfortunately I can't download on my new mobile computer, the Asus 1215b, running the new Fusion APU.

I really hope 11.10 turns out to be a Windows 7 release compared to the Vista that is 11.04.

---

### Post by Hanmac on 2011-05-27
the main problem is tat in 11.04 the linux image has a new API for drivers, and the drivers does not work well with it .. i think


vaapi is not totaly broken or what do you mean?

---

### Post by lakerssuperman on 2011-05-27
If you use the 1.0.8 VAAPI files in the repo video will play but the CPU usage is very high and the video is choppy, regardless if it is high def or not, and will sometimes crash the player.  If I try using 1.0.12 from one of the XBMC ppa's it complete crashes any player that I use it with or will only display audio, in the case of Gnome Mplayer.  In contrast, the version that ships with 10.04 works fine.  CPU usage is extremely low and everything is fluid, even on modest hardware.

---

### Post by rootfairy on 2011-07-13
true that problem with 11.6. i can use ubuntu 11.04 built-in proprietary drivers though i get that fail to link to fglrx-libglx.so error, too.

when i start in ubuntu [unity interface] i have a different vsync behaviour compared to when i start in ubuntu classic [without effects], before it was the same, but it dont know the change i or linux made.  in unity i need vsync of CCC and compiz-tool to have smooth glxgears, in ubuntu classic w/o effects, both need to be disabled to run smooth.

i wonder why the **** those bitches are unable to produce 1 single ******* working driver for ati and especially for CROSSFIRE!

i can do a crossfire chain and enable it, but still it tells me:
> 
terror@ubuntu:~$ sudo aticonfig --lsch

CrossFire chain for adapter 0, status: enabled
  0. 01:00.0 ATI Radeon HD 5700 Series
  1. 02:00.0 ATI Radeon HD 5700 Series 
and:
> terror@ubuntu:~$ sudo aticonfig --lscs
[sudo] password for terror: 
    Candidate Combination: 
    Master: 1:0:0 
    Slave: 2:0:0 
    CrossFire is disabled on current device
    CrossFire Diagnostics:
    CrossFire can work with P2P mapping through GART
    Dongle Capabilities: support PASSTHROUGH |INTERLINK_SW_AFR | INTERLINK_AUTO_AFR | INTERLINK_BLACKING | INTERLINK_SUPERAA glxgears gives me ~9000 fps in ubuntu classic w/o effects, with vsync in unity its about 70 - 80 fps. somehow i destroyed my unity-interface by disabling it and now i cant go back and before that all windows i opened would group in the top right section of the screen, showing no window-controls [close, minimize, etc] and could not be moved.

AND WHY is ubuntu classic w/o effects switching themes on its own day by day and i cant even revert the change it makes?

WHEN WILL LINUX FINALLY BE RULING WINDOWS????????????????? TELL ME??? IM TRYING HARD and wait since 8.04!

ati and ubuntu guys DO SOMETHING! WHY DO YOU RENDER MY CROSSFIRE USELESS????

FAIL!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

:popcorn:

---

