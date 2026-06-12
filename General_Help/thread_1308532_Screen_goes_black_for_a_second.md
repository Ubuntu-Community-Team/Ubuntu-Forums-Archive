---
title: "Screen goes black for a second:"
date: 2009-10-31
forum: General Help
---

### Post by Oranges10e on 2009-10-31
Hi,

right to the problem: I hooked up my 26" fullhd to my Laptop with UNR 9.10. 

I had to do a sudo nvidia-xconfig first to make things work, because I couldn't save my settings with the nvidia-settings. Anyway, after it created a new .xorg file and I got my external LCD running, my screen seems to go black for about a second or less. It's like the blinking of an eye. This is extremely annoying. What could be causing this? I am using the 185 rec. drivers.

Edit: I have tried the 177 and 190 drivers, same result. This happens only as soon as I install the drivers. Without drivers this doesn't happen.

Thanks.

Oranges

---

### Post by Oranges10e on 2009-11-01
push

---

### Post by P4man on 2009-11-01
I dont understand the problem.. it goes black once per boot? Constantly?

---

### Post by Oranges10e on 2009-11-01
Hi,

it goes black constantly.

Once it has sucessfully loaded the desktop, normal boot (everything fine), and I start using my computer, like always, then suddenly, at random, my screen goes black for half a second and then continues as normal. It's like the "blink of an eye" - it's that short but very disturbing. This happens every few seconds and more often every few min. I have manually installed the newest Nvidia drivers (190) to see if they could actually fix this - they didn't.

---

### Post by P4man on 2009-11-01
> **Oranges10e said:**
> Hi,

it goes black constantly.

Once it has sucessfully loaded the desktop, normal boot (everything fine), and I start using my computer, like always, then suddenly, at random, my screen goes black for half a second and then continues as normal. It's like the "blink of an eye" - it's that short but very disturbing. This happens every few seconds and more often every few min. I have manually installed the newest Nvidia drivers (190) to see if they could actually fix this - they didn't.

Sounds like a problem with the tv or cable to me

---

### Post by Oranges10e on 2009-11-01
Hi, it's not a tv, it's a normal LCD fullhd monitor connected via VGA. I have already used a different cable. Like I said, this only happens once the Nvidia drivers are installed, without them, everything is slow but it doesn't do that blackout thing.

PS: Now I am using only one of the LCD's and everything is fine, it's connected digital, though. As soon as I switch over to the other screen or activate it, this problem shows itself once again.

Oranges

---

### Post by P4man on 2009-11-01
> **Oranges10e said:**
> Hi, it's not a tv, it's a normal LCD fullhd monitor connected via VGA. I have already used a different cable. Like I said, this only happens once the Nvidia drivers are installed, without them, everything is slow but it doesn't do that blackout thing.

Oranges

But without the drivers where you able to select the native resolution? I assume the monitor does 1920x1080. Thats more than you should try over an analogue VGA cable. You could try reducing it to 1280 or sonething and see if that cures the black flickering.

---

### Post by Oranges10e on 2009-11-01
Why shouldn't higher resolutions be used via VGA? o,O

Anyway, actually the LCD can do 1900x1200 but I often leave it at 1920x1080. 

Yes, without the Nvidia drivers Ubuntu auto. adjusted the nativ resolution of the LCD. To go down a few resolutions is not an option for me. I paid for the high resolution and I want to use it, especially with fullhd movies. Funny thing is, this didn't happen to me with Jaunty on the same hardware (I've already swapped in my other HDD and tried it, with Jaunty it works without a prob.). 

I remember this problem. I was using the Ubuntu beta without probs, then once all the RC updates came, something must have done this, because this problem started then. 

Oranges

---

### Post by beacon on 2009-11-04
My problem is not quite the same but is obviously related. Whenever I go to Thunderbird, I have the flicker that oranges mentions. The screen doesn't go blank, but as the writer says, there is a fliciker like the blink of an eye, and the screen seems to readjust. It's nothing major (I hope), but annoying. This has only happened since upgrading to Koala.

---

### Post by Oranges10e on 2009-11-04
We are not alone: [http://ubuntuforums.org/showthread.php?t=240399&page=3](http://ubuntuforums.org/showthread.php?t=240399&page=3) 

Oranges

---

### Post by Tetert on 2009-11-15
I have the same issue, but my system freezes straight after the flickering

---

### Post by mac25 on 2009-11-23
I have the same problem on my Quad core AMD dvi connection 64 bit.
Wife's dual core AMD vga connection 32 bit, both Karmic K.
Both use Nvidia restricted drivers, 32 bit on board graphics, 64 bit
7600gt PCIe 2.0 card.

---

### Post by P4man on 2009-11-23
I have seen too it I think. Yesterday I saw it for the first time  and could reprodcuce it by zooming in (using compiz) and then a right click in firefox would cause a sub second black flicker each and every time, A reboot fixed it, havent seen it since. Also using nVidia 185 drivers on a 7900GS. Interestingly I have two monitors, one VGA one DVI and the problem only occurred on the primary monitor which uses VGA.

---

### Post by diamondnular on 2009-11-29
I also have the same annoying problem. I connect my GTX 260 with a Sharp 40" with full HD (1920x1080) resolution. It does happens randomly with normal desktop (less frequent) but very frequent especially when I watch movies. Have been having it for months since upgrading to Jaunty and never found any solution yet.

D.

---

