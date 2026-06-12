---
title: "Shutdown hangs on &quot;deactivating swap&quot;"
date: 2010-03-07
forum: General Help
---

### Post by Bender59 on 2010-03-07
Last night I shut down my computer and left, since it goes automatically after I tell it to shut down. This morning, my computer was still on, with some shutdown messages like "Stopping MySQL server mysqld" and such.
The last line said "deactivating swap..." and didn't appear to be doing anything.

```
# fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ead7f7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19087   153316296    5  Extended
/dev/sda2           19088       60801   335067705   83  Linux
/dev/sda5               1       18236   146480607   83  Linux
/dev/sda6           18237       18479     1951866   83  Linux
/dev/sda7           18480       19087     4883728+  82  Linux swap / Solaris
```Does anyone know what caused this or how to fix it?

EDIT: Nevermind, I Googled it and found the solution.

---

### Post by migel_wimtore on 2010-03-09
Which was? 

Reinstalling initscripts did it for me (thanks be to Aadil H on launchpad). Possibly the same solution you found.

---

### Post by cpressland on 2010-03-09
Post solution please :)

---

### Post by egalvan on 2010-03-09
+1 for posting the solution.

It's the sharing that keeps Linux going,
and it's the Ubuntu Way :)

Thanks!

---

### Post by migel_wimtore on 2010-03-09
Well have you guys tried reinstalling initscripts via synaptic (again props to Aadil H)?

---

### Post by CoolMaxUK on 2010-03-09
Got the same problem here. This started a few days ago. Could this have coincided with the latest Kernel release? A solution would be appreciated :)

EDIT: Found the solution [http://ubuntuforums.org/showthread.php?t=523731]("http://ubuntuforums.org/showthread.php?t=523731")

---

### Post by dcstar on 2010-03-09
> **Bender59 said:**
> 
........
EDIT: Nevermind, I Googled it and found the solution.

Then mark the thread.

---

