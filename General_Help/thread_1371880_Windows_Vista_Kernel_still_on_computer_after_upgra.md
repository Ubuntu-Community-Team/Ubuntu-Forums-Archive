---
title: "Windows Vista Kernel still on computer after upgrade??"
date: 2010-01-03
forum: General Help
---

### Post by allmightymoo on 2010-01-03
Ok so i recently upgraded to win7 (home premium 64bit) from win vista and everything went well. But when i was installing ubuntu i noticed that win vista was taking up part of the C drive (like 10 gigs!) (i saw this in the part of the instalation where you set the ubuntu partition.) SO anyway i was wondering if anyone knew a way to completely get rid of the vista kernel and free up that space its taking up. 

Thanks in advance.

---

### Post by Marrkk on 2010-01-03
I doubt very much its just a windows kernel thats been backed up,
more likely is that because you upgraded to win7 from vista, 

My best guess is that there is some hidden restore partition on your hard drive, for resetting your pc back to its new, shop-fresh vista state.

'if' there IS a hidden 'restore' partition which many new, 
(particularly laptops these days) that may be what you're seeing.
you may also be seeing, in the grub bootloader, the recovery partition. it may look like you have a win vista AND a win7 entry,
if you blow this recovery partition away, you *may need to* update 
grub or grub may get confused on next boot.

this laptop came with vista. but no vista cd, when i booted this new laptop up, it asked me to use 3 blank CDs to restore my pc back to shop new state.i did too.
there was a 30 gig hidden part of the hard drive for some sort of 'recovery' operation.  but i blew that away as soon as i made the CDs.
anyway i had a vista cd anyway, so i used that and my legal vista key when i fancied a play wth vista. did'nt last long though.

if this is the same for you, i would'nt recomend blpwing away the hidden partition unless you're *really* sure you can reinstall the original Windows and junk programs that came with it., if you need to.

i had no intention of ruining my shiny new laptop with vista, or the crapware so i did blow it right away. nice blank new hard drive.

The win7 disc that arrived worked fine, so i can have a blank new hard drive,  install linux win7 or vista easily,.

---

### Post by allmightymoo on 2010-01-03
ok thanks for the info...i'll just leave it alone

---

### Post by Marrkk on 2010-01-04
like i say, i am just guessing.
-anyone else have any ideas ?

if you're running low on disc space .. maybe do your backups and come back on here, and we'll help out !

---

### Post by slooksterpsv on 2010-01-04
Run disk cleanup, it'll give you an option to clean previous OSes, if you try to delete the Windows.old directory, it'll error out, you have to use Disk Cleanup to remove Vista.

---

### Post by allmightymoo on 2010-01-04
ok so i started disk clean up but i dont see anything that says anything about vista or other OSes. Should i hit 'clean up system files'?

---

### Post by Marrkk on 2010-01-04
as the previous poster said, there may well be a way to make more room on the windows drive by doing the usual clean-ups and stuff, 
but it wont give any more space on your linux drive, and it wont delete any
entries in your grub options, it will only clean your windows bit up a little. plus it could delete any syste restore checkpoints, and you never know, you may need em one day. 
if it aint broke !!

---

### Post by slooksterpsv on 2010-01-06
> **allmightymoo said:**
> ok so i started disk clean up but i dont see anything that says anything about vista or other OSes. Should i hit 'clean up system files'?

Yes clean-up system files. That's how I had to do it with my computer.

---

