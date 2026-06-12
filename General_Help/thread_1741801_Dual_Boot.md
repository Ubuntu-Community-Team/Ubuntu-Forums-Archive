---
title: "Dual Boot"
date: 2011-04-28
forum: General Help
---

### Post by Red Wanderer on 2011-04-28
Hello, fellow Ubuntu fans. I've lurked here for a few weeks, but I suddenly feel the need to participate. I just installed the new 11.04 release, which took some getting used to but overall has been a positive experience. However, as much as I'd like to give my thumbs up to the project, it seems there's a few kinks in the system....I've lost the ability to dual boot. My Windows OS partition is still there--I can access it and all of the files within--but now my monitor flashes a rectangular box stating "Input Not Supported" (I will double check that). The message just hangs there for about half a minute before booting up to Linux. I don't use my Windows for much since I downloaded the last Ubuntu release, but I do need it for certain things that I just find easier to do with Windows. Is there any way I could fix this? Should I try to reinstall GRUB?

---

### Post by Quackers on 2011-04-28
Welcome to UF.
In Ubuntu open up a terminal and type in ```
sudo update-grub
``` then watch as grub.cfg is run to see if the Windows Loader is recognised. If it is, reboot and you should get a grub menu with the choice of which OS to boot.

---

### Post by Red Wanderer on 2011-04-28
Quackers,

Sorry to have to bug you with my own problem, as I'm sure this place is packed with people wanting to add their two cents on release day. I did as you suggested, and indeed, it did find the Windows 7 Loader and updated. But the same problem persists regardless...no loader ever comes up while booting. If it helps, it seems to be something wrong with how the monitor is receiving the information--the rectangular box is, at least as I assume, a built in diagnostic message programmed within the monitor itself. I'm not sure why it would be having a problem at that specific point, though. I really have no idea what to do with this.

---

### Post by Hedgehog1 on 2011-04-28
To see the grub menu on your PC, please do this:

```
gksudo gedit /etc/default/grub
```

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


***The Hedge***

---

### Post by nandoae on 2011-04-29
Sorry to interrupt but yesterday i upgrade to the new release 11.04, and y cant manipulate the grub configuration in the old version i use the grubeditor to change the SO boot order. the question is how can i do it now. please help. thanks:D

---

