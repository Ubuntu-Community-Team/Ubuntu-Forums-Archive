---
title: "Swap Partition"
date: 2012-09-30
forum: General Help
---

### Post by ranger1021994 on 2012-09-30
I have 6GB RAM , can i delete the my SWAP partition so as to speed up my ubuntu ?

Swap creation takes a toll on my boot time.

---

### Post by Wheeladrew on 2012-09-30
You COULD, I suppose. It shouldn't effect your boot time very much, though. And within Ubuntu itself, having it available would make processes faster.

---

### Post by ranger1021994 on 2012-09-30
Creation of swap during boot takes 10-15 seconds
That is why i want to delete swap

---

### Post by idoitprone on 2012-09-30
Always keep a swap partition or file because Linux might accident try to access it and cause your system to experience freezes. 

Just delete it and make a swap file, you just lose the ability to hibernate

---

### Post by jerrrys on 2012-09-30
You could just use gparted and turn swap off...or...

You could play around with [swappiness]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F")

[More here]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=turn+off+swap&as_qdr=all&sa=Google+Search&lang=en")

---

### Post by HiImTye on 2012-10-01
it shouldn't take any more than a few cycles to mount the swap partition, check for yourself with
```
sudo swapon -s
```
and take note of the path
```
sudo swapoff -a
sudo swapon <path>
```if something is taking 10-15 seconds, I would look a little deeper to see what it is

---

### Post by mcduck on 2012-10-01
> **ranger1021994 said:**
> Creation of swap during boot takes 10-15 seconds
That is why i want to delete swap

that sounds really unlikely, the swap partition is already on your hard drive, ready to use. (And if mounting the swap partiton iss low, then that's a completely different problem, something related to your hard drive, mounting the drives etc.).

Anyway, removing swap will not speed up your system in any way, and might even have the opposite effect on some situations.

edit: how did you come to the conclusion that turning on swap is slowing your boot? Did you use a bootchart? IF you did, can we see it? Or if you are just basing this on messages output to the screen during non-graphical boot, keep in mind that most messages are actually hidden unless you remove the "quiet" option from kernel parameters in Grub. So what you see on the screen is often a message about a task that has already completed, not something that the system is currently working on. And any slowdowns or boot freezes can be because of something completely different than what's visible on the screen...

---

### Post by ranger1021994 on 2012-10-01
> **mcduck said:**
> that sounds really unlikely, the swap partition is already on your hard drive, ready to use. (And if mounting the swap partiton iss low, then that's a completely different problem, something related to your hard drive, mounting the drives etc.).

Anyway, removing swap will not speed up your system in any way, and might even have the opposite effect on some situations.

edit: how did you come to the conclusion that turning on swap is slowing your boot? Did you use a bootchart? IF you did, can we see it? Or if you are just basing this on messages output to the screen during non-graphical boot, keep in mind that most messages are actually hidden unless you remove the "quiet" option from kernel parameters in Grub. So what you see on the screen is often a message about a task that has already completed, not something that the system is currently working on. And any slowdowns or boot freezes can be because of something completely different than what's visible on the screen...

I ran dmesg and found that swap creation took almost 22 seconds.
Sometimes dmesg shows its udevd taking 22 sec and sometimes it is swap creation.

---

