---
title: "Failed to execute default Terminal Emulator. Input/output error."
date: 2011-12-12
forum: General Help
---

### Post by Marzata on 2011-12-12
In Xubuntu 11.10 while trying to start Htop from the menu I got a window saying: "Failed to execute default Terminal Emulator. Input/output error." 
This is a brand new installation of Xubuntu 11.10 and xfce4-terminal is manually set as a terminal emulator in preferred applications because the default preferred applications disappeared somehow. Any idea for a fix? Thank you!

---

### Post by LewisTM on 2011-12-12
Do you get errors when running
```
exo-open --launch TerminalEmulator
``` 

Of course I assume you have a functional terminal emulator to run that command :)

---

### Post by Marzata on 2011-12-12
> **LewisTM said:**
> Do you get errors when running
```
exo-open --launch TerminalEmulator
``` 

Of course I assume you have a functional terminal emulator to run that command :)

No errors here. This opens a new terminal window. The error is only when I use the menu. See the attachment. Any idea?

---

### Post by LewisTM on 2011-12-13
I think I have the beginning of an explanation.
On my system (Xubuntu 11.10) setting an application to launch in a terminal launches an instance of xterm, NOT xfce4-terminal. Maybe that's a remnant of the old days when xterm was the default terminal emulator in Xfce. Doesn't bother me very much.

You should check that xterm is installed and functional. If I rename /usr/bin/xterm I cannot launch applications inside terminals but I don't get an error message so thay may not be it. Sounds more like a config problem.

This [thread]("http://crunchbanglinux.org/forums/topic/10725/resolved-xfce4-altf2-error-failed-to-execute-default-terminal/") may give you clues.

A quick fix would be to set your launcher command to ```
xfce4-terminal -x htop
```

---

### Post by Marzata on 2011-12-13
Thank you very much and I think I found the solution. I removed and reinstalled the package ```
xubuntu-default-settings
``` and this fixed the problem. I was able to choose the preferred applications again. And xterm is great indeed. And Xubuntu is the best distro. Thank you!

---

### Post by moodle on 2012-03-26
**Alternative Solution**

> **Marzata said:**
> Thank you very much and I think I found the solution. I removed and reinstalled the package ```
xubuntu-default-settings
``` and this fixed the problem. I was able to choose the preferred applications again. And xterm is great indeed. And Xubuntu is the best distro. Thank you!

This solution didn't work for me, but changing the default terminal emulator in Settings Manager -> Preferred Applications did work.

See: [http://ubuntuforums.org/showthread.php?t=1878018](http://ubuntuforums.org/showthread.php?t=1878018)

---

