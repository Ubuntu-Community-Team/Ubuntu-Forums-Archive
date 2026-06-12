---
title: "Logitech QuickCam for Notebook no longer working in 9.10"
date: 2009-11-02
forum: General Help
---

### Post by ireneybean on 2009-11-02
My Logitech camera worked fine in Cheese Webcam Booth and Skype until I upgraded to Karmic Koala.  

Running lsusb I see this line pertaining to the webcam:

> Bus 002 Device 002: ID 046d:08cf Logitech, Inc. QuickCam UpdateMe

The device shows up in Skype, but I get no picture when clicking on "Test".

In Cheese webcam booth I get the "no signal" picture.

I'm not sure where to go from there as everything just worked in Jaunty.

Dmesg has the following when I plug in the webcam

> [ 2333.863929] usb 2-1: USB disconnect, address 2
[ 2341.617053] usb 2-2: new high speed USB device using ehci_hcd and address 5
[ 2341.999598] usb 2-2: configuration #1 chosen from 1 choice
[ 2342.000350] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08cf)
[ 2342.042735] input: UVC Camera (046d:08cf) as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/input/input18


---

### Post by spiderbatdad on 2009-11-02
not sure but having the device id (046d:08cf Logitech) can help you in researching.
You might try the package qc-usb-source in synaptic as it provides a kernel module for these types of cams. I don't know whether you'll have to load the module manually...I would hope not. Try installing the package and rebooting.

---

### Post by ireneybean on 2009-11-02
Thanks.  I installed qc-usb-source from synaptic and rebooted ... but no difference. I'll try doing some research using the device id  ...

---

### Post by spiderbatdad on 2009-11-03
try this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/424594](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/424594)
unplug your cam, run command ```
sudo modprobe -r pwc
```connect the cam again.

---

### Post by ireneybean on 2009-11-03
Tried that also with no luck.  Thank you for your suggestions though.  The help is much appreciated.

I've also found a few other threads with some suggestions that I'm going to take a look at when I get home from work this evening.  
(This one is old but looks helpful in tracking down the problem at least: [http://www.ubuntuforums.org/showthread.php?t=53755&highlight=logitech+webcam](http://www.ubuntuforums.org/showthread.php?t=53755&highlight=logitech+webcam))

I will update this thread if I make any progress.

---

### Post by ireneybean on 2009-11-04
No new information really.  Everything I can find seems to be outdated.  The most recent information seems to be that it should just work.  (which it did in jaunty)

System log has the following when I unplug/replug

> Nov  4 01:00:12 localhost kernel: [  809.748655] usb 2-3.2: USB disconnect, address 5
Nov  4 01:00:17 localhost kernel: [  814.749294] usb 2-3.2: new high speed USB device using ehci_hcd and address 6
Nov  4 01:00:17 localhost kernel: [  815.091517] usb 2-3.2: configuration #1 chosen from 1 choice
Nov  4 01:00:17 localhost kernel: [  815.091725] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08cf)
Nov  4 01:00:17 localhost kernel: [  815.134780] input: UVC Camera (046d:08cf) as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.2/2-3.2:1.0/input/input19
Nov  4 01:00:18 localhost pulseaudio[2537]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Nov  4 01:00:18 localhost pulseaudio[2537]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Nov  4 01:00:18 localhost pulseaudio[2537]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Nov  4 01:00:18 localhost pulseaudio[2537]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Nov  4 01:00:18 localhost pulseaudio[2537]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Nov  4 01:00:18 localhost pulseaudio[2537]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Nov  4 01:00:18 localhost pulseaudio[2537]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.

Which makes no sense in and of itself because the audio on the camera still actually works.  It's the video that does not.

also of interest, this device is actually a "Logitech QuickCam Deluxe for Notebooks" which should have a device id of 09c1

I'm guessing that the UpdateMe listing that I get from the lsusb command indicates that the driver needs updating.  I only wish I could!

---

### Post by ireneybean on 2009-11-04
Tried running from the Live CD for 9.10 and everything still looks just as above, so I'm concluding that whatever happened really was because of the upgrade and not something that I did inadvertantly.

---

### Post by trpnblies7 on 2009-11-05
You might be having the same problem that I and some other people are having, in that my webcam will only run as root. If I try to access my webcam through Cheese or gstreamer-properties, it says permission denied. But if I "sudo cheese" or "sudeo gstreamer-properties", then it works fine. It seems to be some kind of permission problem, but I have no idea how to fix it.

---

### Post by tups34 on 2009-11-05
Hi

I had this same issue with my logitech quick cam pro 4000, in that it works fine under 9.04 but did not under 9.1! :mad:

I got it going by installing the setpwc package.

you can check to see if the modual is installed by doing[COLOR=Red] lsmod | grep -i "pwc"[/COLOR] in a terminal. if not, install it and do a restart (just for good measure;)) [COLOR=Black]

then plug in webcam and start cheese and see if it comes up

hope this helps 
[/COLOR]

---

### Post by ireneybean on 2009-11-06
Running cheese as root (sudo cheese) made no difference.

I tried installing setpwc and restarting.  No difference, however doing the lsmod | grep -i "pwc" still did not show the module as loaded.

---

### Post by jiapei100 on 2009-11-06
I seriously have no idea why my Logitech Pro 4000 also has the same problem on Ubuntu 9.10

But, on my laptop, the webcam some times works !!! Strange !!!

```
lsmod | grep -i "pwc"
pwc                    81632  0
videodev               36736  1 pwc

```

Seriously no idea why some times it works, some times not...

---

### Post by LuxAeterna on 2009-11-07
My old, trusty Logitech webcam does not work in 9.10 either. Like ireneybean, I get the busy signal in Cheese. lsusb shows the webcam as "Logitech, Inc. QuickCam Messenger Communicate", which is correct, but no video. Installing the pwc package did nothing for me, and lsmod does not show it.

---

### Post by tups34 on 2009-11-07
Firstly let me apologise for leading you astray, my earlier post said i had fixed this problem. 

alas i have not! :mad:

What I have found is my web-cam will work only if it is plugged in from boot!

if i boot with it unplugged and then plug it in once ive logged into my desktop then it will not work:sad:

ive tried changing permissions but alas still no good.  boooooo

this is a pain as in 9.04 it worked fine.

still will try some more frigging around and see if i cant sort this out.

---

### Post by sorabsuperstar on 2009-11-08
Same here.

Cam is recognized as 
Logitech, Inc. QuickCam Messanger

but does not work.

This camera used to work under Ubuntu ever since.
Under Ubuntu 9.04 it started having problems under Skype only. But that was Skype's problem I guess as other v4l software could use it properly. Hence with a little trick it also worked under Skype (piping the v4l output of the real camera into a virtual v4l device and use that one in Skype)

But in Ubuntu 9.10 it is totally dead.

---

### Post by ireneybean on 2009-11-08
Well ... I'm glad to know that I'm not alone at least!

---

### Post by Fire_Chief on 2009-11-18
Adding my name to the list of previously working now dead Logitech camera users. Have a Cisco VT Camera (rebranded Logitech Quickcam) that was perfect in 8.10. Fresh 9.10 install and no dice. I do have the module loaded. Running cheese as root is no good. Thankfully this is not critical but more of a fun thing. Still it would be nice if it wasn't broken.

---

### Post by ireneybean on 2009-11-18
Yeah, it's not technically "critical" for me either, however I did spend real money on the webcam, and it worked fine in 9.04 so it's pretty irritating.

---

### Post by crm71 on 2009-12-01
Using a 046d:09a2       Logitech Quickcam Communicate Deluxe/S7500 here.

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) lists this as functional.

Module pwc not added at boot time.  Plugging in usb cam after bootup and modprobing pwc didn't appear to work even though pwc loaded fine.  Log messages looked fine except for > pulseaudio[1602]: alsa-mixer.c: Your kernel driver is broken [...] :confused: an issue with the camera mic input apparently.

But then again perhaps it did.

Running gstreamer or Cheese showing the led lit indicating camera on record.  :-k   I then shined a flashlight into the lens.  Photo sensor seemed to auto adjust after a second or two of lightsaber like action on camera playback and wholla, **picture**. :biggrin:

Maybe there are some ways to initialize the kernel UVC driver to fix this.  I've not tried a boot up with camera plugged in to see if it'll just work.

---

### Post by crm71 on 2009-12-01
On a related note, setpwc really didn't like my cam (no great surprise), probing:

> setpwc v1.2, (C) 2003-2006 by [EMAIL="folkert@vanheusden.com"]folkert@vanheusden.com[/EMAIL]
Current device: UVC Camera (046d:09a2)
Error while doing ioctl VIDIOCPWCPROBE: Invalid argument
Warning: this might not be a Philips compatible webcam!
VIDIOCPWCPROBE returns: &#65533;&#65533;&#65533; - 10842048
Error while doing ioctl VIDIOCPWCGSERIAL: Invalid argument
Serial number: 
Resolution (x, y): 640, 480
Offset: 0, 0
Brightness: 37008
Hue: 0
Colour: 7196
Contrast: 6939
Whiteness: 0
Palette: Unknown! (0)
Error while doing ioctl VIDIOCPWCGCQUAL: Invalid argument
Compression preference: 134524724
Error while doing ioctl VIDIOCPWCGAGC: Invalid argument
Automatic gain control: 134524724
Error while doing ioctl VIDIOCPWCGAWB: Invalid argument
Whitebalance mode: unknown!
Blinking of LED is not supported by the combination
of your webcam and the driver.
Error while doing ioctl VIDIOCPWCGCONTOUR: Invalid argument
Sharpness: 134524724
Error while doing ioctl VIDIOCPWCGBACKLIGHT: Invalid argument
Backlight compensation mode: on
Anti-flicker mode is not supported by the combination
of your webcam and the driver.
Noise reduction mode is not supported by the combination
of your webcam and the driver.
Pan/tilt range is not supported by the combination
of your webcam and the driver.
Get pan/tilt position is not supported by the combination
of your webcam and the driver.
And then there is good ol' pulseaudio regarding cam mic ](*,)

> Dec  1 08:43:49 mine pulseaudio[1602]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Dec  1 08:53:39 mine pulseaudio[1602]: ratelimit.c: 1 events suppressed
Dec  1 08:54:08 mine pulseaudio[1602]: ratelimit.c: 219 events suppressed
Dec  1 08:54:16 mine pulseaudio[1602]: ratelimit.c: 88 events suppressed
Dec  1 08:57:44 mine pulseaudio[1602]: ratelimit.c: 210 events suppressed
Dec  1 08:57:49 mine pulseaudio[1602]: ratelimit.c: 154 events suppressed
Dec  1 08:59:59 mine pulseaudio[1602]: ratelimit.c: 77 events suppressedBut who is a stranger to pulseaudio having hiccups anyway?  :-s

---

### Post by crm71 on 2009-12-01
A few things. I have no prior experience with webcam device problems in linux, so the last few hours of searching and reading have been interesting, including scanning the pwc.if.c 10.0.11 source file to see what module options were available (power_save=1 is one example along with a trace mode, but I'm unsure if Canonical built the module with debug set to enable).

Anyway, by logs and lsmod,

> uvcvideo 59080 0
videodev 36736 1 uvcvideo
v4l1_compat 14496 2 uvcvideo,videodevAre what ubuntu 9.10 provides for me by default.

Odd that v4l2_common is not loaded and that blacklisting v4l1_compat (vl41 is deprecated and quite old) didn't seem to stop modprobe on uvcvideo/videodev from still pulling it back in. ](*,) v4l2_common has to be explicitly added.

Uvcvideo seems to handle the majority of Logitech cams. Removing pwc (it's based on phillips firmware afterall) after unplugging the cam and plugging back in gave same results as mentioned above with just the uvcvideo/videodev/v4l1_compat module support. If you find probe output from setpwc to be mostly lacking, you probably want to avoid using it.  

Using only uvcvideo driver, I still had to shine a flashlight to get sensor to auto adjust out of pitch black while running cheese.  Many webcams on laptops have an auto correcting low light feature as well.  Probably same issue with hopefully a module parameter to correct.  Unplugging and re-plugging back in, the device retained lit functionality--for a time.  After some amount of time (again plugged in or not) the device goes back to a very low sensor setting again (completely black video out until a high luminosity input).  Kind of sounds like a power saving feature again.  :-s  Once functional, frame rate seems extraordinarily slow into cheese at 640x480 (compression setting issue?)

I had no luck getting either:

```
gst-launch-0.10 v4l2src ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink
```(with v4l2_common loaded)
or
```
gst-launch-0.10 v4lsrc ! video/x-raw-yuv,format=\(fourcc\)UYVY,width=640,height=480 ! ffmpegcolorspace ! ximagesink
```to run... both complaining about pipeline unable to pause issues.  Some of these are longstanding issues you'll find in forum searches here and elsewhere going back to at least 2007.

I would suggest looking at [http://www.linuxtv.org/wiki/index.php/Webcams](http://www.linuxtv.org/wiki/index.php/Webcams), particularly uvcvideo and gspca sections.

---

### Post by timvieira on 2009-12-01
You can add me to the list of confused people. The device works just fine if you reboot with it plugged in already, but unplug it and plug it back in and all bets are off. Also, logging out and logging back in again doesn't do the trick.

I tried adding pwc to /etc/modules:
> 
sudo echo "pwc" >> /etc/modules

Then logging out, in, and plugging in the camera but that didn't work. Do you think it needs options as well?

---

### Post by ramjet_1953 on 2009-12-13
Same problem here.
If I remember to plug the camera in before booting, all works OK.

It's a pain when something since Dapper has worked without issue and now it doesn't.

Regards,
Roger :(

---

### Post by ireneybean on 2009-12-14
Since I started this thread, I figured I'd update with what I've found out.  After trying every thing I could think of on my laptop, I tried installing the webcam on two different windows computers with the Logitech drivers from the CD it came with AND the most updated drivers from Logitech's website and saw the same behavior.  So Logitech is replacing the cam as it was still under warranty.

I don't know what caused it to break, but if definitely happened during the Karmic Koala install (worked immediately before installing and did NOT immediately afterwards!)

---

### Post by no2498 on 2009-12-14
you can set vl4 1 an vl4 2 in gstreamer-properties
click video

---

### Post by rockdj on 2010-01-27
Same trouble here with a Logitech Quickcam Pro 4000 on my desktop running 9.10 32-bit.

Although, the difference for me is that the camera *was* working with 9.10 until just last week.  Unsure what, if anything, was updated within 9.10 (maybe that was when I last restarted [I typically hibernate]; will test that theory).  Now, however, it's broken and any application that manages to display output from the camera (without crashing out first) displays a green screen.

Now, off to try and restart the computer.

Any help is greatly appreciated as I do my work via video conferencing...

---

### Post by e.m.fields on 2010-01-28
Solution I think is Easycam software.

It sounds like it takes some building and doing, but I saw at least 3 good reports coming back from this thread.

[http://ubuntuforums.org/showthread.php?t=100384]("http://ubuntuforums.org/showthread.php?t=100384")

---

### Post by countryheartaz on 2010-02-04
Hey guys..I just loaded ubuntu for the first time. Never got my logitech web cam to work with anything. I am NOT a programmer so going to the root or the kernel is NOT my thing. Im an old OS/2 or Microsoft plug and pray sorta guy. I stumbled on something.
Cheese did not work with my cam. Skype did not work with my cam but I loaded an application called guvcview from the ubuntu software center and BOOM..it loaded the correct driver somewhere and now my logitech quickcam notebooks deluxe is working GREAT! YEAH.. The test doesn't work in skype but everyone says that is a problem..

Hope this helps..

Chuck

---

