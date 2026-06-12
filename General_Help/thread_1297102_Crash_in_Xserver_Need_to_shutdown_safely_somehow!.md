---
title: "Crash in Xserver? Need to shutdown safely somehow!"
date: 2009-10-21
forum: General Help
---

### Post by zarthon on 2009-10-21
Help! 
My computer is still running but my screen went blank all of a sudden and now I have no signal to the montior at all. I tried to access the tty / alt-F keys to no avail.
I *REALLY* want to shutdown cleanly because I am running a system with lvm volumes on top of software raid (mdadm). I don't want to risk corrupting my system.... but if their is no other way I will have to do a hardware reset.
If anyone knows of a system monitor that can detect catastrophe and automatically shut down?

I thought that it might have been the Xserver that carshed but now I believe it may be the graphics drivers?
Next i tired to access my workstation for my laptop but I could not ping it. I am not sure i am remembering the correct ip address. 
My latop is currently running windows xp. I can reboot it into ubuntu to solve the situation, and use wireshark to see what the IP address is or see if there is no activity. I believe ahavi and a bunch of firefox windows and tabs must be generating a little traffic.

I have never seen this with linux as far as I can remember. That might be because maybe i just don't push like i was just doing. 
Anyway I'd test this again if it were not so risky!

I have had a stable X-server configuration for some time. I have tried everything I can think of! I was using rdesktop and had recently set gnome to use 4 desktops and a desktop changing effect. I was, at the time, positioning a big rdesktop window to be on the edge of the screen. I usually never make my rdesktop window as wide as my screen which is 1920x1200 but this time i went for 1920x1080 to see if it would increase my productivity any.

---

### Post by zarthon on 2009-10-21
No network activity . The kernel must have bit it ! If anyone has ideas about how to troubleshoot and report bugs I'd follow through on it. I am going to just reset.

---

### Post by jimbauwens on 2009-10-21
Take a look at this :[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

