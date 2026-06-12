---
title: "Performance improvements"
date: 2011-10-08
forum: General Help
---

### Post by MyD0j0 on 2011-10-08
I have a HP Pavilion dv9000 laptop (dv9008nr specifically) which has an AMD Turion dual core cpu and aside from maxing out my memory to 2Gb, I've been searching for ways to improve the performance of my system.  I'm running naughty narwhal 11.04 with Ubuntu Studio real time kernel installed.

I came across this [Improve performance in Ubuntu]("http://ubuntuforums.org/showthread.php?t=189192") thread talking about several options to improve performance, but since it is so outdated, I was wondering if there is yet anything comprehensive for 11.04.  For instance, I was browsing synaptic to find a cpu specific kernel, but I'm either blind or there isn't one (for 11.04).  Also, as I was going through most of the threads I came across information that some things were no longer necessary because they've been implemented in ubuntu since the thread was originated.

anyway...it would sure be great if there were any optimizations someone could suggest and point me in the direction

---

### Post by dcstar on 2011-10-08
> **MyD0j0 said:**
> I have a HP Pavilion dv9000 laptop (dv9008nr specifically) which has an AMD Turion dual core cpu and aside from maxing out my memory to 2Gb, I've been searching for ways to improve the performance of my system.  I'm running naughty narwhal 11.04 with Ubuntu Studio real time kernel installed.
........
anyway...it would sure be great if there were any optimizations someone could suggest and point me in the direction

Use 64-bit.

---

### Post by MyD0j0 on 2011-10-10
Thanks for the reply, David.  

output of uname -a:

eric@mymachine:~$ uname -a
Linux MasterD0j0 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:18:14 UTC 2011 i686 athlon i386 GNU/Linux

Am I misinterpreting this?  I would think this says that I can't run the 64 bit.  If that isn't the case, would I just recompile the kernel?  synaptic shows the images being x86/x86_64 which leads me to believe that the same image is used, just compiled with different options?

thanks for any further assistance you can provide!

---

### Post by mastablasta on 2011-10-10
this command just lists what you are using: [http://www.computerhope.com/unix/uuname.htm](http://www.computerhope.com/unix/uuname.htm)

since you have a dual core porcessor you can use 64bit. (you can just try a liveCD/USB boot of 64 bit version)

also to keep more memory free use lighter desktop environment such as XFCE

---

### Post by snowpine on 2011-10-10
In what way is your performance bad: boot up, launching applications, watching videos, ripping .mp3's, rendering architectural blueprints, etc.? 

In other words, there are many ways in which a computer can be slow, each with a different solution.

If the problem is just general sluggishness than I recommend  using the terminal command 'top' to see what is eating up the most CPU and/or RAM.

---

### Post by Bobhuber on 2011-10-10
> **MyD0j0 said:**
> I have a HP Pavilion dv9000 laptop (dv9008nr specifically) which has an AMD Turion dual core cpu and aside from maxing out my memory to 2Gb, I've been searching for ways to improve the performance of my system.  I'm running naughty narwhal 11.04 with Ubuntu Studio real time kernel installed.

I came across this [Improve performance in Ubuntu]("http://ubuntuforums.org/showthread.php?t=189192") thread talking about several options to improve performance, but since it is so outdated, I was wondering if there is yet anything comprehensive for 11.04.  For instance, I was browsing synaptic to find a cpu specific kernel, but I'm either blind or there isn't one (for 11.04).  Also, as I was going through most of the threads I came across information that some things were no longer necessary because they've been implemented in ubuntu since the thread was originated.

anyway...it would sure be great if there were any optimizations someone could suggest and point me in the direction
Read the last part of this post (swappiness) > [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Install 64/bit OP system as already suggested

---

### Post by MyD0j0 on 2011-10-10
> **snowpine said:**
> In what way is your performance bad: boot up, launching applications, watching videos, ripping .mp3's, rendering architectural blueprints, etc.? 

In other words, there are many ways in which a computer can be slow, each with a different solution.

If the problem is just general sluggishness than I recommend  using the terminal command 'top' to see what is eating up the most CPU and/or RAM.

Except when opening programs nothing jumps out as being overly intensive in top.  On log in, the desktop loads a little slow--better with ubuntu classic than unity.  Occasionally, in a browser, switching tabs almost seems like it is downloading the page again whether i'm using chrome or FF.  Starting Eclipse CDT (also has aptana studio plugin) is the biggest drag, which might take as much as 70% cpu and close to 40% memory. But once it's running, it's like any other program--occasionally slower than I'd like.

---

### Post by snowpine on 2011-10-10
> **Bobhuber said:**
> Read the last part of this post (swappiness) > [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Install 64/bit OP system as already suggested

These are both good suggestions... check your swap usage!

---

### Post by MyD0j0 on 2011-10-10
> **Bobhuber said:**
> Read the last part of this post (swappiness) > [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Install 64/bit OP system as already suggested

Reading up on the swap; thanks for the tip!

---

### Post by MyD0j0 on 2011-10-13
> **Bobhuber said:**
> Read the last part of this post (swappiness) > [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Install 64/bit OP system as already suggested

So I installed 64bit and swap was taken care of by re-installing the new system over the old.  It took just a little over 8 hours to install the new system and then re-install all my applications and import their settings.  The system is moving quite a bit faster now--even eclipse opens/closes in a matter of seconds rather than a minute +.

Thanks to everyone who replied--I apreciate all the tips and advice.

---

