---
title: "Cant even run live cd"
date: 2012-09-14
forum: General Help
---

### Post by Stooshie90 on 2012-09-14
So my brother sent my mother an old laptop he had with windows xp installed but I discovered it has the virut virus on it, and as there is no recovery console installed, and he has sent no discs with it, (im assuming he has none now), I planned to install ubuntu for her.
The problem is, when i boot up the live cd it goes to the square with the two little icons at the bottom, then just a black screen with a flashing line and stops there.
I know the cd works, I tried it on my windows 7 pc, so Im wondering if its the laptop or should I just wipe the drive first.
Dont know much about the laptop, its a presario 2100, looks a few years old, and getting any info from my bro would be next to impossible.
Any advice would be appreciated.

---

### Post by mike555 on 2012-09-14
You might need to push F6 and click "nomodeset" during startup, I think that laptop has ATI graphics card.

---

### Post by Stooshie90 on 2012-09-14
Yes it does. Ill give that try and let you know

---

### Post by Stooshie90 on 2012-09-14
Ok, showing my lack of technical knowledge here, but pressing f6 just brings up the battery calibration for me.
Add to this, also tried it when it loads cd, but just get black screen.

---

### Post by mastablasta on 2012-09-14
see here on where you do this: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
otherwise you might need alternate CD or try Lubuntu (which doesn't use PAE kernel)

---

### Post by Stooshie90 on 2012-09-14
Lubuntu looks more promising, I get the languages and F options, but hitting F6, or even enter on English just seems to freeze it, and leaving to countdown brings up just the flashing line.
i dont know whther to try it with a formatted drive, doubt if that will make a difference, or just give it up as a loss.

---

### Post by shreepads on 2012-09-14
Go Minimal:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

All hail the psychocats!
:lolflag:

---

### Post by CrusaderAD on 2012-09-14
You could try booting from a USB stick and see if that makes a difference.

---

### Post by BrianBlaze on 2012-09-14
I had the same problem and for me the solution was the nomodeset option but to get to it once Ubuntu is loading I hit the left SHIFT button and then a bunch of languages pop-up, I press esc, then I press F6 to choose the nomodeset option :) Hope it works!

---

### Post by Stooshie90 on 2012-09-14
Tried your suggestions now, none worked. I also tried Gparted to wipe the drive clean but it suffers the same fate.
Its like the dvd drive just stops reading, so I think Im going to have to write off this laptop.

---

### Post by rickm1945 on 2012-09-14
Did you try to format your HD before you attempted install?

---

### Post by rickm1945 on 2012-09-14
> **Stooshie90 said:**
> Ok, showing my lack of technical knowledge here, but pressing f6 just brings up the battery calibration for me.
Add to this, also tried it when it loads cd, but just get black screen.

Before you press f6. When at first boot screen with the design at the bottom, press any key, I use the space bar. That will bring up a screen to pick your language, pick yout language, press enter, then  the menu screen will come up then press f6 and with arrow keys go down to "nomodeset" tick/check nomodeset. press esc. key and use live cd or install. There are a couple of choices there. I had the same problem. Hope this helps you. Good Luck

---

### Post by BrianBlaze on 2012-09-14
> **Stooshie90 said:**
> Tried your suggestions now, none worked. I also tried Gparted to wipe the drive clean but it suffers the same fate.
Its like the dvd drive just stops reading, so I think Im going to have to write off this laptop.

CD'S!? Bootable USB's are where it is at these days... also I had an old acer that had the same problem it couldn't read cd's properlly but with bootable USB's I was fine :)

---

