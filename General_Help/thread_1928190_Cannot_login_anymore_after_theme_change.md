---
title: "Cannot login anymore after theme change"
date: 2012-02-19
forum: General Help
---

### Post by kaschenberg on 2012-02-19
I installed a Mac OS theme for my Ubuntu 11 laptop which consisted of me installing gnome-tweak-tools and dumping some icon/theme/cursor files in /usr/share/ folders. After selecting the GTK+ theme part in gnome-tweak-tools I was kicked out of my session and when trying to log back in the screen goes black with some output at the top (nothing critical, just about starting printer spooler) and then I get kicked back to the login screen.

I can only login via the guest account now.

Any help is appreciated. I hope I don't have to reinstall Ubuntu...

---

### Post by Krytarik on 2012-02-19
Reset the setting for the GTK+ theme via command line:

[LIST=1]
[*]At the login screen, press Alt+F1 to switch to the console/tty.
[*]Log in there.
[*]Run:
```
dbus-launch gsettings reset org.gnome.desktop.interface gtk-theme
```
[*]Press Alt+F7 to switch back to the login screen.
[/LIST]
Then try again to log in.

And eventually, discard the rest of that Mac theme set, if you want so.

Regards.

---

### Post by sssuizaaa on 2012-03-24
krytarik,

I am in the same situation as kaschenberg.
I followed your advice. In the grub menu I selected the recovery mode and in the resulting menu I selected root-drop to root shell prompt. Once there I did what you adviced:

gsettings reset org.gnome.desktop.interface gtk-theme

This is what I got:

**(process:642):WARNING**: Command line 'dbus-launch –autolunch=4438d024dd45ef7fb2d3f4ab0000000f –binary-syntax  --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n


and nothing has changed



Any help would be highly appreciated.


Regards,


sssuizaaa

---

### Post by sssuizaaa on 2012-04-05
OK, I finally found how to solve this. In the login screen I did Ctrl+Alt+F1 and then I created a new user.  Login with that new user and went to usr/share/themes and deleted the  themes I had just installed. Then I could login again with my original  user.
  Hope this helps to someone
  Sssuizaaa

---

### Post by Krytarik on 2012-04-05
> **sssuizaaa said:**
> OK, I finally found how to solve this. **In the login screen I did Ctrl+Alt+F1** ...
Ok, nice that you finally at least partly followed my advice :D - I mean *actually*, as opposed to this ;-) :
> **sssuizaaa said:**
> [COLOR=Blue]**krytarik, ... I followed your advice.**[/COLOR] [COLOR=Red]**In the grub menu I selected the recovery mode and in the resulting menu I selected root-drop to root shell prompt.**[/COLOR]
Regards.

EDIT: Upon actually *testing* it myself now, I've noticed that you need to involve "dbus-launch" for the suggested command to work; added it to my initial instructions - but in your case, that wouldn't have helped anyway, because you were running it as root, thus about to change root's settings, not yours. ;-)

---

