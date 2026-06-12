---
title: "Message: Has someone got their MX700 working?"
date: 2006-06-27
forum: General Help
---

### Post by Xecuter on 2006-06-27
I'm having trouble getting all of the buttons on my MX700 working. I've been following the HowTo but I can't get it to work!

Has someone else got their working? Give me a quick tutorial.

---

### Post by Poka64 on 2006-06-27
Tried this HowTo ?
[http://www.ubuntuforums.org/showthread.php?t=188302](http://www.ubuntuforums.org/showthread.php?t=188302)

---

### Post by Xecuter on 2006-06-27
Yes.

---

### Post by Poka64 on 2006-06-27
What happens when you follow the HowTo ?

---

### Post by pormogo on 2006-06-27
I too am using an MX700 mouse/keyboard combo when I follow that tutorial I am unable to get X back up and running after editing xorg.conf, I think this might have to do with how the mouse and keyboard are labeled.


I: Bus=0003 Vendor=046d Product=c50b Version=2100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:10.1-2/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c50b Version=2100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:10.1-2/input1
S: Sysfs=/class/input/input2
H: Handlers=kbd mouse0 event2 ts0 
B: EV=7
B: KEY=ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 0 1878 d800d100 1e0000 0 0 0
B: REL=103

it looks like both the mouse and keyboard are named Logitech USB Receiver. When you create the udev rule in that tutorial would it not be affecting both devices? below is from my  /etc/udev/rules.d/19-local.rules

KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/mx700"

here is (the currently commented out since it breaks X) the mouse section from my /etc/X11/xorg.conf

Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "evdev"
       Option          "CorePointer"
       Option          "Device"        "/dev/input/mx700" #this should be that underlined name from 19-local.rules
EndSection

I can't figure out for the life of me why this isn't working, but I think we might be having the same issue if you're using a wireless KB/M combo with an MX700.

---

### Post by Poka64 on 2006-06-27
I had the same thing with another HowTo, this HowTo that I linked to points out to an old evdev (the current one in dapper is broken).

---

### Post by Xecuter on 2006-06-29
Strange. I got it to work. I discovered that xserver-xorg-input-evdev package was updated and that might have been the problem. So I reinstalled it, restarted GNOME, and got this message:```
(**) Configured Mouse: Device: "/dev/input/mx510"
(EE) Unable to open evdev device "/dev/input/mx510".
(EE) PreInit failed for input device "Configured Mouse"
(II) UnloadModule: "evdev"

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4a56]
1: [0xffffe420]
2: /lib/tls/i686/cmov/libc.so.6(malloc+0x81) [0xb7e01411]
3: /usr/bin/X(xf86optionListCreate+0xb0) [0x80d135f]
4: /usr/bin/X(xf86CollectInputOptions+0x34) [0x80b6d7e]
5: /usr/lib/xorg/modules/input/wacom_drv.so [0xb737f1fd]
6: /usr/bin/X(InitInput+0x1a0) [0x809cfe5]
7: /usr/bin/X(main+0x368) [0x806df94]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7db0ea2]
9: /usr/bin/X(FontFileCompleteXLFD+0x81) [0x806d611]

Fatal server error:
Caught signal 11.  Server aborting
``` (This is not mine. Where can I find my log?)
So I restarted the computer and now it works.

---

