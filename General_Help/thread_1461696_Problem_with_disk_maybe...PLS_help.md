---
title: "Problem with disk maybe...PLS help"
date: 2010-04-24
forum: General Help
---

### Post by antonisasim on 2010-04-24
Hello everyone. I am running ubuntu 9.10 on my laptop and a few weeks now the computer seems to stack every 5-10 min. The screen gets a grey colour (transparent) and I can't do anything. After some sec everything is OK again. I get the following from Log File Viewer. Can someone help. Thank you.


Apr 24 22:03:41 antonis-laptop kernel: [  233.386262] ata1.00: configured for UDMA/133
Apr 24 22:03:41 antonis-laptop kernel: [  233.386295] sd 0:0:0:0: [sda] Unhandled sense code
Apr 24 22:03:41 antonis-laptop kernel: [  233.386300] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 24 22:03:41 antonis-laptop kernel: [  233.386309] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Apr 24 22:03:41 antonis-laptop kernel: [  233.386321] Descriptor sense data with sense descriptors (in hex):
Apr 24 22:03:41 antonis-laptop kernel: [  233.386327]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr 24 22:03:41 antonis-laptop kernel: [  233.386355]         05 bb dd 3d 
Apr 24 22:03:41 antonis-laptop kernel: [  233.386366] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Apr 24 22:03:41 antonis-laptop kernel: [  233.386423] ata1: EH complete

---

### Post by lukeiamyourfather on 2010-04-24
> **antonisasim said:**
> 
Apr 24 22:03:41 antonis-laptop kernel: [  233.386366] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed


Sounds like your disk is on its last leg. Do you have another to swap and test? It could be something else but I'd start with trying a different/new disk. At the least backup anything you haven't already and don't want to lose. Cheers!

---

### Post by antonisasim on 2010-04-24
Thank you for the answer. I thought these thinks too. I have already backed up my files. I can't try an other disk. May be if there is a "software" solution...

---

### Post by lukeiamyourfather on 2010-04-24
> **antonisasim said:**
> Thank you for the answer. I thought these thinks too. I have already backed up my files. I can't try an other disk. May be if there is a "software" solution...

Frequent unrecoverable read errors are not something that is fixable in software. Drives have them every once in a while (a handful of times in a typical drive life) but if a lot show up and its causing issues on a regular basis then the drive is not healthy and needs to be replaced. Cheers!

---

### Post by P4man on 2010-04-24
If smart is enabled and palimpsest isnt warning you about the drive failing, then its also possible its the cable. Often seen pata cables go bad, and its rather cheap and easy to replace.

---

