---
title: "Making Ubuntu Faster"
date: 2009-06-29
forum: General Help
---

### Post by John Private on 2009-06-29
Hi I am new to Ubuntu just recently I installed Ubuntu and I love it so far! Just wondering how would I be able to clean the registry of my computer in Ubuntu and Defrag in Ubunto as well.

~~John

---

### Post by DGortze380 on 2009-06-29
> **John Private said:**
> Hi I am new to Ubuntu just recently I installed Ubuntu and I love it so far! Just wondering how would I be able to clean the registry of my computer in Ubuntu and Defrag in Ubunto as well.

~~John

Your computer doesn't have a registry.

Windows uses a registry.
Linux does not. Nothing to clean.

There are tools to access your Windows registry from Linux (if you're dual booting). But that's rather risky...

Your Linux partition is likely formatted ext3, no need to defragment, etx3 is resistant to fragmentation.

If you have a partition with Windows, or for data, that is formatted NTFS, you may want to defragment that.

There are some tools to do that from linux...
[http://www.linux-ntfs.org/doku.php?id=ntfsdefrag](http://www.linux-ntfs.org/doku.php?id=ntfsdefrag)

---

### Post by sharathpaps on 2009-06-29
> Making Ubuntu Faster
Hi I am new to Ubuntu just recently I installed Ubuntu and I love it so far! Just wondering how would I be able to clean the registry of my computer in Ubuntu and Defrag in Ubunto as well.

~~John 


Hi John, I'm not sure about what you want to accomplish.

 Ubuntu does not have a registry like windows and therefore requires no cleaning. Like in Windows, you don't need to defragment your drive because Ubuntu uses the ext3 filesystem. It is my understanding that very little fragmentation occurs and the integrity of the filesystem is checked every 30 reboots or so.

On the other hand, if you're looking to clean the registry and defrag windows on another partition from ubuntu, I'm sorry I don't know how to do that or if its even possible for that matter...

---------------------

edit: DGortze380 beat me to it... O.o

---

### Post by lovinglinux on 2009-06-29
Welcome to the Linux world. Forget about defrag, registry cleaning, viruses, BSOD and other Windows "features" :)

BTW, I had to format and reinstall Windows every 6 months to cope with performance degradation. Since I switched to Ubuntu and re-installed only when a new release was available. There is no increasing performance degradation like Windows.

---

### Post by John Private on 2009-06-29
> **lovinglinux said:**
> Welcome to the Linux world. Forget about defrag, registry cleaning, viruses, BSOD and other Windows "features" :)

BTW, I had to format and reinstall Windows every 6 months to cope with performance degradation. Since I switched to Ubuntu and re-installed only when a new release was available. There is no increasing performance degradation like Windows.Woah you mean no Viruses?

---

### Post by synapsys on 2009-06-29
Yeah.... I'm almost starting to miss them.....

---

### Post by John Private on 2009-06-29
Thanks Everyone for the Nice Comments Rating From Right Now I rate Linux 10/10 and 10x Better then Stupid Windows.

---

### Post by lovinglinux on 2009-06-30
> **John Private said:**
> Woah you mean no Viruses?

Yep. There are a few created in laboratory as an experiment, but none in the wild. If you want to learn more about this visit one of [these threads](http://www.google.com/search?q=antivirus+needed+site%3Aubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0).

I also recommend [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial

---

### Post by synapsys on 2009-06-30
It's not that viruses can't be written for linux, it's that virus writers don't target linux. Or mac for that matter, but that is starting to change. There are a lot more unsuspecting dodo's running windows.

---

### Post by lovinglinux on 2009-06-30
> **synapsys said:**
> It's not that viruses can't be written for linux, it's that virus writers don't target linux. Or mac for that matter, but that is starting to change. There are a lot more unsuspecting dodo's running windows.

Here we go again...

Is not just that. Until Vista, Windows didn't have UAC and runs as administrator by default. Think about that.

---

### Post by synapsys on 2009-06-30
That is true, and UAC is a definite improvement. But there is no patch for human stupidity. I have personally cleaned 5 vista machines in the last two weeks. I agree that linux is inherently more secure than windows in many different ways, but it's not bullet proof. If linux had a larger following, it would be a bigger target for virus writers.

[http://milw0rm.com/platforms/linux](http://milw0rm.com/platforms/linux)

---

