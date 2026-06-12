---
title: "Changing from Via sound to soundblaster?"
date: 2006-04-25
forum: General Help
---

### Post by UbuntuUbuntu7 on 2006-04-25
Hello.

I have via 8235 onboard sound now. I want to go with my soundblaster live 5.1 instead. Should i in some way uninstall the  drivers for 8235 before i put in live 5.1? How do i do it? And where the heck is the drivers to soundblaster in linux? Certainley not on soundblasters site....

---

### Post by Runefox on 2006-04-25
The drivers for the SBLive should be included with Ubuntu. I'm using one myself, and Hotplug just picked it up and loaded it on the first shot. Maybe you'll have the same luck, but I do recommend disabling your onboard sound in the BIOS first, to make sure the SBLive is the only card being used by Linux (having it as card ID 1 instead of ID 0 can (annoyingly) result in apps using the onboard instead).

If all else fails, just add "emu10k1" to your /etc/modules file, or alternatively just do "modprobe emu10k1". If you need to use the gameport (the system doesn't automatically load it whether it's autodetected or not), also add / modprobe "emu10k1-gp" (all this, of course, without the quotes). That should get you up and running.

One last note, if you want to use soundfonts, you should get the awesfx package, which includes the utility asfxload, which will let you load a soundfont into memory for use with MIDI through your actual card, rather than Timidity. Note that large (>64MB) soundfonts may drop notes. In this case, using Timidity might be best.

---

### Post by UbuntuUbuntu7 on 2006-04-25
Thanks for the answer. I had the soundblaster going, with the onboard sound enabled. But it flipped out a little(i will try it again now, though). With the onboard sound disabled in bios, i cant choose any soundcard in the properties drop-lis at allt...:-k

---

### Post by Runefox on 2006-04-25
Is there any sound output from the card at all? If not, try doing a modprobe emu10k1 and see if that does anything for you.

One other thing to try after that is to do:

sudo /etc/init.d/alsa restart

and see if that does anything. If it does, you might need to add the emu10k1 line to your /etc/modules file.

---

### Post by UbuntuUbuntu7 on 2006-04-25
I had the onboard enabled again in the bios. Then i took out the soundcard from the motherboard and put it back, and now i can choose it again in the drop-list. Thanks. :o

---

