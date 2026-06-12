---
title: "Why one application could take Ubuntu down?"
date: 2011-11-06
forum: General Help
---

### Post by alexei_ on 2011-11-06
This is happening not for first time.
An application (probably because of a bug) could start taking ALL RESOURCES of the system. As result - the system becomes SO SLOW that there for ANY simple ACTION it takes several minutes.

Sometimes I was able (after spending 20 minutes!!! - what a waste of time) to get to a console (Ctrl+Alt+F1) do "ps -ef 
| grep app_name; kill app_id)

But not last time. Last time the issue was created by "vlc". I have NEVER had any problem like this running "vlc" in Windows... however this is not the first time when this happens on Ubuntu.

Is there any way to prevent this issue in the future???
Why Ubuntu does have DEFAULT SETTINGS to prevent this???

I can hardly remember having similar issue with Windows XP Home(yes that was "Home" edition -- at least was not crushing so much as Ubuntu)

---

### Post by coldraven on 2011-11-06
I have not had any problems with VLC in any version of Ubuntu from 8.04 to 11.10.
The only program that occasionally freezes my system is Adobe Flash.
Try running memtest from the grub menu when you boot up your machine.

---

### Post by linuxaddix on 2011-11-06
ive actually ran into problems installing vlc on a friends amd64 11.10.the sound comes out all messed up tried this:
[http://www.ubuntuupdates.org/packages/show/371544](http://www.ubuntuupdates.org/packages/show/371544)
and everything should be alright.

---

### Post by alexei_ on 2011-12-06
Still do not have the answer. How to configure Ubuntu to avoid this in future? The problem is not vlc. There could be any other bad written application which may consume TOO MUCH of resources... Well may be there is a bug in Ubuntu itself?

---

### Post by oldtimer7777 on 2011-12-06
> **alexei_ said:**
> Still do not have the answer. How to configure Ubuntu to avoid this in future? The problem is not vlc. There could be any other bad written application which may consume TOO MUCH of resources... Well may be there is a bug in Ubuntu itself?

You will need to sit with HTop running and patiently wait for the culprit to present itself.  It will show up eventually, and you will know what is the issue -IF- it is what you think it is and not hardware related instead.

sudo apt-get install htop

---

### Post by cortman on 2011-12-06
Would it be possible to write a script and have it autorun that would kill or suspend a program that tries to use any more than a given amount of RAM, CPU cycles?

---

### Post by WorMzy on 2011-12-06
Buy a PC with more than one CPU core.

---

### Post by matt_symes on 2011-12-06
Hi

Take a look at cpulimit

```
sudo apt-get install cpulimit
```

For information

```
man cpulimit
```

You mention vlc. Has it happened with other applications ?

What are the specs of your machine ? what version of Ubuntu are you running ? How much memory do you have ?

```
sudo lshw -c cpu
```

```
uname -a
```

```
cat /etc/lsb-release
```

```
free -m
```

Kind regards

---

### Post by alexei_ on 2011-12-07
@oldtimer7777: -- Yes, I use htop for long time... however sometimes it takes huge amount of time to open it when system freezes.
@cortman -- Yes, I could try to do such script... it may work as long as correct values of memory usage reported... and script actually get executions time.

@matt_symes -- this looks like right direction for troubleshooting. Issues were happening mostly with vlc. Also I have seen similar issue with convert (from imagemagic). Interesting issue with vlc was -- after playing several "mts" video file I could not not play ANY VIDEO... In that case I had to reboot or "kill X".

 I have recently upgraded from 10.10 to 11.04 and then 11.10. Now I have issues described in [Ubuntu 11.10 - Performance issues after upgrade]("http://ubuntuforums.org/showpost.php?p=11493849&postcount=1"). Info about my laptop is also there.

Now I have:

> sudo lshw -c cpu> 

  *-cpu                   
       description: CPU
       product: AMD Athlon(tm) II Dual-Core M300
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 4
       bus info: cpu@0
       version: New Processor Technology
       slot: Socket S1G3
       size: 800MHz
       capacity: 2GHz
       width: 64 bits
       clock: 200MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
       configuration: cores=2 enabledcores=2 threads=2
> uname -a> 
Linux hostName 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
> cat /etc/lsb-release> 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
> free -m> 
             total       used       free     shared    buffers     cached
Mem:          3707       2988        718          0          3        126
-/+ buffers/cache:       2859        848
Swap:        10862        963       9899


---

### Post by matt_symes on 2011-12-07
Hi

You computer specs seem fine as far as CPU and memory go.

I am wondering if the problem is with VLC alone as you have been having freezes when coming out of suspend.

Let's try to check if VLC memory usage is the problem. Follow these steps.

1. Start VLC.
2. Open a console or terminal and type (or copy and paste)

```
rm ~/vlc.dump; while (pgrep vlc); do ps --no-header -p $(pgrep vlc) -o cmd,%cpu,%mem >> ~/vlc.dump; sleep 60; done
```This will take a reading of VLC's memory every minute and write it to the file vlc.dump in your home directory.

3. Start watching one of the videos (mts) that has been causing the problems.
4. When you get the problems kill x from the console.
5. Wait for the script to finish ( this will not be relevant if you have used a terminal in X). It will take up to 60 seconds. Post back the results file here. If it is large then doctor it to be smaller.

Kind regards

---

### Post by alexei_ on 2011-12-09
I am on Ubuntu 11.10 for about 2 weeks. While I am frustrated because of missing features/setting which were before (those need separate thread) the exact issue with vlc did not happened yet. 

I like your script. Most of my "mts" videos are short, so I changed "sleep time" to 5. I got:

> 
vlc /tmp/test.mts 8.6  2.8  
vlc /tmp/test.mt 15.0  2.8  
vlc /tmp/test.mt 20.0  2.8  
vlc /tmp/test.mt 24.5  2.8  
vlc /tmp/test.mt 28.4  2.8  
vlc /tmp/test.mt 32.5  2.8  
vlc /tmp/test.mt 35.8  2.7  
vlc /tmp/test.mt 38.5  2.7  
vlc /tmp/test.mt 38.9  2.7  
vlc /tmp/test.mt 37.1  1.3  
vlc /tmp/test.mt 35.1  1.2 


During usage of 11.10 I observe already reported issues in 
[Ubuntu 11.10 - Performance issues after upgrade]("http://ubuntuforums.org/showthread.php?p=11493849#post11493849")

Looks to me that with every suspend performance downgrade... till freezings of 5-60 seconds becomes hard to accept... Then I do restart. I have to say that since 11.10 the system was not able to shutdown itself yet. Last time I gave it 8 hours ... Then I had to hold power button in order to restart it. During startup it behaves like after crash, it does check disks. With fresh started system there are no freezes.

---

