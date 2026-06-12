---
title: "GRUB2 menu freezes"
date: 2011-05-13
forum: General Help
---

### Post by soelk on 2011-05-13
My Ubuntu 10.11 setup has been working well until today. The first problem I had was that I had to reset my BIOS for some reason (probably unrelated to Ubuntu). After the BIOS reset everything worked fine for a couple of boot cycles, but then the Grub menu froze. The menu options show up, but the cursor is stuck and there is no countdown to start the default option.

I reinstalled Grub2 according to the official guide and that worked fine in the sense that I now have a newer version of Grub2, but this one also freezes. Problem not solved. :(

I suspect one of my old drives is on it's last legs, because I can hear that it is making bad noises (the failing disk is probably the reason why I had to reset my BIOS) but my Ubuntu disk is in good condition. I've disconnected the failing disk, but it doesn't help with my Grub problem.

I read somewhere that some people fixed their Grub menu freeze by unplugging all USB plugs and restarting. I've tried that with no success. Thankful for any input on how to proceed.

---

### Post by soelk on 2011-05-13
The problem with Grub was that it could no longer access the USB keyboard because USB keyboard was disabled in BIOS. It's an old computer... I should have guessed.

I managed to break Grub in my attempts to reinstall it. Problem fixed with Rescatux. Good stuff.

---

### Post by drs305 on 2011-05-13
Glad you were able to solve this one by yourself and shared your solution.  :-)

Since you took the time to mark it SOLVED, you know that is valuable for both helpers and those looking for assistance.

You can do it a bit more 'formally' via the 'Thread Tools' link near the top right of the first post (and it's reversible if necessary). Just thought you'd like to know.

Happy Ubuntu-ing !

---

### Post by soelk on 2011-05-13
Ah thanks. I knew there was an option for that somewhere.

By the way, it could be that unplugging and replugging your keyboard will automatically enable USB keyboard on newer computers. Maybe that's why people have been able to fix the problem by replugging the keyboard.

---

### Post by kushalfunkydude on 2011-12-12
I also faced the same problem and i am searching a solution for it since last 1 month but i didn'nt find it out.
Your answer seems very affective so can you explain me this in detail.
And how can i recover my grub menu from freezing.

---

