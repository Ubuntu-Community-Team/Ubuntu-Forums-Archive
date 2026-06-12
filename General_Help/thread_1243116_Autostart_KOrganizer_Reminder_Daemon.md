---
title: "Autostart KOrganizer Reminder Daemon"
date: 2009-08-17
forum: General Help
---

### Post by mediumhouse on 2009-08-17
Trying to use KOrganiser in Ubuntu 9.04 and the first stumbling block is that the Autostart doesn't work.

"Start Reminder Daemon at login" is checked but it does not actually do anything.

I did this:

gedit "/usr/share/autostart/KOrganiser Reminder Client"

and it appears blank, should I be able to see anything in there?

---

### Post by NathanLT on 2009-08-18
The Korganizer (with a 'z', not an 's') daemon is called korgac. In my /usr/share/autostart folder the configuration file is named korgac.desktop. This is how it reads in my Kubuntu 9.04 setup:

```
#KDE Config File
[Desktop Entry]
Name=KOrganizer Reminder Client
Exec=korgac %i
Icon=korgac
Type=Application
GenericName=KOrganizer Reminder Daemon Client
Terminal=false
X-KDE-autostart-after=panel
X-KDE-autostart-condition=korgacrc:General:Autostart:true
#do not uncomment the following line, else autostart fails
#NoDisplay=true
OnlyShowIn=KDE;
X-Ubuntu-Gettext-Domain=desktop_kdepim
```I'm not sure if this means the autostart will only work in KDE, or if you have to edit the config file, replacing 'KDE' with 'GNOME'?

Nathan

---

### Post by mediumhouse on 2009-08-18
I got the "z" right in the title!

Anyway, I have seen reference to this korgac file in other searches but I don't seem to have one.  So, in essence, I need one for the autostart to work?  Anyone use this in ubuntu and have an example file I could try out?

---

