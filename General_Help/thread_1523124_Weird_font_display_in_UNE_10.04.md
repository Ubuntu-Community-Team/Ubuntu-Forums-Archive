---
title: "Weird font display in UNE 10.04"
date: 2010-07-03
forum: General Help
---

### Post by samanthak on 2010-07-03
Sorry if this is the wrong forum to post this in.

I have been using UNE 10.04 since the stable release came out. A month or so ago, the text on the screen suddenly became very odd - it was like there was some text overlaying some characters and half of other characters would go missing. This has happened twice again today. I don't know if it's related to anything I'm doing on the computer - all three times it has happened while I am using the internet, but it hasn't happened any other time I've used it for the past few months. It also happens for all applications I am using at the time, as well as for the taskbar and menus.

I have tried taking screenshots, but I am told the file is corrupt when I try to view them. The only way I have found to fix it is to shut down and restart my computer.

If it's any help, I'm running this on an HP Mini 210 and I use the GNOME desktop instead of the netbook-launcher.

Please let me know if there are any reasons why this might be happening.

---

### Post by Yarui on 2010-07-03
I was going to say screenshots would be a big help, but apparently you have already tried that.  If you have a digital camera, maybe you could get some shots of what it looks like.  This seems like something that would need to be seen to get some idea of what exactly you are describing.

---

### Post by samanthak on 2010-07-03
> **Yarui said:**
> I was going to say screenshots would be a big help, but apparently you have already tried that.  If you have a digital camera, maybe you could get some shots of what it looks like.  This seems like something that would need to be seen to get some idea of what exactly you are describing.

Ok - I'll try to do that next time it happens.

---

### Post by kerry_s on 2010-07-03
have you disabled nautilus managing the desktop in gconf-editor?

netbook-launcher takes care of mounting & the background, so you need to disable nautilus handling those.

---

### Post by samanthak on 2010-07-03
> **kerry_s said:**
> have you disabled nautilus managing the desktop in gconf-editor?

netbook-launcher takes care of mounting & the background, so you need to disable nautilus handling those.

I haven't done that...I'm very new to Ubuntu (only started using it a few months ago). What do I have to do in gconf-editor to do that?

---

### Post by kerry_s on 2010-07-03
first go to system-> main menu
click on system tools & check configuration editor

this will unhide gconf-editor for easy access from the menu, so you don't have to press alt+f2 & type it out everytime you want to get to the settings.

then just open it & goto apps-> nautilus-> preferences

---

