---
title: "Heating problem between 10.04 and 11.10"
date: 2011-11-22
forum: General Help
---

### Post by deserthowler on 2011-11-22
I'm dual booting on a Dell 1400 N with Ubuntu 11.10 and 10.04.  I don't use 11.10 very much, I usually use open it to do updates and that's about it.  I've been using 10.04 most of the time as I really like it and don't need the latest/greatest.  It works so I'm sticking with it.

I haven't run 11.10 much but yesterday I ran it quite a while.  My computer seemed outrageously warm/hot so I checked the temperature with xsensors and got a temperature of 70 + Centigrade.

I switched to 10.04 and the temperature almost immediately went to 30 + Centigrade.  It usually runs somewhere in the 30 40 Centigrade range.  It felt much cooler to the touch.  I didn't wait for the computer to cool but did a cold reboot and started 10.04 almost immediately.

Earl

---

### Post by 2F4U on 2011-11-22
What graphics card and driver do you use? What desktop environment do you have in 11.10? Unity and KDE with effects enabled may cause the graphics card to get hot. Are there processes running in the background that place a high demand on the CPU?

---

### Post by deserthowler on 2011-11-24
OK.  It's not Ubuntu's fault, it's mine. :redface: I followed some instructions to install MATE from an Internet blog.  All the heating was involved with MATE.  When I switched back to Unity, the temperature went down almost immediately.  Fortunately I backed up the system before I did the install of MATE.  OK, lesson learned.  To paraphrase my biologist friend, "Don't date outside your distro."

Earl

---

