---
title: "remote desktop help"
date: 2006-04-25
forum: General Help
---

### Post by leftyman on 2006-04-25
Hello:

Excuse me for my newbie question, but I really have no idea about this:

I have setup a network in my house and succesfully shared files with samba.

I have my computer (ubuntu) as 192.168.1.2
I have my gaming computer (windows xp pro) connected to my tv in the hall of the ouse (by the way it is 192.168.1.4).

I think (I am not sure) I can remotely log into windows from my ubuntu and have a virtual desktop and do things in the remote computer (even graphically as if I was in front of my windows).

Is this possible?

Is there a howto on this, that tells me what ports to open in my router and in windows xp firewall, what protocols to install and so?

thank you

---

### Post by nanotube on 2006-04-25
[QUOTE=leftyman]Hello:

Excuse me for my newbie question, but I really have no idea about this:

I have setup a network in my house and succesfully shared files with samba.

I have my computer (ubuntu) as 192.168.1.2
I have my gaming computer (windows xp pro) connected to my tv in the hall of the ouse (by the way it is 192.168.1.4).

I think (I am not sure) I can remotely log into windows from my ubuntu and have a virtual desktop and do things in the remote computer (even graphically as if I was in front of my windows).

Is this possible?

Is there a howto on this, that tells me what ports to open in my router and in windows xp firewall, what protocols to install and so?

thank you[/QUOTE]
dont know about a specific howto, but look at tightvnc or ultravnc for remote desktop type stuff.

---

### Post by OffHand on 2006-04-25
Download VNC and install it on XP.
To control my Mac I use xvncviewer.
```
sudo apt-get install xvncviewer

```

---

### Post by yopnono on 2006-04-26
Use Gnome-RDP or tsclient. But the Gnome-RDP support remote sound much better.

---

