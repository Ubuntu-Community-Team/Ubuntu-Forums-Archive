---
title: "Grub problems"
date: 2010-03-22
forum: General Help
---

### Post by sbrenneis on 2010-03-22
I shut down my laptop, which is running Ubuntu 9.10, without any problems. When I got home and tried to boot it, it finishes the POST and then I get a blank screen with a cursor for a few seconds. The word "GRUB" then appears in the upper left hand corner and that's it. The system is hung and I have to power off.

I've seen a lot of discussion that 9.10 uses grub2. Any ideas how I get out of this? Do I need to downgrade to legacy grub?

Thanks.

---

### Post by quixote on 2010-03-23
If I understand it right, you're not even getting a grub command line, right?  It's hung before grub even fully loads?  Then, obviously, you can't fix it from the grub command line (for which there are good instructions [here]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")). 

Barring that, I think your best bet (only bet?) is to boot from a LiveCD, and get at grub that way, following instructions at that same link on how to proceed.  Or you can let it boot, and edit various files, also as in the above Grub2 doc page.

Strange that it blew up so totally from one day to the next.  Is it possible that maybe the hard disk failed spectacularly?

---

