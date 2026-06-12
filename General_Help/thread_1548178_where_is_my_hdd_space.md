---
title: "where is my hdd space???"
date: 2010-08-07
forum: General Help
---

### Post by miha2 on 2010-08-07
hello everyone, i've been using ubuntu for about 2 months, so i'm a newbie. i have a question - i installed wine (if it helps, of course) (a long time ago) and now all my hdd space (on linux partition, installed through Wubi) is all gone, in an unknown direction... i mean, i have 0 bytes left. when i delete something, be it small or big, something eats everything that was deleted. the OS works so far so good, but who knows, maybe it'll eat it too. might it be a virus? i checked with nod32 online scanner, and it found nothing. i just want to know if it's a virus and if it works under wine, and what should i do, since i don't want to uninstall wine, and want to use linux AND windows programs on my linux. as i said, it eats only linux partition, i have the same amount for at least day on my windows pc (started watching for it only today). so, what do i do? and also, a question about firefox (though not required to answer right now) it won't hit enter in my search bar. i mean, it won't load google's search

---

### Post by Revolutionary101 on 2010-08-07
Go to Applications>Accessories>Disk Usage Analyzer to see where all your HDD space has gone. I think it is the best program for this situation.

---

### Post by miha2 on 2010-08-08
ok, so it shows almost all blue, like, down-leftish side. what's that? and it's only /home directory.

---

### Post by mikewhatever on 2010-08-08
When you install Ubuntu with Wubi, there is no Linux partition. Why don't you explain why you think there is something wrong with the 'hdd space'.

---

### Post by cariboo on 2010-08-08
This really isn't a security question, moved to General Help.

---

### Post by miha2 on 2010-08-08
i don't know. it's just all gone. and what's that blue space? is it somehow bad? well, ok, if you still have questions about what's gone, here's the answer. before i got this (let's call it virus for now)  virus, i didn't have any problems. i could delete, download, all with no problem. now whenever i delete something, or even do something, all i have is either 4 bytes or 0. that's sad, especially if you know there are viruses for windows that do that, and since i have wine, it might work against me. in fact, i can't even watch youtube videos, since i have no memory left.

---

### Post by Revolutionary101 on 2010-08-08
> **mikewhatever said:**
> When you install Ubuntu with Wubi, there is no Linux partition.

This is true, but when you install Ubuntu via Wubi you select how much space on the HDD is reserved for Ubuntu. Even though Wubi does not create a partition, it still limits the amount of space Ubuntu can take up.

I think you must have reached the limit that you set when you install Ubuntu via Wubi.

---

### Post by mikewhatever on 2010-08-08
> **miha2 said:**
> i don't know. it's just all gone. and what's that blue space? is it somehow bad? well, ok, if you still have questions about what's gone, here's the answer. before i got this (let's call it virus for now)  virus, i didn't have any problems. i could delete, download, all with no problem. now whenever i delete something, or even do something, all i have is either 4 bytes or 0. that's sad, especially if you know there are viruses for windows that do that, and since i have wine, it might work against me. in fact, i can't even watch youtube videos, since i have no memory left.

You've installed Ubuntu inside Windows to use wine to run Windows programs. This is a rather odd situation. Why not run the programs in Windows? Wubi is intended for trying out Ubuntu without partitioning, and not for long term usage.
Anyway, if you think wine is the problem, uninstall it.

---

### Post by miha2 on 2010-08-08
i might, but if it's true, then why when i delete something, the reserved free space goes to zero after some time? i don't download, i don't really understand where it goes. i have my firefox cache for 50 mb, and i tried deleting a 250 mb file, the same result. i use windows programs, but well, i've been using then in windows environment too, and it's all clean. so, what i guess is that it really is a virus that works under wine, though as i said, windows space is not being touched. i don't want to uninstall wine, neither do i want to have that virus. 

by the way, looks like i now can read the disk usage analyzer. it shows the stuff where i go to frequently. so, if i clean the temp folder, does it mean it'll return all my space?

**Mikewhatever**, if you're so smart, try using windows with lots of viruses. i think i'm smart in this case switching to linux. though i could use mac instead. there are way much more stuff for it. and since it's paid, you have lots of fully-supported programs for it. and even though most of them are paid, it won't change anything. it's mac.

 also, if it helps, my update manager hangs up if i push the update button

---

### Post by miha2 on 2010-08-08
oh, wow... looks like all the space really slow but goes to the Windows part... at least yesterday i had 8 gb there, now i have 8.2... that's weird. any ideas?

**P.S. **imagine that! it looks to me that it happened because when Terragen (Windows program) hung up, i restarted through a button. i mean, i was holding it for 6 seconds, so it would force shut down my computer, and then restarted.  (oops, didn't know can't do this)

---

### Post by CharlesA on 2010-08-08
> **miha2 said:**
> 
**Mikewhatever**, if you're so smart, try using windows with lots of viruses. i think i'm smart in this case switching to linux. though i could use mac instead. there are way much more stuff for it. and since it's paid, you have lots of fully-supported programs for it. and even though most of them are paid, it won't change anything. it's mac.

 also, if it helps, my update manager hangs up if i push the update button

If you are smart, you won't get viruses.

If you are going to be using Wine instead of Windows, why not just wipe Windows and run Ubuntu 100%?

---

