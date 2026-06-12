---
title: "What does %wa in &quot;top&quot; signify?"
date: 2009-09-29
forum: General Help
---

### Post by theWrkncacnter on 2009-09-29
Hi all
I'm trying to get the most performance out of an old computer. One of the things that bugs me is that the hard drive is often very noisy -- I checked top, and it showed around 65.8 to 90%wa. Sometimes it is zero or low for a while.

first of all, what does wa stand for, besides "wait"
second, what is causing it to be so high?
third, what can I do to fix it?

I know this is probably not enough information, but I'm not sure what else to find out. My top processes are "Xorg," "firefox-3.5," and "beagled"

thank you for your help!

---

### Post by KlinerDraken on 2009-09-29
[wa -> iowait: Amount of time the CPU has been waiting for I/O to complete.]("http://ubuntuforums.org/showthread.php?t=99500")


Reading the comments on that post sounds to me that your computer is waiting on the hard drive to read/write. Maybe its going bad?

---

### Post by undecim on 2009-09-29
This if from the "top" manual (man top):

```
 2c. CPU States
       The CPU states are shown in the  Summary  Area.  They  are  always
       shown  as  a  percentage  and are for the time between now and the
       last refresh.

       [...]

        wa  --  iowait
          Amount of time the CPU has been waiting for I/O to complete.
```

This means that the CPU is waiting on the hardware to do something. It seems that a piece of hardware (perhaps the noisy hard drive? but we shouldn't jump to conclusions...) is running slowly.

---

### Post by jruden on 2009-09-29
Rather than suspecting the hard drive to be slow I would start checking memory allocation. It maybe that your older computer is struggling to get the programs running to fir within the main memory so it is forced to start swapping out memory to disk => a lot of disk I/O. In that case adding some more ram would be preferably. It may also be possible to switch to more efficient applications, but often it is not worth the effort compared to the relatively cheap memory prices.

---

### Post by kerry_s on 2009-09-29
> I'm trying to get the most performance out of an old computer. 

what are the specs?
beagle is a big, do you really need it?
what are you trying to tune?


i use a 10 year old rig.

---

### Post by theWrkncacnter on 2009-10-23
Thanks for all your replies everyone!

It's a PIII, 733MHz computer with the maximum supported memory: 3x128MB. I would add more memory if I could, but alas I've reached the ceiling for this computer. I don't know how to find hard drive specs, but the hard drive is as old as the computer. I added a new, secondary hard drive that I use mainly as storage that is fast and quiet. I probably don't need beagle if another, more prudent search tool exists.

The computer lags whenever the wait is high -- it isn't always high, but when it is, it's frustrating

---

