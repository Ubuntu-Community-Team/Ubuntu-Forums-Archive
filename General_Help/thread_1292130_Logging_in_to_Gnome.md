---
title: "Logging in to Gnome"
date: 2009-10-15
forum: General Help
---

### Post by Mikalosh on 2009-10-15
Hi Can someone help please I wanted to create another user to instead of just logging in automatically and I have inadvertently selected the screen where you scan for a serving host but of course I have not defined one so when I click on refresh it returns that it could not find a serving host. I have tried cancelling but it keeps coming back to the same screen. I can reboot to recovery screen and go into a terminal but from there I do not know where to look to disable this and just get back to logging in normally.:(

I am using Ubuntu 9.04

---

### Post by zvacet on 2009-10-16
You can create new user in system<admin>users& groups.

---

### Post by mbeach on 2009-10-16
it sounds like you have the xdm chooser there. When I do the same thing, the cancel button puts me into the normal login screen.

If I were to guess, you may need to edit your 
/etc/gdm/gdm.conf-custom

mine looks like:
```

[daemon]

AutomaticLoginEnable=true

AutomaticLogin=mbeach

[security]

[xdmcp]

[gui]

[greeter]





GraphicalThemes=Human


```
Just a guess here though.

---

