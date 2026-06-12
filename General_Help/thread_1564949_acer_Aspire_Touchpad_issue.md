---
title: "acer Aspire Touchpad issue"
date: 2010-08-31
forum: General Help
---

### Post by Goatbuoy on 2010-08-31
Hi all!

This has been a problem for lots of people on many different threads, most of the threads end with "have you tried pressing Fn F7?", whereby the user says no, and the thread closes.  This was the first thing I tried, and then I hit the forums and no answers were available.

I installed the Netbook Remix of Ubuntu 10.04 yesterday on my acer aspire one, and my touch pad doesn't work.  USB mice work, and the pad is also visible in /proc/bus/input/device - I tried bypassing the shortcut key with modprobe -r psmouse && modprobe psmouse to see if it was the button that wasn't working, but I figured it was because the icon appears on screen when it is pushed.
I also thought it might be the actual pad that is damaged, but the two buttons either side of the pad are also unresponsive.
Dmessage | grep synaptics shows the following:

 8.128273] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000
[    8.222385] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9

Another point that might be worth mentioning is that when X loads, for literally a split second the touch pad is active - initially I thought this was because I knocked the USB mouse, but I unplugged it and it still happened.

There is also an entry in the Xorg.0.log file that says:
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)

Can anyone help with this matter?

---

### Post by zmoky on 2010-08-31
I'm having the same problems here with my Acer One zg5

at some point the mouse focus and click stops working.

the keyboard tab is the only solution for reaching some buttons.

i succeed to pass that by removing some accessibility feature as I read on some forum but i don't think that is a solution

---

### Post by Goatbuoy on 2010-09-01
Aye - I've checked through the accessibility options but none of them solve this.... are there any guru's out there who can send some wizardry this way??

---

### Post by zmoky on 2010-09-02
there is an feature in the accessibility options somewhere it says that when you type text to disable the touchpad so somehow I believe the bug comes from there.

for example some times you can enabled back the touchpad by using the Fn+F7 function, 

or the method I was talking the the previous post was made using mousetweaks somehow disable or enabling something in accessibility I really don't remember how... but anyway that wasn't a very good solution because an the restart you had to repeat the process.

in conclusion: 
i really recommend you to try the fn+f7 function when that happens again to see if that works for you

---

### Post by zmoky on 2010-09-02
... ah yes .... you just have to write in console
```
# mousetweaks
```
an alert will appear something that says to log out, ... you click log out and login back again

and after that the mouse clicks and focus should work until next restart when you have to repeat the process .... but 

that's not a solution.... 

as i said in the previous post,... try fn+f7

;)

---

### Post by Goatbuoy on 2010-09-02
No luck I'm afraid - mousetweaks did nothing, nor did disabling typing disable or pressing Fn F7.  Maybe I should log this bug?

---

### Post by zmoky on 2010-09-02
In this case I suppose you can submit this bug.

good luck :)

---

### Post by rapsball4 on 2010-10-10
Just bought a new Acer Aspire One D255 and am disappointed I can't get this working.  The trackpad is hyper sensitive and seems to click at random, even when I managed to get to the Mouse settings and disable clicks on the trackpad.  I plugged in a USB mouse and the pointer moves normally but it doesn't click.  I tried mousetweaks from the terminal but it didn't change anything.  I tried slowing down the mouse pointer settings to the minimum and that didn't slow it down at all either.

Have any other fixes been found?  Is it fixed in the current RC of 10.10?  Or at the very least will it work if I buy a new USB mouse?

---

### Post by zmoky on 2010-10-11
I've noticed that the touchpad has the same behavior in windows 7 also. So my opinion is that the touchpad has a driver problem, which possibility it has been propagated to linux platforms also. 

So my sugestion is to search and complie a more stable and new synaptic touchpad driver which may improve the functionality.

I haven't tried this yet because I solved the touchpad problem by using a usb mouse which works great in windows 7 (but windows 7 works slowly in my acer :) ).

I will install ubuntu again on the netbook and try the above but later when I will have more time, or when I hope that the driver will be updated

---

### Post by zmoky on 2011-05-22
it works great now after a BIOS update . no more touch pad problems.

---

### Post by dragonfly41 on 2011-05-22
Since you are an **[COLOR=Blue]Acer user[/COLOR]** I have a question ..

I've been trying to install ubuntu 10.10 on an Acer Aspire 3613WLMi notebook.

but after installing I cannot get an Internet connection (connection is fine on other laptops such as the one I'm using now).

I've tried LiveCD's ..

Parted Magic 
xubuntu 10.10
pclinux-gnome


In the latter this was detected ..

eth0: Realtek Semiconductor C. Ltd. RTL-8139/8139C/8139C+

but still no connection from any of these.

Can you advise what network driver you are using?

---

### Post by Foxparke on 2011-12-18
With the Acer Aspire One, Alt+Fn+F7 toggles the Trackpad on and off, although it is still detected by the system.

---

