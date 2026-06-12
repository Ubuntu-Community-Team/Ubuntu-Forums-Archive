---
title: "MBR Damage - need to manually fix"
date: 2010-03-17
forum: General Help
---

### Post by six30two on 2010-03-17
I'm running Windows 7 on my desktop (But Ubuntu 9.10 on two laptops), and I have an odd problem.

I backed up my system from one HDD to another HDD, and in the process the MBR of the destination drive got fouled up and now sees Windows Vista and Ubuntu (even though I never used anything Ubuntu - I assume the backup program used an ubuntu build).

Is there any way... No, I know there is. I had the answer once but lost it.

HOW do I manually edit my MBR to remove the Ubuntu reference and rename Windows Vista to Windows 7? Please note Ubuntu was never dual booted, let alone installed at all, on the HDD in question.

Thanks in advance :)

EDIT:

I solved the situation by using the bcdedit commands (type bcdedit /? in the command line to see the help file) and I manually removed the Ubuntu entry in the boot manager.

Before doing all this, I had tried the various fixMBR commands, but none of them worked - either manually or through the DVD. the bcdedit manual fix did what I needed.

---

### Post by prodigy_ on 2010-03-17
Err. May I ask - what exactly is the problem and what are you trying to accomplish?

In any case, if you'll boot from Windows 7 DVD into recovery console and use ```
bootrec /FixMbr
``` command, it'll replace MBR.

---

### Post by six30two on 2010-03-17
I solved the situation by playing with the command line bcdedit, and manually changing the boot manager entries. Works perfectly now :)

Thanks for the help, though!

---

