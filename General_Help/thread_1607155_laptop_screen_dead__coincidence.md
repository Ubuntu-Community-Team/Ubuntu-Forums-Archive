---
title: "laptop screen dead:  coincidence?"
date: 2010-10-27
forum: General Help
---

### Post by acmagee on 2010-10-27
I wanted to log out from the terminal, so I used the command I found [here]("http://ubuntuforums.org/showthread.php?t=665536"), gnome-session-save --kill.

I got the logout dialog and clicked log out...and then my screen went black.  And won't return, even though I've restarted several times.  It's definitely just the display because I'm writing this with my laptop connected to my TV.  Hitting Fn+F8 to switch displays doesn't do anything.

Is this related to the command above, or did my screen just pick an inopportune time to die?  It's a Dell Latitude D830, if that matters.

---

### Post by blueridgedog on 2010-10-27
If you do not get any output on the screen when booting (prior to loading an operating system) then it would seem to be a hardware issue.  I know of no way that killing a gnome session can impact computer hardware.  

Since you can boot and use the laptop with your TV as a monitor, I suggest you try going into the BIOs of the Dell and reseting it to factory defaults.

---

### Post by acmagee on 2010-10-27
Nope, restoring the bios doesn't do anything.  Any other ideas or should I start looking for a new laptop?

Does the screen turn off when you use that command?  I guess that could have just been the fatal cycle.

---

### Post by hrickh on 2010-10-27
> **acmagee said:**
> Nope, restoring the bios doesn't do anything.  Any other ideas or should I start looking for a new laptop?

Does the screen turn off when you use that command?  I guess that could have just been the fatal cycle.
How did you restore the bios? With the external monitor attached?

R.
==

---

### Post by gradinaruvasile on 2010-10-27
Which video card does it have? Intel or nvidia? I had a D630 that had nvidia card and the card died (Quadro NVS 135M, bad cooling caused by faulty manufacturing) - replaced without charge.

And the 630 has a test mode built in the BIOS (memory+cpu+display), probably the 830 too - a few times it broght the display back to normal for me until it crapped out completely. See if you have it and give it a try.

---

### Post by acmagee on 2010-10-27
> **hrickh said:**
> How did you restore the bios? With the external monitor attached?

R.
==

Yeah, that's the only way I can see what I'm doing.  Nothing appears on the screen even before the OS boots.

> Which video card does it have? Intel or nvidia? I had a D630 that had  nvidia card and the card died (Quadro NVS 135M, bad cooling caused by  faulty manufacturing) - replaced without charge.

And the 630 has a test mode built in the BIOS (memory+cpu+display),  probably the 830 too - a few times it broght the display back to normal  for me until it crapped out completely. See if you have it and give it a  try. 	

I've got the same card, so I guess I'll see what nvidia has to say.  If my card were bad, would I still be able to use the external monitor?

I don't see anything that looks like a test mode in the BIOS menu.

---

