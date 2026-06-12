---
title: "screen turning black after 5 secs of work"
date: 2009-09-12
forum: General Help
---

### Post by peachtree195 on 2009-09-12
I am running Jaunty 9.04, a quite fresh change from Windows, which i got rid of a few weeks ago. Yesterday what happened to me - in the middle of a conversation with someone via skype, not even touching the computer, the keys, the touch pad - the screen turned black and this is how it stayed. The skype conversation was unaffected though. All this happened out of nowhere. When i tried to restart it - it was okay at the beginning when you see the log-in screen and options of a start then turned black again after 5 secs of being there. Acutally when you take a really close look at it - the screen is not entirely black - you can hardly see the desktop through, but impossible to do anything or read anything. Almost totally black.

Turning the light in screen settings up does not help of course.

The gnome failure-free version at startup runs perfectly - screen looks great, just like always, like nothing happened.

---

### Post by P4man on 2009-09-12
sounds like the backlight is turned off.
A possible quick fix: press control alt F1 to open a (non graphicsl) full screen terminal, then press control alt F7 (or possible F8 or F9) to return to the GUI. IS stuff visible again now?

something else to try, go to system > prefences > power management and turn off the "dim screen on inactivity" (I think its called, not on a laptop here).

---

### Post by peachtree195 on 2009-09-14
Hey, thanks for your help - i tried both, no luck. When you change to terminal - the "normal" light level stays on for about a few seconds, then goes black, when you go back - the same - it goes back on but quickly gets black. Actually it sometimes stays on longer with the terminal turned on only. I did some research about this - it is a hardware problem. Some said it was the backlight, some it was the inverter - a little device under the screen that produces the right voltage for the backlight of the monitor. Someone smarter than me have informed me that first i should try replacing the inverter (around 10 dollars), because this is what goes down first when there is no obvious mechanical injury to screen, then in the second line think of a backlight. Then he said that even though the replacement backlight is inexpensive to purchase it requires a dust-free environment and some experience to replace it the right way - so without any specialized help he recommends rather replacing the whole screen instead. The inverter - on the contrary - seems easy to mount - i just took the screen frame off and the cables coming in and out of an inverter are mounted on clips so you basically click it out, put a new one in clicking it in.

Well, thats what i could find out - perhaps this might help somebody else, too. If all this is not just a piece of misinformation that someone gave me - looks like the first helping post from my side. Just give me more beans for it! :)

I will let you know how the replacement worked out and whether it was the thing.

---

### Post by P4man on 2009-09-14
If you are in the BIOS or grub screen, does the screen turn black as well? If it does, I agree its a hardware issue. If it doesn't, then probably its not a hardware problem, but a software problem related to your backlight. I had it in ubuntu 8.10 on an acer laptop, after logging in, or when resuming from standby, the backlight would be off (switching to a tty and back did solve it for me though).

Im not sure if you are using a laptop or PC, but doing your own soldering on a monitor is probably about the last thing id try...

---

### Post by peachtree195 on 2009-10-16
Finally had to replace both the inverter, which worked well for 4 hours and the screen went black again, and then the backlight. 

The unlike the inverter, backlight was a bit tricky to replace. I would recommend getting the backlight (a fluorescent light source that is located at the bottom of your screen within its construction) within another LED display but broken for some reason. Watch the size - it has got to be the same. Some sellers will provide you with such backlight within a damaged LCD display and this is the way it is shipped. They say it is from display models that got broken so the backlight is not used and is extra protected from damage in transportation. How much of this is a trick to sell old broken equipment i do not know but there is one good thing coming out of this - by dismounting a backlight from an old display you will learn about the LED panel structure - so when you are dismounting yours - you will have done it by now with the old one. I found it very helpful and I would recommend this option.

---

