---
title: "Mouse freezes after log in"
date: 2010-08-18
forum: General Help
---

### Post by oomar on 2010-08-18
I have a Hp pavillion dv5 (laptop) running Ubuntu 10.04 with all of the updates. When i start it up i can move around the mouse just fine. As soon as I hit enter to log in, the mousepad on my laptop stops working completely. The mousepad doesnt work nor do the buttons. However, if I plug in a USB mouse the USB mouse works fine, but the mousepad doesn't. So.... Any idea how to fix this?

---

### Post by oomar on 2010-08-18
bump.

I need help guys

---

### Post by Ampi on 2010-08-18
I don´t know about your case but it once happened to me on my acer one laptop, I had some combo key on the keyboard to lock the keyboard that I wasnt aware of. The combo key was one of the Fn keys and the sign on it was a picture that I didnt recognized as locking..

---

### Post by oomar on 2010-08-18
i dont think thats the problem. would i be able to type and use the keyboard if it was?

---

### Post by oomar on 2010-08-18
come on guys my only other option is a complete re-install and i dont want to do that again RIGHT after I set up everythign how i wanted it

---

### Post by oomar on 2010-08-18
i made a test account and it could use the mouse fine so its a problem with the configuration on my particular user. any ideas?

---

### Post by JBAlaska on 2010-08-18
Cut and paste from [This](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727) bug report:

To bring your touchpad back to life, enter the following command:

```
gconftool --type bool --set /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```

The key "/desktop/gnome/peripherals/touchpad/touchpad_enabled" is where gnome-settings-daemon remembers that you disabled your touchpad. This is the reason, why it is disabled even after a reboot.

The issue will re-appear, next time you disable your touchpad. You need to prevent gnome-settings-daemon from disabling your touchpad in the first place, because the Synaptics touchpad driver does this already. To do so, run the following command in a terminal:

```
gconftool-2 --type string --set /apps/gnome_settings_daemon/keybindings/touchpad ""

```

This dissociates the key to lock your touchpad from gnome-settings-daemon. If for any reason, the latter command breaks the lock touchpad support for you, than you probably have a different issue. To re-associate the key with gnome-settings-daemon, run this command:

```
gconftool-2 --type string --set /apps/gnome_settings_daemon/keybindings/touchpad XF86TouchpadToggle
```

---

### Post by oomar on 2010-08-18
that worked! Thank you so much!

---

### Post by chips24 on 2010-08-18
hey, i have the same problem, along with a whole bunch of other ones!!):P):P

---

### Post by Ampi on 2010-08-19
So you solved it with the help in this thread or do you need help? :)

---

