---
title: "Problem wIith Desktop Effect"
date: 2009-09-04
forum: General Help
---

### Post by t4ggs on 2009-09-04
I have an inspiron 1245 with intel 4500 HD grafic chip and has been working perfectly in jaunty till now, i dont know why suddenly compiz stop working and when i try enablen desktop effects it says: "desktop effects could not be enabled"  dont know what is the problem....any help would be most appreciated

---

### Post by t4ggs on 2009-09-04
I dont know if this is any help...this is the output of compiz

```
ytagger@ytagger-laptop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1No kernel support for execution fencing, disabling texture tiling
Comparing resolution (1366x768) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: No kernel support for execution fencing, disabling texture tiling
present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0



```

---

### Post by nbtrap on 2009-09-04
Do you have the appropriate drivers installed? Go to System >> Administration >> Hardware Drivers. Try uninstalling them and reinstalling, then restarting. If that still doesn't work, assuming you're on gnome, delete the gnome configuration folder at /home/<name>/.gnome2 (beware, this will revert your desktop to how it looked when you first installed the OS).

---

### Post by nbtrap on 2009-09-04
Actually ignore the part about the drivers. Just delete the configuration folder. It looks like you have the drivers.

Then restart, or I think it'll work if you just log out and back in.

---

### Post by nbtrap on 2009-09-04
Scratch that. You want to delete the folders /home/<name>/.gconf and /home/<name>/.gconfd if it exists. Sorry. After you do so and log out and back in, you should be able to enable the effects if your drivers are installed.

---

### Post by t4ggs on 2009-09-04
thanks mate, it worked....could u please explain me why it worked and suddenly stoped? and why erasing those files helped?? thanks again

---

### Post by nbtrap on 2009-09-04
Well, to pinpoint exactly what was wrong would be impossible without looking at the configuration files in that folder. But I CAN tell you that, as you probably saw, deleting those folders restored your desktop settings to their defaults and, therefore, got rid of whatever was causing the problem. Sorry I can't really help you more. At least you got it working huh?

---

### Post by t4ggs on 2009-09-05
well thanks anyway

---

