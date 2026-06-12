---
title: "Ubuntu resolution"
date: 2009-10-24
forum: General Help
---

### Post by falven on 2009-10-24
Hello,
I just installed Ubuntu on Windows, it installed fine, when i logged in the resolution and colors were really messed up so i went to change the resolution, I saw really weird resolutions, so i picked 800X600 thinking it was because i need to download my video card drivers, and then my screen says no support. Please help me fix this, I have been searching for hours...

---

### Post by cowboy7305 on 2009-10-24
i had a problem ages ago and i was told to do this
Reboot using your HD (i.e. not using LiveCD), then...

If you used System -> Preferences -> Screen resolution:
Press Alt+F2
Enter: gnome-display-properties
You can use Alt+Left click to move the window around

If you used randr:
Press Alt+F2
Enter: gnome-terminal
You can use Alt+Left click to move the window around
Enter: sudo xrandr -s 1280x800
Enter: your_password
no idea if this helps 
but it might

---

