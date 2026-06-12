---
title: "updated to karmic and enabled compiz then freeze"
date: 2009-10-30
forum: General Help
---

### Post by nathang1392 on 2009-10-30
i updated to karmic and enabled compiz, and now every time i boot i freeze instantly. i know i can drop back into the terminal from grub, but i dont have any experience so i dont know actually what commands to use. im on an intel mobile graphics driver. anyone have any advice?

---

### Post by kerry_s on 2009-10-30
the intel drivers are still pretty useless, i have to use "xforcevesa" just to get to the gui. so i'm using the vesa driver right now.

---

### Post by nathang1392 on 2009-10-30
right now i cant really get to anything. as soon as i get the desktop i freeze. any ideas of how to get out of this predicament?

---

### Post by exploder on 2009-10-30
A clean install might have been a better option than upgrading because of all of the changes Karmic brings to the table. Unfortunately, upgrading tends to leave a lot of old config files all over the place. I have Intel graphics and desktop effects work fine for me. 

If you want to fix your upgraded install the first place to start looking is in Synaptic. Remove any residual config files that are present and proceed to check out your installed applications for problems. Turn off Compiz untill you are finished so your system does not lock up in the middle of anything. 

Purging Compiz and reinstalling it might help.

---

### Post by exploder on 2009-10-30
> right now i cant really get to anything. as soon as i get the desktop i freeze. any ideas of how to get out of this predicament?

Somehow you need to disable Compiz before the starts up. Try a forum search on this because I know it can be done.

---

### Post by nathang1392 on 2009-10-30
> **exploder said:**
> A clean install might have been a better option than upgrading because of all of the changes Karmic brings to the table. Unfortunately, upgrading tends to leave a lot of old config files all over the place. I have Intel graphics and desktop effects work fine for me. 

If you want to fix your upgraded install the first place to start looking is in Synaptic. Remove any residual config files that are present and proceed to check out your installed applications for problems. Turn off Compiz untill you are finished so your system does not lock up in the middle of anything. 

Purging Compiz and reinstalling it might help.


oh that was actually a typo, i didnt actually upgrade, i just installed. sorry.

---

### Post by exploder on 2009-10-30
> oh that was actually a typo, i didnt actually upgrade, i just installed. sorry.

No problem. I would still try and turn off Compiz so you can get to the desktop and go from there. What graphics card are you using?

---

### Post by nathang1392 on 2009-10-30
Intel® Graphics Media Accelerator X3100, thats what i got from the site. i it doesnt make sense let me know and i will try to find it again.

---

### Post by kerry_s on 2009-10-30
> **nathang1392 said:**
> right now i cant really get to anything. as soon as i get the desktop i freeze. any ideas of how to get out of this predicament?


i haven't figured out, how to access the rescue mode yet, i had to use the live session.

use the live to add "Driver "vesa"" to your xorg.conf, that should automatically disable effects.
from the live session press **alt+f2**, type-> **gksudo nautilus /**
make your way to /etc/X11/xorg.conf

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by 5nak3 on 2009-10-31
I have no idea if this will work, I didn't really understand where you get stuck.

But if you can get to the gdm screen if you press ctrl+alt+f1 it should take you to a terminal screen. From there i think if you login and then type "metacity --replace" then press ctrl+alt+f7 you should be able to use your PC with metacity as opposed to compiz.

This will give you access to a gui so you can try and solve the problem.

Another thing that helped me was adding "compiz --replace" to my startup applications. Before I did that I could log in with metacity, but compiz would not load, so i had to invoke it at startup to get my wobbly windows.

Sorry if this is not of any use to you, just thought maybe this may be of interest.

---

### Post by artheon on 2009-11-02
I seem to be having the same problem. I can log in normally, and the system continues to work (time keeps getting updated and the mouse pointer moves), but as soon as I click any icon or something like that, everything freezes. To me, it appears to be compiz. When I start a failsafe GNOME session everything works.

To do that: start up, login screen appears, click username, some options appear at the bottom of the screen from which you select session: failsafe GNOME 

Hope this helps.

---

### Post by artheon on 2009-11-02
> **5nak3 said:**
> 
... Sorry if this is not of any use to you, just thought maybe this may be of interest.

Your post was helpful for me. Thank you.

---

### Post by nathang1392 on 2009-11-03
well originally everyhting was fine. i downloaded compiz settings manager and enabled reflection, as soon as i clicked it instant freeze. i have been trying to experiment. if i go into recovery mode at grub i can drop to the terminal as root. if i type startx i go into a working desktop. i tried to go change what i messed up, but as soon as i reboot into the normal install it just loads and as soon as its about to show the desktop everyhting freezes and i have to hold power to get out.

---

### Post by artheon on 2009-11-03
For me, a useful workaround was the suggestion of 5nak3: log in, strike ctrl-alt-F1 to go to a terminal, and type "metacity --replace" then press ctrl+alt+f7 you should be able to use your PC with metacity as opposed to compiz. Next, I turned off all desktop effects. Everything works now, except for everything that relies on compiz, of course. I don't really care about compiz anyway, so I'm just going to wait until this is sorted out. I'll try to check regularly to see if I have something useful to add. Greetings.

---

### Post by locketine on 2009-11-03
the metacity --replace command was giving me a "unable to access xwindows" but then I found this command which worked. I might have added a sudo in there as well, I'm not sure.

```
metacity --replace & killall compiz compiz.real
```

---

### Post by locketine on 2009-11-04
> **nathang1392 said:**
> i updated to karmic and enabled compiz, and now every time i boot i freeze instantly. i know i can drop back into the terminal from grub, but i dont have any experience so i dont know actually what commands to use. im on an intel mobile graphics driver. anyone have any advice?

Hey, I had the same problem and apparently it was caused by dual displays. All I had to do was disable the other display and then manually start compiz. It worked fine, so I rebooted and guess what? No freezing.

---

### Post by Syam on 2009-11-18
I had the same problem after enabling reflection plugin. I had to login via failsafe-gnome and disable reflection.

---

### Post by moloth on 2009-11-20
Yes! That fixed my foxcon 45csx that was freezing after booting. Hope they fix that intel driver soon.

Anyway I did this:

Ctrl-Alt-F1 -> logged in -> killall compiz compiz.real
Ctrl-Alt-F7 -> Terminal -> metacity --replace

All sorted!

---

