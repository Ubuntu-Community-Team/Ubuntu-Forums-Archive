---
title: "Ratpoison doesn't appear in GDM menu"
date: 2009-11-21
forum: General Help
---

### Post by ragein on 2009-11-21
I'm running Karmic and have just installed ratpoison from apt-get which seemed to work ok but when I logout to try and run ratpoison it doesn't appear in the GDM options.  Having looked for a solution I found out that Debian have changed how window managers work with the GDM  and apparently I need to add /usr/share/xsessions/ratpoison.desktop with the following contents:-

> [Desktop Entry]
Name=Ratpoison
Comment=This session logs you into Ratpoison
Exec=/usr/bin/ratpoison
TryExec=/usr/bin/ratpoison
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=ratpoison-session

This puts it into the options menu but when I try to login all I get is an Ubuntu splash screen with a working mouse pointer and then nothing, I cannot kill x with ctrl-alt-backspace and have to re-boot before I can do anything.

I have also tryed variations on this such as "EXEC=ratpoison" and tryed it without the last line.  I'm sure that i'm doing something wrong but can't figure out what so thanks in advance if any of you can figure it out.

---

### Post by ragein on 2009-11-21
Sorry that was my stupidity the ratpoison.desktop file does work and does what it's supposed to do I had simply remembered the wrong key combo to bring up a terminal in ratpoison.

---

### Post by kensanata on 2012-01-27
Thanks, worked! In 2012, no less. :)

---

### Post by lisati on 2012-01-27
> **kensanata said:**
> Thanks, worked! In 2012, no less. :)

Nice to know. The thread can now go back to sleep.

---

