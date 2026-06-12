---
title: "Connect a few linux boxes"
date: 2011-05-11
forum: General Help
---

### Post by TeaGoblin on 2011-05-11
Hey

I would like to set up a connection between four laptops. I want to use this connection in three ways, so perhaps three different solutions might be needed:

1- I want to be able to remotely administrate the other linux laptops via a console, not graphical desktop sharing.

2- I want to be able to view those remote desktops, so graphical desktop sharing.

3- I want to be able to share files (photos, music) between the laptops.

I use KDE, those laptops use Gnome. Three of the laptops connect to the same router, the fourth is in a different country.

Please suggest what solutions (protocols and clients/servers) you would recommend that I use for these three needs.

---

### Post by nothingspecial on 2011-05-11
ssh with X forwarding.

---

### Post by carl4926 on 2011-05-11
> **nothingspecial said:**
> ssh with x forwarding.
+1      :-)

---

### Post by TeaGoblin on 2011-05-11
What about point 3?
Point 3 must be simple enough for noobs to use, they must be able to just copy and paste files in a file manager.

---

### Post by nothingspecial on 2011-05-11
nautilus-connect-server

over ssh

---

### Post by carl4926 on 2011-05-11
> **TeaGoblin said:**
> What about point 3?
Point 3 must be simple enough for noobs to use, they must be able to just copy and paste files in a file manager.
Yes
ssh via Nautilus

You might want to be careful though. Port 22 the default ssh port is better changed
I use a public key + password login too

---

### Post by TeaGoblin on 2011-05-12
I'm having great results with X over ssh, still need to try nautilus over ssh.

---

### Post by carl4926 on 2011-05-12
Just choose File > Connect to Server > ssh >
Enter the details

However my Ubuntu or Mint servers don't like my settings
openSUSE has no problem
Still not figured it out because I can ssh to them from a terminal and use fish:// from kde remotes :confused:

---

### Post by TeaGoblin on 2011-08-03
Works great!

I use this in Dolphin:
fish://remoteuser@ip:port/home/user/

e.g.
fish://john@192.168.0.100:80/home/johnf/

---

