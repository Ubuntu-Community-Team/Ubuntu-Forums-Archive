---
title: "Ubuntu detects wrong processor"
date: 2011-12-08
forum: General Help
---

### Post by gunksta on 2011-12-08
OK, I'm at a loss on this one. I reinstalled my laptop to get a nice clean start. I'm running a Lenovo X220 with a second generation i5 processor. But, htop shows me only having 2 cores (I had 4 before I reinstalled) and ```
head /proc/cpuinfo
``` shows that I have Dual Core E5200. I don't think my processor changed just because I reinstalled the OS.

So, the question becomes -- How can I force Ubuntu to re-detect the processor? I want to use all of my 'cores', not just two of them.

Yes - I do realize that two of the cores are created by hyperthreading, but my point is that before reinstalling htop showed 4 cores and now it shows 2 and tells me my processors is a mid-2008 dual core processor.

---

### Post by killermist on 2011-12-08
I am definitely not an expert on how the kernel deals with multiple cores, but I have a theory.
It could be that the hyperthreading, being essentially just some extra cache on the chip to make context changes (rotating from thread to thread) "less expensive" (faster), it is really just 2 cores, and it is more efficient for the kernel to treat it as just 2 cores (and just silently benefit from the increased speed of context changes) than to treat 2 cores as 4 cores and actually lose efficiency.

Just a theory, and if I'm totally off base, I'm sure a more informed person will correct me shortly.
I would say that as CPUs are one of the elements of the system that is most commonly similar, and predictable, if you just did a fresh install, it is probably configured by default to use the CPU in the most efficient manner the CPU is capable.  But, again if I'm off base, I'm sure I will be corrected (which I don't mind, because it'll mean that I learn more in the process).

[edit]
Pre-assuming that I am wrong, do you remember what the CPU was being detected as before you reinstalled?
What is the output of ```
head -n 12 /proc/cpuinfo
```

---

### Post by gunksta on 2011-12-09
I am a complete moron. Last night, I had several tabs open. One of them was logged into my server which does run an older dual core processor. I was running htop on my server. Normally, I have a tmux config running that gives me a yellow bar across the bottom of the terminal when I am logged into a remote machine and green across the bottom when I am on my local machine. I don't have all that set up yet on this machine and I am apparently more dependent on it that I realized. I only figure out this morning that the "wrong" cpuinfo was from my server, not my local machine.

Doh.

---

