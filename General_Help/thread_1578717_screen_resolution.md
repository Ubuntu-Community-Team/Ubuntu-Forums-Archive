---
title: "screen resolution"
date: 2010-09-20
forum: General Help
---

### Post by Hal9002 on 2010-09-20
Hi
I've been having a problem with screen resolution. It won't go above 800x600. Can anyone help me with this?

---

### Post by crichard on 2010-09-20
Make sure you installed your Graphics drivers.....
System -> Administration -> Hardware Drivers

---

### Post by efflandt on 2010-09-20
You have to provide some info if you want help.

What video chip (output from **sudo lspci -v** related to it)?

Are you using default video or proprietary drivers?

What type of monitor and native resolution.  And how is it connected (guessing VGA, because DVI or HDMI are usually more automatic, at least with default drivers)?

You can test different video modes in X using **xrandr** command, at least for default video drivers, with modelines you get from **gtf** or **cvt**.  [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

