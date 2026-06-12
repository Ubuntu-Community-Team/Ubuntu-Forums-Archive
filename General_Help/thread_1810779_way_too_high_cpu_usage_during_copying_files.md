---
title: "way too high cpu usage during copying files"
date: 2011-07-23
forum: General Help
---

### Post by dochegal on 2011-07-23
hi!

got a kind of problem here with kubuntu 11.04 (64bit). every time i copy files (especially big ones) i get 100% cpu usage (all cores) on my dualcore (intel core2duo 6700 @ 3,2 ghz). it does not matter if i copy files local of via nfs to my nas.
any ideas?

---

### Post by dochegal on 2011-07-24
dma is activated

---

### Post by bakegoodz on 2011-07-24
Is one of the disk NTFS? I find the opensource ntfs-3g driver (Built-in Ubuntu) is a real CPU hog. I found out that Paragon's free NTFS linux driver has much better performance and CPU utilization. But it only works with command line Mount or you can put it in the fstab, doesn't work with GUI mount tools.

---

### Post by dochegal on 2011-07-25
no, the local filesystem is ext4, also on the nas which is accessed via nfs.

---

### Post by bakegoodz on 2011-07-26
In a terminal run " top " during the copy. What process is using up the processor?

---

### Post by mvmacd on 2011-07-26
Are you sure it's 100% "CPU" usage?  I have a CPU meter GNOME widget, and whenever I copy files, the 'IOWAIT' goes up 100%. I used to think it was flooring the CPU, till I looked up what the green color was: IOWAIT

---

### Post by dochegal on 2011-07-27
when i run top during copying it shows that nautilus needs about 60% cpu tops. kde's system monitor still shows about 100% on both cores. maybe top does not show everything?

---

### Post by evanh on 2011-08-07
Same here.  When copying a file from one drive to another I can max out both cores (200%) and it doesn't quite make transfer rate spec for the drives either.  When copying within a single drive it's about 160% typical.  These are large files too, the tests are 1GB+.  Even tried dd with 1MB block size - exactly the same result.  Read and write separately - same result.  So, it's a low-level problem.  This behaviour occurred when I changed from Unbuntu 10.04 (32 bit) with Gnome, which I can still switch back to and get full speed transfer at a mere 15% (I think) CPU burn, to Kubuntu 11.04 (64 bit) with KDE.  I'm, as of yet, unsure if it's Kubuntu specific or the general 11.04 release.  Time to download vanilla Ubuntu 11.04 I guess ...

---

### Post by evanh on 2011-08-07
Ugh!  This forum wipes all formatting!

---

### Post by evanh on 2011-08-07
Wow, it is Kubuntu.  I just tried Ubuntu 11.04 (32bit) release and also the 64 bit release from live CD.  Both performed flawlessly.  I then tried the Kubuntu 11.04 live CD for my main install and, sure enough, 100% CPU for my now standard test:  dd if=/dev/sdx of=/dev/zero bs=1MB

---

### Post by evanh on 2011-08-07
Tested both Kubuntu 10.10 and 10.04 now and both have the same bug.  This is a little shocking.  How can all the Kubuntu releases have such a flaw when none of the Ubuntu releases appear to be affected?

---

### Post by evanh on 2011-08-07
> **mvmacd said:**
> Are you sure it's 100% &quot;CPU&quot; usage?  I have a CPU meter GNOME widget, and whenever I copy files, the 'IOWAIT' goes up 100%. I used to think it was flooring the CPU, till I looked up what the green color was: IOWAIT

Hmm, unless this is the reason.  Maybe KDE's monitor shows an IOWAIT as busy.  That wouldn't be sensible as a wait is non-used time but I guess anything's possible.  It would solve the query though.  Have to get the monitor program fixed then.

---

### Post by evanh on 2011-08-07
Ok, yep, got a little worked up on this one.  Damn monitor proggie!

I just gave top a whirl and got 17% for dd.  There doesn't appear to be a total cpu usage figure but there was the following line:

Cpu(s):  1.3%us,  7.3%sy,  0.0%ni, 48.0%id, 43.2%wa,  0.0%hi,  0.2%si,  0.0%st

I'm guessing id is short for idle and that each core is worth 50% of overall CPU capability.  That's a bit silly too, each core should be worth 100%.  So, anyway, there is 43.2% in waits which is 86% of one core.  That sounds about bang on what I'm expecting for flawless operation.


PS:  I figured out how to make paragraphs in this forum  :)

---

### Post by dochegal on 2011-08-15
hi!
thank you very much - so it's kubuntu...
ubuntu isn't really an option for me since i really hate unity and starting with 11.10 there'll be no gnome 2.32 anymore. maybe i'll switch to fedora or opensuse... xfce looks interesing...

---

### Post by evanh on 2011-08-18
No no, Kubuntu is fine.  Waits are idle time.  It's just KDE's CPU monitor progie badly reporting waits as busy instead of idle.

---

