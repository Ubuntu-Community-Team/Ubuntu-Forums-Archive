---
title: "Synaptic Package Manager and the &quot;broken&quot; filter"
date: 2009-06-28
forum: General Help
---

### Post by DarkReaper1432 on 2009-06-28
[B][SIZE=3]Okay, so this is my first post, been reading around and found that you need to use the broken filter in Synaptic Package Manager to fix the "You have 1 broken package on your system!" message, so I go to synaptic and it says: "[/SIZE][SIZE=3]There is another synaptic running in non-interactive mode. Please wait for it to finish first." 
So, I have been frustrated for awhile now, not that I know enough to figure out where to start, any idea's?

Any help would be greatly appreciated :D
[/SIZE][/B]

---

### Post by Steelmourne on 2009-06-28
That probably means that another package manager is running. Close down update manager, terminal, synaptic, if they are running then restart synaptic. If you still get errors restart the pc and then start synaptic again.

---

### Post by DarkReaper1432 on 2009-06-28
Thank you, I was over thinking it all, reboot worked like a charm!

---

### Post by kokkus on 2009-06-28
If it happens again after reboot, start your pc, and from grub you go to recovery mode and choose "repair broken packages" from the list.

EDIT: OH you fixed it. well I am glad you got it solved.

---

