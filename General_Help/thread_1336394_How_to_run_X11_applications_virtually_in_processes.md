---
title: "How to run X11 applications virtually in processes (no X)?"
date: 2009-11-24
forum: General Help
---

### Post by frenchn00b on 2009-11-24
it is to run skype without using xorg 

here is a solution but not good enough:
[http://insitu.lri.fr/metisse/docs/metisse-architecture.png](http://insitu.lri.fr/metisse/docs/metisse-architecture.png)
compositor

---

### Post by diesch on 2009-11-24
Maybe *xvfb* is what you want:

 Xvfb provides an X server that can run on machines with no display
 hardware and no physical input devices. It emulates a dumb framebuffer
 using virtual memory. The primary use of this server was intended to be
 server testing, but other novel uses for it have been found, including
 testing clients against unusual depths and screen configurations, doing
 batch processing with Xvfb as a background rendering engine, load testing,
 as an aid to porting the X server to a new platform, and providing an
 unobtrusive way to run applications that don't really need an X server but
 insist on having one anyway.
 .
 This package also contains a convenience script called xvfb-run which
 simplifies the automated execution of X clients in a virtual server
 environment. This convenience script requires the use of the xauth
 program.

---

### Post by frenchn00b on 2009-11-24
> **diesch said:**
> Maybe *xvfb* is what you want:

 Xvfb provides an X server that can run on machines with no display
 hardware and no physical input devices. It emulates a dumb framebuffer
 using virtual memory. The primary use of this server was intended to be
 server testing, but other novel uses for it have been found, including
 testing clients against unusual depths and screen configurations, doing
 batch processing with Xvfb as a background rendering engine, load testing,
 as an aid to porting the X server to a new platform, and providing an
 unobtrusive way to run applications that don't really need an X server but
 insist on having one anyway.
 .
 This package also contains a convenience script called xvfb-run which
 simplifies the automated execution of X clients in a virtual server
 environment. This convenience script requires the use of the xauth
 program.


wow it works !!
```
  #!/bin/sh


killall -e skype

killall -e skype Xvfb

 Xvfb :2 &

 DISPLAY=:2 ; export DISPLAY ; skype &


while [ 1 ] ; do sleep 1h  ;  amixer -c 1 set 'Mic',0 100 ; done



```


[B][COLOR="Red"]I still fight to know how to make it work at start power on of the linux in /etc/rc2.d ?[/COLOR]

[COLOR="Red"]Do you know if I need xorg, can I remove XORG and RUN XVFB with apt-get remove xorg packages?

[/COLOR][/B]



---

---

### Post by jelevin on 2009-11-30
I am trying to set up a cron script to run something hourly.  The script contains

```
DISPLAY=:8
# Start the framebuffer.
Xvfb $DISPLAY -screen 0 800x600x24 &
export DISPLAY
/usr/local/bin/myprogram
```
and when I run from the command line I get
```
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
(EE) config/hal: NewInputDeviceRequest failed (2)
Xlib:  extension "RANDR" missing on display ":8.0".
```

Any thoughts regarding these errors?

---

### Post by diesch on 2009-12-02
> **frenchn00b said:**
> 
I still fight to know how to make it work at start power on of the linux in /etc/rc2.d ?

I never tried that. What problems do you have?

> **frenchn00b said:**
> 
Do you know if I need xorg, can I remove XORG and RUN XVFB with apt-get remove xorg packages?

You can at least remove the xerver-* packages except for xsrver-common. The package dependencies should tell you if you try to remove anything xvfb or your applications still need.

---

### Post by diesch on 2009-12-02
> **jelevin said:**
> 
```
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!

```
It's looking for fonts in this folder but can't find any. Just ignore it

> **jelevin said:**
> 
```
 (
(EE) config/hal: NewInputDeviceRequest failed (2)

```

Input device configuration via HAL doesn't work. I guess you don't want to use input devices with this anyway so it's not  a problem.

> **jelevin said:**
> 
```

Xlib:  extension "RANDR" missing on display ":8.0".
```Any thoughts regarding these errors?

The RandR extension isn't supported so you can't change resolution and orientation on the fly. Shouldn't be a problem either.

---

