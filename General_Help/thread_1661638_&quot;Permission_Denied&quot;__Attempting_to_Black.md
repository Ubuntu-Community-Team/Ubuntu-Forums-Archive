---
title: "&quot;Permission Denied&quot; / Attempting to Blacklist rt2800pci"
date: 2011-01-06
forum: General Help
---

### Post by Serson_Person on 2011-01-06
Hey,

I've been trying to fix an issue with NetBook 10.10 freezing on shutdown.  I found another post which I'm assuming may be my solution, but I get a permission denied when I try to follow it's instructions.

Here's the post:

> 
                                  **Re: Shutdown problem with netbook version 10.10**             
                                                                     Quote:
                                                                      Originally Posted by **WrightPC**                     [[IMG]http://georgia.ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://georgia.ubuntuforums.org/showthread.php?p=10199111#post10199111")                 
                 [I]I found my answer [here]("https://answers.launchpad.net/ubuntu/+question/132350").
Add "blacklist rt2800pci" to "/etc/modprobe.d/blacklist-wlan.conf" with the following command:
     Code:
     sudo echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist-wlan.conf 
then reboot. 

Suspend to Ram works reliably.
Hibernate to disk works reliably.
Random boot failures have disappeared.

All is well.[/I]
                                 


Hi, I'm sure this post is older but it looks like what I need to do,  however when I type the line in the terminal is says "Permission Denied"

Know any way past this?



---

### Post by Krytarik on 2011-01-07
Just try it that way:
```
sudo gedit /etc/modprobe.d/blacklist-wlan.conf
```

---

### Post by Serson_Person on 2011-01-09
Thanks man,

Shutdown/Suspend/Restart related issues conquered...

Any cure for random freezes?  I've heard Debian is a fairly stable OS, but I am in love with Ubuntu for some reason.  So if I can figure out this random freeze problem that would be awesome.

I don't know if anything in particular causes it, but sometimes the computer will just freeze and lock up, and the only thing that can be done is hold the power button til it turns off.

---

### Post by Krytarik on 2011-01-09
As you may already know, Ubuntu is based on Debian, thus I wouldn't expect a heavy increase in stability. But a reasonable decrease in usability.

That freeze thing is indeed a bummer, look in "/var/log/messages" for any valuable error messages.

---

### Post by Serson_Person on 2011-01-11
Yeah, I know Ubuntu is based of Debian.  In fact, many of the questions I search on Google about Ubuntu, end up having somebody within the forum recommending Debian.

I've also read in posts that it's basically a hardware compatibility issues, so I guess now I'm wondering are compatibility issues fixed through updates in time, or is it basically game over?

---

### Post by Krytarik on 2011-01-12
I've not heard that about Debian more often. In fact I would even say that the hardware support is better in Ubuntu. Anyway, it seems that much people are having difficulties with wifi cards and their respective drivers. I cannot confirm that personally, the wifi card of my mum's machine runs just fine with Ubuntu, though we had indeed some issues back in Gutsy 7.10, periodically disconnects, I upgraded the machine last summer.

Greetings.

---

