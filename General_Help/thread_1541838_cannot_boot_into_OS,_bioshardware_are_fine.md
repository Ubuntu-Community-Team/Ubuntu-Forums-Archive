---
title: "cannot boot into OS, bios/hardware are fine"
date: 2010-07-29
forum: General Help
---

### Post by WinterMadness on 2010-07-29
Today when I turned my laptop on it went to the bios like normal, and after that all I saw was a cursor.

I am able to boot into a live CD and view my files on my hard drive

im using Lucid Lynx. and there was a kernel update kind of recently that required a restart but i didnt do that immediately.

please let me know what I can do to fix it.

---

### Post by WinterMadness on 2010-07-29
bump

---

### Post by WinterMadness on 2010-07-29
lots of posts going on today....

---

### Post by prodigy_ on 2010-07-29
Kernel updates sometimes break things.

Care to give some more info? What video card does your laptop have? Did you try to boot in recovery mode?

---

### Post by ov3rcl0ck on 2010-07-29
Instead of booting into recovery mode, you should try booting into a older kernel, then you will be able to start fixing the problem, whatever it may be.

You might want to try these commands:
> 
sudo apt-get update
sudo apt-get install -f
sudo apt-get check


Then maybe to make sure you're system was fully updated you might wanna try this:
> 
sudo apt-get update
do-release-upgrade
sudo apt-get upgrade


I put the release upgrade in there in case you didn't upgrade properly.

---

