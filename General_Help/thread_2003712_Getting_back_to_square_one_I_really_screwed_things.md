---
title: "Getting back to square one? I really screwed things up."
date: 2012-06-14
forum: General Help
---

### Post by Roger-H on 2012-06-14
Okay, from the beginning: I installed Lubuntu 12.04 via USB stick onto a friends notebook computer, a Thinkpad R52. I set it up to dual boot between Windows XP and Lubuntu.

Everything was working fine except for the sound. It was not detecting the hardware. I Googled and found a page (cannot find it now) that recommended running a couple of commands to make sure that alsa was installed correctly.

Unfortunately, after I ran the command and came back, I saw that the command was installing Ubuntu (not Lubuntu) packages like Libreoffice, Gnome libraries, etc. Oh boy. I was concerned about interrupting this process, when the machine shut itself down (the machine has a problem with the CPU fan overheating, it does this sometimes.

I rebooted. It boots to Lubuntu, but now the LXDE panel is messed up and I can't seem to fix it, and there are various things like the scrollbars being replaced with the new-style Ubuntu ones. It's a mess.

Anyway, my first question is, how do I restore this back to a "vanilla" Lubuntu 12.04 configuration? After that, what is the best way to go about troubleshooting the sound?

---

### Post by deadflowr on 2012-06-14
Your bigger concern should be the CPU shutting down because of overheating, this should never happen, and can be detrimental to all other components within the system.

---

### Post by Roger-H on 2012-06-14
Yeah, I'm working on solving the hardware problem. There's no airflow under the notebook and I'm going to be blowing out the vents with compressed air. The friend is a smoker and there's most likely some crud in there that isn't helping things.

Any suggestions for the software issues?

---

### Post by Rodney9 on 2012-06-14
```
sudo apt-get install pavucontrol
```

Pavucontrol lets you select which sound source you wish to use.



For How-To's and Information on Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

For How-To Screen-Casts on Lubuntu

[http://blip.tv/rss/bookmarks/206798](http://blip.tv/rss/bookmarks/206798)

Rodney

---

### Post by Henkdroid on 2012-06-14
You could try:
```
sudo apt-get remove ubuntu-desktop
```
This should remove the Ubuntu stuff and put you back to Lubuntu.

---

### Post by Roger-H on 2012-06-16
Thanks so much to everyone for the guidance, that helped me set this system straight.

---

### Post by marinara on 2012-06-16
just use the usb to install lubuntu, and format the old lubuntu partition.  shouldn't take very long.
there's sound troubleshooting threads on the help.ubuntu.com wiki

---

