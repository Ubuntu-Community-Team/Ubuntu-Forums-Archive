---
title: "I broke it :("
date: 2010-01-16
forum: General Help
---

### Post by New5teve on 2010-01-16
Im real new to ubuntu, and linux in general. I had finally go tmy netbook set up the way i wanted it, everything was working great. The notification popups were annoying me so i was trying to disable them. I used this string in a terminal:
[FONT=Courier New]sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled [/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]After rebooting i had nothing but a taskbar. :( No icons, no panels, nothing but wallpaper and the taskbar. I can't even figure out how to open up a terminal. Any help would be appreciated. Hopefully there is a way to load synaptics and reload the desktop somehow?[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]Some info about my system.[/FONT]
[FONT=Courier New]Acer aspire one with Ubuntu netbook remix. 9.04 install with 9.10 upgrade.[/FONT]
[FONT=Courier New]I usually load the gnome desktop enviornment. I also have KDE installed (i think)[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New][/FONT] 
[FONT=Courier New]Any help will be greatly appreciated.[/FONT]

---

### Post by Leppie on 2010-01-16
have you tried the run program function (ALT+F2)?
if you type xterm, it should open a terminal window

---

### Post by nerdy_kid on 2010-01-16
or hit <ctrl> <F1>
login
run
```

[FONT=Courier New]sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service[/FONT][FONT=Courier New].disabled [/FONT][FONT=Courier New]/usr/share/dbus-1/services/org.freedesktop.Notifications.service[/FONT]

```then
```

sudo reboot

```

---

### Post by New5teve on 2010-01-16
UPDATE: OK, i got my desktop loaded again, many thanks. Failed the first time and said not a directory or file. But i double checked the command and had a typo. It worked great and everything is loading fine... MUCH thanks nerdy_kid! You rock!

Now... is there any way to disable these silly annoying popup notification windows?

---

### Post by Leppie on 2010-01-16
there was a typo in that command:
```
[FONT=Courier New]sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service[/FONT][FONT=Courier New].disabled [/FONT][FONT=Courier New]/usr/share/dbus-1/services/org.freedesktop.Notifications.service[/FONT]
```

there was a space between .service and .disabled ;)

---

### Post by New5teve on 2010-01-16
I read somewhere to try:
sudo chmod -x /usr/lib/notify-osd/notify-osd
I'm going to give it a whirl and see what happens (crossing fingers)
Thanks to all that have helped. You guys are a blessing

---

### Post by nerdy_kid on 2010-01-16
> **Leppie said:**
> there was a typo in that command:
```
[FONT=Courier New]sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service[/FONT][FONT=Courier New].disabled [/FONT][FONT=Courier New]/usr/share/dbus-1/services/org.freedesktop.Notifications.service[/FONT]
```there was a space between .service and .disabled ;)

sorry :sad:

> **New5teve said:**
> MUCH thanks nerdy_kid! You rock!

thanks! :D

---

### Post by New5teve on 2010-01-16
For anyone else annoyed by the new ubuntu notifications.
sudo chmod -x /usr/lib/notify-osd/notify-osd
Worked great, it stops it. I'd not recommend using the command about notifications/services etc... It sucked, and did not work out for me at all, however i've seen several posts that depict that as the fix. Anyway, much thanks to everyone who helped me out here, this forum is worth a million bucks to anyone new to ubuntu.
                                                  -Steve

---

### Post by gradinaruvasile on 2010-01-16
i installed the old style notification-daemon, and linked its executable instead if notify-osd. Works like a charm.

---

