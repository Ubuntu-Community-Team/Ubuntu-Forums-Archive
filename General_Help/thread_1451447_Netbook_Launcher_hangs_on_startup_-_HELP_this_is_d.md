---
title: "Netbook Launcher hangs on startup - HELP this is driving me NUTS!!!"
date: 2010-04-10
forum: General Help
---

### Post by samirotiv on 2010-04-10
Hi everybody,
I'm a pro Windows user, but I'm kinda new to Linux/Ubuntu.

I've installed Ubuntu Netbook Remix on my notebook and I've having terrible hiccups. When I boot the notebook, it comes to the login screen and I login, and all is well so far.

After the login animation, it shows me my wallpaper, and the top panel, and the netbook-launcher is just launching when a portion of the screen turns white - like it's hanged. I press Ctrl+Alt+F1, Alt+F4 and Alt+F2 but with no luck. The only way out of this is a cold reboot(pressing the power button for 4 seconds). After a number of reboots, it logs in.

I don't know if this helps or if it has anything to do with the problem, but I added Pidgin to the startup applications a few days back.

This is really driving me insane. I'd appreciate all the help I can get.

Samir.

[IMG]http://img386.imageshack.us/img386/7613/dsc04130v.jpg[/IMG]

---

### Post by samirotiv on 2010-04-11
Bump - Pleeease help..!!..I can't get any work done:(

---

### Post by Sin@Sin-Sacrifice on 2010-04-11
Cold reboots = bad. Try ctrl+alt+SysRq+REISUB for lockups. For the screen have you tried xfix? Bare with me because I haven't used this stuff in a while but you can reboot into recovery mode and there should be an option to run xfix. If not you can load the root terminal and run ```
Xorg -configure
```

---

### Post by samirotiv on 2010-04-11
Thanks for replying, I got into 'Failsafe GNOME', and I pressed Alt+F2 and opened up Google Chrome to see this. BTW What is REISUB?? I'll just try out the 2 commands you put in.

BTW do I run xorg --configure from the normal desktop or from recovery mode??

Samir.

---

### Post by Sin@Sin-Sacrifice on 2010-04-11
You can't run the Xorg command from a GUI. You have to run it from a command line interface. If you reboot into recovery mode (listed in grub right under your normal boot kernel) you can "Drop to root shell" and run it. REISUB are the letters on your keyboard. While holding ctrl+alt+SysRq press each letter in that order. I also forgot to mention it's the right ctrl and alt buttons.

---

### Post by samirotiv on 2010-04-11
Oh I thought that was a typo. I'll try it out in the evening. I'm not sure I know how to 'drop to a root shell' but I'll try and figure it out.

Thanks again,

Samir.

PS. I don't have a right control key on my notebook keyboard :(

---

### Post by samirotiv on 2010-04-11
I just tried it out. I'm afraid there's no such command:(.

Thanks again for the hotkey. Can you tell me exactly what it does??

---

