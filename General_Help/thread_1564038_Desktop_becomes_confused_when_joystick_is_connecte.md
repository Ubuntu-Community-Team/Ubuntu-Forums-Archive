---
title: "Desktop becomes confused when joystick is connected"
date: 2010-08-30
forum: General Help
---

### Post by Irvine_himself on 2010-08-30
I am running Lucid Lynx with the Gnome Desktop on an Optiplex GX270. Over the weekend, I bought this Ubuntu compatible Joystick [http://info.maplin.co.uk/Module.aspx?ModuleNo=48309](http://info.maplin.co.uk/Module.aspx?ModuleNo=48309)

I have calibrated it using "jstest" and "jscal" and have written a bash which sets the calibration parameters when I connect the joystick. On the surface, everything seems hunky dory, but some very confusing things happen when multiple  windows are open on the same Desktop.

The exact symptoms are difficult to describe, but for example: 

1) I cant switch windows by using the taskbar, I can only collapse or expand windows
2) In documents or web pages where there is an inset with a horizontal slider, the  inset gradually creeps to the left if the pointer is inside the inset.

There are various other weird things happen which are difficult to pin down, but essentially I can only have the Joystick plugged in when actually playing a game.

I don't know if it is relevant, but I also have a "Trust Mini Graphics Tablet" and a mouse permanently plugged in and this combination cause no problems.

I believe "evtest" monitors real-time input from a device such as a joystsick, but I cant find any documentaion and when I just try to run it, I get errors telling me I have the wrong parameters?

Does anyone have any ideas?

---

### Post by Irvine_himself on 2010-08-30
I can give a little bit more detail now, maybe it will help someone help me: I have finally figured out how to work "evtest" and mouse movement while the joystick is connected are "_sometimes_" interpreted as coming joystick.


A sample "evtest" output while pointing at the joystick and only moving the mouse is:

```
irvine@irvine-desktop:~$ evtest /dev/input/event6
Input driver version is 1.0.0
Input device ID: bus 0x3 vendor 0x458 product 0x301c version 0x100
Input device name: "Padix Co. Ltd. USB, 3-axis, 4-button joystick"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 288 (Trigger)
    Event code 289 (ThumbBtn)
    Event code 290 (ThumbBtn2)
    Event code 291 (TopBtn)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value    135
      Min        0
      Max      255
      Flat      15
    Event code 1 (Y)
      Value    124
      Min        0
      Max      255
      Flat      15
    Event code 6 (Throttle)
      Value     10
      Min        0
      Max      255
      Flat      15
  Event type 4 (Misc)
    Event code 4 (ScanCode)
Testing ... (interrupt to exit)
Event: time 1283172946.867115, type 3 (Absolute), code 1 (Y), value 126
Event: time 1283172946.867130, -------------- Report Sync ------------
Event: time 1283172946.899112, type 3 (Absolute), code 1 (Y), value 124
Event: time 1283172946.899126, -------------- Report Sync ------------
Event: time 1283172965.928557, type 3 (Absolute), code 1 (Y), value 126
Event: time 1283172965.928572, -------------- Report Sync ------------
Event: time 1283172965.968551, type 3 (Absolute), code 1 (Y), value 124
Event: time 1283172965.968565, -------------- Report Sync ------------
Event: time 1283173073.122169, type 3 (Absolute), code 1 (Y), value 126
Event: time 1283173073.122184, -------------- Report Sync ------------
Event: time 1283173073.146174, type 3 (Absolute), code 1 (Y), value 124
Event: time 1283173073.146201, -------------- Report Sync ------------
Event: time 1283173075.441857, type 3 (Absolute), code 1 (Y), value 126
Event: time 1283173075.441872, -------------- Report Sync ------------
Event: time 1283173075.473855, type 3 (Absolute), code 1 (Y), value 124
Event: time 1283173075.473871, -------------- Report Sync ------------
Event: time 1283173107.381570, type 3 (Absolute), code 1 (Y), value 126
Event: time 1283173107.381586, -------------- Report Sync ------------
Event: time 1283173107.429565, type 3 (Absolute), code 1 (Y), value 124
Event: time 1283173107.429580, -------------- Report Sync ------------
Event: time 1283173109.909232, type 3 (Absolute), code 1 (Y), value 126
Event: time 1283173109.909248, -------------- Report Sync ------------
Event: time 1283173110.013217, type 3 (Absolute), code 1 (Y), value 124
Event: time 1283173110.013232, -------------- Report Sync ------------
Event: time 1283173281.246235, type 3 (Absolute), code 1 (Y), value 125
Event: time 1283173281.246251, -------------- Report Sync ------------
Event: time 1283173325.088350, type 3 (Absolute), code 0 (X), value 136
Event: time 1283173325.088366, -------------- Report Sync ------------
Event: time 1283173425.730847, type 3 (Absolute), code 1 (Y), value 123
Event: time 1283173425.730864, -------------- Report Sync ------------
Event: time 1283173425.802835, type 3 (Absolute), code 1 (Y), value 125
Event: time 1283173425.802849, -------------- Report Sync ------------
Event: time 1283173469.364987, type 3 (Absolute), code 1 (Y), value 124
Event: time 1283173469.365003, -------------- Report Sync ------------

```I also noticed that in terms of output generated by  "evtest" the effect is much more pronounced if I re-boot and do not calibrate the joystick. This raises the question:

Is it a problem solely of calibration, (ie too sensitive a dead zone,) or is it something much more fundamental like a bug in the joystick driver?

I would be grateful for any advice at all?

---

### Post by Irvine_himself on 2010-08-30
Okay, I have kept plugging away at this and think I have found the problem. I notice that this post is coming up regularly on my Google searches, along with a number of other recent posts related to similar problems in the Ubuntu Lucid release. A number of unsatisfactory solutions have been proffered without explanation. These proffered solutions involve deleting or editing important files. Well for the record here is my solution with explanation and it does not involve deleting or editing anything:

1) The "X.Org X server -- joystick input driver" conflicts with the "joystick package driver," stick to just installing "joystick" and "evtest".  see [https://help.ubuntu.com/community/Joystick_lshal](https://help.ubuntu.com/community/Joystick_lshal) If you decide to stick with the "X.org solution" then you will lose the calibration tools and may have to start editing some very esoteric files.

2) To avoid this, use the "joystick" package, however there is a bug in the package available from the repos "joystick-20051019-9" see [https://bugs.launchpad.net/ubuntu/+source/joystick/+bug/448446](https://bugs.launchpad.net/ubuntu/+source/joystick/+bug/448446) To get around this, download and install "joystick-20051019-12" from the Debian archive at [http://packages.debian.org/sid/joystick](http://packages.debian.org/sid/joystick)

Reboot the computer and check everything works using "jstest" and your game of choice. 

For me this seems, (for the moment,) to have cleared up all the problems related to Ubuntu Lucid Lynx confusing the mouse and the joystick. :D

---

