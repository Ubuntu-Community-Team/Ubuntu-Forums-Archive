---
title: "Desktop environment freeze after login"
date: 2011-03-19
forum: General Help
---

### Post by torsades on 2011-03-19
Here is my problem:

My ubuntu 10.10 desktop environment freezes at right after login, with the window prompt to "unlock keyring" in the foreground. The cursor still can be moved around the screen with the touchpad or mouse. Mouseover of Docky elicits the usual animation but there is no response to clicking it. There is no other response elicited from moving the mouse over or clicking anything else on the screen, including the taskbar and the hot corners i have set up. However the screen still goes dim and to sleep when left unattended and can be reawoken. The netbook also still recognises when it is plugged into a power source.

Background info: 

I have been dual booting windows 7 starter and ubuntu 10.10 desktop edition for about 2 months now on my ASUS eeepc1005pe netbook with no issues till now. The problem only started when i booted up into windows 7 starter without having shut down ubuntu completely. My netbook was hibernating when i mistakenly chose to boot into win 7 starter at the bootloader. Now this freeze happens every single time i try to boot into ubuntu. But i am still able to boot into win 7 starter without any problems. 

The same sequence of events occurs each time i try to start ubuntu. The boot goes fine, then the automatic login occurs, then compiz loads fine then my desktop environment appears with all the same windows and programs open on the desktop as the last time i had managed to use ubuntu except that the keyring login prompt appears in the foreground and then everything freezes as i have described.

Any help in solving this problem would be greatly appreciated because i really cannot stand win 7 starter and i want to be able to use ubuntu again. Thanks!

---

### Post by torsades on 2011-03-20
Bump!

Anybody? I'm desperate to get ubuntu working again. If only there was a keyboard shortcut to a task manager to kill rouge processes like control+alt+delete in windoze. If i force shut down the frozen netbook the same desktop appears and freezes when i restart, the same programs open and the same freeze occurs. Please help!

---

### Post by Krytarik on 2011-03-20
Please try this:
- boot into "recovery mode"
- choose "root shell prompt"
- remove your "saved-session":
```
rm /home/USERNAME/.config/gnome-session/saved-session/*
```
- reboot with Ctrl+Alt+Del

---

### Post by torsades on 2011-03-20
Thank you SOOO much, works like a charm! I am extremely grateful!
This problem must have occurred because i booted up into windows while ubuntu was still hibernating. I'll make sure i dont do that again.
Thanks!

---

### Post by Krytarik on 2011-03-20
Great that it worked! :D

You're welcome!

---

### Post by QLee on 2011-03-20
[QUOTE=torsades]... 
If only there was a keyboard shortcut to a task manager to kill rouge processes like control+alt+delete in windoze.
...[/QUOTE]
Next time you want something like that there is something similar. If you still had kbd access you could do Alt+F2 and run gnome-system-monitor and have a look at the Processes tab where there is an  End Process button for GUI ending of a process.

---

### Post by Krytarik on 2011-03-20
> **QLee said:**
> Next time you want something like that there is something similar. If you still had kbd access you could do Alt+F2 and run gnome-system-monitor and have a look at the Processes tab where there is an  End Process button for GUI ending of a process.
I'm afraid that would not have been fast enough in this case.

---

