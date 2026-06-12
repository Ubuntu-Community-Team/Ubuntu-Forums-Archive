---
title: "Symlink wont delete"
date: 2012-06-18
forum: General Help
---

### Post by tez1982 on 2012-06-18
Strange one. I was setting up my IR receiver. I wanted to make it static, it's usb so sometimes jumps to different numbers in /dev/input

I used 

sudo ln -fs /dev/input/event$(cat /proc/bus/input/devices | grep -A 3 "em28xx IR" | grep Sysfs | sed -e "s/^.*\(.\)$/\1/") /dev/input/irremote

however irremote always points to the wrong device (for some reason it points to HDA HDMI device)

I've tried unlink and rm, also overwriting it with a new symlink. But whatever happens as soon as I reboot the old symlink appears pointing at the wrong device.

I tried creating a new symlink with

sudo ln -fs /dev/input/event$(cat /proc/bus/input/devices | grep -A 3 "em28xx IR" | grep Sysfs | sed -e "s/^.*\(.\)$/\1/") /dev/input/irusb

but again, as soon as I reboot the new symlink is gone and the old one pointing at the wrong device is back.

Am I missing something obvious, I can't seem to find anything via google.

thanks

---

