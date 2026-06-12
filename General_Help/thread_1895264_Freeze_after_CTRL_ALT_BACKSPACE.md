---
title: "Freeze after CTRL ALT BACKSPACE"
date: 2011-12-14
forum: General Help
---

### Post by hypertyper on 2011-12-14
I've enable the CTRL ALT BSP shortcut so I can easily restart X. Now "suddenly" when I try using it, my system gets stuck with no real error message. Initially I got a "disconnected from plymouth" error. Then I ran apt-get upgrade and update. I don't get the error message any more but the system doesn't get back to the desktop still.

I installed archlinux on a separate partition yesterday which was sharing swap space. I created new swap space now and changed fstab for xubuntu but that hasn't made any difference.

What's different between a normal boot and restarting X?

I don't understand xubuntu's boot sequence in terms of files it loads. Witch archlinux it's very obvious because you're in charge of it all. I don't know where xubuntu gets its configuration from which in this case I assume is the root of all evil.

If anybody can tell me the files to look at I'll see what I can do. I'll try take a pic of the screen where the system hangs.

I'm in a rush so it's uncropped...edit, thumbnail

[[img]http://www.abload.de/thumb/img_20111214_1730096djcw.jpg[/img]](http://www.abload.de/image.php?img=img_20111214_1730096djcw.jpg)

I can go to CTRL ALT F1 and type startx which gets me into a default xfce session, not my normal desktop. I'm so confused...

When I try to reconfigure lightdm this happens: (post research, I doubt this has to do with the problem)
```
seb@sebXubuntu:~$ sudo dpkg-reconfigure lightdm
[sudo] password for seb: 
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_NAME missing
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_PACKAGE missing

```

---

