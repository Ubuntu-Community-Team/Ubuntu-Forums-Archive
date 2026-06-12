---
title: "Remove old/un-needed kernal versions."
date: 2010-01-04
forum: General Help
---

### Post by yo2boy on 2010-01-04
I did "uname -a" and it's showing that I'm using 2.6.31-16-generic of the Linux Kernel. Now, in the GRUB2 boot menu, it's showing

2.6.31-14-generic & recovery
2.6.31-15-generic & recovery

and the current one: 2.6.31-16-generic & recovery.

I would like to remove the old ones because of the pileup they're creating.

Other info: I have wXP pro as my dualboot OS.

---

### Post by MelDJ on 2010-01-04
you can remove them in synaptic

---

### Post by yo2boy on 2010-01-04
I'm just nervous that it will do damage so, which ones?:

[IMG]http://i.imgur.com/Cepc3.png[/IMG]

---

### Post by MelDJ on 2010-01-04
removing either i think will cause the other one to be removed as well. this is just for 14. you will have to do the same for 15 too 
if you are nervous, i recommend you to leave it as it is and instead edit your GRUB as it the kernel takes up only about 100mb of space.

---

### Post by mcduck on 2010-01-04
Just uninstall the kernel image,headers and restricted modules for the kernel versions you want to get rid off.

You can also use the Computer Janitor (System/Administration/Computer Janitor), it will automatically offer to remove any kernels apart from the current one and one older version.

---

### Post by snowpine on 2010-01-04
Always keep at least 2 kernels (the current one, plus one older one you know to be stable). 

Showing older kernels in Grub is the default behavior because it gives you an easy way to roll back to a stable configuration. As mentioned above, the disk space used is very little, I do not see how this qualifies as a "pileup". :)

---

### Post by mcduck on 2010-01-04
> **snowpine said:**
> Always keep at least 2 kernels (the current one, plus one older one you know to be stable). 

Showing older kernels in Grub is the default behavior because it gives you an easy way to roll back to a stable configuration. As mentioned above, the disk space used is very little, I do not see how this qualifies as a "pileup". :)

In long term it definitely does waste disk space, one kernel with all related files is actually over 300MB, so just after three kernel updates you have wasted a gigabyte of disk space. Keep on running the same system for couple of years without removing any old kernels and you end with many gigabytes worth of wasted disk space.

But I agree about keeping one older kernel available in the menu, at least unless you are confident about fixing a broken system with live-CD and chroot. There just isn't any reason to keep more than that one older version.

---

