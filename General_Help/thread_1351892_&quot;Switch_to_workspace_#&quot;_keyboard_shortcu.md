---
title: "&quot;Switch to workspace #&quot; keyboard shortcut not working anymore + Wacom tablet issues"
date: 2009-12-11
forum: General Help
---

### Post by GarGar on 2009-12-11
So I've just got a new laptop, and switched from windows to Karmic. I have to say it's been a confusing, interesting and frustrating process, though I'm liking it, even if compatibility is rather frustrating to handle for me.

(RESOLVED mostly)
 ANYWAY, just a small problem, but I've had the "Switch to workspace #" keyboard shortcuts set to (mod4, windows key)super + 1, 2 and 3, and just last night I was fiddling around in compiz with the desktop plugins and disabled desktop wall, and even after setting everything back to how it was and re-enabling desktop wall, the "Switch to workspace #" shortcuts would NOT work, even when I tried setting the hotkeys to all kinds of things. So I figured maybe a restart would fix it, because the preferences did get stuck like that once until I restarted, but the shortcuts still won't work at all. I really like being able to switch to exactly the workspace I want with one hand, so I'm wondering if anyone knows how I can fix this?

[B]One other little nitpick, I really wish tablet compatibility was more supported, I still cannot find a way to be able to set expresskeys, or the &quot;Pan/Scroll&quot; function. I've even tried installing the official driver on Virtualbox running XP but it gives me an error saying &quot;A supported tablet was not found on the system&quot; and I got Paint Tool SAI working perfectly on there, as well. If I can't resolve the tablet issue soon I'm thinking about hooking up a netbook with XP to another monitor and just using that for drawing.    
[/B] 
**Thanks for any help on easing the converting process**

---

### Post by GarGar on 2009-12-11
Looks like I found a solution to the hotkey problem, I just switched to Cube + Cube Rotate plugins in compiz and set hotkeys there, and I'm satisfied. Still though, if someone has a miracle solution for the tablet issues, I'm open.

---

### Post by Favux on 2009-12-11
Hi GarGar,

Welcome to Ubuntu Forums!

You didn't say what Wacom tablet you have.  I don't know if it is a miracle solution or not but you might want to look at [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") on the Wacom tablets thread.

I hope this is helpful.

---

### Post by GarGar on 2009-12-11
Thanks Favux, I'll check that out. 

About the tablet, it's an Intuos3 6x8. model number PTZ-630.

---

### Post by GarGar on 2009-12-11
I've tried what's in that post, and it works great. Almost.

> Now "xinput --list" and "xsetwacom list" entered in a terminal should agree with each other and return the linuxwacom names stylus, eraser, cursor (if you have the Wacom mouse), and pad.When I do this, stylus and eraser do match up, but there is no cursor.

```
stylus           stylus    
eraser           eraser
```I open up wacomcpl and there's no cursor device either, of course, so I can't configure the mouse, which I do use often. Another important (to me) problem is no Pan/Scroll option, I usually have that on my second side switch and scroll all over the place, but it's nowhere to be found. ExpressKey settings would be nice too, of course, but I don't use them anyway.

Thanks for the help, it would be nice to work this out.

---

### Post by Favux on 2009-12-11
Hi GarGar,

Great!  Progress.

First to rule out a hardware problem does the Wacom mouse (cursor) work in Windows?

Does the mouse plug into your Intuos3 via a usb cable?  Is it plugged in when you boot?  It looks wireless.  Do you have it in proximity to the tablet when you boot?

Which .fdi did you use?

---

### Post by GarGar on 2009-12-11
I've had this tablet for almost a year now, and I've used it on two different Windows computers without any problems. I haven't used it on the dual-boot Windows on this specific laptop yet, because it's still completely bare (need to get around to installing drivers...)
 
 The mouse is wireless, just like the stylus; the tablet is plugged in every time I boot (even if that's not what you meant); the mouse IS close when I boot, but it doesn't actually detect it unless it's on the tablet, maybe I should try that next..?
 
 I used the '[Favux_new-generic_rc1_10-linuxwacom.fdi.txt]("http://ubuntuforums.org/attachment.php?attachmentid=138849&d=1260140121")' at the bottom, I figured the top one was for Jaunty, especially considering they're named different.

---

### Post by Favux on 2009-12-11
Hi GarGar,

> the mouse IS close when I boot, but it doesn't actually detect it unless it's on the tablet, maybe I should try that next..?
Yes.

If that doesn't work let's look at a lshal with the mouse sitting on the tablet:
```
lshal>GarGar_lshal.txt
```
Right click on it and compress it with Create Archive and then attach it to your next post with Manage Attachments.

The first .fdi is for usb tablets in Jaunty and Karmic.  The second for serial tablets and the third, the one you used, is for both (all) tablets.

---

### Post by GarGar on 2009-12-12
Booting with it on the tablet didn't help. Here's the lshal

---

### Post by Favux on 2009-12-12
Hi GarGar,

Well the info.callout to hal-setup-wacom is working:
```
wacom.types = {'eraser', 'cursor', 'pad'} (string list)
```
And eraser is set up correctly.  However cursor and pad:
```
udi = '/org/freedesktop/Hal/devices/usb_device_56a_b1_noserial_if0_logicaldev_input_subdev_1'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_b1_noserial_if0_logicaldev_input'  (string)
  info.product = 'stylus pad'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_b1_noserial_if0_logicaldev_input_subdev_1'  (string)
  input.device = '/dev/input/event6'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'pad'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_b1_noserial_if0_logicaldev_input_subdev_0'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_b1_noserial_if0_logicaldev_input'  (string)
  info.product = 'stylus cursor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_b1_noserial_if0_logicaldev_input_subdev_0'  (string)
  input.device = '/dev/input/event6'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'cursor'  (string)
```
When HAL adds an extension on subdev, like subdev_0 and subdev_1, it's saying that sub-device does not exist.  So that's why the mouse and pad (tablet) buttons aren't working, HAL doesn't think they exist.

If you are plugging the tablet into a usb hub plug it directly into a usb port on the computer.  Check the usb cable and make sure it is firmly in the tablet end and computer port end.

---

### Post by GarGar on 2009-12-12
It is plugged directly into the laptop and the cord seems fine. I can try it on a different computer tomorrow to confirm.

---

### Post by Favux on 2009-12-12
Hi GarGar,

Good idea.  Since you don't have a Windows partition yet to rule out a hardware problem that's the best alternative.  Does the Intous3 need a usb 2.0 port?  Is the one on the laptop 2.0 or 1.1?

You could try the first .fdi (the usb one) on the post I linked you to just to be thorough.  I don't think it will fix it though.

---

### Post by GarGar on 2009-12-12
I do have a Windows partition, actually, it's just completely bare. I've been too busy trying to figure out everything else to install drivers and such.

The USB ports are definitely 2.0, and I know it can run on 1.1 because I did once, so it's not that.

I'll try the tablet on Windows, as well as the other .fdi and get back to you tomorrow.

---

### Post by GarGar on 2009-12-12
Good news! I used the top .fdi and I'm pretty sure it works just as it should, wacomcpl detects mouse and pad now, and I can set speed and buttons enough how I want them.

One little thing though, the button settings still don't have a Pan/Scroll option, which I used with the stylus very often for scrolling pages, even if I can set a keystroke to a paow,n hotkey for other programs. I hope a Pan/Scroll option gets implemented soon.

Now, how about this.
[IMG]http://i48.tinypic.com/308inwo.jpg[/IMG]
I've heard of alot of people having problems with USB devices on Karmic and VB3, and I'm wondering if you (or anyone else) knows something about what I can do to fix this? I've already added and checked a filter in the Virtualbox settings, though it's greyed out once I actually start it up.

Once again, thanks for all the help, I've made quite a bit of progress and leaned alot as well.

EDIT: Alright, I fixed it (almost). I just had to edit Users and Groups and allow myself to "Use Virtualbox" but now it gives me a VERR_READ_ERROR message when it tries to "create a proxy device". I'll make a new topic if I can't figure it out myself.

---

### Post by Favux on 2009-12-12
Hi GarGar,

Outstanding!  You're welcome.

The post with the .fdi's has some links for setting up the pad.  Also see the LWP"S [HOWTO]("http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom").

Sorry, can't help you with usb in VirtualBox in Karmic.  Best idea is to start a new thread.  One topic per thread is usually best.

---

