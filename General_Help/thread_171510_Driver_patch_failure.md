---
title: "Driver patch failure"
date: 2006-05-06
forum: General Help
---

### Post by anubix on 2006-05-06
I recently purchased an orinoco gold classic card.
it works just fine out of the box, but of course i can't put it into monitor mode without patching the drivers.  I have tried repeatedly, and with slight variations the steps in [http://ubuntuforums.org/showthread.php?t=79160](http://ubuntuforums.org/showthread.php?t=79160) to no avail.

i don't get any errors untill i try to "patch -p1 --dry-run < orinoco-0.15rc2-dragorn-02.diff"

this is what it spits out:
sam@portos:/orinoco/orinoco-0.15rc4$ sudo patch -p1 --dry-run < orinoco-0.15rc2-dragorn-02.diff
patching file orinoco.c
Hunk #1 FAILED at 447.
Hunk #2 succeeded at 415 with fuzz 2 (offset -95 lines).
Hunk #3 succeeded at 721 with fuzz 1 (offset -455 lines).
Hunk #4 succeeded at 778 with fuzz 1 (offset -454 lines).
Hunk #5 succeeded at 798 (offset -454 lines).
Hunk #6 succeeded at 909 (offset -454 lines).
Hunk #7 succeeded at 1882 (offset -464 lines).
Hunk #8 succeeded at 2492 (offset -469 lines).
Hunk #9 succeeded at 4255 with fuzz 2 (offset -553 lines).
Hunk #10 succeeded at 4383 with fuzz 2 (offset -602 lines).
Hunk #11 FAILED at 4466.
2 out of 11 hunks FAILED -- saving rejects to file orinoco.c.rej
patching file orinoco.h
Hunk #1 succeeded at 110 (offset -30 lines).
patching file prism2header.h

so obviously the patch isn't inserting properly in orinoco.c
what can i do about getting stubborn hunks # 1 and 11 to insert?
i've tried doing a "sudo /etc/init.d/pcmcia stop" and removing the card during the dry-run patch process with the same results.

i don't know where to start to figure out how to make this work.  any direction is greatly appreciated.

pz

---

