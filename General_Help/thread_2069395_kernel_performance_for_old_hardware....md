---
title: "kernel performance for old hardware..."
date: 2012-10-10
forum: General Help
---

### Post by mardybear on 2012-10-10
Greetings linux experts....

I'm a longtime Ubuntu user (~6 yrs) and prefer to run old hardware (<1Ghz processor, <512MB ram). For this reason i've stuck with older Ubuntus (8.04, 10.04) and prefer to run with openbox desktop to keep things lean.

I've been doing some distro research but can't find an answer. Seems as though many previous Ubuntu users have switched to Arch linux and often mention how lean and non-bloated their installs/systems run.

I'm happy with Ubuntu and the performance is okay, considering the old hardware.

Question: If Ubuntu 8.04 uses linux-headers 2.6.24 and the latest Arch linux uses linux-headers 3.5.6, won't the most recent install of Arch (they use a rolling release system) run heavier/slower than my old Ubuntu 8.04 install?

This is my hunch, can anyone with actual experience confirm?

Thanks in advance,

Mardybear

---

### Post by mikewhatever on 2012-10-10
Newer kernels are not necessarily always slower, sometimes, they'd have better hardware support and optimizations, which makes things faster.

As for wich distro is leaner or faster, it's really up to you: what programs and services you install at boot, what DE and programs you use, etc. Both Ubuntu and Arch allow for a very minimal and a very bloated setup, as well as middle grounds, and I strongly suspect that claims like "distro x is so much faster then y" are pure nonsense.

Ubuntu 8.04 had a much leaner Gnome DE, compared to some contemporary DEs.

---

### Post by twipley on 2012-10-10
I would really go with Lubuntu if I were you.

[http://lubuntu.net/](http://lubuntu.net/) -- 12.10 is coming out in 8 days! ;)

---

### Post by jerrrys on 2012-10-10
I was thinking that lubuntu may interest you.  It has openbox for a wm and even though its running the 3.x kernel you have the option to go with the non pae version.

---

### Post by mardybear on 2012-10-10
Howdy...

Thanks for your replies. There are a lot of Lubuntu fans on this forum! I appreciate your responses but my intention wasn't to start a favourite distro thread.

As per my original post, i was hoping someone with actual experience might be able to confirm whether a linux-header 2.6.xx versus linux-header 3.5.x actually runs faster or slower on their particular system. I realize there will be hardware differences between my system and someone elses.

Thanks mikewhatever...i also realize that software and desktop environment choices make a difference. That's why i run openbox.

FYI: My linux-header 2.6.xx shows as 76MB and the Arch linux website lists the installed 3.5.x linux-header as ~50MB...does that mean that my older/less advanced header actually has a larger footprint?

Thanks in advance,

Mardybear

---

### Post by pissedoffdude on 2012-10-10
As a poster above mentioned, the newer kernel's aren't necessarily slower.  Why not give arch+openbox a shot?  If the newest kernel does happen to be slower, you can still compile a 2.6 version from the AUR and use it as your default, or try a version of the kernel with the BFS patch

---

### Post by mardybear on 2012-10-10
Thanks pissedoffdude...

I'm leaning towards giving Arch linux a try but i hate to distro jump, enjoy keeping old installs running as long as possible and don't actually have the hard drive space to spare for a multi-boot linux system. So before i spend a fair amount of time and effort installing and setting up an Arch linux install i just wanted to know if anyone out there has actually tried this already for comparison....might save me a lot of effort.

On the otherhand....by the time this thread is completed i probably could already have a test install running ;)

Anyone out there actually tried these kernels to see if there's a difference (2.6.xx vs 3.5.x performance on older hardware). I notice that a lot of Arch linux users often jump between Ubuntu and Arch but typically return back to Arch in the end.

Thanks again for any users who can post about their experiences between these kernel differences.

Mardybear

---

### Post by mikewhatever on 2012-10-10
> **mardybear said:**
> ...

As per my original post, i was hoping someone with actual experience might be able to confirm whether a linux-header 2.6.xx versus linux-header 3.5.x actually runs faster or slower on their particular system. I realize there will be hardware differences between my system and someone elses.
That doesn't make much sense. From what I can guess, you are probably after kernel performance benchmarks, which are numerous and public. For example: [http://www.phoronix.com/scan.php?page=article&item=linux_kernel_test2439&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_kernel_test2439&num=1)


> 
FYI: My linux-header 2.6.xx shows as 76MB and the Arch linux website lists the installed 3.5.x linux-header as ~50MB...does that mean that my older/less advanced header actually has a larger footprint?

Thanks in advance,

Mardybear

What sizes are those? I am afraid I've no idea what you are talking about.

---

### Post by mardybear on 2012-10-11
hi again mikewhatever...

Thanks for the link but Linux Kernel Benchmarks Of 2.6.24 Through 2.6.39 does not provide a comparison of linux kernel 2.6 vs 3.5 (my original post), so it's not helpful. 

I haven't been able to find any info that compares 2.6 and 3.5 for performance. If you come across this type of information please let me know. Google is usually my friend but not this time.

Mardybear

---

### Post by critin on 2012-10-11
I'm using an old Dell desktop, circa 2002, Intel® Pentium(R) 4 CPU 2.40GHz with no enhancements added.

I'm running Natty with a 2. something kernal, and 12.10 xubuntu with the latest kernal.  I can tell no difference in them.  They both work just fine for me.  They seem fast enough, certainly they do not stall or lag.

---

### Post by 2F4U on 2012-10-11
I am running Archlinux with 3.5 and 3.6 kernels on two ThinkPads (X31 and T41 from ca. 2003 with Intel Centrino processors). I can compare the performance to a 10.04 install and there is no difference. I think what is more important than the kernel is the rest of the system, e.g. what desktop environment you are using, what background processes/daemons are running, and what software you use. This determines you experience.
For me, Archlinux runs very well on those old laptops and I am happy that I took the effort to install Arch on them. Besides, Archlinux is one of the few remaining Linux distributions that provides i386 kernel which do not require a pae-capable CPU (both ThinkPads have non-pae CPU's) and that was one important reason for me to choose Archlinux.

---

### Post by mardybear on 2012-10-11
2F4U and critin: Thanks for letting me know about your experiences as it makes me less apprehensive about upgrading to the latest Arch Linux or a newer but leaner version of Ubuntu. I was initially apprehensive about upgrading to a newer and 'improved' kernel only to find my old hardware getting bogged down.

Thanks again,

Mardybear

---

