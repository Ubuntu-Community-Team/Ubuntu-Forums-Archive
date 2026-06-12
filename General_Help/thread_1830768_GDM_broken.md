---
title: "GDM broken"
date: 2011-08-22
forum: General Help
---

### Post by Darcy Rayner on 2011-08-22
Hi, I've had Ubuntu 11.04 installed on my desktop since it's release. Up until an hour ago, it was working fine. I clicked on an update from the update manager, now booting into a graphical mode is completely broken, (the start-up load hangs at 'Check Battery State ... [0k]'). I restarted my computer, and booted into safe mode, and launched the terminal. This all works fine. I then typed :
```
sudo gdm start
```into the command prompt, hoping that I would be able to start things manually. Instead, it spat out this:
```

gdm-binary[230]: WARNING: Unable to load file '/etc/gdm/custom.conf'. No such file or directory.
gdm-binary[230]: WARNING: Unable to find users : no seat-id found.
gdm-binary[230]: WARNING: Gdm Display: display lasted 0.070467 seconds

```The last line was printed about 8 times, with slightly different times, before it gave up and failed. Some information which might help, I have Gnome 2, Unity and KDE (not sure which version), installed. My graphics card is the GTX 275, and I have driver the Nvidia driver 275.21. So yeah, I think the update has gone and moved custom.conf somewhere, but I have no idea on how to fix it.  I have a graphics programming assignment due on Friday and I would be eternally grateful if I could get this fixed well before then.  Thanks.

---

### Post by ron999 on 2011-08-22
Hi
Using safe mode...
I suppose you need to make sure gdm is still installed OK:-
```
sudo apt-get install gdm
```

Then try to start it with this command:-
```
sudo service gdm start
```

---

### Post by Darcy Rayner on 2011-08-22
Hi, thanks for the reply. I've followed your method and tried to make sure that the install was okay. It seems to produce the same results though. I then went on to create a copy of a /etc/gdm/custom.conf from somebody else's machine, which managed to wipe out the first error line, but not the second. Here is what I used: ```
[daemon] 
  
 TimedLoginEnable=false 
 AutomaticLoginEnable=False 
 TimedLogin=<username> 
 AutomaticLogin=<username> 
 TimedLoginDelay=30 
 DefaultSession=gnome-classic 
  
 [security] 
  
 [xdmcp] 
  
 [gui] 
  
 [greeter] 
  
 [chooser] 
  
 [debug] 
  
 [servers]
```

Anyway, after that I tried to do a clean re-install of GDM, but the same error message still persists.

---

