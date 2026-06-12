---
title: "Keyboard acting weird AFTER log in in Lucid"
date: 2010-08-12
forum: General Help
---

### Post by NormInNorman on 2010-08-12
I've been using Lucid for a couple of months and my keyboard has always worked fine. now, after one of the updates in the past week my keyboard has started acting flaky. It works normally to log in, but after I am logged in it won't recognize a key press until after holding down on it for a second. That makes it a bit hard to use. When I disconnect/reconnect it starts working, but that is really a pain in the **** and doesn't fix the problem. When I log out an log back in again it starts flaking out again. So far I've tried:

[LIST]
[*]Turning it off and on again (thanks IT crowd)
[*]Removing the keyboard from the hub in the monitor and hooking it directly to the back of the computer
[*]Using a different keyboard
[*]Changing USB ports
[*]Booting into low graphics mode
[*]changing my evdev.conf file like explained [here]("http://blog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/")
[*]Reinstalling ubuntu-desktop and gdm as explained [here]("http://ubuntuforums.org/showthread.php?t=1481718")
[*]Slamming keyboard on the desk repeatedly
[*]Cursing at Ubuntu
[/LIST]

None of those worked, so I created another user account on the machine. Guess what? It works fine for that account. So evidently there is something wrong with my user directory. I tried unchecking every single thing in my "Startup Applications" and ... still the same thing. So now I don't know what to do besides re-creating my account from scratch. Everything is about how I like it, so I really don't want to do that. Besides, that seems like a really Windows type of thing to do.

So any other ideas on how to debug this? I've wasted more than half a work day on this and I'm growing tired of looking at it.

---

### Post by dabl on 2010-08-12
Is Bluetooth running there?  Do you need it?  Just guessing here ...

---

### Post by NormInNorman on 2010-08-12
> **dabl said:**
> Is Bluetooth running there?  Do you need it?  Just guessing here ...

No bluetooth adapters are on the machine. It's a Dell Precision T7400 if that helps. It's a fairly vanilla machine, although it does have a firewire port.

---

### Post by dabl on 2010-08-12
I would run top or htop and take a look at the running processes, while the flakiness is happening.  Then, for comparison, log out and log in as the other user, and do the same there.  Maybe you can spot something sucking up CPU cycles, or accessing the USB bus all the time, or something like that.

I assume you've run ```
lsusb
``` and everything looks normal?

---

### Post by NormInNorman on 2010-08-12
Thanks for the idea. I just tried looking but I can't really see anything using more than 1% of the CPU at any time. None of it seems out of the ordinary, but I'm not THAT advanced of a user that I recognize all the processes. I might try switching back and forth a bit more.

lsusb doesn't look weird I guess. I'm assuming "Dell Computer Corp." is my keyboard.

That reminds me, I did see something a bit weird in my xorg log. Or maybe it's normal, I wouldn't know:

```
(II) config/udev: Adding input device Dell Dell Multimedia Pro Keyboard (/dev/input/event4)
(**) Dell Dell Multimedia Pro Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Dell Dell Multimedia Pro Keyboard: Applying InputClass "Dell Dell Multimedia Pro Keyboard"
(**) Dell Dell Multimedia Pro Keyboard: always reports core events
(**) Dell Dell Multimedia Pro Keyboard: Device: "/dev/input/event4"
(II) Dell Dell Multimedia Pro Keyboard: Found keys
(II) Dell Dell Multimedia Pro Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell Multimedia Pro Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Dell Dell Multimedia Pro Keyboard (/dev/input/event5)
(**) Dell Dell Multimedia Pro Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Dell Dell Multimedia Pro Keyboard: Applying InputClass "Dell Dell Multimedia Pro Keyboard"
(**) Dell Dell Multimedia Pro Keyboard: always reports core events
(**) Dell Dell Multimedia Pro Keyboard: Device: "/dev/input/event5"
(II) Dell Dell Multimedia Pro Keyboard: Found absolute axes
(II) Dell Dell Multimedia Pro Keyboard: Found keys
(II) Dell Dell Multimedia Pro Keyboard: Configuring as mouse
(II) Dell Dell Multimedia Pro Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell Multimedia Pro Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) Dell Dell Multimedia Pro Keyboard: initialized for absolute axes.
```

I find the "Configuring as mouse" sort of weird. It has a volume "wheel" on it, so maybe that is it. None of that probably matters though because it happens with another plain jane keyboard too.

---

### Post by dabl on 2010-08-12
The X configuration should be the same for all users.  The fact that it doesn't go flaky for the other user points to a configuration "setting" in your user directory -- one of those zillion hidden "dot" files and folders. I don't know how to tell which one it might be, except for some difference in the running processes when you are logged in.

The quickest (and most Windows-like) fix would be to nuke everything that starts with a dot in your user home folder, and then log in again.  Of course you'll lose every custom setting by doing that.

---

### Post by NormInNorman on 2010-08-12
Yeah, I just looked and there are about 75 configuration files/folders (at the top level at least). I may try moving them all somewhere then systematically moving them back until things break again.

This wouldn't make any sense to me, but one thing I have changed from the defaults is my keyboard shortcuts. I like using the windows keys for moving between workspaces and stuff like that. I think I'll try figuring out which files those are stored in and start with them. What doesn't make sense to me about it though is after re-plugging in the keyboard those shortcuts work fine.

---

### Post by NormInNorman on 2010-08-16
IT'S FIXED!

I've been messing around with FreeNX and danged if I wasn't having the same problem after I logged into a completely separate session remotely.  Well, after a loooooong afternoon of removing configuration files, logging off then back on and testing the keyboard I FINALLY got my keyboard to work.  I don't know exactly what the problem was, but it resides in the "~/.gconf/desktop/gnome/accessibility" directory. With it gone, things are now working fine. I guess some update must have messed with something in that directory because I've never knowingly changed any accessibility settings.  Anyway, I'm just glad it's fixed.

dabl, thanks for the help!

---

