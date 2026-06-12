---
title: "tesco w109 vga webcam"
date: 2011-04-13
forum: General Help
---

### Post by Irony on 2011-04-13
I have a tesco w109 vga webcam (640x480) but it doesn't seem to work in Ubuntu.

[IMG]http://i.ebayimg.com/00/$%28KGrHqEOKm4E2UiRPiNFBNl09Bcs2w~~_35.JPG[/IMG]

In Skype I get the following;

```
USB Camera (093a:2620) (/dev/video0)
```

so it appears to be detected. Nothing shows up in Cheese, just a black screen.

Does anyone know if drivers are available for this webcam - I've done the usual googling but can't find any reference to Ubuntu and w109.

---

### Post by Irony on 2011-04-14
What? Nobody knows, useless lot!

---

### Post by no2498 on 2011-04-15
[http://www.danielogawa.com/webcam.html](http://www.danielogawa.com/webcam.html)

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)



with the cam pluged in open a terminal type lsusb click enter
that should give you the number and name of the cam

in cheese click edit preference
see if you can change the settings

if not in your package manager look for and install v4l2ucp
it comes up in system/preferences as video4linux control panel
you can change things in it

---

### Post by Irony on 2011-04-16
Installed v4l2ucp then ran lsusb;

```
Bus 009 Device 002: ID 093a:2620 Pixart Imaging, Inc.
```

Went into sleep mode then came back and ran vlc command again and I get a picture through vlc!

```
~$ vlc v4l2:///dev/video0
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
[0x84a540] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0x7f07d1f55b20, 0x7f07d1f55a80)
Warning: call to signal(13, 0x1)
Warning: call to srand(1303364156)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:5493): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
```

I can also go to vlc directly and do the same thing by hitting;

```
play > capture device > play
```

However nothing through Skype yet...

```
~$ LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l2convert.so' from LD_PRELOAD cannot be preloaded: ignored.

```

Pushing test in Skype options does nothing - just a black thumbnail image.

v4l2ucp says;

```
driver: pac7311
card: USB Camera (093a:2620)
```

---

### Post by Irony on 2011-04-16
Also tried;

```
~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
```

Skype starts but no video.

Any suggestions?

---

### Post by Irony on 2011-04-16
Success!

Used the following command;

```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

I run 64 bit Ubuntu but I'm guessing skype uses 32 bit v4l1compat.so.

I then made a script calle skype;

```
#!/bin/sh
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skypecam
```

I put it in the /usr/bin directory after renaming the skype executable to skypecam - I made the script executable and now I can start skype as normal and the webcam work!

Thanks to no2498 for getting me on the path.

---

### Post by Irony on 2011-04-21
Failure...

The webcam worked for a few days, at the end of each day I would do a full shutdown of the computer then the next day boot up as normal and use skype.

But yesterday the webcam would not work with anything, nothing on skype, vlc or gstreamer.

The light on the webcam comes on when I try skype, vlc or gstreamer (and I can't then shut it off unless I reboot) but no picture.

I've not uninstalled or installed anything since the webcam so am stuck as to a solution.

```
~$ LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skypecam
libv4l2: error turning on stream: Input/output error
```

---

### Post by no2498 on 2011-04-21
you may need to change the plugin to auto find your cam in gstreamer

---

### Post by Irony on 2011-04-21
I am wondering whether I could install one of the listed 'unavailable' plugins that shows in gstreamer-properties - perhaps plugin 'qcamsrc'. I cannot see how to actually install these however...

```
~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
libv4l2: error turning on stream: Input/output error
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video0'. [gstv4l2object.c(1952): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: Input/output error]
```

---

### Post by no2498 on 2011-04-21
this is the list i get

gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'


you did not say if the cam came on

---

### Post by Irony on 2011-04-21
Yes the camera light comes on indicating power to the camera and it is registered as before as

```
driver: pac7311
card: USB Camera (093a:2620)
```

But the picture in skype is just a black box and with gstreamer it is just an error output.

It looks like our unavailable plugins are the same but you presumably have an esdsink plugin, but googling says that is a sound plugin...

---

### Post by no2498 on 2011-04-21
ok open a terminal type dmesg click enter
after it stops 
you may need to restart the computer im not sure

retry gstreamer-properties

---

### Post by Irony on 2011-04-21
Success!

Well I don't know... I figured I would uninstall VLC 1.1.4 and install the latest VLC 1.1.9 for Lucid via this;

```
https://launchpad.net/~n-muench/+archive/vlc
```

It installed and updated these;

```
libavcodec52 (4:0.5.1-1ubuntu1.1) to 4:0.6.2-1u1
libavdevice52 (4:0.5.1-1ubuntu1.1) to 4:0.6.2-1u1
libavformat52 (4:0.5.1-1ubuntu1.1) to 4:0.6.2-1u1
liborc-0.4-0 (0.4.3-5) to 1:0.4.11-2~ppa1
libpostproc51 (4:0.5.1-1ubuntu1.1) to 4:0.6.2-1u1
libschroedinger-1.0-0 (1.0.9.is.1.0.8-0ubuntu1) to 1.0.10.1-2~ppa1
libswscale0 (4:0.5.1-1ubuntu1.1) to 4:0.6.2-1u1
```

And now the webcam magically works again in skype, gstreamer and vlc, at least for now...

Thanks again no2498 for getting me thinking of different options.

---

### Post by no2498 on 2011-04-21
you are welcome

---

### Post by Irony on 2011-04-22
Failure...

After booting up the next morning the webcam is back to not working.

I notice that the number has changed from;

```
driver: pac7311
card: USB Camera (093a:2620)
```

to

```
driver: pac7311
card: USB Camera (093a:2622)
```

I don't know whether that might be confusing it.

Here is dmesg after resuming from suspend;

```
  698.238072] sd 9:0:0:0: [sdb] Starting disk
[  698.358835] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[  698.601640] pac7311 5-2:1.0: no reset_resume for driver pac7311?
[  698.601642] snd-usb-audio 5-2:1.1: no reset_resume for driver snd-usb-audio?
[  698.601644] snd-usb-audio 5-2:1.2: no reset_resume for driver snd-usb-audio?
[  698.601707] gspca: disconnect complete
[  698.601855] PM: resume of drv:usb dev:5-2 complete after 353.815 msecs
[  698.601860] PM: resume of devices complete after 6629.611 msecs
[  698.602710] gspca: probing 093a:2622
[  698.610657] gspca: probe ok
[  698.610662] gspca: probing 093a:2622
[  698.632884] PM: resume devices took 6.660 seconds
[  698.632914] PM: Finishing wakeup.
[  698.632915] Restarting tasks ... done.
[  698.873902] r8169: eth0: link up
[  698.916052] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)
[  699.023389] CPU0 attaching NULL sched-domain.
[  699.023393] CPU1 attaching NULL sched-domain.
[  699.023395] CPU2 attaching NULL sched-domain.
[  699.023396] CPU3 attaching NULL sched-domain.
[  699.100297] CPU0 attaching sched-domain:
[  699.100300]  domain 0: span 0-3 level MC
[  699.100302]   groups: 0 1 2 3
[  699.100305] CPU1 attaching sched-domain:
[  699.100307]  domain 0: span 0-3 level MC
[  699.100308]   groups: 1 2 3 0
[  699.100311] CPU2 attaching sched-domain:
[  699.100313]  domain 0: span 0-3 level MC
[  699.100314]   groups: 2 3 0 1
[  699.100317] CPU3 attaching sched-domain:
[  699.100318]  domain 0: span 0-3 level MC
[  699.100319]   groups: 3 0 1 2
[  709.791759] eth0: no IPv6 routers present
[  757.619698] gspca: set alt 0 err -71
```

---

### Post by no2498 on 2011-04-22
have you retried gstreamer-properties
and make sure the plugin is set to auto find the cam
ive had to redo mine after using it in vlc

---

### Post by Irony on 2011-04-24
Yes, I've tried several variations.

Basically it comes down to this; the webcam works but only immediately after I install VLC. Obviously uninstalling and re-installing VLC is not a practical route for using the webcam, however it must mean that something is not being loaded or initiated on boot-up.

---

### Post by no2498 on 2011-04-24
see if this program can find the cam

guvcviewer

---

### Post by Irony on 2011-04-25
I think I may have discover the problem...

I decided to investigate gstreamer so installed gstreamer-tools and issued the command;

```
gst-launch v4l2src ! video/x-raw-yuv,width=640,height=480,framerate=30/1 ! xvimagesink
```

But kept getting error messages about prerolling and input output errors. I tried all sorts of commmands.

Then I came across a fellow who said delete the hidden;

```
.gstreamer-0.10
```

Surely it couldn't be that simple... but it worked. Now everything works...

I will have to await some reboots but if all it takes is deleting .gstreamer-0.10 then I can live with that.

Once again thanks no2498 for keeping the thread live.

Note booted up again and it didn't work, but disconnected the camera (pulled out the usb socket) deleted .gstreamer-0.10 put camera back in an issued;

```
gst-launch v4l2src ! video/x-raw-yuv,width=640,height=480,framerate=30/1 ! xvimagesink
```

and everything works again.

It is important to physically disconnect the camera and reconnect it or else it complains that a pipeline is in the socket, even if .gstreamer-0.10 is deleted.

---

### Post by no2498 on 2011-04-25
glad you got it working again

---

### Post by Irony on 2011-05-15
Unfortunately it turned out that this didn't solution work again.

I've now boxed the webcam - in short Lucid can use the webcam but refuses to do so.

---

