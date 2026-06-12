---
title: "dapper smp kernel?"
date: 2006-06-02
forum: General Help
---

### Post by ioannis on 2006-06-02
I upgraded from 5.10 to 6.06 with the Update Manager. The upgrade froze at the PCMCIA services point, but after re-start I used sudo dpkg --configure -a and everything completed apparently fine. Now dapper works great, but the smp version of the kernel was not installed. I went to Package Manager to install it (like I believe I did a long time ago when installing 5.10) but it shows that the kernel images available are 2.4.27-12, while I am running 2.6.15-23-686 ! Am I looking in the wrong place? Is the smp version of dapper available? If so, how do I get it?

Thanks!

---

### Post by ioannis on 2006-06-02
Actually, I just used System Monitor and noticed the 2 CPUs. So I guess although uname -r  doesn't say its the smp kernel, it actually is. Does this make sense?

---

### Post by Robgould on 2006-06-02
Yeah....smp support is built in now. You don't have to use the smp package anymore.  For example, if you install the 686-smp it is the same as the 686.

---

### Post by 5-HT on 2006-06-02
A nice change in Dapper is that the 686 kernel supports SMP. 
There is no longer a need to install a separate 686-SMP kernel.

HTH

Edit: Too slow

---

### Post by ioannis on 2006-06-02
Thanks.

Is update manager supposed to be listing an older version of the kernel? Or is there something wrong in my repository listing?

---

### Post by 5-HT on 2006-06-02
[quote=ioannis]Thanks.

Is update manager supposed to be listing an older version of the kernel? Or is there something wrong in my repository listing?[/quote] 
What older kernel(s) are listed, and which one(s) do you have installed (apart from 2.6.15.23-686)?

---

### Post by ioannis on 2006-06-02
Sorry I mistyped I should have said Package Manager, not Update Manager, but in any case: if I search for kernel in Package Manager, the kernel-images listed are versions 2.4.27-12 (for all the different architectures), and it shows as none of them installed. Under linux-image, I have 2.6.12-10-686 and -smp installed. I guess I was looking at only kernel-image, and not linux-image, whatever the difference is...
Thanks.

---

### Post by 5-HT on 2006-06-02
[quote=ioannis]Sorry I mistyped I should have said Package Manager, not Update Manager, but in any case: if I search for kernel in Package Manager, the kernel-images listed are versions 2.4.27-12 (for all the different architectures), and it shows as none of them installed. Under linux-image, I have 2.6.12-10-686 and -smp installed. I guess I was looking at only kernel-image, and not linux-image, whatever the difference is...
Thanks.[/quote] 
Yup. I'm seeing those as well using only Dapper sources, though I wouldn't recommend installing a 2.4 kernel in Dapper for obvious reasons.

If you were seeing those kernels in update-manager, that would be a different matter.

HTH

---

### Post by garyng on 2006-06-02
um, that is very strange. What is the rationale of keeping 2.4 kernel ? Its LVM2 package(which is installed by default) would bark if I have kernel less that 2.6.12

---

### Post by PowerLlama on 2006-06-03
I'm confused. I installed Dapper (well I tried to upgrade but the upgrade hosed my linux install), and it's saying I only have one processor in the system monitor but I have a dual core machine.

---

### Post by 5-HT on 2006-06-03
[quote=PowerLlama]I'm confused. I installed Dapper (well I tried to upgrade but the upgrade hosed my linux install), and it's saying I only have one processor in the system monitor but I have a dual core machine.[/quote] 
Is it one of those intel core duos? 
If so, did you install the 686 kernel?
```
 sudo apt-get install linux-686
``` 
If you do a ```
 cat /proc/cpuinfo 
``` does it list the two cores?

Alternatively, does entering ```
top 
``` and pressing '1' a few times cycle through the cores?

---

### Post by PowerLlama on 2006-06-03
It's an AMD dual core. I just installed Dapper, I haven't installed any other kernels. Should I install the 686 one?


And no, it's only listing one.

---

### Post by 5-HT on 2006-06-03
[quote=PowerLlama]It's an AMD dual core. I just installed Dapper, I haven't installed any other kernels. Should I install the 686 one?


And no, it's only listing one.[/quote]I'm not really familiar with AMD at all, but this thread should be of help:
[http://ubuntuforums.org/showthread.php?t=85917]("http://ubuntuforums.org/showthread.php?t=85917")

It recommends installing the k7-SMP kernel for newer AMD dual core processors.
However, doing a quick search around packages.ubuntu.com indicated that the k7 kernel, along with the 686 kernel, now includes SMP support.

So something like this should work:
```
 sudo apt-get install linux-k7 
``` 
As a side-note, you should be able to use the 686 as well.

HTH

---

### Post by migster85 on 2006-06-03
I have a Pentium 4 3.4GHz HT processor, not SMP, and after upgrading to 6.06 from 5.10 "cat /proc/cpuinfo" shows that I have 2 CPUs now. Can the new 686 SMP kernel recognize that I don't have an SMP machine? If not then I think I'll go back to the older kernel.

Thanks,
Max

---

### Post by PowerLlama on 2006-06-04
[QUOTE=5-HT]I'm not really familiar with AMD at all, but this thread should be of help:
[http://ubuntuforums.org/showthread.php?t=85917]("http://ubuntuforums.org/showthread.php?t=85917")

It recommends installing the k7-SMP kernel for newer AMD dual core processors.
However, doing a quick search around packages.ubuntu.com indicated that the k7 kernel, along with the 686 kernel, now includes SMP support.

So something like this should work:
```
 sudo apt-get install linux-k7 
``` 
As a side-note, you should be able to use the 686 as well.

HTH[/QUOTE]
Ahh, that's the thread I used in my last install. Thanks for the help.

It seemed to bork my XGL though.

---

### Post by manemannen on 2006-06-04
ioannis - I had the same problem with the stalling when the upgrade-manager was configuring the pcmcia-cs. Nothing worked so I had to hard reset the poor thing. And surprise surprise - now it doesn't start up. It fails when trying to start the PCMCIA servises. Any tips on how to proceed?

---

