---
title: "Ubuntu Server Down After Update - ish"
date: 2011-10-18
forum: General Help
---

### Post by Haneef Mubarak on 2011-10-18
SO... 

Background:
Software - Ubuntu Server 32-bit - HDD uses Linux encryption via sda5_crypt
     LAMP Stack
         phpMyAdmin
     Webmin
         Usermin
     vsftpd
     netatalk
     ubuntu-desktop (must be started whenever you want it, use startx)

Hardware - Dell Dimension 4000
     Pentium 4
          3.06 GHz
          32-bit
          36-bit PAE
          Unicore (Single-Core)
          HyperThreading Enabled
     DDR1 RAM
          Slot 1: 768 Mb
          Slot 2: Empty
          Slot 3: Empty
          Slot 4: Empty
     Intel HDA

For more details, ask me.

Pre-Friday:

System (BIOS) Battery low. I shut down the computer. I tried to remove it, but the Creative SB Audigy (PCI Soundcard) was in the way. So I removed it, then changed the battery. I didn't replace it, since it wasn't working anyways.

Friday, the 14th of October, 2011:

I launched the GUI for the upgrade (to Oneiric) because I thought it would be easier. Next I do the upgrade, downloads within an hour, but install takes a loooooong time. It restarts after the upgrade, and it launches the GUI. I leave it on as I usually do, since it actually hosts a website.

Saturday, the 15th of October, 2011

I test the sound on the integrated Intel HDA, but it doesn't work. I notice the PCI Soundcard on the table. I shutdown the system and place the Soundcard back into that specific PCI slot (the last and only open one). I turn on the computer and log into the CLI. "Funny, no GUI?", I think. Then i test it from an external device, and none of the services work. I go back to the computer and try 'startx'. It doesn't work.

Please Help.

All help leading to a resolution is appreciated.

-Haneef Mubarak

---

### Post by Haneef Mubarak on 2011-10-21
[color="red"]**_[font="verdana"][size="4"]bump!!![/size][/font]_**[/color]

---

### Post by Haneef Mubarak on 2011-10-26
Bump!

---

### Post by Haneef Mubarak on 2011-10-27
BUMP!!! Please, I've waited for so long already!

---

### Post by fdrake on 2011-10-27
did you try rebooting without the sound card? what about a live cd ?

---

