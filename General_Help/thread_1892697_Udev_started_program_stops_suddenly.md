---
title: "Udev started program stops suddenly"
date: 2011-12-08
forum: General Help
---

### Post by mschot2 on 2011-12-08
I hope someone can help me,

I would like to run a program in the background every time I plug my usb ir remote controle receiver into my pc, as it remaps the keys of my cheap remote control into the keys I need it to be for boxee.

I managed to get the background script running with udev when i plug the usb deice in, but for some reason the script(and its parent udevd --deamon) stops after about a minute without any messages in /var/log/udev.

My udev rule is as follows:
```
ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="0755", ATTRS{idProduct}=="2626", RUN+="/usr/local/hid_mapper_beta/hid_mapper --manufacturer 0755 --product 2626 --map '/home/media/keymap' --lookup-id > /dev/null 2>&1 &"
```

when i run ```
/usr/local/hid_mapper_beta/hid_mapper --manufacturer 0755 --product 2626 --map '/home/media/keymap' --lookup-id > /dev/null 2>&1 &
``` straight from terminal it all keeps running just fine.

The program needs to be run as root but udev does this so I do not think it is a permissions thing. I find it just so strange that it stops after a minute or so..

I'm currently running ubuntu 11.10.

Any help or pointers would be much appreciated

---

