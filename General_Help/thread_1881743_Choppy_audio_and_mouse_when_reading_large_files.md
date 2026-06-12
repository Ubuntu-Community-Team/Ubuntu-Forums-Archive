---
title: "Choppy audio and mouse when reading large files"
date: 2011-11-16
forum: General Help
---

### Post by marinara on 2011-11-16
I installed Lubuntu (oneric) 3 days ago,  first time using ubuntu.

I've noticed that when I start up a virtual machine, or hash a large file, my audio cuts in and out (stutters) and my mouse pointer gets choppy.

Is this a bug?  Can I fix it?

---

### Post by Rodney9 on 2011-11-16
> **marinara said:**
> I installed Lubuntu (oneric) 3 days ago,  first time using ubuntu.

I've noticed that when I start up a virtual machine, or hash a large file, my audio cuts in and out (stutters) and my mouse pointer gets choppy.

Is this a bug?  Can I fix it?

What are the specifications of your machine ?

Have a look at 'Task Manager' in 'System Tools' to see what your memory and CPU are up to, you may be maxing them out.

Check out [The Lubuntu One Stop Thread]("http://ubuntuforums.org/showthread.php?t=1844755") for Tips How-To's and Screen-Casts on Lubuntu


Rodney

---

### Post by marinara on 2011-11-16
Thanks Rodney, but running 1 application +  Audacious is not going to max out my CPU, and running a bittorrent client is not going to max out my RAM.

Athlon II 3.0Ghz
780GM-a motherboard
4 GB 
SATA II

---

### Post by marinara on 2011-11-16
Rodney, you are probably right about this.

I just ran grep on a 8GB file, which should have caused the audio to drop out, but it didn't.

I apologize.

I'll try maxing out the CPU and see if that causes the audio to stop.

**EDIT 
I have just tried stressing the CPU with 2 threads of pi (super pi)
no audio drops.  I'm thinking the problem might be something like a vmware driver, or maybe an NTFS driver

---

