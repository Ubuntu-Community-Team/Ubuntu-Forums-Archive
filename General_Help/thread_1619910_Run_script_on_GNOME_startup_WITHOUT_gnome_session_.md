---
title: "Run script on GNOME startup WITHOUT gnome session manager"
date: 2010-11-12
forum: General Help
---

### Post by Ctorpor on 2010-11-12
I'm currently building a ubuntu distro and would like to run a script on GNOME startup. I've read about doing it through the session manager but I have to do it through chroot so I'll need to set it up as a terminal command. Is there a way to add an item to the Session Manager from terminal or, even better, a directory where I can put the script so it will run on start?

---

### Post by sisco311 on 2010-11-12
The system wide autostart directory is /etc/xdg/autostart/ and the autostart directory in the user's home is ~/.config/autostart. You have to copy the application's .desktop file (i.e. from /usr/share/applications/) to one of this directories. Or if you want to create a custom .desktop file, run something like:
```
cat << EOF >> ~/.config/autostart/name.desktop
[Desktop Entry]
Name=**name**
Comment=**comment**
Exec=**command**
EOF

```

For more info check out:
[http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html)
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

---

