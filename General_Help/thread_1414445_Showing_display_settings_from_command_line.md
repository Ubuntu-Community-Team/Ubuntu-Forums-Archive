---
title: "Showing display settings from command line"
date: 2010-02-23
forum: General Help
---

### Post by riotboi on 2010-02-23
I'm sure this is a very simple task but I don't have a lot of experience with Linux.  I need to view what my display adapters settings are, specifically the refresh rate.  I have found plenty on how to change the settings but not how show its current setup. I am troubleshooting an vga splitter/extender issue on a digital signage unit where the master screen syncs up but the remote screen does not, I think it has to do with H-Sync V-Sync or refresh rate. Thanks in advance.

---

### Post by DaithiF on 2010-02-23
Hi, use
```
xrandr

```

example output ... showing my refresh rate is 60
```
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       60.0*+
   640x480        59.9  

```

---

### Post by riotboi on 2010-02-23
THANKS FOR THE REPLY!!
But.......I think I may be screwed. I think our version of Linux is stripped down for security and may not support that command.  I have tried that command but it comes back with "can't open display". I dunno

---

### Post by DaithiF on 2010-02-23
are you logged in remotely?  Your display environment variable doesn't seem to be set.
try:
```
DISPLAY=:0.0; xrandr
```

---

