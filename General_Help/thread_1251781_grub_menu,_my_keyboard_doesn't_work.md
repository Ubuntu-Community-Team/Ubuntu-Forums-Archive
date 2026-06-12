---
title: "grub menu, my keyboard doesn't work"
date: 2009-08-28
forum: General Help
---

### Post by orestis25 on 2009-08-28
Hi everybody, 

I have the following problem:

I had windows xp installed and at some point I installed ubuntu 8.04. Everything has worked perfectly.

The other day, I set up a desktop pc for a friend at my house, which means that I unplugged the PS/2 keyboard. My friend left and I tried to boot my PC, having of course plugged in the keyboard.

However! The keyboard doesn't seem to work (long live lucasarts) until the log in screen of ubuntu turns up (from then on everything works fine). I cannot access bios, cannot select windows in the grub menu as the up and down arrow keys don't work and ubuntu loads after 10 secs.

Any ideas?
Thanks

---

### Post by P4man on 2009-08-28
is it an USB keyboard?
Maybe he has to enable "legacy USB support" in the BIOS to make his keyboard work without drivers. I guess you'll need to attach a different keyboard to be able to set that in the bios...

---

### Post by P4man on 2009-08-28
btw, plugging and unplugging a PS/2 keyboard (or mouse) while the machine is powered on *can* fry your motherboard. Despite what most ppl think, PS/2 is not hot pluggable

---

### Post by orestis25 on 2009-08-28
It'a ps/2 keyboard, sorry for the ommision

---

### Post by P4man on 2009-08-28
ok silly suggestion: you sure you didn't put the keyboard in the mouse port ? Keyboard should be purple on the motherboard.

---

### Post by orestis25 on 2009-08-28
Not so silly, as I admit i plugged it in without looking. Anyway, it's in the purple one.

(we all know that the purple tentacle is more dangerous than the green one)

---

### Post by P4man on 2009-08-28
are you using one of those small USB to PS2 convertors ? If so, obviously try connecting it as usb.

Either way, if you got a ps/2 keyboard and you cant get in the bios.. something is wrong. Either with the keyboard, the system or the bios. You could try resetting your bios.

Also, are you using a PS/2 Mouse ? If so, disconnect it. from wikipedia (of all places lol):

> As noted, in a standard implementation both PS/2 ports are usually controlled by a single microcontroller on the motherboard. This makes design and manufacturing extremely simple and cheap. However, a rare side effect of this design is that a malfunctioning device can cause the controller to become confused, resulting in both devices acting erratically. The resulting problems can be difficult to troubleshoot (e.g. a bad mouse can cause problems that appear to be the fault of the keyboard).

---

### Post by orestis25 on 2009-08-28
I am using a usb mouse and a PS/2 keyboard without any usb adaptors. I cannot get into bios because the keyboard seems to be dead and the F2 key(to enter setup) doesn't work either.

When the log in screen pops up, the keyboard works fine as in ubuntu as well.

---

### Post by P4man on 2009-08-28
I can only suggest then to reset the BIOS.. usually involves shorting 2 pins and removing the battery. See your motherboard manual.

---

### Post by HiImTye on 2009-08-28
I would double check that your F2 key actually works in Ubuntu once you've booted up, could be that you just don't use it so you *think* that it doesnt work while youre booting up and it works when its finished

also try fully removing it and plugging it back in again

also try checking that all the pins are OK as well as the sockets in the PS/2 port

---

### Post by orestis25 on 2009-08-28
I tried to put a usb keyboard. The keyboard works only when I reach the ubuntu log in screen. I cannot enter the bios or change something in the grub menu.

Both PS/2 and usb keyboards don't seem to work when the computer is booting. What can I do?

---

### Post by P4man on 2009-08-28
reset your bios. There isn't much else left if even the bios isnt responding to keypresses.

---

### Post by orestis25 on 2009-08-28
Thanks for the help so far. I did not hot-plug the keyboard, I did not however close the switch of the power from behind. I don't know if this stands, but maybe somehow there was some coulomb left and that did the damage in the motherboard.

Now, I checked when exactly my keyboard becomes active by pressing continously capslock while booting and looking at the light. The moment the grub menu goes off (and ubuntu starts loading) the keyboard becomes active. 

I am assuming that while booting the motherboard has a built in mechanism to "read" the keyboard (both  PS/2 and usb keyboards) and when an Operating System (in my case ubuntu by lack of choice) starts it "reads" the keyboard with the use of another mechanism.

Trailing this thought, the problem must lie in the motherboard's built in mechanism. (the PS/2 pins are fine, and the behavior is the same for usb). 

My only choice from what I gathered from your responses is to reset the bios by unpugging/plugging its battery and hope for the best, right? I  have not done this before, but tomorrow I will give it a try. (inglourious basterds await me)

Thanks for your help

---

### Post by P4man on 2009-08-28
removing the battery alone is not enough usually. Unless you wait a VERY long time. You also have to short 2 pins. Its a so called jumper that you move from pin 1-2 to pin 2-3. Motherboard manual will explain it (and if you dont have, you should be able to download it). Just make sure you unplug the power cable while doing this. 

let me know.. 
...how inglourious basterds was :)

---

### Post by orestis25 on 2009-08-29
OK... should I worry about backing up files, is there a format at the end of the job?

The basterds were greats.
Good acting (Brad Pitt is great), the story is well written with the traditional 15-minutes long dialogues of Tarantino which are very very tenseful, not too much violence (only a bit of scalping) and a complete lack of respect to history (to be expected)

Ultimately, I would describe the film as... funny. Wait till Pitt speaks italian. I recommend it for sure

---

### Post by P4man on 2009-08-29
no resetting the bios is no risk for your data. Its not a bios upgrade either, so you dont have to backup it up. It just resets the bios settings, its pretty save, aside from messing up the computer time and perhaps boot order, it does nothing to fear :) Ill go see "basterds next weekend" :)

---

