---
title: "Xubuntu cursor size"
date: 2011-11-06
forum: General Help
---

### Post by mike555 on 2011-11-06
Any one know how to get bigger cursor arrows to stick in Xubuntu 11.10 after a restart ?
 I got the cursor to be bigger by doing this, but it doesn't survive a restart ......

  

1) Select a different cursor theme
2) ALT + F2 (or Run Program)
3) xfwm4 --replace

---

### Post by Toz on 2011-11-06
This lead me to the solution: [https://bugzilla.xfce.org/show_bug.cgi?id=7683]("https://bugzilla.xfce.org/show_bug.cgi?id=7683").

Basically, change your mouse cursor theme in Settings Manager->Mouse (for example, to redglass), then edit the file **/usr/share/icons/default/index.theme** like so:
```

[Icon Theme]
Inherits=redglass

```
...then log out and back in again for it to take effect. It affects the login screen as well, in that you'll see the new cursor theme there.

---

### Post by mike555 on 2011-11-06
Thanks, but that didn't help with size , I even tried different themes , but no help,.......... lots of people are having this problem on different forums , no cure yet.

---

### Post by Toz on 2011-11-06
Oh, the size. Not sure if this helps, but I was able to get the size to stay everywhere but on the xfce apps by adding:
```

Xcursor.theme: redglass
Xcursor.size:  48

```
...to ~/.Xdefaults. However, when I hover over the desktop (or any xfce app), cursor size returns to normal. Might be a bug in xfce.

---

### Post by mike555 on 2011-11-06
I tried that but maybe put it in wrong place? I put it after what I have and it didn't make a difference.
this is my .Xdefaults file


! Xft settings ---------------------------------------------------------------

Xft.dpi:        96
Xft.antialias:  true
Xft.rgba:       rgb
Xft.hinting:    true
Xft.hintstyle:  hintslight
Xft.lcdfilter:  lcddefault


! xscreensaver ---------------------------------------------------------------

!font settings
xscreensaver.Dialog.headingFont:        -*-dina-bold-r-*-*-10-*-*-*-*-*-*-*
xscreensaver.Dialog.bodyFont:           -*-dina-medium-r-*-*-10-*-*-*-*-*-*-*
xscreensaver.Dialog.labelFont:          -*-dina-medium-r-*-*-10-*-*-*-*-*-*-*
xscreensaver.Dialog.unameFont:          -*-dina-medium-r-*-*-10-*-*-*-*-*-*-*
xscreensaver.Dialog.buttonFont:         -*-dina-bold-r-*-*-10-*-*-*-*-*-*-*
xscreensaver.Dialog.dateFont:           -*-dina-medium-r-*-*-10-*-*-*-*-*-*-*
xscreensaver.passwd.passwdFont:         -*-dina-bold-r-*-*-10-*-*-*-*-*-*-*
!general dialog box (affects main hostname, username, password text)
xscreensaver.Dialog.foreground:         #EDEDED
xscreensaver.Dialog.background:         #202020
xscreensaver.Dialog.topShadowColor:     #202024
xscreensaver.Dialog.bottomShadowColor:  #202024
xscreensaver.Dialog.Button.foreground:  #EDEDFF
xscreensaver.Dialog.Button.background:  #444
!username/password input box and date text colour
xscreensaver.Dialog.text.foreground:    #EDEDFF
xscreensaver.Dialog.text.background:    #444
xscreensaver.Dialog.internalBorderWidth:24
xscreensaver.Dialog.borderWidth:        20
xscreensaver.Dialog.shadowThickness:    2
!timeout bar (background is actually determined by Dialog.text.background)
xscreensaver.passwd.thermometer.foreground:  #A9B7C4
xscreensaver.passwd.thermometer.background:  #202020
xscreensaver.passwd.thermometer.width:       8
!datestamp format--see the strftime(3) manual page for details
xscreensaver.dateFormat:    %I:%M%P %a %b %d, %Y

---

### Post by Toz on 2011-11-06
Yes, I put it at the end of that file. Did you log out and back in again?

---

### Post by Toz on 2011-11-06
Found this article: [http://forum.xfce.org/viewtopic.php?id=3517]("http://forum.xfce.org/viewtopic.php?id=3517"), but it still doesn't fix the cursor in the xfce apps. Then I started thinking that maybe this is because of the switch to gtk3. Came across some references to a ~/.config/gtk-3.0/settings.ini file. I tried making some changes there, but still no luck.

---

### Post by mike555 on 2011-11-07
Ok, I think I have got it figured out ,

To changer arrow size in Xubuntu;

in ;   Xfce-settings
Just go to settings manager, mouse and select your theme

 
in "~/.gtkrc-2.0" add
gtk-cursor-theme-name="the-theme-name"
gtk-cursor-theme-size=48

of course put in your  theme name , and the size you want.

and you will need to restart for settings to take effect.

---

