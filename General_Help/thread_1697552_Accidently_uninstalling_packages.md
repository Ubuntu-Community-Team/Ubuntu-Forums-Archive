---
title: "Accidently uninstalling packages"
date: 2011-03-01
forum: General Help
---

### Post by Zalib on 2011-03-01
OK so while I was uninstalling some packages that I didn't want I guess I uninstalled almost all of the basic packages that come with kubuntu when you install it. Stuff like system settings, dolphin, konsole, the media players. I was wondering if there is a basic package out there that I can install without getting each one individually because I might miss something. Please help I can't really do much with kubuntu right now.

---

### Post by zenwalker on 2011-03-01
I didnt understand whats exactly your looking for. 

All packages in one or the other way dependent. So use package manager to resolve this.

---

### Post by ankspo71 on 2011-03-01
Hi,
The package you need to reinstall is called kubuntu-desktop.

If you don't have a working package manager installed, and since konsole got removed, use the following advice:

Press Ctrl+Alt+F2 (press Ctrl+Alt+F7 to come back to the desktop if needed)
Log into the terminal window with your username and password.
then use this command:
```
sudo apt-get install kubuntu-desktop 
```

If it says it is already installed, add the --reinstall option to the end to reinstall it:
```
sudo apt-get install kubuntu-desktop --reinstall
```

Now you can reboot or press Ctrl+Alt+F7
Hope this helps.

---

### Post by mastablasta on 2011-03-01
you can install KDE again.
 
or find the packages you need in kpackagekit

---

### Post by Zalib on 2011-03-01
> **ankspo71 said:**
> Hi,
The package you need to reinstall is called kubuntu-desktop.

If you don't have a working package manager installed, and since konsole got removed, use the following advice:

Press Ctrl+Alt+F2 (press Ctrl+Alt+F7 to come back to the desktop if needed)
Log into the terminal window with your username and password.
then use this command:
```
sudo apt-get install kubuntu-desktop 
```

If it says it is already installed, add the --reinstall option to the end to reinstall it:
```
sudo apt-get install kubuntu-desktop --reinstall
```

Now you can reboot or press Ctrl+Alt+F7
Hope this helps.

Hey thanks for that and I did install it but it doesn't reboot normaly or at all really. Is there something I'm missing? I did install kubuntu-desktop and waited the two minutes it took to do that but when I went to reboot the screen poped up with the kubuntu logo and those four dots under it and then the screen keeps changing from really bright to really dark like some graphic thingy. I don't know what's going on.

---

