---
title: "Problem restoring GRUB"
date: 2011-03-11
forum: General Help
---

### Post by mssever on 2011-03-11
Since my hard drive was about to die, I replaced it, after using dd to make an image of each partition. Now, I've used dd to restore the partitions on the new drive. The problem is that my hard drive is unbootable.

First, from the live USB, I attempted to run ```
$: sudo grub
root (hd0,5)
```
The command grub isn't present on the live USB (Ubuntu 10.10). So, I set up a chroot to my system (Ubuntu 10.04 Netbook, using GRUB1 as GRUB2 doesn't work on my hardware).

In the chroot environment, sending the command "root (hd0,5)" results in the following error: "Error 21: Selected disk does not exist". I've tried setting the numbers to every reasonable (and unreasonable) value I can think of, just in case I made a mistake, but to no avail. Google searches don't turn up anything that looks relevant to me.

I managed to get grub installed from my live USB, but it's GRUB2, for which I have no configuration. It's possible that these days it might be compatible with my hardware, but I have no desire to spend the time to find out. At any rate, I just get a GRUB prompt at boot time, and I can't figure out what to type to manually boot.

Another curious thing that might be relevant is that in my non-chroot environment, bash tab completion only finds /dev/sda2 (my swap partition), not any of my data partitions. Yet, I can mount those other partitions just fine.

Can anyone help me get my computer to boot?

(By the way, it's an HP Mini 110.)

---

