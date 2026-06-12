---
title: "How to boot back into W7?"
date: 2011-07-11
forum: General Help
---

### Post by iarehenry on 2011-07-11
I installed Ubuntu 11.04 via Wubi on my Windows 7 yesterday. Stupidly, I edited the windows boot manager and made Ubuntu the default OS to pick @ 0 seconds. Now I'm trying to get back to W7 to do some things but I can't. Help? :confused:

---

### Post by Mark Phelps on 2011-07-11
Next time you boot, press F8 quickly and repeatedly -- even if it starts beeping at you.  If that works, you will see the OS selection screen, where you should then be able to select Win7.

---

### Post by iarehenry on 2011-07-11
> **Mark Phelps said:**
> Next time you boot, press F8 quickly and repeatedly -- even if it starts beeping at you.  If that works, you will see the OS selection screen, where you should then be able to select Win7.

Nope, doesn't work. It shows the boot manager screen really fast and automatically select Ubuntu still. It doesn't allow me time to select Windows 7.

---

### Post by Rubi1200 on 2011-07-11
Hi and welcome to the forums iarehenry :)

For future reference, 2 things one should definitely NOT do with a Wubi install:

1. make it the default OS

2. change the timeout to 0 (or in fact anything less than 15 seconds)

If you have, or can get hold of, the Windows recovery disk you can fix this by changing the timeout back to 15 or 30 seconds.

That should at least get you back into Windows I hope and then you can change the default OS.

However, this may not work and I only know of the solution to change the timeout so I will ask someone else to look at this thread and offer some perspectives.

---

### Post by iarehenry on 2011-07-11
> **Rubi1200 said:**
> Hi and welcome to the forums iarehenry :)

For future reference, 2 things one should definitely NOT do with a Wubi install:

1. make it the default OS

2. change the timeout to 0 (or in fact anything less than 15 seconds)

If you have, or can get hold of, the Windows recovery disk you can fix this by changing the timeout back to 15 or 30 seconds.

That should at least get you back into Windows I hope and then you can change the default OS.

However, this may not work and I only know of the solution to change the timeout so I will ask someone else to look at this thread and offer some perspectives.

Thank you! This didn't happen before so I don't know why it's acting like this now. Before on 10.10 I could still go to the windows boot manager by pressing F8 even if Ubuntu was set on default and 0 secs. This time I couldn't and that's very weird.

Anyways, I have fixed the issue. 

For future references:

Booted up Windows 7 recovery disk. 
Ran cmd prompt and entered
```
bcdedit /timeout 5
```
rebooted and was able to select between operating systems again.

---

### Post by Rubi1200 on 2011-07-11
Okay, that is great news and I am glad you fixed it :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

