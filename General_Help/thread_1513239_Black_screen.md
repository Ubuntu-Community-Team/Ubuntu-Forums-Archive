---
title: "Black screen"
date: 2010-06-19
forum: General Help
---

### Post by talool1210 on 2010-06-19
Hi!

I have an HP laptop pavillion dv2000 series with ubuntu 9.10 installed. I've been using ubuntu for over a year. Last night, while the laptop was running I closed the lid (screen) for 15 minutes then when I opened it back the screen was black. I moved the mouse and touched the keyboard but nothing happened. So I decided to switch it off from the power button. Once I turned on the power button, the screen turned black without showing the Hp logo or anything else. I started restarting it a lot of times but with no results. Is something wrong with ubuntu or with the laptop itself? What's the solution to my problem? I'm starting to worry that I may lose all my data.

Please help!

Thanks!

---

### Post by dino99 on 2010-06-19
dont worry about your data, its only a "resume" problem, boot into recovery mode, then watch logs (.xsession-errors and /var/log/)

---

### Post by irv on 2010-06-19
Put the live CD in the drive and boot to the live OS. If it boot find then you know it is not the laptop. Easy test.

---

### Post by talool1210 on 2010-06-19
How do I boot into recovery mode if I cant see anything?!

---

### Post by irv on 2010-06-19
> **talool1210 said:**
> How do I boot into recovery mode if I cant see anything?!

I take it you don't even see the grub menu?
To make sure it not your laptop screen hook a external monitor to you laptop and try boot with that. Can you hear you drive spin up when you turn on the laptop?
I had something like this happen on my old laptop, and what I had to do was unplug the power source remove the battery take the bottom of cover off the laptop and remove a small on the motherboard battery leave it sit for a few minutes. Then put everything back together and it booted up again. I am not say this will fix it, but if you have nothing else to try it's worth a shot.

---

### Post by dino99 on 2010-06-19
> **talool1210 said:**
> How do I boot into recovery mode if I cant see anything?!

at end of bios process, hold "shift" key down to see grub menu

---

### Post by smellyman on 2010-06-19
disconnect power and remove the battery.

Then reconnect....

---

### Post by talool1210 on 2010-06-19
I hooked my laptop to an external monitor but nothing appeared on it.

---

### Post by talool1210 on 2010-06-19
I kept holding down the shift key but also nothing happened.

---

### Post by talool1210 on 2010-06-19
And I also tried the live cd idea, also nothing appeared on the screen.

The laptop is simply running and the screen has a background light but it's black.

---

### Post by irv on 2010-06-19
Do the Battery and power thing and if that doesn't work, you have some hardware problems and may have to have it looked at. If you have any friends that know hardware have them take a look at it for you.

---

