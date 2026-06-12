---
title: "internet without gdm"
date: 2009-09-24
forum: General Help
---

### Post by Esthellin on 2009-09-24
I disabled gdm on startup. Logging in and running startx works fine.
After running startx however, I have to reenter my password for the Network Manager applet, as it says it is "locked".
Normally, gdm would run, I would login, and the nmapplet would start.

The only reason I have this applet is to get the wireless internet to work. Without it, the net doesn't connect.
I do not have gnome-panel running at all in the session, but if nm-applet is not started - no interwebz.

Because I don't have gnome-panel, what is the proper way to get the wireless connections occuring and therefore be able to have internet acess after login without gdm and before running startx?

EDIT: Power button now doesn't work. Normally, pressing it comes up with the Shutdown, Restart etc dialog, now it does nothing.

---

### Post by Shazaam on 2009-09-24
```
To find out what wireless networks are available to you, type
iwconfig wlan0 scan

To attach to an open, non-encrypted network, type
iwconfig wlan0 essid netname
where netname is the essid of the network you want to connect to.

If you only have encrypted networks available, you might be in a bit more trouble. I haven't actually managed to get that working at all yet, though theoretically, it should work something like this:
iwconfig wlan0 key s:password
iwconfig wlan0 essid netname
where password is your password and netname is the essid of the network you want. The s: means that the password is in string format. If you know the hex version of your password, then instead of saying s:password you'd just type in the hex of the password like this:
iwconfig wlan0 key 0123-4567-89

```
From here...
[http://theledgeofknow.blogspot.com/2008/10/wireless-connection-from-command-line.html](http://theledgeofknow.blogspot.com/2008/10/wireless-connection-from-command-line.html)

---

