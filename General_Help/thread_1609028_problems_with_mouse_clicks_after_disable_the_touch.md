---
title: "problems with mouse clicks after disable the touchpad, in ubuntu 10.10"
date: 2010-10-29
forum: General Help
---

### Post by bumblew84 on 2010-10-29
I have HP DV6 laptop. when i disable the touchpad, the mouse clicks doesn't respond anymore! and i need to restart the laptop :(

This happen to me in Ubuntu 10.04 and 10.10

Any solution? any workaround? Thanksss!

---

### Post by gufide on 2010-10-29
you should try to go to mouse preference. You use touchpad or a usb mouse? If you use touchpad, send my the name of. You should try to seach: model name of your mouse space ubuntu on google

---

### Post by bumblew84 on 2010-10-30
thanks for your answer, but doesn't is the mouse problem.

This is a gnome bug i think, and only hapend with some laptopts. No matter what mouse you use

---

### Post by opethfan89 on 2010-11-26
I experience the same problem on my HP dv7-3060US model laptop. If I plug in my logitech USB mouse and then disable the touchpad (using the button that is on it), Ubuntu will stop responding to my mouse clicks. I'm then forced to restart and keep the touchpad running (which is inconvenient if I'm typing and accidentally stroke the touchpad).

Does anyone have any more information on this?

---

### Post by anra78 on 2010-11-27
Same problem with my HP dv5 and Ubuntu 10.10. I just install the latest version after been using 8.1.4 version that hasn't this problem. If anyone knows what is this about, thanks !!!!

Good luck.

---

### Post by tanpopo_chan on 2011-02-21
I have a dv6-2145es, and I have the enable/disable button as well...
In my case the problem came from the key bindings which kept saving the off state as permanent.

This is how I fixed it.

First I opened a terminal and opened the configuration editor. That is, I opened a terminal and typed:
```
gconf-editor
```

Then, I navigated to **apps -> gnome_settings_daemon -> keybindings**.

Inside keybindings I looked for the value called **touchpad**.

Finally, I double-clicked on the value and left it blank. It should look something like this:
[[IMG]http://img580.imageshack.us/img580/5959/78488225.th.jpg[/IMG]]("http://img580.imageshack.us/i/78488225.jpg/")

Aaand, that's how I fixed mine! =D

---

