---
title: "Black Screen After grub???"
date: 2010-08-12
forum: General Help
---

### Post by Franklin383 on 2010-08-12
Ok I installed Ubuntu 10.4 on a HP Pavilion a705w desktop and works great!!! I have a Emachines flat screen that I wanted to hock up to it. Well when I did, I got a black flickering  screen right after the grub, then after a few sec then nothing, I could see the mouse pointer, then i didn't, I see the mouse pointer, now I don't, (This was the flicker) Then black screen stayed and no mouse pointer. I tried the "e" at the grub and typed in the nomodeset trick and that did not work. I can hock up the old monitor and works great, its just to big for my desk and the flat screen would be why cooler.

Thinks

---

### Post by [Shawn] on 2010-08-12
I've had a simular issue.
Before I found out it was my graphics card giving me the trouble I seen a thread about the refresh rate.
Go to the display settings and move the Refresh rate to what It currently is to something lower.

---

### Post by Franklin383 on 2010-08-15
Well, right now i cant. When I boot the computer every thing go's good Intel grub....Then the screen (Monitor) starts making a clicking sound??? I cant do much of any thing???

BTW....I installed Ubuntu 10.4 inside of windows xp. I am going to delete the Ubuntu from add & remove programs and use the live cd and see if that helps. I read some where this mite be the case???

---

### Post by Franklin383 on 2010-08-15
Ok something is really wrong here....I deleted the ubuntu from add & remove programs in windows and booted with the live cd. Every thing go's great intell Installing Systems, About 53% into it and the installing system box went blank Just a wight box on the screen now and the hard drive light went out (not flashing) ??? If it where the display card wouldn't it NOT show the background?

---

### Post by [Shawn] on 2010-08-15
Does the LiveCD have any scratches or any type of damage?

---

### Post by Franklin383 on 2010-08-19
[Solved]....

Sorry its been a few days cents I last posted, I found what was wrong.....Shawn you where right , It was the graphics card. I was going to run install one more time, but this time I went into the BIOS to setup Ubuntu 10.4 to boot with a usb flash drive cents the cd/dvd was not working. I thought I would poke around and see what the BIOS was set to, and to my surprise the video was set to PCI not on board video...I do not have a PCI video. So I set it to (on board video) and it works great now. I did not know it would even show any thing on the screen with it set that way weird I know!! But all is working good now thinks for the help!!!!

---

