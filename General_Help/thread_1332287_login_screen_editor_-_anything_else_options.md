---
title: "login screen editor - anything else? options?"
date: 2009-11-20
forum: General Help
---

### Post by jzacsh on 2009-11-20
[http://ubuntuforums.org/showthread.php?t=1300640](http://ubuntuforums.org/showthread.php?t=1300640)
This can't possibly be the end of the discussion?..

I haven't [tried this yet]("http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html"), but there's gotta be a better way... I mean, if editing via the command line is possible then why can't a gui front be established for those same edits (*and shoved back in the ubuntu _menu > system > pref_*)
**STRAIGHT OUT OF: [http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html](http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html)**
[LIST=1]
[*]Logout of your current session and return to the GDM
[*]Switch to the tty command line prompt using Ctrl-Alt-F1
[*]Login using your normal login/password
[*]at the command line prompt type: export DISPLAY=:0.0
[*]then type: sudo -u gdm gnome-control-center
[*]Switch back to the gdm screen using ALT-F7
[*]The gnome-control-center should be loaded. Use it to configure your GDM.
[*]Click on the Appearances icon, in appearances you can change your GDM's font, theme and background image.
[*]Close the gnome-control-center and login normally.
[/LIST]

Outside of issue of listing possible users for login, I also have xfce login-screen prefs installed (*though I'm not using xfce*) and now would like to switch back to see the new one (*but don't want to get rid of xfce all together*) there must be a normal way to get to this editor, right (*it seems like right now, my only choice would be uninstalling xfce prefs*)?

---

### Post by dcstar on 2009-11-21
> **jzacsh said:**
> [http://ubuntuforums.org/showthread.php?t=1300640](http://ubuntuforums.org/showthread.php?t=1300640)
This can't possibly be the end of the discussion?..

I haven't [tried this yet]("http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html"), but there's gotta be a better way... I mean, if editing via the command line is possible then why can't a gui front be established for those same edits (*and shoved back in the ubuntu _menu > system > pref_*)
.........

Just because some developers use command line does not mean that there is no GUI:

Applications-System Tools-Configuration Editor.

This can be enabled in System-Preferences-Main Menu.

---

### Post by Pheros on 2009-12-07
Is there any way to get this option to stick between kernel updates?  

As soon as I upgraded to 2.6.31-16 it went back to listing the users, even though "disable_user_list" was still checked in the configuration editor.

---

