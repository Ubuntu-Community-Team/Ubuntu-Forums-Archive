---
title: "Hard disk thrashing!"
date: 2012-09-21
forum: General Help
---

### Post by joeb21 on 2012-09-21
Hi, I run lubuntu 12.04 and have twice in as many days had the problem whilst using Firefox that the hard disk begins to thrash and my system literally grinds to a halt. During this time the mouse pointer moves like molasses with a huge latency and the system does not respond to mouse clicks or keyboard input (tried shortcuts for the terminal and task manager). After waiting upwards of 15 minutes I had to resort to a hard reboot. :mad:

Regardless of what is causing this problem (possibly the flash plugin?), how can the OS allow a rogue application to completely take over like this? Also, does anyone have any tips on what I could try when it inevitably happens again? Fortunately I'd saved changes to files I'd had open at the time, but next time I might not be so lucky.

---

### Post by drdos2006 on 2012-09-21
Check your hard drive with the Disk Utility -> Smart Data.
Run the Check Hard Disk for Errors from the Smart Data section, see if that helps.

I throw my Hard drives away after 3 years use and replace.

regards

---

### Post by joeb21 on 2012-09-21
> **drdos2006 said:**
> Check your hard drive with the Disk Utility -> Smart Data.
Run the Check Hard Disk for Errors from the Smart Data section, see if that helps.

I throw my Hard drives away after 3 years use and replace.

regards

I'll give it a go.

Thanks.

---

### Post by oldos2er on 2012-09-21
How much RAM do you have, and what size is your swap partition?

---

### Post by joeb21 on 2012-09-21
> **oldos2er said:**
> How much RAM do you have, and what size is your swap partition?

1 GB RAM and no swap partition - I'm using wubi.

---

### Post by oldos2er on 2012-09-22
> **joeb21 said:**
> 1 GB RAM and no swap partition - I'm using wubi.

You could try running a memory monitor while running Firefox, since it sounds like your RAM is filling up and has no place else to go (i.e., no swap), so to speak.

Or do a normal install.

---

### Post by black veils on 2012-09-22
firefox >> preferences >> advanced >> general tab >> use hardware acceleration when available (disable this)

could that make a difference?

---

### Post by oldos2er on 2012-09-22
Hi black veils, please start your own thread, "thread hijacking" is considered rude. Thanks!

---

### Post by black veils on 2012-09-22
I was offering possible help, nothing else actually.

---

### Post by joeb21 on 2012-09-22
> **oldos2er said:**
> You could try running a memory monitor while running Firefox, since it sounds like your RAM is filling up and has no place else to go (i.e., no swap), so to speak.

Or do a normal install.

I did a bit of searching and it looks like wubi uses swap files in place of a swap partition. Under normal circumstances Firefox doesn't appear to be using an excessive amount of memory. 

The two times I had the thrashing problem I wasn't even able to change window focus, so analysing the memory situation is difficult.

---

### Post by joeb21 on 2012-09-22
> **black veils said:**
> firefox >> preferences >> advanced >> general tab >> use hardware acceleration when available (disable this)

could that make a difference?

I'll look into this as well. Thanks.

---

### Post by oldos2er on 2012-09-22
Found this on the WubiGuide site:

"Improving disk performance

Poor disk performance is usually due to a fragmented drive or to a low amount of memory (frequent swapping).

You can use jkdefrag to defragment from within Windows.

download jkdefrag [http://www.kessels.com/JkDefrag/](http://www.kessels.com/JkDefrag/)

unzip
run: jkdefrag c:\ubuntu (or c:\wubi in 7.04 and above)"

---

