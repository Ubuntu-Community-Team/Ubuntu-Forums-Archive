---
title: "Chromium crashes then ubuntu logs out when scrolling"
date: 2010-12-19
forum: General Help
---

### Post by EienTatsu on 2010-12-19
Sometimes when I scroll down certain pages using chromium it crashes then the screen turns black and i am presented with the log in screen. I think this is X crashing but I'm not sure. Can someone please help me because this is very very aggravating.

---

### Post by wojox on 2010-12-19
What version of Ubuntu and Chromium are you using?

How did you install Chromium? (ppa, repo's, website...)

---

### Post by EienTatsu on 2010-12-19
> **wojox said:**
> What version of Ubuntu and Chromium are you using?

How did you install Chromium? (ppa, repo's, website...)

I'm using Ubuntu 10.10. The latest beta release of chromium through the beta ppa. But originally I had installed it through the package manager and had the same problem so it's not because of the beta release.

---

### Post by wojox on 2010-12-19
> **EienTatsu said:**
> I'm using Ubuntu 10.10. The latest beta release of chromium through the beta ppa. But originally I had installed it through the package manager and had the same problem so it's not because of the beta release.

How about any other browser's? Firefox for instance.

Try running chromium from the terminal:

```
chromium-browser
```

Then surf around and see if it gives you any indication. Also look in /var/log/Xorg.0.log

---

### Post by EienTatsu on 2010-12-19
> **wojox said:**
> How about any other browser's? Firefox for instance.

Try running chromium from the terminal:

```
chromium-browser
```

Then surf around and see if it gives you any indication. Also look in /var/log/Xorg.0.log
It's hard to cause so I'm not positive but I think it only happens in chromium. Calling from terminal problem still occurs

Surf around? if x crashes I can't see the terminal output.

---

### Post by wojox on 2010-12-20
Look in /var/log/Xorg.0.log

---

### Post by EienTatsu on 2010-12-20
These are the last lines of the log file
any ideas?

```
[174934.220] (II) XINPUT: Adding extended input device "btnx keyboard" (type: KEYBOARD)
[174934.220] (**) Option "xkb_rules" "evdev"
[174934.220] (**) Option "xkb_model" "pc105"
[174934.220] (**) Option "xkb_layout" "us"
[174934.220] (II) config/udev: Adding input device btnx keyboard (/dev/input/js0)
[174934.220] (II) No input driver/identifier specified (ignoring)
[174934.220] (II) config/udev: Adding input device btnx mouse (/dev/input/event7)
[174934.220] (**) btnx mouse: Applying InputClass "evdev pointer catchall"
[174934.220] (**) btnx mouse: always reports core events
[174934.220] (**) btnx mouse: Device: "/dev/input/event7"
[174934.280] (II) btnx mouse: Found 20 mouse buttons
[174934.280] (II) btnx mouse: Found scroll wheel(s)
[174934.280] (II) btnx mouse: Found relative axes
[174934.280] (II) btnx mouse: Found x and y relative axes
[174934.280] (II) btnx mouse: Configuring as mouse
[174934.280] (**) btnx mouse: YAxisMapping: buttons 4 and 5
[174934.280] (**) btnx mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[174934.280] (II) XINPUT: Adding extended input device "btnx mouse" (type: MOUSE)
[174934.280] (II) btnx mouse: initialized for relative axes.
[174934.280] (II) config/udev: Adding input device btnx mouse (/dev/input/mouse1)
[174934.280] (II) No input driver/identifier specified (ignoring)
```

---

### Post by EienTatsu on 2010-12-21
I don't mean to be a pest but this is seriously bothering me. :(

---

### Post by EienTatsu on 2011-02-27
Anyone else experiencing this

---

