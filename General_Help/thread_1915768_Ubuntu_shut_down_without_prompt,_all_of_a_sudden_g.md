---
title: "Ubuntu shut down without prompt, all of a sudden grub shows up and long error message"
date: 2012-01-26
forum: General Help
---

### Post by malenkylizards on 2012-01-26
This is on my girlfriend's computer, I wasn't around for the first event and can only go off of what she said and what I can find (which isn't much).

So recently, she was using her computer and it prompted her to save all her documents so she could shut down.  She acquiesced, and after it shut down, it's been acting in this way.

Since the last formatting, it's only ever had Ubuntu on it, so grub never popped up.  However, now it does, with the following options:


After the top option in recovery mode has been chosen, it scrolls through too many error messages to see.  In the interest in brevity (since I can't copypasta), I'll only copy the last five lines, but there are over a page of similar errors.

[14.024288][c010a3b9] default_idle+0x49/0xb0
[14.024288][c010a476] c1e_idle+0x56/0x110
[14.024288][c0101fcc] cpu_idle+0x8c/0xd0
[14.024288][c05c6e32] start_secondary+0x10c/0x112
[14.024288] panic occurred, switching back to text console

EDIT: This has been what's happened the past several times, but now there is a new case that happens intermittently.  Instead of the above, after I make the same selection, I get an error message that's too quick to read in its entirety, but the important gist is "unreliable CPU thermal sensors; monitoring disabled".  Then I get the ubuntu loading screen and it actually makes it to the login screen, but the mouse and keyboard are unresponsive!  This only happens, if I were to estimate, every five or six times.

---

### Post by LinuxFan999 on 2012-01-26
What are the specifications of her computer?
How old is it?

---

### Post by grahammechanical on 2012-01-26
As a wild guess. I would say that the machine is overheating. Can you enter the BIOS. It may have a section that will show you the temperatures of the CPU and motherboard if that is possible.

I have installed XSensors. It Gives a GUI display of temperatures and fan speeds.

Does the machine use a proprietary video driver. I use Nvidia. That driver comes with a setting utility to give the video adapter temperature. So, if this machine is using a proprietary video driver it should have its own settings utility and it may give the temperature of the video card.

As a precaution make sure there is a good air flow and the vents are notb locked with fluff. You could also check to see if the CPU, the RAM, and the video card are seated correctly in their slots.

Regards.

---

