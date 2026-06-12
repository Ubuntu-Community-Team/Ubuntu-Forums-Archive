---
title: "Vbox best setting"
date: 2009-12-30
forum: General Help
---

### Post by escaleraroyal on 2009-12-30
My Hp laptop has
core2duo 1.6 ghz
3 gb ram
128mb video card

Installed virtualbox:
guest Ubuntu
host Win7

What is the best sytem setting I should give to guest Ubuntu?
Currently, I gave 128mb video card (total size, also used 64mb) and 400mb ram.

But somehow Ubuntu is still slow in Virtualbox. Any ideas why? Is it the setting conf which is lagging it? Anyone could share some light?:(

---

### Post by barnex on 2009-12-30
Have you installed the Guest Additions (Devices>Install Guest Additions)? That makes quite a difference for e.g., the video performance.

Other tips: Use a virtual SATA hard disk instead of the default IDE disk. I also guess giving your guest less video memory and more normal RAM might speed things up. Finally, try playing with the virtual machines advanced settings. Some of them say they "slightly" decrease performance but can actually matter a lot.

---

### Post by nerdtron on 2009-12-30
Ubuntu guest on Windows host is slower compared to Windows guest on Ubuntu host based from my experience.
Since you have dual core cpu, try allocating both cores to the guest especially if you are running it in seamless mode.
I think CPU and hard drive speed is the bottleneck for a virtual machine.

---

### Post by howefield on 2009-12-30
Guest additions and improve the ram.

400 megs is fairly low, although it_should_run ok at that. Give it a gig of RAM.

---

### Post by escaleraroyal on 2009-12-31
Played around with the Vbox setting. I'm using 128mb for the video card and 1500 RAM and piix3 IDE controller type. These settings did the trick and my Ubuntu guest is running faster than never but after a day on Ubuntu seems to lag again.:(

---

### Post by howefield on 2009-12-31
What do you mean by "after a day"

Is that a day of continual running both the host and the guest simultaneously ?

Does it get better after a reboot ?

---

### Post by escaleraroyal on 2009-12-31
> **howefield said:**
> What do you mean by "after a day"

Is that a day of continual running both the host and the guest simultaneously ?

Does it get better after a reboot ?


Yes, a continual running bot the host and the guest.

it guest better after a reboot. But I don't wanna reboot it.

---

