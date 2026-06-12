---
title: "Ubuntu &quot;deleting&quot; Hal.dll?"
date: 2010-10-17
forum: General Help
---

### Post by Mugsy323 on 2010-10-17
Is anyone else having this problem?

Frequently (but with no predictability), Ubuntu 10 (both 10.04 & 10.10, both 32bit and 64bit versions) "deletes" hal.dll from my Windows/System32 folder, which I must then copy back to get Windows (XP) to boot again.

I say "delete" because half the time, **the file is still there**, Windows just doesn't seem to recognize it, and I must copy my backup of Hal.dll over it... which I do from Ubuntu ironically. Once I get Windows running again, I go into Windows/System32 and write-protect hal.dll, but it doesn't matter because (as I said), half the time the file ISN'T deleted, but for some reason, Windows doesn't detect it until I overwrite it with a fresh copy (after which XP boots normally).

I have no idea why this keeps happening. I scanned both Windows and Ubu for viruses and found nothing (I'm currently running a fresh full install of Ubu-10.10 following a reformat, so a virus is unlikely anyway.)

This ONLY happens on those few occasions I use Ubuntu (my primary OS is still Windows), so I KNOW this is an Ubu problem. It first started happening after I installed Ubu-10.04. I've been using Ubu since version-7, so this is a new issue. I have both 32 & 64 bit versions of Ubu-10 on two different USB connected drives, and it doesn't seem to matter which I use before this happens.

Anyone else encountering this, or am I the only one? Very strange.

---

### Post by howefield on 2010-10-17
> **Mugsy323 said:**
> Anyone else encountering this, or am I the only one? Very strange.

There are very few problems where you will be the "only one"

Have a browse here, (there are plenty of other threads to browse)

[http://ubuntuforums.org/showthread.php?t=1445839](http://ubuntuforums.org/showthread.php?t=1445839)

---

### Post by Mugsy323 on 2010-10-17
> **howefield said:**
> There are very few problems where you will be the "only one"

Have a browse here, (there are plenty of other threads to browse)

[http://ubuntuforums.org/showthread.php?t=1445839](http://ubuntuforums.org/showthread.php?t=1445839)
I saw all these posts before I posted my question, but NONE of them describe this as a *recurrent* problem.

---

### Post by Grepomate on 2011-03-24
This is covered elsewhere, posting here to help.

Your problem is most likely associated with the boot.ini entry corresponding to the Windows installation pointing to the incorrect location. 

Try this to fix it, notice you'll need the Windows recovery CD:
1- Boot from the Windows installation media (CD).
2- After loading initialization files you'll see a menu with 3 options, press "R" for Repair.
3- Will prompt to select the Windows installation to work with, most likely #1, so enter "1", then Enter.
4- It'll then ask for the Administrator password: enter it if you assigned one, otherwise just press Enter.
5- You'll then be presented with a prompt that looks like this: C:\WINDOWS>
6- Type bootcfg /scan, after a few minutes it will show the windows installations identified, you should see at least one, if not most likely your Windows is corrupted and you'll have to reinstall from scratch.
7- In most cases you'll see "[1]: C:\WINDOWS".
8- Just to make sure, type bootcfg /rebuild, it will then ask to confirm that you want to add the installation it found. Press "Y" for Yes.
9- You should be back at the C:\WINDOWS> prompt.
10- Type EXIT then press Enter, the system should reboot to Windows normally.

Hope this helps, otherwise post your results to examine further.
G|

---

### Post by Mugsy323 on 2011-03-24
> **Grepomate said:**
> This is covered elsewhere, posting here to help.
Thanks for the update, though the problem seems to have resolved itself many months ago (after upgrading to 10.10). I don't know why, but it hasn't happened again in so long, I forgot about this post.

Thanks again.

---

