---
title: "no log in screen after booting"
date: 2009-09-14
forum: General Help
---

### Post by gary_ragel on 2009-09-14
Ubuntu 9.04
ATI Radeon 3200HD (onboard)

I recently got 9.04 up and running on my new setup. The last time I rebooted, I noticed 2 errors just before the boot screen shows up: 

ata1: softreset failed (device not ready)
ata2: softreset failed (device not ready)

the ubuntu load screen then shows, and instead of getting the log in screen, I get this mess:
[IMG]http://i28.tinypic.com/14ubyph.jpg[/IMG]

it flashes on and off 3 times and then stays like this, not allowing me to go any further.

---

### Post by Tim Sharitt on 2009-09-15
First, some basic info. Did you install the restricted fglrx driver?

Are you able to post the contents your /etc/X11/xorg.conf file from another OS or a terminal (Ctrl+Alt+F1, F2, etc)?

This is a long shot but, just so we don't get ahead of ourselves, are there problems with the splash screen, displaying a terminal (Ctrl+Alt+F1, F2, etc)?

---

### Post by gary_ragel on 2009-09-15
The last driver I installed was the ATI Advanced driver; probably should have mentioned that the first time, sorry.
 
Also, I'm brand new to Linux (been a windows user for 15 years) and I'm not sure how to get the contents of the xorg.conf file. While booting, I select recovery mode and then drop to the root shell. Been searching for a way to display the contents of the xorg.conf file. What command would I enter to do that?

---

### Post by gary_ragel on 2009-09-15
wait here we go, got this by typing less /etc/X11/xorg.conf into the root shell:
 
Section "Device"
Identifier "Configured Video Device"
Endsection
 
Section "Monitor"
Identifier "Configured Monitor"
Endsection
 
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
Endsection

---

### Post by P4man on 2009-09-15
Perhaps its easiest you revert to vesa drivers, so you have a gui again.

boot in a root shell and type:

```
sudo nano /etc/X11/xorg.conf
```

(note the X in X11 is an uppercase)

Find a section that looks somewhat like this:
```

Section "Device"
      Identifier "Configured Video Device"
Endsection
```

change it to:
```

Section "Device"
        Identifier      "configured Video Device"
        Driver          "**vesa**"
EndSection
```

press control+X and Y to save.
enter "reboot" to reboot and see if you got a gui again. it will be sluggish, but we can take it from there.

(updated message to match your xorg)

---

### Post by gary_ragel on 2009-09-15
OK I added the Driver          "**vesa**" line in the xorg.conf file, saved, and rebooted. Same thing happens; I get the Ubuntu "loading" screen, then a big mess (still no gui), although this one looks a bit different from the first pic:
 
[IMG]http://i31.tinypic.com/2uotbuo.jpg[/IMG]

---

### Post by gary_ragel on 2009-09-15
decided since i didn't have anything on the hd that couldn't be easily replaced, i re-installed 8.04 using a live cd and performed the upgrade to 9.04. everything seems to be running smoothly for now; i'll stay away from that ati driver, though. thanks for the help/intro to xorg.conf

---

