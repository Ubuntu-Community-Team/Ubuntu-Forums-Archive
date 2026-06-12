---
title: "Lost screen borders and maximize/close icons"
date: 2010-07-30
forum: General Help
---

### Post by Quackers on 2010-07-30
Last night everything was fine and running normally.
When I booted up today all my windows have no borders and the maximize/minimize/close buttons are all gone! WTF? :o  Did somebody eat them?
I have read many threads with several fixes but none has worked for me :(
I have uninstalled emerald as I thought that may be the cause, but it's still the same.
Screen effects are still present (wobbly windows).
Any ideas would be good, thanks.

---

### Post by hhh on 2010-07-30
Did the Window Decorations plugin in Compiz get disabled accidentally? Also, try restarting Compiz (Alt+F2 to get the run dialog, then run "compiz --replace" w/out quotes).

---

### Post by Quackers on 2010-07-30
Thanks for the reply hhh.
I've tried a few terminal commands and some worked until I exited the terminal, then the top bar disappeared again.
The only thing that works permanently is to disable visual effects (in appearance). But that means my wobbly windows disappears :-)  Not ideal but a temporary workaround.

The compiz --replace instruction returned comments about no time stamp and somehting about "and therefore it sucks"  :-)
Actually thinking about it that may have been the metacity --replace instruction

---

### Post by dino99 on 2010-07-30
into console, try: metacity --replace

---

### Post by Quackers on 2010-07-30
Thanks dino99, but see recent edit above :-)

---

### Post by ricardo.gloe on 2010-07-30
What is your current WM? 

easy way to check is in Ubuntu Tweak>Startup>Session Control>Window Manager

Try changing the WM to "gnome-wm" and apply. Then load gnome-wm to the current session: Type "gnome-wm" in terminal.

Hope that works.

BTW, if it works, but doesn't save on next reboot, add command "gnome-wm" to Startup Applications.

---

### Post by Quackers on 2010-07-30
ricardo.gloe thanks a million :-)
After re-installing emerald and following your advice I now have my borders and top bar back :-):-):-)
Even on exit from terminal the top bar stayed there. If it disappears again later I'll follow the last part of your instructions.
BTW, what do you think happened?
Thanks again.

---

### Post by Quackers on 2010-07-30
Just to make sure I included gnome-wm in the startup applications then rebooted.
100% successful and I still have the wobbly windows :-)
Many thanks.

---

### Post by ricardo.gloe on 2010-08-02
After a lot of searching, I think I have found a solution.

Adding a window manager to startup applications (the famous compiz --replace or gnome-wm) is a bad fix, because you're probably replacing a system loaded window manager previously loaded with this command, after boot.) 

I haven't found the culprit, but I think it's either Wine, Playonlinux or an Nvidia update. 

Anyway, re-installing gnome-session and gdm seemed to have worked, because I have windows, borders and max/min buttons on boot and no compiz or gnome-wm in startup applications.

I'd love to know if by re-installing these two (and removing any commands to window-managers in startup applications) you also fix your problem.

---

### Post by Quackers on 2010-08-02
Thanks for the info ricardo.gloe.
Unfortunately I'm not on that laptop until tomorrow, but will loook into it. I haven't installed Playonlinux, but I do have Wine installed. I also have the recommended nvidia driver installed (via Hardware Drivers).

---

### Post by Quackers on 2010-08-02
Lol, maybe it wasn't as solved as I thought!
I just rebooted and on re-starting my borders were gone again! So I took out the gnome-wm from the startup applications and rebooted. Borders are now back again. Hmm, maybe I've not heard the last of this niggle yet :-)

---

