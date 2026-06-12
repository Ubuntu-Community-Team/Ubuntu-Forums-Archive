---
title: "Scroll wheel not working"
date: 2011-05-05
forum: General Help
---

### Post by wordsforthewise on 2011-05-05
I just upgraded to 11.04 from 10.04 and now the scroll wheel on the mouse doesn't work.  Super frustrating! Any ideas/suggestions?  There's no scroll wheel option or anything in the mouse preferences menu...:confused:

---

### Post by joe2012 on 2011-05-07
I'm having the same issue

---

### Post by imrazor on 2011-05-08
I managed to get the scroll wheel working on my PS/2 mouse. As far as I know, this technique will only work on a PS/2 mouse. As near as I can tell, Ubuntu detects some PS/2 mice as "generic" mice; that is, as only having two buttons and that's it. I had to force the kernel to treat my mouse as a Microsoft Intellimouse to get the scroll wheel working. To verify this, look at /var/log/Xorg.0.log and see if there are some lines referencing a "PS/2 Generic Mouse". 


[FONT=Lucida Console][SIZE=4][COLOR=Red]**CAUTION: The following commands change your GRUB configuration, and could conceivably render Ubuntu or other OS's unbootable.** [/COLOR][/SIZE][/FONT]

Open a terminal, and type:
```
$ sudo nano /etc/default/grub
```In nano, look for a line that starts with:
```
GRUB_CMDLINE_LINUX_DEFAULT=
```Following this line will be some text in quotes. Insert "psmouse.proto=imps" into the line, so that the whole thing looks something like:
```
GRUB_CMDLINE_LINUX_DEFAULT="psmouse.proto=imps quiet nosplash"
```Then hit CTRL-X to exit, then Y to save your changes. 
You will then need to type:
```
$ sudo update-grub
```to update your boot menu. You should then be able to reboot and enjoy a functional scroll wheel. Additionally, /var/log/Xorg.0.log should now recognize your mouse as "ImPS/2 Generic Wheel Mouse".

---

### Post by wordsforthewise on 2011-05-09
Thanks for the help, but it's still not working.  I also tried changing the "nosplash" part to "splash" since that's how it was originally in my grub file.  More info:  I'm using an IntelliMouse Explorer 4.0 USB/PS2 (plugged in via USB).

---

### Post by imrazor on 2011-05-13
> **wordsforthewise said:**
> Thanks for the help, but it's still not working.  I also tried changing the "nosplash" part to "splash" since that's how it was originally in my grub file.  More info:  I'm using an IntelliMouse Explorer 4.0 USB/PS2 (plugged in via USB).

The only other suggestion I have is to try "psmouse.proto=exps" for your Explorer mouse.

---

### Post by andry_yosua on 2011-05-13
i'm having exactly the same problem
edit xorg.conf, but didn't resolve anything..
any suggestion?:confused::confused:

---

### Post by wordsforthewise on 2011-05-14
balls.  still not working, even after trying "psmouse.proto=exps"

---

### Post by donniesito on 2011-05-16
I am having somewhat the same issue:

I upgraded to 11.04 as well, and at first everything worked like a charm. Over the last couple of days however, the scroll wheel stopped working.... In one direction.

I can scroll down, but cannot scroll up.  Doesn't matter the application or window, it's the same. In the case of GoogleEarth, I can zoom out, but can't zoom in using the wheel.

I dual-boot with Win7, and in Windows the mouse works fine, so I know it's not an issue with the mouse itself.

So guys.. I have half the problem you do lol - What about it?  Why would the scroll wheel work in one direction, but not the other?

---

### Post by Kryzzalid on 2011-05-19
Hi.

I have got the same problem here. The wheel was working fine until i updated to 11.04. I noticed in Xorg.0.log that the mouse is detected as a 9 buttons one.. but it has only 3 (right, left and the wheel). Here is what the log says:

```
 HID 09da:001a: Applying InputClass "evdev pointer catchall"
[    20.555] (II) Using input driver 'evdev' for 'HID 09da:001a'
[    20.555] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.555] (**) HID 09da:001a: always reports core events
[    20.555] (**) HID 09da:001a: Device: "/dev/input/event4"
[    20.555] (--) HID 09da:001a: Found 9 mouse buttons
[    20.555] (--) HID 09da:001a: Found scroll wheel(s)
[    20.555] (--) HID 09da:001a: Found relative axes
[    20.555] (--) HID 09da:001a: Found x and y relative axes
[    20.555] (II) HID 09da:001a: Configuring as mouse
[    20.555] (II) HID 09da:001a: Adding scrollwheel support
[    20.555] (**) HID 09da:001a: YAxisMapping: buttons 4 and 5
[    20.555] (**) HID 09da:001a: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.555] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input4/event4"
[    20.555] (II) XINPUT: Adding extended input device "HID 09da:001a" (type: MOUSE)
[    20.560] (II) HID 09da:001a: initialized for relative axes.
[    20.560] (**) HID 09da:001a: (accel) keeping acceleration scheme 1
[    20.560] (**) HID 09da:001a: (accel) acceleration profile 0
[    20.560] (**) HID 09da:001a: (accel) acceleration factor: 2.000
[    20.560] (**) HID 09da:001a: (accel) acceleration threshold: 4
[    20.561] (II) config/udev: Adding input device HID 09da:001a (/dev/input/mouse0) 
```

Is there any way to configure the mouse manually? Thank you:)

---

### Post by wordsforthewise on 2011-05-26
holy scheisse! its working now! after I did the most recent updates and rebooted, it seems to work.  Awesome! \\:D/\\:D/\\:D/\\:D/\\:D/

---

### Post by wordsforthewise on 2011-06-28
Aw weak...just ran another update with a bunch of stuff, and the scroll wheel isn't working!!! WTF ubuntu...i thought you were cool.:mad:

---

### Post by sketchyjustin on 2011-07-13
Came here via google. Scroll wheel doesn't work for me anymore either. 3button USB Microsoft Optical Mouse. Can't find any help on Google.

---

### Post by Kryzzalid on 2011-07-20
Hi.

My scroll wheel still doesn't work. Update or not... It works on Xubuntu Maverick and windows but doesn't on the latest Xubuntu. Like I said before i think it's because Xubuntu sees it as a 9 buttons wireless mouse (A4 Tech Co., Ltd Wireless Mouse & RXM-15 Receiver according to lsusb). But it's just a cheap optical USB 2-button-scroll-wheeled VALUE Mouse. Again is there any way to reconfigure the mouse? Thank you

---

### Post by KryptoKalEl on 2011-09-15
Thanks.  :)
Just adding psmouse.proto=imps to my GRUB_CMDLINE_LINUX_DEFAULT line worked for me.

---

