---
title: "best way to share files between two 11.04 ubuntu computers?"
date: 2011-07-22
forum: General Help
---

### Post by princeofnam on 2011-07-22
I used to use Connect to Server via SSH but I don't see that option any longer.

---

### Post by docbop on 2011-07-22
Just open a terminal window and type ssh and the address of the other computer. Then log on.  If you just want to copy files you can use scp.        If these computers on the same network why not setup file sharing?  Install Samba or NFS and connect them.   If you search the net there are tons of Samba tutorials. Install the admin tool Webmin and real easy to configure Samba and maintain users.

---

### Post by nothingspecial on 2011-07-22
You don't need samba, that's for sharing with windows.

The connect to server option is now under file in the nautilus menus rather than an option in the sidebar.

See screenshot

[ATTACH]198090[/ATTACH]

---

### Post by princeofnam on 2011-07-22
why is port 22 generally preferred?

I forgot this is obnoxiously slow (2.2 MB/s).  Would connecting the computers together with an ethernet cord perhaps quicken things? Right now the laptop is wireless and the desktop is wired.

---

### Post by Using Debian on 2011-07-22
> **princeofnam said:**
> why is port 22 generally preferred?

I forgot this is obnoxiously slow (2.2 MB/s).  Would connecting the computers together with an ethernet cord perhaps quicken things? Right now the laptop is wireless and the desktop is wired.

SSH uses encryption and this can slow down your transfers a little, but if your laptop is wireless and your desktop is wired, it would be best to continue or use SSH to make sure your data is not "absorbed" by any one or thing like network sniffers or packet capture tools.

If you are simply at home, and you did a great job of securing your Wifi (64-character password [GRC]("https://www.grc.com/passwords.htm") and filtered by my MAC address in the router settings) then yes, I would enable usage of directly transferring without the need for SSH.  Also make sure your Wireless connection on your laptop is connected at the max speeds of your Wireless Router...

Example:

Linksys Wireless Router 802.11 b/g/n
+
Wireless Card "N"

Meaning, your router is capable of transferring at "N" level speeds (*802.11n* network equipment supports up to 300 Mbps of rated bandwidth)

and the laptop you are using, has a N level adapter installed or attached


Links:
[http://compnetworking.about.com/od/wireless/f/80211n-300-mbps.htm](http://compnetworking.about.com/od/wireless/f/80211n-300-mbps.htm)

---

### Post by Slim Odds on 2011-07-22
> **princeofnam said:**
> why is port 22 generally preferred?

I forgot this is obnoxiously slow (2.2 MB/s).  Would connecting the computers together with an ethernet cord perhaps quicken things? Right now the laptop is wireless and the desktop is wired.

22 is the default assigned port number for Secure Shell

[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)

Also, rsync is much better than scp for many files.

---

