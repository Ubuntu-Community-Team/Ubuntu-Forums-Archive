---
title: "does Ubuntu have an equivalent to &quot;Ctrl+Alt+Delete&quot;"
date: 2009-11-16
forum: General Help
---

### Post by Gatorade on 2009-11-16
when a program freezes up in windows and you do "Ctrl+Alt+Delete" to force quit the program.

is there any way to do that in Ubuntu?

---

### Post by dyous87 on 2009-11-16
Right click on your panel, click "Add to panel" and add the "Force Quit" icon. When a program is not responding, simply click the force quit icon and then click the program window and it will force quit.

Regards,
David

---

### Post by HardcoreSSG on 2009-11-16
On XFCE (I hate gnome) you can get Xkill which force quits the program.
Or on gnome you can add the Force quit item to your panel.

---

### Post by Gatorade on 2009-11-16
> **dyous87 said:**
> Right click on your panel, click "Add to panel" and add the "Force Quit" icon. When a program is not responding, simply click the force quit icon and then click the program window and it will force quit.

Regards,
David

what do you mean by "right click on your panel" ?

where's that?

---

### Post by dyous87 on 2009-11-16
If you are running Ubuntu (gnome) right click on the panel at the top of the screen. The panel is the bar that has "applications, places, system etc). Just right click on an empty part of the panel with no icons. Then click on add to panel, and add the force quit icon.

---

### Post by Gatorade on 2009-11-16
thanks, I got it.

---

### Post by dyous87 on 2009-11-16
Glad I could help :D

Regards,
David

---

### Post by keplerspeed on 2009-11-16
ctrl-alt-delete does have functionality in ubuntu, it will bring up a logout/shutdown/restart menu. Alternatively, you could use the system>Administration>system monitor to kill a process, if you know what the process is called, or use kill or pkill in the terminal.

---

### Post by Faolan84 on 2009-11-16
There is a way to reboot your system if it is totally unresponsive, however, it is a last ditch to force your system to reboot and should never be used in a casual manner because "Bad Things (TM)" (data loss) can happen if this is done improperly.

Hold down ALT + Sys Rq and type with ten seconds between each letter: REISUB

This will cause the system to reboot immediately after hitting "B".

Under no circumstances do you ever skip the first five letters, they are crucial to process and doing so WILL result in definite breakage.

---

### Post by Gatorade on 2009-11-16
thanks for the info guys. it may come in handy one day.

Faolan, 

I hope I never comes across a situation where I need to use that method.

what about just holding the power button down 'til it powers off? I've done that before without damaging anything.

is that bad to do?

---

### Post by dcstar on 2009-11-16
> **Gatorade said:**
> 
........
what about just holding the power button down 'til it powers off? I've done that before without damaging anything.

is that bad to do?

[LIST=1]
[*]Risky
[*]Yes.
[/LIST]

System-Administration-System Monitor will allow you to see and kill all processes.

---

