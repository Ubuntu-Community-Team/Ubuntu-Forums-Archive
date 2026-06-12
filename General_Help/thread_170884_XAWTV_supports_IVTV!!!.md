---
title: "XAWTV supports IVTV!!!"
date: 2006-05-05
forum: General Help
---

### Post by dlai on 2006-05-05
LOOOK AT THIS GUYS!!!!!!! Finally an application that supports mpeg2-encoding cards like pvr-150, pvr-550 and pvr-350. Now you can change channels and watch tv in the same application with good
quality!!!!

If you don't know how to install ivtv-drivers you can go [here]("http://help.ubuntu.com/community/Install_IVTV_Edgy")

Quote:
Getting started and Overview about the changes in xawtv version 4.x
================================================== =================


Changes/Status Overview
-----------------------

New Features + Changes

* MPEG software decoding, and based on that:
- support for DVB cards, including Budget cards.
**- support for MPEG Encoder cards (ivtv).**
* reworked configuration framework.
* switch over to gtk as X11 GUI toolkit.

Dropped Features

* Overlay without Xvideo extention.
* Resolution switching for fullscreen.

Obsolete (likely will be dropped)

* motv application (gtk-ported xawtv will take over

work needed (i.e. broken/untested/incomplete right now)

* movie recording.
* lirc support.
* documentation is outdated.
* fbtv & ttv.

Ok I tried making a deb for all of you! but I'm really not sure it works, can you please try it out.
It is important that you ```
sudo apt-get remove xawtv-plugins pia scantv
``` there might be more I'm not sure. Here is a link to the file: [xawtv with nodvb]("http://www.imi.aau.dk/~jfur05/linux/xawtv-nodvb_3.9-1_i386.deb")
It depends on way to many things, so better go with the source file.
----------------------------------------------------- If the deb doesn't work------------------------------------------------------------

This is what i ended up installing to make it compile.
```
sudo apt-get install libice-dev libsm-dev libxaw-headers libxaw7-dev libxmu-dev libxmu-headers libxpm-dev libxt-dev libxv-dev libxvmc-dev x11proto-video-dev libmad0-dev libmpeg2-4-dev zvbi libzvbi-dev libjpeg62-dev libncurses5-dev automake1.9 libgtk2.0-dev
```

This is from the xawtv new in 4.x.... the cvs version already have ivtv support , and it is now playing on my dapper-box....
you can download it [here.]("http://dl.bytesex.org/cvs-snapshots/xawtv-20061123-095905.tar.gz")
```
./autogen.sh
./configure --disable-dvb
make
sudo make install
```

--------------------------------------
27. June 2006
Looks like i missed some things... just updated to the new cvs version and put libgtk2.0-dev in the end of the dependency list... oops
---------------------------------------
7. July 2006
Well now i updated the .deb package i sure hope it works.. it worked on my comp, but the dependencies might be faulty, if they are please contact me through the forum....

---------------------------------------
2. December 2006
Fixed some small errors (thanks disturbedsaint),added the newest cvs-snapshot

---

### Post by dlai on 2006-06-08
Well after all i tried the .deb myself and it seemed to work flawlessly, when my ivtv drivers where correctly installed.... hope you experience the same...
Best Regards

---

### Post by kraz on 2006-06-26
Cant find the .deb file in the URL you put here..any help?

---

### Post by kraz on 2006-06-26
OIK..so I ended up trying to compile the thing as you instructed, but where did the executable go? Sorry I'm quite new to this...

---

### Post by dlai on 2006-06-27
I'm sorry i accedently deleted the .deb i will see if i can recompile it later... if you open up the terminal and write xawtv it should work.

---

### Post by kraz on 2006-07-02
No. Somehow the binary of "xawtv" doesnt show up in my system after I compile. All other files are created just fine just xawtv binary isnt, and it seems i get no errors at compile time, so I really dont understand...

---

### Post by dlai on 2006-07-03
Try ```
sudo apt-get install libgtk2.0-dev
``` and then compile again, that might do the trick

---

### Post by dlai on 2006-07-07
The deb package is up and running again... Hope you can use it!

---

### Post by dlai on 2006-07-09
I've heard that some users have problems with running xawtv, that it might freeze X... Anybody had the same issues, and even solved them? My only guess can be that one need to run ```
scantv
``` before running xawtv... because maybe the PAL freezes but I'm not sure. Furthermore it might help enabling 3D-acc. if it is possible. For enabling the ivtv-drivers before installing xawtv please follow this [guide]("http://hyams.webhop.net/mythtv/myth_ubuntu.html")....
with one addition you copy everything in the folder /usr/lib/hotplug/firmware/ to
/lib/firmware/<kernel ver.>/ aka.```
sudo cp /usr/lib/hotplug/firmware/* /lib/firmware/<kernel ver.>/
```

---

### Post by bosonflux on 2006-07-10
I have finally managed to get my PVR 150 working with Xawtv. However, I had no luck with the Ubuntu version in the repositories. You can start xawtv with
~# xawtv -remote and it wont freeze X, but the screen is still black and seems to have no input.

I completely removed the Ubuntu version of Xawtv and installed the .deb that
dlai has posted. There were some dependency problems that were resolved by
apt-get -f install. After that, xawtv came up with a picture, I ran scantv and it entered all my channels. Scantv must be run with xawtv not running or it hangs, at least for me. Now I'm just trying to fine tune ivtv and testing various recording modes.

Thanks to dlai for a working xawtv .deb! Link is in an above post.

---

### Post by valmar on 2006-07-12
Hello everyone! I am using Kubuntu dapper. My card is Hauppauge PVR 350, I am using ivtv 4.4 (nothig more recent works for me) and compiling the last snapshot of xawtv from source. I compiled xawtv using the directions given above. I used scantv and started xawtv. First I had choppy playboack with a band of apparently random colours in the bottom of the screen. Finally the program crashed and since then if I try to start xawtv I get a segmentation fault. Maybe you can help, please! Feel free to be technical, I want to learn!

     Valerio

---

### Post by dlai on 2006-07-13
bosonflux: I'm glad you got it working, I sent you a mail, but I noticed today that my smtp was not set up correctly, now it is sent anyway, hope you can use it, the help i have given is almost the same as the last post.
valmar: I have no idea how to help you here... maybe you can post the output when the segmentation fault happens. I do not know the differences between the 350 and the 150(I use 150), I don't know if they have any driver differences or something.

---

### Post by bosonflux on 2006-07-15
Valmar,
   I wish I knew all the answers. I got mine working by using ivtv 4.6 with the debian xawtv posted by dlai in an above post. I first had to remove the 
xawtv, scantv, pia, and xawtv-plugins. Then proceed with new install.

good luck

---

### Post by atezun on 2006-10-21
where exactly does xawtv save its recordings by default

---

### Post by dlai on 2006-10-22
Don't know have not tried myself

---

### Post by ivarka on 2006-11-24
Hi!

I'm trying to compile a the newest version of xawtv, but since I'm not used to compiling my own stuff I got some (basic) problems...

Download the driver
- Did a "sudo apt-get install libgtk2.0-dev"
- Figured out I needed autoconf: "sudo apt-get install autoconf"
- Did "./autogen.sh" but it returned:

cp: cannot stat `': No such file or directory

The autogen.sh looks like this

> 
#!/bin/sh
inst=$(ls	/usr/share/automake*/install-sh \
		/usr/local/share/automake*/install-sh \
		2>/dev/null | head -1)
set -ex
autoconf
autoheader
rm -rf autom4te.cache
cp "$inst" .

So I guess "inst" is the problem...

What to do?

Ivar

---

### Post by dlai on 2006-11-26
are you using edgy?? did you install build-essential?

---

### Post by dlai on 2006-11-26
Just tried it out, I can't make it work either... I even tried the version from the 11. of November.

---

### Post by brottman on 2006-11-27
This is sweet that my Hauppaugge pvr-usb2 finally works with this new version 4.0 of xawtv. Will this version get included with the next release (Feisty) when it is released?

---

### Post by disturbedsaint on 2006-11-28
dlai:
The .deb you posted depends on a lot of stuff that seems to be unneccessary
```
 xawtv-nodvb depends on libzvbi0 (>= 0.2.11); however:
  Package libzvbi0 is not installed.
 xawtv-nodvb depends on gcc-4.0 (>= 4.0.3-1ubuntu5); however:
  Package gcc-4.0 is not installed.
 xawtv-nodvb depends on pkg-config; however:
  Package pkg-config is not installed.
 xawtv-nodvb depends on imake (>= 1); however:
  Package imake is not installed.
 xawtv-nodvb depends on libgmime2.1-cil; however:
  Package libgmime2.1-cil is not installed.
 xawtv-nodvb depends on libzvbi0; however:
  Package libzvbi0 is not installed.
 xawtv-nodvb depends on gnome-screensaver; however:
  Package gnome-screensaver is not installed.
 xawtv-nodvb depends on gnome-system-tools; however:
  Package gnome-system-tools is not installed.
 xawtv-nodvb depends on libevolution-cil; however:
  Package libevolution-cil is not installed.
 xawtv-nodvb depends on gok; however:
  Package gok is not installed.
 xawtv-nodvb depends on deskbar-applet; however:
  Package deskbar-applet is not installed.
 xawtv-nodvb depends on gnome-utils; however:
  Package gnome-utils is not installed.
 xawtv-nodvb depends on mono-classlib-1.0; however:
  Package mono-classlib-1.0 is not installed.
 xawtv-nodvb depends on gnome-pilot; however:
  Package gnome-pilot is not installed.
 xawtv-nodvb depends on gnopernicus; however:
  Package gnopernicus is not installed.
 xawtv-nodvb depends on rhythmbox; however:
  Package rhythmbox is not installed.
 xawtv-nodvb depends on linux-kernel-headers (>= 2.6.11.2-0ubuntu18); however:
  Package linux-kernel-headers is not installed.

```


And the first part out of your initial post should read
```
[COLOR="Red"]sudo[/COLOR] apt-get remove xawtv-plugins pia scantv
```
instead of
```
apt-get remove xawtv-plugins pia scantv
```
:)

---

### Post by disturbedsaint on 2006-11-28
Well, just compiled it myself and (after finding out which packages where needed for it to compile) it works now.

But:
It doesn't display any video. It says:
> mpeg ts: no pids given and no PAT found
can't open: /dev/video0

/dev/video0 does work when CATing to an MPEG file or when opened in MPlayer.
Does anybody have a clue as to what might be te problem?

---

### Post by disturbedsaint on 2006-11-29
Well, I just forced an install from the .deb provided in the first post and that results in the same problem.

Could someone who's got it working plz post the results from the following commands:
```
xawtv -hwlsfig
```
```
xawtv -hwconfig
```

Thanks in advance!

---

### Post by dlai on 2006-12-02
> **disturbedsaint said:**
> dlai:
The .deb you posted depends on a lot of stuff that seems to be unneccessary
```
 xawtv-nodvb depends on libzvbi0 (>= 0.2.11); however:
  Package libzvbi0 is not installed.
 xawtv-nodvb depends on gcc-4.0 (>= 4.0.3-1ubuntu5); however:
  Package gcc-4.0 is not installed.
 xawtv-nodvb depends on pkg-config; however:
  Package pkg-config is not installed.
 xawtv-nodvb depends on imake (>= 1); however:
  Package imake is not installed.
 xawtv-nodvb depends on libgmime2.1-cil; however:
  Package libgmime2.1-cil is not installed.
 xawtv-nodvb depends on libzvbi0; however:
  Package libzvbi0 is not installed.
 xawtv-nodvb depends on gnome-screensaver; however:
  Package gnome-screensaver is not installed.
 xawtv-nodvb depends on gnome-system-tools; however:
  Package gnome-system-tools is not installed.
 xawtv-nodvb depends on libevolution-cil; however:
  Package libevolution-cil is not installed.
 xawtv-nodvb depends on gok; however:
  Package gok is not installed.
 xawtv-nodvb depends on deskbar-applet; however:
  Package deskbar-applet is not installed.
 xawtv-nodvb depends on gnome-utils; however:
  Package gnome-utils is not installed.
 xawtv-nodvb depends on mono-classlib-1.0; however:
  Package mono-classlib-1.0 is not installed.
 xawtv-nodvb depends on gnome-pilot; however:
  Package gnome-pilot is not installed.
 xawtv-nodvb depends on gnopernicus; however:
  Package gnopernicus is not installed.
 xawtv-nodvb depends on rhythmbox; however:
  Package rhythmbox is not installed.
 xawtv-nodvb depends on linux-kernel-headers (>= 2.6.11.2-0ubuntu18); however:
  Package linux-kernel-headers is not installed.

```


And the first part out of your initial post should read
```
[COLOR="Red"]sudo[/COLOR] apt-get remove xawtv-plugins pia scantv
```
instead of
```
apt-get remove xawtv-plugins pia scantv
```
:)

yes I know about the .deb but I'm quite a noob at packaging I'm sorry... but if anyone is willing to package it better, I will host it!
I will fix the how to thanks...

---

### Post by dlai on 2006-12-02
from now on I would recommend installing ivtv by following this [https://help.ubuntu.com/community/Install_IVTV_Edgy]("https://help.ubuntu.com/community/Install_IVTV_Edgy"), hope it helps!

---

### Post by smsmith050 on 2007-03-03
xawtv -hwls
This is xawtv 4.0-pre, running on Linux/i686 (2.6.15-27-686)

probing dvb devices ...

probing vbi devices ...
 [vbi] /dev/vbi0             WinTV PVR 250                        0000:02:07.0

probing video devices ...
 [v4l2] /dev/video0          WinTV PVR 250                        0000:02:07.0
 [v4l] /dev/video0           WinTV PVR 250
 [xv] port:160               xv port: 160 (NVIDIA Video Inte

probing dsp devices (playback) ...
 [alsa] plughw:AudioPCI,0    Ensoniq AudioPCI / ES1371 DAC2/
 [alsa] plughw:AudioPCI,1    Ensoniq AudioPCI / ES1371 DAC1
 [oss] /dev/dsp              /dev/dsp
 [oss] /dev/adsp             /dev/adsp

probing dsp devices (record) ...
 [oss] /dev/dsp              /dev/dsp

probing mixers ...
 [alsa] hw:AudioPCI          Ensoniq AudioPCI / SigmaTel STA
 [oss] /dev/mixer            SigmaTel STAC9721,23

xawtv -hwconfig
This is xawtv 4.0-pre, running on Linux/i686 (2.6.15-27-686)

device configuration "WinTV PVR 250":
      bus      = 0000:02:07.0
      video    = /dev/video0
      vbi      = /dev/vbi0
      sndrec   = [unset, using default]
      sndplay  = [unset, using default]
      mixer    = [unset, using default]
      control  = [unset]

device configuration "xv port: 160 (NVIDIA Video Inte":
      bus      = [unset]
      video    = port:160
      vbi      = [unset]
      sndrec   = [unset, using default]
      sndplay  = [unset, using default]
      mixer    = [unset, using default]
      control  = [unset]

---

