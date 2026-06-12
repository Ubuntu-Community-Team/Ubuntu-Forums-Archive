---
title: "how do I get ubuntu 11.04 to recognize my external video card"
date: 2011-08-09
forum: General Help
---

### Post by cold37 on 2011-08-09
how do I get ubuntu to recognize my external video card?
i move my old hard drive from one computer to a new computer running ubuntu 11.04 how can i make it see the new video card?

---

### Post by Synoc on 2011-08-09
umm simply moving a hard drive from one PC to another can cause a system crash as it's set to use the original hardware. that said: you should first go to System> administration> additional drivers. 

that should see if you are using the current driver for your card. if it doesn't find the driver for you card, it should recommend one and ask you to use it, then it's jsut point and click, usually.

---

### Post by 3rdalbum on 2011-08-09
What video card, what does Additional Drivers say (does it offer a driver download?) and have you tried removing the xorg.conf file?

And what exactly are the symptoms of "it doesn't recognise the card"? Do you get a blank screen, or just no 3D acceleration?

---

### Post by cold37 on 2011-08-09
it was a nVidia and now Video adapter
Intel® Graphics Media Accelerator 950

---

### Post by Synoc on 2011-08-09
can you bring the old card to the new PC? or is it the wrong card type? Intel integrated Video cards are not a popular favorite of Linux. had one, it never worked right. the most common thing i heard from forums was "That should work"

---

### Post by cold37 on 2011-08-09
no that did not work i like to fix this i just dont know how

---

### Post by Mark Phelps on 2011-08-10
> **cold37 said:**
> no that did not work i like to fix this i just dont know how

3dalbumn asked you a bunch of questions.  If you're NOT going to provide answers, we can't help you here ...

---

### Post by 3rdalbum on 2011-08-13
> **cold37 said:**
> it was a nVidia and now Video adapter
Intel® Graphics Media Accelerator 950

Remove the xorg.conf file which is located in /etc/X11/xorg.conf.

Note, the Intel GMA950 is not an external video card, it's integrated on the motherboard. I think this got us confused.

If removing xorg.conf does not help, then please post back and answer the questions I asked before.

---

