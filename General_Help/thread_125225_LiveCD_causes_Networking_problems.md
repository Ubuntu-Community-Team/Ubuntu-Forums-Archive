---
title: "LiveCD causes Networking problems"
date: 2006-02-03
forum: General Help
---

### Post by C J Pro on 2006-02-03
I gave my friend a LiveCD of Ubuntu.  After using the Live CD to try Breezy, he was unable to connect to the internet in Windows XP.  And when he reinserted the Live CD into his drive, Ubuntu was unable to connect to the ntp server and was also unable to connect to the internet.  I'm checking on DNS settings right now as I have the same ISP as him and have had problems with their DNS before.  But is it possible that a Linux Live CD can cause this?

---

### Post by dcstar on 2006-02-03
[QUOTE=C J Pro]I gave my friend a LiveCD of Ubuntu.  After using the Live CD to try Breezy, he was unable to connect to the internet in Windows XP.  And when he reinserted the Live CD into his drive, Ubuntu was unable to connect to the ntp server and was also unable to connect to the internet.  I'm checking on DNS settings right now as I have the same ISP as him and have had problems with their DNS before.  But is it possible that a Linux Live CD can cause this?[/QUOTE]
Possibly his network card settings were changed, a power off (pulling the power plug out, not just the front switch) may reset the card and fix the problem.

---

### Post by stream303 on 2006-02-04
[QUOTE=C J Pro]I'm checking on DNS settings right now as I have the same ISP as him and have had problems with their DNS before.  But is it possible that a Linux Live CD can cause this?[/QUOTE]

The first thing I check when running a live-cd that seems to have slow or time-out dns problems is **/etc/resolv.conf** and make sure that the nameserver(s) are the same as your isp's nameservers.

If not, a quick temporary fix is to manually edit **/etc/resolv.conf** to make sure that your isp's nameservers are the first ones in the list.   (sudo gedit /etc/resolv.conf)

Are you using a broadband modem and a router running dhcp?  If so, it might be possible that your /etc/resolv.conf is being overwritten on each reboot / re-lease.

---

### Post by alamba on 2006-02-04
And to answer your question...no..live cd is not and can not create this problem on your xp installation. /etc/resolv.conf is your best bet unless your ISP DNS itself is acting up.

A

---

