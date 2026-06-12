---
title: "Suspend stops working with new RAM"
date: 2009-08-18
forum: General Help
---

### Post by adempewolff on 2009-08-18
The last few times I have tried to suspend to RAM on resume I have gotten a flashing white cursor.  I just replaced both slots of RAM last night and was wondering if that could have anything to do with it and what I might be able to do to make suspend work.

I replaced a 1GB DDR2 533mhz and 1 GB DDR2 667mhz with two 2 GB DDR2 800mhz although the bios is just recognizing it as 667mhz.

I'm using 9.04 amd64 and suspend to RAM has always worked with the very rare exception (usually when I did something silly with peripherals while suspending and resuming).

Any suggestions would be appreciated!

---

### Post by dcstar on 2009-08-19
> **adempewolff said:**
> The last few times I have tried to suspend to RAM on resume I have gotten a flashing white cursor.  I just replaced both slots of RAM last night and was wondering if that could have anything to do with it and what I might be able to do to make suspend work.

I replaced a 1GB DDR2 533mhz and 1 GB DDR2 667mhz with two 2 GB DDR2 800mhz although the bios is just recognizing it as 667mhz.

I'm using 9.04 amd64 and suspend to RAM has always worked with the very rare exception (usually when I did something silly with peripherals while suspending and resuming).

Any suggestions would be appreciated!

Boot up to the Memtest option and see if it tests ok.

---

### Post by adempewolff on 2009-08-20
ran memtest 4 times and it passed each time. any other ideas?

---

### Post by The Cog on 2009-08-20
I could be talking rubbish, but maybe suspend uses the swap partition for storage? If so, maybe you should check that your swap partition is big enough to hold an image of your new bigger RAM. Just a thought.

---

### Post by Nburnes on 2009-08-20
> **The Cog said:**
> I could be talking rubbish, but maybe suspend uses the swap partition for storage? If so, maybe you should check that your swap partition is big enough to hold an image of your new bigger RAM. Just a thought.
Yea I thought that is what the swap partition did also.

---

### Post by adempewolff on 2009-08-21
that is suspend to disk (hibernate).  and the swap portion is bigger than the new amount of RAM.

suspend to ram saves the state information in the memory which is kept powered to keep that information there.

---

### Post by The Cog on 2009-08-21
Ah. Thanks for the clarification.

---

