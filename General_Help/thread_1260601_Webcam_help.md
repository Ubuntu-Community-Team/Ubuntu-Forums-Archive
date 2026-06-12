---
title: "Webcam help"
date: 2009-09-07
forum: General Help
---

### Post by racie on 2009-09-07
Hey there Ubuntu users.  I've had issues installing an old webcam on Windows, so now I'm trying to see if it'll work on Ubuntu.  I've done some Googling and found that my webcam was supported with the old [spca5xx](https://help.ubuntu.com/community/Spca5xx) driver.  However, I am aware that the spca5xx driver has been replaced with a different one so I'm completely lost.  It is connected to my computer right now via USB and nothing is happening.  Where do I start?

Oh, and it's a D-link DSC 350 webcam.

Thanks.

---

### Post by racie on 2009-09-07
Anyone?

---

### Post by arman.haghi on 2009-10-09
G'day mate,

I've got the exact same camera and just got it working (again), so here goes at trying to help. There's a lot of solutions out on other posts (including old posts I's made) but this series of steps seems the best fix.

1.

First of all, plug your webcam into a USB port

It should 'beep' and the red light next to the viewfinder should switch on (make sure it has light hitting the lense, this seems to effect the red light). If this doesn't happen, either your USB port is dead, your USB cable is dead or the camera is.

2.

Open up a terminal and check that your box picks it up:

```
lsusb
```

you should see this somewhere in the list of results:

> Bus 002 Device 003: ID 084d:0003 Minton Optic Industry Co., Inc. S-Cam F5 Digital Camera

If you don't then again, it's a fundamental USB connectivity problem. I'm assuming you do see this and continuing.

3.

Go to:

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

and download:

gspcav1-20071224.tar.gz

(unless your kernel is below 2.6.11, in which case you should download spca5xx-v4l1goodbye.tar.gz)

4.

extract it and run the gspca_build script as root, i.e.

```
sudo ./gspca_build
```

If all goes well, then we're almost in business - but here's where the camera can be very buggy. It's like the thing is emotional.

5.

Most people have trouble getting it to show up as /dev/video0 which is your 'video device' as far most programs will be concerned (e.g. Skype).

Check to see if you have it:

```
ls /dev/vid*
```

If you get "/dev/video0" then you should be able to see it in some applications now (e.g. Skype seems to work well). Any problems thereafter is an application specific issue.

6.

If not, then add gspca on a new line at the bottom of your /etc/modules file, making sure that there is a empty line after it.

```
sudo nano /etc/modules
```

so it'll look something like this (obviously examplemodule_1 is there as an example of other things you may find in there):

> 

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

examplemodule_1
examplemodule_2
gspca




This'll make sure gspca is loaded at boot time; so reboot your machine with the camera plugged in to your usb port, and after the reboot check to see if it's there now:

```
ls /dev/vid*
```

7.

After you reboot, if it still isn't there or if the /dev/video0 disappears, or the camera 'hangs' every now and then, which it does, then try unplugging the camera, replugging it in (ignore the usb device things that come up, just hit cancel) and then you need to

7.a. 'remove' the module

```
sudo modprobe -v -r gspca
```

7.b. 'reinstall' the module

```
sudo modprobe -v gspca
```

7.c. then check to see if you now have the /dev/video0

```
ls /dev/vid*
```



OK, you may already know most of that, let me know if this was of any use or if you're still having trouble and I'll try to help.

PS I often have to go through the steps 7.a-b-c. above to refresh the device, so I'm made this little bash script (attached) which I run from a link on my desktop.

---

### Post by racie on 2010-11-05
My apologies!  I can't believe I never replied to this post!  Thanks for your response.

I actually never got my webcam working, and it seems like very few people have.  The gspca module is bundled with my current kernel, so it would not work for me to build it.  The webcam appears to be detected by Ubuntu just fine, but the problem is that there is no /dev/vide0.  Apparently, this is quite a problem with this webcam.

Things I have tried
```
sudo modprobe gspca
```
which yields
```
FATAL: Module gspca not found.
```

So then I tried
```
sudo modprobe gspca_main
```
and
```
sudo modprobe gspca_spca500
```

This does not result in any errors, but it does not create video0.  Although strangely, this seems to work for a some people.

Anyone have any ideas?

*edit* I forgot to add... I have tested the webcam in Windows, so I really don't think that it doesn't work because it's old.  However, it does behave strangely and does not work with most webcam software (in Windows).

---

