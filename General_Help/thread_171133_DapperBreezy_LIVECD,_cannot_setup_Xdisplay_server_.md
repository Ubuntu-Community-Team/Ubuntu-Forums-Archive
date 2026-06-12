---
title: "Dapper/Breezy LIVECD, cannot setup Xdisplay server (radeon x600)"
date: 2006-05-06
forum: General Help
---

### Post by Adamant1988 on 2006-05-06
I'm using an ATI radeon x600, I've had this problem with almost every linux installation, but I can't seem to get a fix in Ubuntu linux in either Breezy Badger or Dapper Drake Live CD's. I was able to get PClinuxOS and Mepis live CD's running using a Vesa driver, but I haven't had as much luck in Ubuntu, which I really want to try... any assistance would be appreciated.

---

### Post by neouser99 on 2006-05-06
are you attempting to boot into the dapper livecd interface? or get the full ati fglrx drivers installed? what do you mean by you can't setup Xdisplay server? xorg won't start?

-neo

---

### Post by Adamant1988 on 2006-05-06
Yeah Xorg won't start. I get a blue box telling me it's not configured correctly and then a bunch of gibberish.   Also I'm attempting to get into either the Breezy or Dapper interface, I'd just like to see a GUI preferebly in Dapper.

---

### Post by neouser99 on 2006-05-06
anyway you could get the error log posted??? also, have you tried changing the driver to use the vesa driver in the Xorg.conf file?

-neo

---

### Post by Adamant1988 on 2006-05-06
I've run "live xdriver=vesa" at the suggestion of another forum and no I don't think I can post the log, it's on THIS computer so I have no way of getting a copy of it..., I'll try to take a picture.

No picture.. batteries are dead in my camera.... =\

> Failed to start the X server (your ghapical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagose the pronblem?
^^^ ERROR

---

### Post by Dryer Lint on 2006-05-08
I have an unsupported Ati card, too (Radeon x1300 or something) and had the same problem upon installing Ubuntu.

However, I think the only thing I did was change driver from "radeon" to "vesa" and everything was fine.

You should look into the sections about your monitor and gfx card in the xorg.conf and check if they are setup correctly. Delete stuff like insane resolutions your card/monitor doesn't even support (I had that once).

---

