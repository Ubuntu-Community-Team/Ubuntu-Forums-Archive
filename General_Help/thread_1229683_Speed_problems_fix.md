---
title: "Speed problems fix?"
date: 2009-08-02
forum: General Help
---

### Post by Lavaeagle on 2009-08-02
I am not sure what happend, but as I was playing with the Add/Remove Programs and Synaptic Package manager my computer slowed down more and more.

Is there something like:
CCleaner
Auslogics
or
Defraggler?

Is there just a way to speed things up in Ubuntu like deleting lots of unecessary programs or registry cleaner or something?
Please help!

---

### Post by Revolutionary101 on 2009-08-02
What is your CPU speed? Also I don't think there is a defrag software for Ubuntu because with ext3 or ext4 there is no need to defragment your hard drive.

---

### Post by Lavaeagle on 2009-08-02
I'm not exactly sure, i never had to bother to know like I did with my desktop.

With windows 7 though it ran smoothly for a long time but i knew how to keep that clean,
It's not a hardware problem it's one of those problems where something in the system is getting filled up and effecting my speed.

---

### Post by Revolutionary101 on 2009-08-02
Open system monitor and check if your swap space is being used. If it is that might be why you are having performance issues.

---

### Post by Lavaeagle on 2009-08-02
You may be onto something about CPU's but my laptop sped up a lot after i went through cleaning out programs through synaptic package manager that i didn't need.

Im monitoring it for a second here and i might be red lining my CPU's i hope not.

---

### Post by nikhilbhardwaj on 2009-08-02
you could compile your own kernel
that really speeds things up

---

### Post by jocampo on 2009-08-02
> **Lavaeagle said:**
> You may be onto something about CPU's but my laptop sped up a lot after i went through cleaning out programs through synaptic package manager that i didn't need.

Im monitoring it for a second here and i might be red lining my CPU's i hope not.

Linux is really fast without downloading or installing anything extra. You do not need to defrag hd or things like that, ext3 and ext4 do not need of that. If you want to speed up your system a bit (in case you feel is not as fast as used to be) turn off some services so they won't start automatically when you turn your PC on.

You can certainly check your system resources via console this way:

```
free -m
```

SWAP value should be really low or zero and the more RAM in cache, the better. Take a look on your CPU activity; values close to 90% or more during a lot of time could be a good indicator that there is something wrong.

---

### Post by Lavaeagle on 2009-08-02
I went through my start up and unchecked anything unecessary.

CPU hovers around 30 - 50 mainly spiking to 100 every once in a while randomly

I was watching my swap values and it was 0

I was noticing a pattern that if i leave my laptop on for about 6 hours it slows down or weird things will happen.

---

### Post by Revolutionary101 on 2009-08-04
What is your CPU speed?

---

### Post by martinbaselier on 2009-08-04
A cpu which is between 30-50% is not normal, assuming the system is idle. Running **top** from a terminal is a better way to research cpu usage. The system monitor takes quite a lot of power to run in my experience. 

Cron is running in the background to do maintenance tasks. Chances are that it will run some scheduled process when the laptop is on for a longer time. 

About the myth that linux doesn't need defragmenting. It's partly true. The truth is that linux has far less fragmentation than windows. So you don't to do it as often. To see if your system is fragmented, press esc when booting to enter grub. Then choose recovery mode and run a diskcheck (fsck) from the next menu. You would only need to worry if the fragmentation is high (bigger than 30%) 

I use this for defragmenting:
[http://vleu.net/shake/](http://vleu.net/shake/)
Use with care and I don't know if it will work on ext4.

This is nice for cleaning up your system.
[http://www.ubuntugeek.com/ubucleaner-simple-bash-script-to-keep-your-ubuntu-system-clean.html](http://www.ubuntugeek.com/ubucleaner-simple-bash-script-to-keep-your-ubuntu-system-clean.html)
Be very careful with that one, it can remove more than you want. In my case it removed all my kernels, not just the old ones I don't use anymore. Luckily I saw it and reinstalled the kernel before rebooting. Otherwise it would have been an interesting challenge to fix it. 

Since it's a good idea to keep at least a few old kernels around, you might consider turning that particular part off.

---

### Post by the8thstar on 2009-08-04
Install BleachBit from the repositories.

---

### Post by Lavaeagle on 2009-08-07
Processor type
Mobile AMD Sempron&#8482; Processor 3600+ 
 	 	 &#8226; , Level 2 cache 256 KB, Up to 1600 MHz system bus running at AC/DC Mode 25 Watt

...:/

@ the8thstar doing....now

---

