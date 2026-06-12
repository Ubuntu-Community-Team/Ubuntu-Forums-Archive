---
title: "Network icon vanished"
date: 2011-08-27
forum: General Help
---

### Post by t0p on 2011-08-27
I used to have an icon on my top panel that would show me my network status (ie if the computer was online or offline).  But now, for no apparent (to me) reason, that icon has disappeared; and I can't find it in the "add to panel" menu.

What's happened?  How do I get the icon back?  I'm using Ubuntu 10.04.

Cheers!

---

### Post by CatKiller on 2011-08-27
I can't remember exactly what it was called in 10.04, but it's part of at least one of the Indicator applets. You also need to be running Network Manager.

---

### Post by Enigmapond on 2011-08-27
It's some kind of minor bug as I experience that on occasion. Most times I just reboot and it comes back. Another time I had to go to Startup Application, un-check the Network Manager and then check it again. Reboot and it's back...:confused: But I deal with it.

---

### Post by debd on 2011-08-27
the applet is called nm-applet

I had this problem when I used to configure my network through pppoeconfig

it used to reappear if my /etc/network/interfaces contained only
```
auto lo
iface lo inet loopback
```

I just used 
```
pon dsl-provider
poff dsl-provider
```

to start and close internet connections.

---

### Post by t0p on 2011-08-27
Thanks for the feedback.

I think I have discovered the problem.  Googling showed me that this often hands in when more than one user is signed in at a time.  Yesterday a friend was using my computer, then when she left, she didn't logout.  So, when I logged in, she was too, and I had no network icon.

Now I've logged her out and restarted and stuff, my network icon has reappeared.

Thanks to everyone who responded to my plea for help.  I think this problem is [SOLVED].

---

