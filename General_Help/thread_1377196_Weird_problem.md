---
title: "Weird problem"
date: 2010-01-10
forum: General Help
---

### Post by Jiawen on 2010-01-10
A few days ago, I had a static discharge (ESD) that seems to have messed my system up somehow. I can't figure out exactly what's gone wrong.

The first problem was that my home partition was completely full, and many settings seemingly got overwritten. My Xfce panel icons were mostly missing, for example, and all my bookmarks in Thunar were lost. This seems to be because, while the ESD happened, I was using Listen music player to download podcasts and it seems to have used up all remaining space on my home partition and then some. Also, on login, SCIM was taking up 100% of CPU time constantly, meaning I couldn't do anything else. I figured out that Listen had filled all remaining space and, presumably, somehow overwritten some configurations, so I deleted those and my .listen configuration files, and stopped SCIM from loading on boot, which allowed some room to work in. 

Xfce now boots up properly, and it seems like most files (documents, graphics, etc.) are still where they should be, although my Xfce panel and Thunar settings did not recover. I haven't completely overwritten my home partition from a backup yet because, if everything is still okay, I don't want to lose data from the past couple weeks (I did a backup two weeks ago). I've just resigned myself to reconfiguring Xfce and Thunar from scratch. 

I checked the other partitions; they all seemed okay. (None were full up, in other words.) The only problem was in my home partition.  

Now, though, it seems like there's a further, or underlying, problem: everything is running really slowly. Changing tabs in Firefox, for example, takes several seconds every time, where usually it takes a fraction of a second. Changing desktops or windows also takes many seconds. What could be causing this?

Fsck says all my partitions are okay, at least with a basic check; I ran a fuller check on my root partition, and it took a long time, so I haven't run one on my home partition, which is even bigge). I'm currently running memtest86+; it's on pass 7 and hasn't detected any errors yet. 

If memtest86+ runs for a few more hours and doesn't detect any errors, what should be my next step? Could it be the CPU, and if so, how would I diagnose this? What other tests should I run?

Thanks!

---

### Post by Jiawen on 2010-01-10
It seems to be related to Compositor, as I found from [this e-mail list]("http://foo-projects.org/pipermail/xfce/2008-March.txt"). Disabling the composite plugin in my xorg.conf and then rebooting (not just restarting X) appears to have solved the slow window/tab/etc.-changing problems. I can't figure out why it happened, but for now, things seem to be working better.

---

