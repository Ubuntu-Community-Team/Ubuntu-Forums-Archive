---
title: "Logitech MX 5500 woes"
date: 2009-11-03
forum: General Help
---

### Post by DonSlice on 2009-11-03
First off, I love Karmic. It's a beautiful operating system. I've managed to get ushare working on my server (also with Karmic!) so I can replace one of my XP servers. One more to go!

With that being said, I'm having a bit of an issue with the Logitech MX5500 bluetooth keyboard/mouse combo.

Everything works fine, perfectly even, after the initial login/bootup. When my computer is idle for an extended period of time (hours; while I sleep), the mouse no longer works as it should.

Normally, the middle button/scroll wheel is "clicky" style and allows you to use it as a middle button. When the computer is idle and I come back to it, the properties change. Instead of "middle click" it becomes "switch to free scroll".

Let me know what sort of information you need, and I'll try my best to get it for you (going to be at work all day, but should be able to ssh into the box).

Thank you in advance!

---

### Post by Giblet5 on 2009-11-03
The middle-button switch on my MX700 triggers just before the purely-mechanical clicky/freewheel toggles.

Take your mouse to the top of Everest, far away from any computer. Push the middle button and observe that it still toggles the clicky/freewheel modes. Now, treat your hands for frostbite and return to the forum.

I suspect that, in the morning, you press the middle button 5 grams harder than you do the weary night before, triggering the mechanical toggle.

It could also be that the mouse driver stops recognizing the MX and starts using the PS/2 driver, though I can't see any reason why that would trip the solenoid that electrically disables the mechanical toggle. My BT 700 works the same way all of the time. Overnight. Weekend. So does my wife's.

I recommend that you wait until morning and immediately grab a copy of /var/log/Xorg.0.log and look through it for mouse driver changes.

If you can walk away overnight without locking your screen, you might want to start xev, put your mouse cursor in the xev window, and walk away for the night. Maybe you'll log an unusual event.

---

### Post by DonSlice on 2009-11-03
> **Giblet5 said:**
> It could also be that the mouse driver stops recognizing the MX and starts using the PS/2 driver, though I can't see any reason why that would trip the solenoid that electrically disables the mechanical toggle. My BT 700 works the same way all of the time. Overnight. Weekend. So does my wife's.

I recommend that you wait until morning and immediately grab a copy of /var/log/Xorg.0.log and look through it for mouse driver changes.

If you can walk away overnight without locking your screen, you might want to start xev, put your mouse cursor in the xev window, and walk away for the night. Maybe you'll log an unusual event.

Managed to grab Xorg.log, but I don't see any keyboard/mouse related warnings or errors. The only thing interesting is that I see a few lines beginning with "Macintosh mouse button emulation"

Tonight, I'll leave the cursor sit in xev to see if anything happens. If I can pull the log file over in the next hour or so, I'll post that as well.

Thank you.

---

### Post by DonSlice on 2009-11-04
Well, I found the issue. It's when the mouse itself turns off through inactivity/manual shut off.

Next question: Is there something I can restart to grab the mouse again so it doesn't go into free spin mode on middle click?

---

### Post by DonSlice on 2009-11-04
Okay, this is my bad. This isn't a bug.

It seems that when the computer is in Windows, the Logitech driver gives some instruction to the mouse on how to behave. When it shuts off (or sleeps), this information is discarded and it goes back to its "driverless" mode.

---

### Post by Giblet5 on 2009-11-04
> **DonSlice said:**
> Okay, this is my bad. This isn't a bug.

It seems that when the computer is in Windows, the Logitech driver gives some instruction to the mouse on how to behave. When it shuts off (or sleeps), this information is discarded and it goes back to its "driverless" mode.

They're even BETTER mice now, huh? ;)

Don't forget to mark this SOLVED with the Thread Tools dropdown above...

---

### Post by scumie on 2009-11-04
Unfortunately it is not solved.
I'm having the same problem. On Jaunty I used to configure the middle mouse with btnx or revoco. Seems that both are broken for Karmic.
I'll see if I can fix it and post a solution soon.

---

