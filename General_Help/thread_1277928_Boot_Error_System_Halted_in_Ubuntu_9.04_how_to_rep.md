---
title: "Boot Error System Halted in Ubuntu 9.04 how to repair??"
date: 2009-09-28
forum: General Help
---

### Post by dolgion1 on 2009-09-28
Hello everybody,

A week ago or so my work computer running Ubuntu 9.04 started getting 
a boot error: system halted problem at boot up.
My machine only runs ubuntu 9.04, and it does get to GRUB.
But no matter which option I select, the above error occurs, even for the recovery modes.

The only thing that seems to let me boot is to first do a memcheck.
Now, i'm still a noob in this kind of thing and i don't understand what happens in memcheck exactly, all that i can see is red blocks coming up each time, which i suppose are damaged blocks of memory.

I think my harddrive is screwed, or maybe is it some sort of problem with the CMOS battery, like i've seen in other forums/threads?

If anybody has experienced this problem, i would be glad for some advice.

---

### Post by sedawk on 2009-09-29
Hello!

The tool memcheck tests for errors in RAM. If this reports errors
your RAM is broken and needs to be replaced.
( Sometimes remounting it or swapping RAM "boards" might help too.
  But that is Voodoo ...).
If you have a CD drive try to boot a Live-CD - I guess
it will fail to boot too.

---

### Post by pawhtiobo on 2009-09-29
Hi :)
 
After de test of trying to boot liveCD.... if it succeed...if not, you can try removing the RAM module, clean the RAM contacts with an ink eraser (blue side) and try it again...sometimes it can be a poor contact between the RAM Module and the MB.
  
see ya...

---

### Post by dolgion1 on 2009-09-29
Thanks for the tips!
I'll try doing that soon as I get a cd in my hands.
For now, after doing a 2h memcheck, it seems to boot normally again :D

---

