---
title: "wbar launch command"
date: 2009-11-23
forum: General Help
---

### Post by tosat on 2009-11-23
I want to add some icons in the wbar config, for example I added Facebook with the command "glaunch facebook.desktop" but it doesn't work (however "glaunch firefox.desktop, glaunch gmail.desktop,...etc" work fine). What is the right command to launch apps with wbar?

Thank you

---

### Post by spcwingo on 2009-11-23
Whatever the name of the executable is.  For example Firefox would be "firefox".  To further explain here is a copy of my .wbar from my home folder:

```
# The Bar && Font
i: /usr/share/wbar/iconpack/wbar.osx/mybg8.png
t: /usr/share/wbar/font/12
c:

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/KONSOLE(SYSTEM).png
c: nautilus --no-desktop --browser
t: Nautilus

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/KONSOLE2.png
c: gnome-terminal
t: Terminal

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/KONQUEROR.png
c: firefox
t: Firefox

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/EMAIL.png
c: thunderbird
t: Thunderbird

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/PIDGIN.png
c: pidgin
t: Pidgin

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/OPENOFFICE-WRITER2.png
c: openoffice.org3
t: OpenOffice

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/GIMP.png
c: gimp
t: Gimp

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/PLAYER.png
c: totem
t: Totem

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/CONFIGURE.png
c: ubuntu-tweak
t: Tweak

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/LOGOUT.png
c: gnome-session-save --kill
t: Logout
```

If you need any more help just let me know.

---

### Post by tosat on 2009-11-24
Thank you, it works now. In fact, for Facebook I have to type 'prism-facebook' and not only 'facebook'.

---

