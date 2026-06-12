---
title: "Internet stopped working"
date: 2010-03-09
forum: General Help
---

### Post by Newbie456 on 2010-03-09
[FONT=Arial][SIZE=3]hi all. I took the courage yesterday  to install ubuntu 9.10. Internet was working absolutely fine (wireless), but brightness controls were not working (they still don't). So I went to this page *[https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)*, and ran following command(s)
**killall gnome-settings-daemon gnome-power-manager**
Now since then I cant get the internet working, and cant see the wifi connection on task bar. I have restarted the laptop but no avail.
Please help.

PS: any help on how I can reduce the brightness of monitor. I am using SONY VIAO VGN FZ38M, with Nvidia 8400M GT.
I have tried several threads and tried all sorts of things, like xbacklight, or somthing to do with sudo ... VGA/LCD/brightness... etc.

I'd really appreiciate any help, as this time I am determined to continue using ubuntu (well uptill now).

Thanks.[/SIZE][/FONT][SIZE=3]
Kaz[/SIZE]

---

### Post by nightwolf2k5 on 2010-03-09
Hi,

Right click on the task bar on top and add the "Notification Area" to your panel. That should sort out the network manager being displayed.

If that does not work, in your login screen, make sure that the session (which should be at the bottom) is set to Gnome and not Failsafe Gnome.

If that too does not work, try this link [http://ubuntuforums.org/showthread.php?t=1311790&page=2](http://ubuntuforums.org/showthread.php?t=1311790&page=2)

Hope it helps.

---

### Post by Newbie456 on 2010-03-10
Thanks mate,
The failsafe Gnome was some how selected by default.
Now working fine.:D

---

