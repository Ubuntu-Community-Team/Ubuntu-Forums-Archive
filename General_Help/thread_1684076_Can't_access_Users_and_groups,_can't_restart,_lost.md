---
title: "Can't access Users and groups, can't restart, lost icons in notification panel"
date: 2011-02-08
forum: General Help
---

### Post by kralleman on 2011-02-08
Hi!
When I started up my laptop this morning alot of stuff was wrong. I first noticed that my network notification icon had dissappeared along with the battery status indicator. I could not connect to internet, not even with a cable. I tried to restart, but to my surprise this was no longer possible from the menu. I was logged out instead, and the same happened when I tried to shut down from the menu. I also tried to access "Users and groups" from the system menu but all I got was an error message.

Someone tried to help me with the networking stuff but it he couldnt figure it out (I think he was trying with the network manager). We also tried to add the network manager icon back in the startup applications, but it still did not load.

The weird thing is that I've been running ubuntu on that laptop for a month or something and I've been doing updates regularly and I've had no problems with these things. I did nothing special with the laptop yesterday and when I turned it off everything was working.

[B]Anyway, my problems are:
- I'm a newbie when it comes to Linux
- Cannot restart/shutdown from menu (sudo reboot works from terminal)
- Cannot access "Users and Groups" from the systems menu
- Missing network and battery status icons in the top right part of the panel
- Internet is not working, not even with a cable[/B]

Laptop is pretty useless without these functions so help is most welcome!

---

### Post by kralleman on 2011-02-08
For some reason I now tried "killall nm-applet" from the terminal and it returned "nm-applet: no process found". I then tried to start it using "sudo nm-applet" (i was not allowed to start it without the sudo command for some reason) and it returned:
"(nm-applet:13328): DEBUG: old state indicate that this was not a disconnect 0"

This shows the icon in the panel but if i click it it says that the wired network is disconnected and that the wireless network devices are not ready. This of course was not the case yesterday when I was able to use internet.

---

### Post by kralleman on 2011-02-08
Noone?

I've been googling for hours now. Starting to get really pissed with these annoying bugs.

---

### Post by kralleman on 2011-02-08
I'm solving this right now by re-installing Ubuntu. Painful, but I can't really spend more time on it.

Hopefully someone figures this out for other people with the same problem.

---

