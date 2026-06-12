---
title: "Can't Log On in The System"
date: 2010-06-24
forum: General Help
---

### Post by JCM_Pico on 2010-06-24
[SIZE=2]Hello there,
I was experimenting WINE in my Ubuntu machine. After a while I've decided to remove it.
I uninstalled the application that I installed using WINE (Steam - Day of Defeat)
And then i ran the following command
         sudo apt-get remove wine*
I checked (using tab) and only wine, wine1.2 and wine-gecko where there to remove.

After doing this I shutdown my computer. When I turned it on again everything was fine until I had to pass trough the login page... 
I've inserted my credentials and then when I clicked in "Log In" it appears a dark screen and then again the Log In screen.....

I already tried many things but the problem still continues....
Is there anybody that could give me some Help?

Thank you for the attention       [/SIZE]

---

### Post by arrange on 2010-06-24
Can you boot into a LiveCD, mount your Ubuntu partition and look at the */var/log/apt/term.log* file to see what really happened when you uninstalled the packages?

---

### Post by JCM_Pico on 2010-06-24
Well, I can boot in a LiveCD but how can I mount my partition?

---

### Post by arrange on 2010-06-24
Go to *Places* on the upper panel and click on the partition.

---

### Post by JCM_Pico on 2010-06-24
[SIZE=2]Ups its a big mess, [/SIZE]


Start-Date: 2010-06-24  18:44:30
Remove: wine1.2 (1.1.42-0ubuntu4), gnome-control-center (2.30.1-0ubuntu1), ubuntu-desktop (1.197), indicator-applet (0.3.7-0ubuntu1), indicator-me (0.2.6-0ubuntu1), wine (1.1.42-0ubuntu4), indicator-applet-session (0.3.7-0ubuntu1), libgnome-window-settings1 (2.30.1-0ubuntu1), wine1.2-gecko (1.0.0-0ubuntu4), gnome-applets (2.30.0-0ubuntu2), xorg (7.5+5ubuntu1), compiz (0.8.4-0ubuntu15), gnome-panel (2.30.0-0ubuntu2), winbind (3.4.7~dfsg-1ubuntu3), gnome-session (2.30.0-0ubuntu1), compiz-gnome (0.8.4-0ubuntu15)
End-Date: 2010-06-24  18:45:00
[SIZE=2]
Is it recoverable?  [/SIZE]:( 
[SIZE=2]Is there some way to install the missing packages from the LiveCD?[/SIZE]

---

### Post by arrange on 2010-06-24
Yes, no problem. :)
Boot into *Recovery Mode*, choose the **root** or **netroot** option, and type```
apt-get install ubuntu-desktop
```If no errors, type *reboot* and try normal boot now.

---

### Post by JCM_Pico on 2010-06-24
Is just to press ESC while loading the system right... Cause I'm not being  able to get to the recovery mode option

---

### Post by arrange on 2010-06-24
If you don't see the Grub menu while booting, I think you must press *Shift*. Then choose the *recovery mode* option.

---

### Post by JCM_Pico on 2010-06-24
Thank you very much 
The problem has been solved, I can log on successfully

---

