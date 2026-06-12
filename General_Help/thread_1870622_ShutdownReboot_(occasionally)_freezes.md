---
title: "Shutdown/Reboot (occasionally) freezes"
date: 2011-10-27
forum: General Help
---

### Post by Dark Slipstream on 2011-10-27
My computer would occasionally freeze when I shutdown or rebooted the computer for whatever reason. As of late, every time I shutdown or restart it freezes and now it's becoming a PITA.

I have no idea how to debug this and really need some help :(.

---

### Post by cryptotheslow on 2011-10-27
You could try this:

Before you shutdown / reboot use Ctrl+Alt+F1, login and enter this:

```
tail -f /var/log/messages
```

That should give you a scrolling list of what's being written out by most processes.

Ctrl+Alt+F7 to get back to your desktop, and hit Shutdown, then Ctrl-Alt-F1 to flip back to the tail screen.

Hopefully, the lock up will occur before the tty process displaying that screen gets killed and you will see what the last thing that happened was.

Otherwise it's going to be a case of rebooting and trawling back up the log files. /var/log/syslog and /var/log/messages as a start point.

---

### Post by sidewalkcynic on 2011-10-27
I'm having similar problems today - froze on log out and freezes from boot.



one of the things I found in the /var/log/syslog
```
Notice: NX (Execute Disable) protection missing in CPU!
```

This is my first experience in making /var it's own partition and it is full, I thought it cleans itself out, or over-writes itself.

---

### Post by Dark Slipstream on 2011-11-18
GNOME-SETTINGS-DAEMON Solution

[LIST=1]
[*]Open a terminal and type **sudo apt-get remove gnome-settings-daemon**.
[*] Type **y** to remove **gnome-settigs-daemon**, including any additional programs listed.
[*] After the removal is completed type **sudo reboot -f** in the terminal. (Without -f you risk freezing during the reboot)
[*] Let it boot normally. After the boot splash screen, nothing should appear (on new tvs you will get a "No Signal" message, thats good); wait about 5 minutes, press Ctrl+Alt+Delete then reboot your machine using the reset button.
[*] Hold shift during boot-up and boot into the recovery console.
[*] Select root shell prompt.
[*] Login using an administrator account.
[*] Type **mount -o rw,remount /** in the recovery console.
[*] Type **apt-get install gnome-settings-daemon** into the recovery console.
[*] Type **reboot** into the recovery console and boot into ubuntu normally.
[*] Open a terminal and type **sudo apt-get install gnome-control-center indicator-session indicator-power indicator-datetime**. (This will restore the remaining system packages that were removed during the first step)
[/LIST]

The above solution has worked for me. The gnome-settings-daemon no longer crashes after any period of time (thus far); and reboot/shutdown freezing related to the gnome-settings-daemon no longer occurs. (May not have any effect if another package is causing a similar problem)

---

