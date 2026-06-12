---
title: "Problem with X Server on bootup."
date: 2006-01-26
forum: General Help
---

### Post by DAXP on 2006-01-26
I tried installing the nVidia drivers in [this HOWTO.]("http://www.ubuntuforums.org/showthread.php?t=75074&highlight=howto+nvidia") I got to the part that required restarting the X Server. I did so, and the PC froze. After restarting, everything is normal up to the loading screen, before the log in screen. At that point the screen flickers between a black screen saying something like:

Ubuntu 5.10 Login
Username:

and a white screen with the nVidia logo. After a while another thing pops up, saying it can't be loaded and asks if I want to see a debug/output file. Don't really know what to do with that, though. =/ 

Any ideas on what to do?

---

### Post by xmastree on 2006-01-26
Are you familiar with terminal commands? Ctrl-Alt-F1 and login, then run ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf
```And change the line in the Device section from nvidia to either **nv** or **vesa**. That ought to get you back into your desktop.

Actually, if you backed up your xorg.conf in the first place you could restore it again.```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.nvidia
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
``` and restart the x server.
That'll put you back to where you were before you broke it. :rolleyes:

---

### Post by DAXP on 2006-01-26
Alright, I'm going to print that and try it. Hopefully when I post again I'll be in Ubuntu.

EDIT: The first command didn't work, said the directory didn't exist or something similar. Second command gave me a blank text file. Before this I know the files were there, however...and I don't think I backed it up, I just followed the directions for method 1 in that HOWTO.

EDIT2: Just decided to reinstall Ubuntu. Had a few other problems, thought this would get rid of all of them. It did. Thanks for trying to help, though. It's very much appreciated.

---

### Post by xmastree on 2006-01-26
[QUOTE=DAXP]EDIT: The first command didn't work, said the directory didn't exist or something similar. Second command gave me a blank text file.[/quote]Both of these symptoms suggest that you were in the wrong directory. Since you've started over, we'll never know...
> Thanks for trying to help, though. It's very much appreciated.You're welcome, and I'm glad you got it fixed.

---

### Post by Icefox on 2006-01-26
Visit [http://icefox.info](http://icefox.info)

---

