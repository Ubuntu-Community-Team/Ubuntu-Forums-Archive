---
title: "Prevent the sleep state from being lost on power failure"
date: 2010-05-17
forum: General Help
---

### Post by terranair on 2010-05-17
Hi.
When I tell the computer to go to sleep and there is a power failure the sleep state is lost.
Is there a way to prevent this?
I already know about hibernate and I'm using it but sleep is faster and there is no complete loading of the computer (BIOS, Grub and so on) it just goes directly into the desktop.
As far as I know the sleep state is done when everything is in RAM and the computer is turned off but the RAM sticks still receive power. Is this true?
Thank you for your input.

P.S. Can this be done with hibernate and SSD drives? As far as I can tell from what I've read it will be the same but with no state loss. Is this true?

---

### Post by Peter09 on 2010-05-17
Basically in the sleep state everything is turned down to a low power state, but power is maintained to the system (especially RAM). RAM will not remember anything if power is lost.
 
Hibernation, on the otherhand, writes everything to disk (which will remember after power loss), and then turns everything off. On power up all is read back from disk, which is why it is slower.
 
Its been the dream of many manufactures to produce cheap and fast RAM that remembers even when power is lost. Unfortunatly no one has won the prize yet.

---

### Post by iponeverything on 2010-05-17
+1 

Grab yourself a cheep UPS to keep RAM from losing power.

I think that SSD and hibernate would work too.. Maybe not quite as fast as RAM.

---

