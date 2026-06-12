---
title: "Remote desktop non-local connection... ?"
date: 2010-03-15
forum: General Help
---

### Post by Hado on 2010-03-15
Under remote desktop in
System > Preferences > Remote Desktop

There is a line that says:
"Your desktop is only reachable over the local network. Others can access your computer using the address ***.***.0.**."

But there are no clear options to allow my computer to access my desktop from a non local network.  How can I get my laptop to connect to my remote desktop at home from a distant connection?

---

### Post by Arekun on 2010-10-21
i'm having the same problem

---

### Post by KeyserSoze93 on 2010-10-22
Port forwarding.

Install openssh-server.

Set up your router to forward port 22 to your desktop PC (with the IP your VNC server told you you could access your PC from.)

 Every router is different - see your manual.

Visit whatsmyip.com or the like to find your external IP.

Then, install xtightvncviewer on your laptop and run something like:

```

xtightvncviewer -via *.*.*.* localhost

```

Where *.*.*.* is your EXTERNAL IP (not what is says your IP is on your LAN, but what it says when you visit whatsmyip.com from your home PC.)

You'll need to enter your computer password to authenticate SSH. If you plan to keep port 22 open on the router, consider using keybased SSH authentication.

Hope it helps. It sounds a bit complicated but it's not too hard and it's pretty useful.

---

