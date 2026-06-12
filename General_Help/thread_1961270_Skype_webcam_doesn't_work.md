---
title: "Skype webcam doesn't work"
date: 2012-04-18
forum: General Help
---

### Post by tornadoes28 on 2012-04-18
My webcam in Skype does not work. I see the cam device in Skype but no picture. The webcam works when I use Cheese as well.

---

### Post by kohoutek1 on 2012-04-18
Can you tell us what you have tried so far to get the cam working? Skype settings, system settings, LSB video?

---

### Post by tornadoes28 on 2012-04-18
I have Skype set to start video automatically when I have a call. But when someone  calls they can't see me. I run the Skype test but there is no video picture.

I looked around in system settings but I am not sure where there are settings for the webcam.

---

### Post by kohoutek1 on 2012-04-19
Is your camera built in, or USB?

---

### Post by coldraven on 2012-04-19
Go to the "Test video" page in Skype Options and shine a light at your webcam. Can you see anything?
It could be that the brightness is too low. You can fix it by quitting Skype and running
guvcview. Its in the repos.
Either crank up the brightness or uncheck "Auto Gain" then quit, no need to save, and try Skype again

---

### Post by mörgæs on 2012-04-19
Does this help?
[http://ubuntuforums.org/showthread.php?t=1899379](http://ubuntuforums.org/showthread.php?t=1899379)

---

### Post by mastablasta on 2012-04-19
you can try this (copy& paste into terminal):
```
 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

```or
```
 
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

```

---

### Post by tornadoes28 on 2012-04-19
> **kohoutek1 said:**
> Is your camera built in, or USB?

USB Logitech

---

### Post by tornadoes28 on 2012-04-19
> **coldraven said:**
> Go to the "Test video" page in Skype Options and shine a light at your webcam. Can you see anything?
It could be that the brightness is too low. You can fix it by quitting Skype and running
guvcview. Its in the repos.
Either crank up the brightness or uncheck "Auto Gain" then quit, no need to save, and try Skype again

Tried that but that's not it.

---

### Post by tornadoes28 on 2012-04-19
> **mastablasta said:**
> you can try this (copy& paste into terminal):
```
 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

```or
```
 
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

```

I tried those before and I keep getting these errors.

ERROR: ld.so: object '/usr/lib/libv4l/v4l2convert.so' from LD_PRELOAD cannot be preloaded: ignored.

(skype:3226): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype:3226): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype:3226): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype:3226): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

---

### Post by tornadoes28 on 2012-04-19
I had same problem with the last version of Ubuntu. Before I was able to use it with the preload but not this time for some reason.

---

### Post by tornadoes28 on 2012-04-19
Ok, I just tried this:

LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype

and although I still get all those error messages in the terminal, the camera works now. But what's up with all the error messages?

---

### Post by More or Less on 2012-04-20
Do you know if Skype works in 12.04 Beta yet?  I got it working in 11.10, but I can't seem to find a download for it in 12.04.  If I should make a new thread on this issue I will, but since it is Skype related, I thought I would just post here instead.

---

### Post by mastablasta on 2012-04-20
> **tornadoes28 said:**
> Ok, I just tried this:
 
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
 
and although I still get all those error messages in the terminal, the camera works now. But what's up with all the error messages?
 
 
forgot what it means exactly. it's written somewhere on Skype Linux forums.
 
anyway you cannow create a scritpt and launcher, so that you just double click it to launch it.

---

