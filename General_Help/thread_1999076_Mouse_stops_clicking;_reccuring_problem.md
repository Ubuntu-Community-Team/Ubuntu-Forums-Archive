---
title: "Mouse stops clicking; reccuring problem"
date: 2012-06-07
forum: General Help
---

### Post by The Thunder Chimp on 2012-06-07
Hello!

I installed yesterday Ubuntu 12.04 on my laptop, which was running on Debian 7 until then. I installed MATE (a GNOME 2 fork) on Ubuntu 12.04 because I can't stand GNOME 3 or Unity. My Debian 7 ran on GNOME 2.

And here's a problem that happened on both operating systems, though differently.
At any random moment, the mouse's left button stops clicking. And it probably isn't related to the mouse I use since the touchpad is always simultaneously struck.

It happened twice since yesterday and it doesn't go away until reboot. Actually, I was talking to a friend and as I couldn't left-click anymore, I managed to get around with the right button only (though much *much *slower). And then the right-click button died too, at which point I hit ctr-alt-F1 to enter the Command Line interface. I logged in and typed in ```
kill -9 -1
```which usually does the effect of a soft reboot, resetting the Graphical User Interface and bringing me back (after pressing ctr-alt-F7) to the log in screen. But instead, the computer just froze there and I had to hold the power button to reboot. 
And here I am a few minutes later.

Actually, under Debian, it happened often for the left-click but the problem cured itself after a minute or so.

Can someone pull me out of this? What is this plague? And please, *please*, don't try to convince me back into Unity.

Thanks a lot! ;)

---

### Post by The Thunder Chimp on 2012-06-08
Bump! :)

---

### Post by The Thunder Chimp on 2012-06-12
Re-bump! :)

---

### Post by The Thunder Chimp on 2012-07-16
Bump!

---

### Post by The Thunder Chimp on 2012-07-21
Bump[-o<

---

### Post by chocklet on 2012-07-21
Your symptoms are very similar to those that appeared on my wife's PC (12.04 Unity).  My wife's USB mouse buttons stopped working occasionally.  The mouse pointer was fine, but there was no response to the buttons.  I could use her PC for hours and not experience the same problem. 

It turned out that the problem was related to her backlit USB keyboard.  When she changed the color of the keyboard backlight (hardware switch), her mouse buttons would sometimes stop working.  No, after as many questions as I dare, I still don't understand her reasons for switching back and forth between colors.  Anyway, the problem was resolved when she decided that she could settle upon one color.

You might experiment with any USB devices that are connected to your laptop.  If the touchpad never has a problem with no USB devices attached, then that might be a clue.

---

### Post by Kaeptenblaubaer on 2012-08-14
Bump
You gotta solution yet?

My hardware: Thinkpad T61 / Intel Graphics

---

### Post by nanogennari on 2012-11-02
I'm with exactly the same ploblem, i'm running ubuntu 12.10, when i start a session with MATE the mouse stop clicking...

Any one has any clue of what may cause this?

---

### Post by tlootno on 2012-11-18
I have the same problem.

- Lenovo 3000 N100, when using the mouse pad it stops clicking.
- I connected my RAT7 and the same problem persist.
- Then I connected wy wife's Genius Mini-Traveler, very basic mouse and works perfectly.

The problem is that I want to use or the mouse pad or my worderfull RAT7.

This problem exists since the dawns of time and nobody come and give a definitive answer.

I know that a mouse is only important for non hardcore guys like me, but I really like to use it.

Help guys!!!

---

### Post by Resistent on 2012-11-18
The mouse functionality stopped working on my 5 year old laptop.
I read about a solution and made a 
>   metacity --replace 
in the terminal, it worked.

---

