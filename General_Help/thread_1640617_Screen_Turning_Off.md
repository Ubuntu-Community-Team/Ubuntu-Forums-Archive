---
title: "Screen Turning Off"
date: 2010-12-08
forum: General Help
---

### Post by ngcattell on 2010-12-08
I recently installed 10.10 and I have a problem with my screen dimming then going black after a few minutes of inactivity and asking for my password once i move the mouse.  This is very irritating when im watching videos and i need help in figuring this out.
I have tried going to system>pref>power management and changing the setting for putting the display to sleep when inactive to **never** but it still occurs.
What should i do?

---

### Post by idi0tf0wl on 2010-12-08
Open a terminal by navigating to Applications->Accessories->Terminal and type this exactly:
```
sudo dpkg-reconfigure xserver-xorg
```

Type your password when it asks you to and hit enter. Let it do its thing. When it's all said and done, reboot. Let us know how it went.

---

### Post by ngcattell on 2010-12-08
i entered it and rebooted but the problem still persists

---

### Post by tredegar on 2010-12-08
Check your "Screensaver" preferences.

---

### Post by wog on 2010-12-08
The default for screensaver is 5 minutes, and a fade-to-black screen. Try setting screensaver to the maximum (2 hours), and then uncheck "Lock screen when screensaver is active".

---

### Post by ngcattell on 2010-12-08
problem sloved thanks:)

---

