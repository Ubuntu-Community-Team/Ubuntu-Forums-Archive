---
title: "disable keyboard in x"
date: 2011-02-20
forum: General Help
---

### Post by stevezau on 2011-02-20
Hi All,


XORG is detecting my keyboard as shown in the xorg log below..


Is there some way i can disable this keyboard?? I've been searching for hours on how to create a udev rule but everything ive tired does not work.


```

[    20.822] (II) config/udev: Adding input device Leadtek WinFast DTV Dongle Gold (/dev/input/event2)
[    20.822] (**) Leadtek WinFast DTV Dongle Gold: Applying InputClass "evdev keyboard catchall"
[    20.822] (**) Leadtek WinFast DTV Dongle Gold: always reports core events
[    20.822] (**) Leadtek WinFast DTV Dongle Gold: Device: "/dev/input/event2"
[    20.900] (II) Leadtek WinFast DTV Dongle Gold: Found keys
[    20.900] (II) Leadtek WinFast DTV Dongle Gold: Configuring as keyboard
[    20.900] (II) XINPUT: Adding extended input device "Leadtek WinFast DTV Dongle Gold" (type: KEYBOARD)
[    20.900] (**) Option "xkb_rules" "evdev"
[    20.900] (**) Option "xkb_model" "pc105"
[    20.900] (**) Option "xkb_layout" "us"
[    20.900] (**) Option "xkb_options" "lv3:ralt_switch"

```

---

