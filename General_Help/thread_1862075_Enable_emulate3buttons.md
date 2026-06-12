---
title: "Enable emulate3buttons?"
date: 2011-10-16
forum: General Help
---

### Post by temp4746 on 2011-10-16
There doesn't seem to be any option what so ever to enable the emulate3buttons feature in Ubuntu 11.04 or 11.10
gpointing-device-something doesn't remeber it's settings and as such broken (It doesn't even get added to the dash when using Unity...)
xorg.conf is no more...
And searching doesn't give any help on how to enable this.

---

### Post by temp4746 on 2011-10-17
I'm reallu wondering how to achive this, I can't find any guides that work.
Oh I'm running Ubuntu under VirtualBox if it matters.
 
Seriously why isn't this just a setting in the mouse properties...

---

### Post by Piacj on 2011-10-17
...

---

### Post by temp4746 on 2011-10-17
> **Piacj said:**
> ...
That's not very helpful you know...
 
Please help me... :(

---

### Post by Piacj on 2011-10-17
> **temp4746 said:**
> That's not very helpful you know...
 
Please help me... :(

Sorry. I was going to suggest using gpointing-device-settings (which works okay here), but then I read that you'd already tried that. 

Anyway, the bug is already [reported]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/874237") so hopefully it will be fixed soon.

---

### Post by temp4746 on 2011-10-17
> **Piacj said:**
> Sorry. I was going to suggest using gpointing-device-settings (which works okay here), but then I read that you'd already tried that. 

Anyway, the bug is already [reported]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/874237") so hopefully it will be fixed soon.
Yeah gpointing-device-settings can enable it but it's not persistent see this [BUG]("https://bugs.launchpad.net/ubuntu/+source/gpointing-device-settings/+bug/489830"), add to that that it's [not appearing in the dash]("https://bugs.launchpad.net/ubuntu/+source/gpointing-device-settings/+bug/876852"). It's pretty broken. And since even generating a xorg.conf and adding it to it doesn't work it's quite broken.

They should still really add this setting to the standard gnome settings menu for the mouse.

---

