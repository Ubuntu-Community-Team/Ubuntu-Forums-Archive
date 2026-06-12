---
title: "Samba, networking ubuntu/ubuntu"
date: 2009-11-18
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-11-18
I have a wireless network between a lappy (ubuntu) and a desktop (ubuntu).For the most part I have no problem w/ it, Until I reboot either machine. Once logged back in the network is gone. I been going through a process of removing from sysaptic, and letting samba install again from creating a shared folder. Does samba not start upon boot-up?

---

### Post by Giblet5 on 2009-11-18
I'd start with the networking issue. That's the biggie.

Are you using wireless, or ethernet? Static IP, or "automatic"?

---

### Post by Feelin_froggy8877 on 2009-11-18
The lappy is wireless, connected to a linksys router witch is connected to desktop through ethernet. IP I believe is automatic.

---

### Post by Giblet5 on 2009-11-18
Nice setup! I assume that you configured network-manager to automatically connect to the defined networks. Is that correct?

I never use network-manager. IMO, it's not ready.

I install wicd (removes network-manager). It has a better interface, it has a better icon, it does more in a smaller footprint. Then I drop the nm-applet from the startup applications since it obviously won't work anymore. Log off. Log in. Better network management is yours.

That will fix the network issues.

As for Samba, it should start at reboot. Mine does.

Take a look at /var/log/samba/log.smbd and see if there's an obvious problem.

---

### Post by Feelin_froggy8877 on 2009-11-18
Thanx, and no i have not actually configured anything. Only installed samba. Ill install wicd and see what I can get into.

That's the weird thing, I loose my network on every reboot.

---

### Post by nikgare on 2009-11-18
If you're just doing linux/linux networking, you'll probably get better results if you use nfs.
This is a good (and simple) guide:
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

---

### Post by Feelin_froggy8877 on 2009-11-18
Ok, for the configuration for nfs, the server would be the desktop and the client would be the laptop, correct? So how would I find out the ip's of each. The configuration of networking w/ linux just seems kinda confusing.

---

### Post by Feelin_froggy8877 on 2009-11-25
any assistance w/ this?

---

### Post by audiomick on 2009-11-25
Hi.
As far as I know, trying to allocate fixed IPs on a linux machine opens a big ugly box, but I could be wrong. We'll wait for other opinions on that.

My solution to wanting to know what IP is who was to reserve IPs in the router. 
You'll need to know the MAC address of your network interfaces. They are usally on a sticker on the case somewher. If there not, there are tools that will read them, but I am afraid I don't know them off hand.

---

