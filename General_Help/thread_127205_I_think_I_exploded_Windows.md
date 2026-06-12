---
title: "I think I exploded Windows"
date: 2006-02-08
forum: General Help
---

### Post by PerfectSelf on 2006-02-08
Yep. I've been doing a lot of beginner Linux tinkering on my laptop over the last month. I've kept my WindowsXP install on the HDD and installing various Linux distros in the free space that I created. 

Over the past couple of days, I've found it impossible to boot back into Windows. I configured the menu.lst file in GRUB a variety of ways, but it refuses to detect my Windows partition (or at least do anything useful with it). More than likely, I probably screwed up the MBR. As such, I wanted to start fresh again, delete Linux, and return my Windows partition back to its original size. I followed the instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=113630"). Windows fails the error check. "File system corrupt or not formatted" the screen says. I can't view the details of the partition because the Terabyte program cannot mount it. 

My impression after all this is that I've screwed with my partitions and bootloaders so much over the last month that I've done some sort of serious damage somewhere. If my Windows install is truly corrupted, it's not too big a deal since I have little of importance installed in Windows.

What are your opinions on this? Am I just screwed? Something I'm missing?

---

### Post by ice60 on 2006-02-08
hi, do you have any windows error meassages you can post?

there's a very nice program in synaptic called Testdisk which can recover lost partitions too.

---

### Post by PerfectSelf on 2006-02-08
Windows error messages? I can't even boot Windows up to get Windows error message, if that's what you mean.

I'll have to take a look at Testdisk.

---

### Post by bonzodog on 2006-02-08
It does sound like the windows partition is screwed beyond use, but this could be the ideal time to reformat the entire disk (all of it) and make your machine linux only. You won't regret it, I promise you.

---

### Post by Lord Illidan on 2006-02-08
Can you read the Windows partition from Ubuntu? If not, then you do have some serious probs with Windows. If you are not using it, wipe it!

---

