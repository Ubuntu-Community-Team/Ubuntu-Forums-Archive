---
title: "Installing the latest ATi driver (fglrx) fails on 9.10"
date: 2010-05-22
forum: General Help
---

### Post by blueturtl on 2010-05-22
Hi guys.

I got tired of not being able to run any 3D apps on my integrated Intel and went out and came home with a ATi Radeon HD 4650. Skip the bit about how I could have gotten an nVidia (they didn't have any HTPC compatible low-profile nVidias on shelf).

Actually the card works very well, it runs all the 3D apps I've thrown at it so far (and quite a bit faster too).

My problem is with video playback: it is jerky. The framerate stalls and then speeds up and is out of sync. When not out of sync, there is tearing. Yes I have tried turning Compiz off, didn't do anything. Weird thing is the CPU utilization is really low, so everything should be working.

I figured I would update the video drivers to the latest available on ATi website (following the instructions [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Troubleshooting")) but I've ran into trouble with the installer:
```

execstack -c debian/fglrx-amdcccle/usr/lib/bin/amdcccle
execstack: cannot open "debian/fglrx-amdcccle/usr/lib/bin/amdcccle": No such file or directory
make: *** [binary-install/fglrx-amdcccle] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
```

How do I proceed from here? If you've got a fix for the video with the drivers in the repositories that is cool also. I don't necessarily need the latest drivers.

Thanks!

---

### Post by blueturtl on 2010-05-23
Ok... now I got the packages to build by following the instructions [here]("http://www.phoronix.com/forums/showpost.php?p=124877&postcount=32").

Steps as follows:
Extract the driver with ```
sh ati-driver-installer-10-4-x86.x86_64.run --extract
```

Then edit the package file with ```
nano fglrx-install.something/package/Ubuntu/dists/karmic/package
```

Change the file by commenting out the very last line like this:
> 
[COLOR="Red"]binary-install/$(PKG_control)::
        execstack -c debian/$(PKG_control)/$(DRIDIR)/bin/amdcccle[/COLOR]

[COLOR="Blue"]binary-install/$(PKG_control)::
        **#**execstack -c debian/$(PKG_control)/$(DRIDIR)/bin/amdcccle[/COLOR]

Then ```
cd fglrx-install.something
```
and ```
./ati-installer.sh 10.04 --buildpkg Ubuntu/karmic
```

---

### Post by blueturtl on 2010-05-23
New problem...

I try to install the built driver packages

fglrx-amdcccle_8.723-0ubuntu1_amd64.deb
fglrx-kernel-source_8.723-0ubuntu1_amd64.deb
fglrx-modaliases_8.723-0ubuntu1_amd64.deb
libamdxvba1_8.723-0ubuntu1_amd64.deb
xorg-driver-fglrx_8.723-0ubuntu1_amd64.deb
xorg-driver-fglrx-dev_8.723-0ubuntu1_amd64.deb

by doing a ```
sudo dpkg -i *deb
```

But the package xorg-driver-fglrx fails to install with "too many errors".

dpkg-divert tells me it wants to replace file /usr/lib/xorg/modules/extensions/libdri.so with /usr/lib/fglrx/libdri.so.xlibmesa (but that obviously isn't working out).

I don't dare reboot until I can get the xorg-driver package installed.
Any help?!

---

### Post by Chaotic Caveman on 2010-05-23
I am having a similar problem with the one package not installing. At this point the driver is finally listed as an option in HARDWARE DRIVERS. I ended up rebooting and sent to the low graphics mode screen.  I am frustrated 'cause I havn't hit that duh moment yet. I just want to do this and cut bill gates out. It would be easier if I knew what I was doing.

---

### Post by blueturtl on 2010-05-23
Ok... and the solution to the latter problem was to force the removal of the original driver:

```
sudo dpkg --remove --force-all xorg-driver-fglrx
```

After this I was able to install the video driver:

```
sudo dpkg -i --force-all xorg-driver-fglrx_8.723-0ubuntu1_amd64.deb
```

Time to restart and see if anything works any more...

---

### Post by blueturtl on 2010-05-23
The new drivers are now installed and working!

However video playback is still jerky. :(
Looks like once I resize the video it actually plays too fast in relation to the audio. I wonder how I could get that fixed...

---

### Post by blueturtl on 2010-05-23
Playback was improved greatly by going to

System -> Preferences -> Sound

Then on the Devices tab I disabled the video card HDMI audio device.

Video still tears and some files don't play right, but this helped greatly.

Further suggestions?

It doesn't look like it's related to prosessing power as some hi-def clips play almost perfectly whereas some really low resolution clips are jerky.

---

### Post by blueturtl on 2010-05-23
Turning off desktop effects seems like a definite fix (except for mild tearing in fast scenes).

Figures. You're getting there ATi, keep going...

---

### Post by blueturtl on 2010-05-23
VLC works as well if you choose the OpenGL output method. This way videos run with Compiz about as well as they run on Totem without Compiz.

Still... Nothing I have tried so far has completely gotten rid of tearing.

```
Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Capabilities" "0x00000800"
	Option	    "TexturedVideoSync" "on"
	Option	    "OpenGLOverlay" "on"
	Option	    "OverlayOnCRTC2" "0"
	Option	    "UseFastTLS" "on"
	BusID       "PCI:1:0:0"
EndSection
```

This is my xorg.conf device section for the time being.

The capabilities option supposedly enables VSYNC... Textured Video Synchronization sounds as promising, but so far they haven't made a bit of difference.

---

### Post by Chaotic Caveman on 2010-05-23
I am grateful that you had the same type of issues I had at the same time I was.  You have done good work here. Forcing the removal of the original driver.  This was my duh moment. Thank you, thank you!
My driver now works!

---

### Post by Chaotic Caveman on 2010-05-23
Got any idea about the transparent icon/box that is in the lower right of my screen now? It says,

AMD 
Testing
use only

If you could inform me about how to remove this, you'd be my hero for the day.  Not that I'm saying your not already.

---

### Post by blueturtl on 2010-05-24
> **Chaotic Caveman said:**
> Got any idea about the transparent icon/box that is in the lower right of my screen now? It says,

AMD 
Testing
use only

If you could inform me about how to remove this, you'd be my hero for the day.  Not that I'm saying your not already.

Where did you download your driver? I am asking because I don't have a logo on my screen ... and because I know there is a OpenGL 4 pre-release driver on ATi's site. Would explain the 'testing use only' bit. :)

If you downloaded the driver like any normal person, then my guess is to head down to the Catalyst Control Center and see if you can disable the logo from there.

Don't thank me, thank Google. I'm just monologing in my own support thread. :D If I stumble on a solution I'll PM you.

--

On my own agenda, I seem to have solved the video tearing issue... but this is a bit unfortunate: it seems to happen only on the HDMI output. When I switched to VGA D-SUB the tearing is now gone. This is of course unfortunate for those of you who'd prefer to be using the digital output. If I find a solution I will post here.

---

### Post by blueturtl on 2010-05-24
> On my own agenda, I seem to have solved the video tearing issue... but this is a bit unfortunate: it seems to happen only on the HDMI output. When I switched to VGA D-SUB the tearing is now gone. This is of course unfortunate for those of you who'd prefer to be using the digital output. If I find a solution I will post here.
Ok seriously.

I thought I fixed the tearing, but it appears it is only fixed for videos that have the exact same resolution as the display. For instance the resolution used on HDMI was 1366x768. No video files are that size, but many are 1280x720 which happens to be the resolution I tested on the VGA out. Any videos not matching that resolutions still exhibit tearing. Considering there are lot's of different size videos out there, I am pretty much screwed until I can figure out what exactly causes the tear. :confused:

---

### Post by blueturtl on 2010-05-25
The definite tear solution:

Finally got proper video playback.
This is the solution for me on Ubuntu 9.10 Karmic Koala:

/etc/X11/xorg.conf Device section:

```
Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Capabilities" "0x00000800"
	Option	    "TexturedVideoSync" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "OverlayOnCRTC2" "1"
	Option	    "UseFastTLS" "on"
	BusID       "PCI:1:0:0"
EndSection
```

Compiz/Desktop effects: OFF

With these settings video playback woks flawlessly IF your player supports OpenGL output (VLC and MPlayer do at least, Totem/GStreamer does not at the time of writing).

This works consistently for me on both the HDMI and VGA outputs and all video files.

Now I am left with the minor annoyance of neither Mplayer nor VLC being able to stop the screensaver.

---

