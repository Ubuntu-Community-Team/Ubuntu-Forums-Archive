---
title: "Wireless Networking Fail"
date: 2010-04-25
forum: General Help
---

### Post by Lancelot59 on 2010-04-25
Well I'm having an issue with my wireless networking. Every time I try to connect to my hidden network it just keeps spamming a big sign that says &quot;Disconnected&quot;. I'm not exactly sure what's going wrong here. I've tried disabling the devices and restarting them, and nothing seems to make this thing work. 

I haven't restarted yet, because I have some stuff to do still. So I'm stuck on a hardline. I'm running an HP dv7t. Does anyone else have any issues like this?

(Sorry, I just noticed this is in the wrong spot)

---

### Post by hopstah on 2010-04-27
I don't know if this will help you, but I was struggling for a long time to get my wireless (with WPA2 encryption) working under Linux.  It worked fine in Windows (XP and 7), but never in Linux.  It turns out that Ubuntu didn't like having a hidden SSID on my network.  Try un-hiding your SSID on your router to see if that helps.

---

### Post by P4man on 2010-04-27
Try narrowing the problem down a bit, by unhiding the access point (hiding am SSID  really doesnt help securing it btw, its trivial to scan for hidden networks) and by disabling WPA/WEP encryption (a more likely cullpit). Does it connect properly then?

Also tell us what wifi card you have. Open a terminal (programs > accessories > terminal ) and type in the following commmand:

```
lspci
```

and report the output here.

> Does anyone else have any issues like this?

unfortunately, yes. Many wifi chipsets have undisclosed specifications and the vendors arent releasing linux drivers, so  the only way to get them working under linux is reverse engineering windows drivers or lots of trials and errors. This works fine for a surprisingly large number of wifi chipset, but not all, and especially some new ones may not work perfectly (or at all) yet.

However, there is one workaround which almost always works, that is ndiswrapper. That lets you use windows drivers under linux (only for wifi cards). Its in the repository (or Ubuntu Software Center, look for "wireless windows drivers"), but lets first see what card it is and if we cant solve it using native drivers.

---

### Post by Lancelot59 on 2010-04-27
Yes I have the SSID hidden. I really didn't think it was that easy to scan for a hidden network. How does one do that?

Unforunately we might have to fake the windows drivers. My stuff has intel written all over it. I cut out the excess stuff to save space.

```

02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

For the most part it works pretty well. Occasionally on login it takes bloody ages to connect to the network. This is the first actual loss of connection I've had.

I wonder if ndiswrapper would also help with the audio issues I have.

---

### Post by P4man on 2010-04-27
> **Lancelot59 said:**
> Yes I have the SSID hidden. I really didn't think it was that easy to scan for a hidden network. How does one do that?


Security through obscurity rarely works. And especially in this case. I think its even possible from the command line, but if not, install something like [Kismet]("http://www.kismetwireless.net/index.shtml") and it will list all hidden SSIDs. Plenty of utilities for windows to do the same.
> 
Unforunately we might have to fake the windows drivers. My stuff has intel written all over it. I cut out the excess stuff to save space.

```

02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

For the most part it works pretty well. Occasionally on login it takes bloody ages to connect to the network. This is the first actual loss of connection I've had.

Thats a fairly common wifi card, and afaik its rather well supported. Did you update your ubuntu? What version are you running anyway?

Anyway, id still try unhiding the network as it serves no real purpose, see if that helps.

> I wonder if ndiswrapper would also help with the audio issues I have.

No. ndiswrapper is only for wifi drivers, nothing else. If you have posted about your audio problem, gimme a link.

---

### Post by Lancelot59 on 2010-04-27
If I remember correctly Kismet was a part of PHLAK.

I'm running Karmic and I keep it as up to date as possible. I'll unhide the SSID, hopefully that should eliminate the issue.

Here is the thread I made about the subwoofer issue, but nobody replied to it. [http://ubuntuforums.org/showthread.php?t=1353340](http://ubuntuforums.org/showthread.php?t=1353340)

I spent a lot of time searching around before making that post.

---

