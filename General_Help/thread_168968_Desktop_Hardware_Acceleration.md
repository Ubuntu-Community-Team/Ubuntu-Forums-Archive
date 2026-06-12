---
title: "Desktop Hardware Acceleration?"
date: 2006-05-01
forum: General Help
---

### Post by lucky2 on 2006-05-01
ello!

Quick question, hope someone can help.

Im using Ubuntu 5.10, pretty much standard.

I've added Azureus, Skype, Firefox latest.. I'm pretty much trying to leave Windows behind.

My problem is watching streaming media, I've installed the latest Nvidia drivers using the how-to. I think OpenGL works (games, screensavers) but streaming video uses nearly 100% cpu cycles (even overclocked) In Firefox 1.5.0.1, and the Gdesklets apps (toolbars etc) add loads. Its seems my desktop is not using hardware acceleration... Should I go for beta Dapper Drake, or is there a way with Breezy Badger?

Cheers!. :)

::edit::

tvtime only uses around 30% cpu cycles when playing back tv

---

### Post by Jason_25 on 2006-05-01
You didn't post your hardware specs.  It sounds like you need a fairly powerful PC to do what your asking of it.  So your only real problem is 100% cpu usage with streaming video in firefox?  What firefox plugin are you using that causes this?  Have you tried others?

---

### Post by lucky2 on 2006-05-01
Jason_25::

Yes,
Specs (sketchy)

km400a via chipset (abit va20 mobo (yes I am going to upgrade :P))
athlon 2000xp cpu
new nvidia6200 (not the 6200a with extra pipelines)
sblive value
generic RAM, mostly BIOS options set to defaults. (ie: auto)
dell m770 monitor etctec

I just want watching video through browser* to be smooth. :)

---

### Post by Jason_25 on 2006-05-01
With those specs you should have good playback.  Are you using the nvidia display driver?  I assume your using the totem firefox plugin.  Have you tried the mplayer plugin?

---

### Post by lucky2 on 2006-05-01
No, The Mplayer plugin (i think i need to do some more looking into this)

I htink i Need to look into Mplayers plugin options

---

### Post by Jason_25 on 2006-05-01
Actually I would investigate which display driver your using and your xorg configuration.  I am using the mplayer plugin on dapper with like 5% cpu use with the nvidia driver.

---

### Post by lucky2 on 2006-05-01
Will try, thanks

---

