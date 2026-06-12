---
title: "HP touchpad/mousepad not working anymore :("
date: 2010-06-13
forum: General Help
---

### Post by Werner7 on 2010-06-13
Hey, not so sure what happened but this is how i think what happened. A friend got annoyed while typing that he moved the mouse, or something, and clicked the physical touchpad lock button on my HP DV5 laptop. After unlocking it, it wouldn't work, neither the keyboard :S. So after a hard restart it worked again! Woo! but  unfortunately it doesn't work once I logged in. So a usb mouse works! but its annoying to have to use a usb mouse when your on the run. If I lock the touchpad again, and unlock it, the keyboard wont work, neither will a usb mouse. Or it does but its funny, you can only click on windows, close buttons, minimize, ect. And browser tabs. But not on my applications menu, neither will keyboard shortcuts work, neither anything on the panels. So only hard reboots!

1. Touchpad doesn't work anymore after locking and unlocking it.
2. Restarting didn't help. 
3. only usb mouse works.


Any ideas? Thanks. Will be VERY much appreciated.
Running HP Dv5 1005TX
Ubuntu 10.04 64Bit
Thanks.

---

### Post by codingfreak on 2010-06-13
I am seeing the same BEHAVIOUR with HP Pavilion dv6000 laptop. :(

Found out that it has been reported in launchpad as a bug in 10.04
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/578040](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/578040)

---

### Post by Werner7 on 2010-06-13
Hmm, is there something like system restore in Ubuntu?

---

### Post by quirks on 2010-06-25
Hi, I was having the same issue. I believe that the Synaptics touchpad driver and Gnome both disable the touchpad individually. For some reason, Gnome (in particular gnome-settings-daemon) fails to re-enable it; which is why you end up with a dead touchpad, once you disable it.

Here is what fixed it for me (HP Pavilion DV6730ec):

First of all, open a terminal. Press Alt+F1 to open the applications menu and choose the Terminal application from the accessories or use an external mouse to so.

To bring your touchpad back to life, enter the following command:

```
gconftool --type bool --set /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```

The key "/desktop/gnome/peripherals/touchpad/touchpad_enabled" is where gnome-settings-daemon remembers that you disabled your touchpad. This is the reason, why it is disabled even after a reboot.

The issue will re-appear, next time you disable your touchpad. You need to prevent gnome-settings-daemon from disabling your touchpad in the first place, because the Synaptics touchpad driver does this already. To do so, run the following command in a terminal:

```
gconftool-2 --type string --set /apps/gnome_settings_daemon/keybindings/touchpad ""
```

This dissociates the key to lock your touchpad from gnome-settings-daemon.

Hope this helps. I recommend rebooting after this procedure and check if this really fixed it for good. I noticed that the error only occurs only once after a reboot.

You also might be interested in this Ubuntu bug tracker entry: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727?comments=all)

---

### Post by corruptor1972 on 2010-06-26
This worked for me on my DV5.  Woo-hoo!  :popcorn:

---

### Post by Werner7 on 2010-07-15
Yay yay yay!

Thanks alot for that one, sorry for this very late reply, but I was on holiday for a lil while.

Worked wonders.

Regards

---

### Post by DrDamage on 2010-09-23
Thanks a bunch for this solution, it worked wonders on my DV6700 as well :)

---

### Post by mitsumits on 2010-10-03
It worked for me as well (dv7). Thanx a lot. But the touchpad is not fully functional any more. Can't tap on it and cannot scroll up+down.
Any suggestions?

---

### Post by unknown23 on 2011-01-18
can someone please help me, this is not working as a solution for me, i have the same problem

acer - aspire 1350

i am using ubuntu 10.04

any help in this matter is greatly appreciated.

---

