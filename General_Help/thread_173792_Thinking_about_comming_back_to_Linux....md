---
title: "Thinking about comming back to Linux..."
date: 2006-05-10
forum: General Help
---

### Post by Patrick-Ruff on 2006-05-10
hey all, I'm considering comming back to linux again, but, there was only a few issus that drove me away from it in the first place, if such issues can be resolved, I'll gladly come back. here are the issues.. I was using Ubuntu Breezy on the following laptop..
1.6Ghz Pentium M 2MB L2 Cache
512MB Ram
dial modem (which I never could get to work and don't really expect to)
ATI's Mobility Radeon X300 64MB PCI-E
ALPS Touch Pad etc.

This is a Dell Inspiron 6000, and I had the following problems before I quit linux, 1. Lack of battery power in comparison to windows, I got a good 1-2 more hours on windows then Ubuntu, and I never saw the logic in that.
2. Could never get the video card to work to its fullist. couldn't even achieve 15FPS on Warcraft 3 (the only game I intend to play on this).
3. The LED WiFi light would never come on, and it got a bit annoying, since the FN F3 still turned on WiFi but the light never comes on... kinda hard. 
4. always had some trouble with the touch pad. could never really get full sensitivity, turn off tap clicking etc.


I'm pretty sure that was the only major issues that drove me away from Linux... can you guys help me?

thanks

---

### Post by djroadrash on 2006-05-10
i think the problem with your battery was related to acpi, just have to configure it correctly, the ati card on the laptop probably needs the correct drivers to work fully on 3D, the light i really don t know.
:KS

---

### Post by dickohead on 2006-05-10
You can try and get your graphics card working, but being an ATI it's doubtful. NVidia provides good support for Linux, but ATI does not.

With the touchpad you can turn that off using something similar to:
synaptics touchpad=0
search this forum for synaptic touchpad and you'll find an answer to that one.

did your wireless work at all? If there's just no lights that's not such an issue, but if it never powers up, you could try a different wireless card (Netgear WG511T works well), or do a google and see if anyone else has had success with your wireless card.

Battery life could be due to many things, but the mostobvious is probably CPU Scaling, when your processor is idle in XP it will drop the MHz down to a lower speed, Breezy does this, so too does Dapper. It doesn't work well with the 64bit install, but the i386 kernel on 32bit and 64bit processors works a treat and I get longer from Dapper than I did XP.

Your modem may work through something called: linmodems... I think, give it a google if it's an issue, otherwise I wouldn't worry too much.

---

### Post by nocturn on 2006-05-11
You could check it with the latest Dapper LiveCD

---

### Post by Patrick-Ruff on 2006-05-12
well...I want the little LED light working since its kinda annoying to be unaware if the wireless is on or not... kinda strange tho, I was able to get my graphics card drivers working 100% in SUSE 10, but theres not enough community behind it. but yeah the wireless works I just don't like the fact that the light doesn't work.

---

### Post by Patrick-Ruff on 2006-05-12
*bump* let this thread not be lost to all that exists.

---

