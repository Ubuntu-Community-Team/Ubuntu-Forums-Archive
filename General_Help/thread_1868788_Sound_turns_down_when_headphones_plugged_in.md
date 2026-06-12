---
title: "Sound turns down when headphones plugged in"
date: 2011-10-24
forum: General Help
---

### Post by keyblademaster on 2011-10-24
Hey guys, I'm on 11.10 and whenever I plug in headphones, the volume turns down to quiet levels. If I go into alsamixer and turn up the "speaker" volume, it comes back. Any help?

---

### Post by oldtimer7777 on 2011-10-24
> **keyblademaster said:**
> Hey guys, I'm on 11.10 and whenever I plug in headphones, the volume turns down to quiet levels. If I go into alsamixer and turn up the "speaker" volume, it comes back. Any help?

Open sound preferences and select from the drop down menu in Output either Analogue Headphones or Analogue Speakers and see which helps the most.

---

### Post by keyblademaster on 2011-10-25
same issue with both.

---

### Post by oldtimer7777 on 2011-10-25
> **keyblademaster said:**
> same issue with both.

What kind of hardware are you running?

---

### Post by keyblademaster on 2011-10-25
It is an asus n53sv.
([specs here]("http://www.asus.com/Notebooks/Multimedia_Entertainment/N53SV/"))

---

### Post by oldtimer7777 on 2011-10-25
> **keyblademaster said:**
> It is an asus n53sv.
([specs here]("http://www.asus.com/Notebooks/Multimedia_Entertainment/N53SV/"))

Does this happen when you boot from a live stick of Ubuntu 10.10 Maverick?  Is the sound problem still there? Make one with Startup Disc Creator to compare on a thumb drive to quickly check it. Could be really simple.

---

### Post by keyblademaster on 2011-10-25
ok. i had an old live cd laying around of maverick, so i booted up and had the same issue.

---

### Post by effenberg0x0 on 2011-10-25
Speakers should mute, HP should have sound at normal levels when you plug a HP. 

Maybe Realtek ALC269 jack sense is not supported out of the box with current driver. 
ALC892 right now is not supported, maybe others aren't too. 

Please file a bug report on Launchpad for package alsa-driver. Go to [https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect) and use a descriptive title like "Realtek ALC269 HP Jack Sense not working". 

Alsa devs may request specific tests for you to perform.

Regards,
Effenberg

---

### Post by keyblademaster on 2011-10-26
Great. Thanks guys. :mrgreen:

---

### Post by soldave on 2011-10-26
Having this exact same problem and it's damn annoying with 11.10.

Let me know if you find any solution to it.

---

### Post by oldtimer7777 on 2011-10-26
> **soldave said:**
> Having this exact same problem and it's damn annoying with 11.10.

Let me know if you find any solution to it.

When I reboot my 11.10 system after making changes to Sound Preference, they revert back to the default settings. I want to set my audio output for Headphone jack only.  It works, but then it forgets the settings after I reboot. Really annoying when I have my headphones on and I reboot in the middle of class.. 

But of course this doesn't happen in 11.04 or previous versions..

---

