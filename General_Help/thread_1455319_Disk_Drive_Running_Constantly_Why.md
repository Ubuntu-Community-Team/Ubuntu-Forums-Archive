---
title: "Disk Drive Running Constantly? Why?"
date: 2010-04-15
forum: General Help
---

### Post by redwoodguy on 2010-04-15
System:
Ubuntu 9.10
Gateway SX2802 (Core 2 Quad)
4GB RAM
750GB drive

Everything was fine for the first 6 months. Now in the past couple weeks, my disk drive is running nearly constantly. I can hear it rattling away in the background no matter what I am doing. Typically, I just have Firefox open, and that disk drive is sounding like it's writing the whole thing over and over. 

I've opened the system monitor and looked for something obvious, but everything says, "sleeping". The computer seems to operate fine - no crashes, no odd behavior. 

What's this thing doing?

---

### Post by lovinglinux on 2010-04-16
The problem persists when you close Firefox?

---

### Post by redwoodguy on 2010-04-25
Ok, I believe I have found the problem and made the fix. I opened my Firefox add ons and I disabled "speed dial" and "Gmail Notifier." Problem gone. I don't even know how Speed Dial got installed. I don't ever remember adding it. It apparently is always looking ahead to your favorite sites and caching them. 

Everything now seems normal. Man, that was driving me nuts.

---

### Post by lovinglinux on 2010-04-25
> **redwoodguy said:**
> Ok, I believe I have found the problem and made the fix. I opened my Firefox add ons and I disabled "speed dial" and "Gmail Notifier." Problem gone. I don't even know how Speed Dial got installed. I don't ever remember adding it. It apparently is always looking ahead to your favorite sites and caching them. 

Everything now seems normal. Man, that was driving me nuts.

Each Spee Dial bookmark has an option to check for site updates, so it draws the thumbnail again on a regular interval. You can disable that in the preferences, so when you create new dials they don't update automatically. Additionally, you can change the behavior for each dial individually, by right-clicking on them and selecting "Edit", then setting the "Refresh" option to "Never". Your problem was probably not Spee Dial fault, but a problematic site being loaded by it.

---

