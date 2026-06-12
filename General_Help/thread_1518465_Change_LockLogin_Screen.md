---
title: "Change Lock/Login Screen"
date: 2010-06-26
forum: General Help
---

### Post by RedSingularity on 2010-06-26
Any news as to changing the Lock and Login Screens for the newer versions of Ubuntu?  Many of the items on gnome-look.org are useless on newer versions.  Personally I dont think they should have messed with that feature in the first place.  Changing your screens to fit what you like was great.

---

### Post by sisco311 on 2010-06-27
GDM now uses GTK themes. To change the theme add gnome-appearance-properties to GDM's autostarted applications:
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out. Select a new theme/wallpaper/font. Log in and remove gnome-appearance-properties to GDM's autostarted applications:
```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by RedSingularity on 2010-06-27
Hey Sisco, long time no see buddy:)

Anyhow in order to change the login screen I need to change the theme of the whole computer?  The GTK themes effect the whole look of the X window system.  I only wanted to change the login screen look.  It was nice and easy in previous versions of Ubuntu.

---

### Post by Spr0k3t on 2010-06-27
Actually, when using that method it only changes the theme for the user "gdm".  So you can give it any theme you want, it will not affect your personal theme or the theme of any new users even after the changes made.

---

### Post by RedSingularity on 2010-06-27
For example, lets say I want [this](http://gnome-look.org/content/show.php/Acemone?content=101301) theme.  I can no longer install it?  Since Version 9.10 i mean.

---

### Post by Spr0k3t on 2010-06-27
If you can find the GTK2.0+ theme that looks like that with window decorations and controls, yes it's possible.  However, it requires hacking at the raw elements of GDM2 to make it happen.  There are components I still do not understand about GDM2 but have feverously tried to get it working (all through VM in my testing).

Here's an example shot I did with the gtk theme darklooks and some custom color/icon tweaking.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=161733&stc=1&d=1277673655[/IMG]

---

### Post by RedSingularity on 2010-06-27
Oh now i see:)  Well Here is hoping that they make it as easy as it was in the original GDM.

Thanks :) :)

---

### Post by drink_stir on 2010-10-12
I may be a little late on the reply but there is always this...

1. Logout of your current session and return to the GDM
2. Switch to the tty command line prompt using Ctrl-Alt-F1
3. Login using your normal login/password
4. at the command line prompt type: [COLOR=blue]export DISPLAY=:0.0[/COLOR]
5. then type: [COLOR=blue]sudo -u gdm gnome-control-center[/COLOR]
6. Switch back to the gdm screen using ALT-F7
7. The gnome-control-center should be loaded. Use it to configure your GDM.
8. Click on the Appearances icon, in appearances you can change your GDM's font, theme and background image.
9. Close the gnome-control-center and login normally.

i got this from [http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html](http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html)

Havent tried it since I upgraded to Lucid, but it worked in Karmic.

---

