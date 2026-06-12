---
title: "Power failed - now I can't boot up"
date: 2011-10-26
forum: General Help
---

### Post by mbuell on 2011-10-26
Sheesh - this is like my dog ate my homework - my cat stepped on my UPS on/off button and killed the power. WAAaaaahhhhh!

So, now I can not boot. The computer mostly stalls at a blinking cursor - not even a command line. But a couple of times it tells me "no operating system". 

Now - the basics - 10.04, LTS release. 

So, I figured grub. 10.04 uses Grub2, so I get boot-repair and run it. 

No change. 

Using the live CD I can see the drives and partitions, I've checked the file systems - A-ok.

Next I will try the manual repair methods listed for grub2, but meanwhile, anybody got any other suggestions?

---

### Post by mbuell on 2011-10-26
Update:

Manual methods, including chroot methods, failed. Chroot purge method failed due to lack of /var/lib/ files and folders - don't ask me, I'm just reporting, eh?

So, I think I will reinstall, but that requires some specific planning to protect all the user files on this computer's partitions. 

We will see. So far, no good. Manana, maybe.

---

### Post by oldtimer7777 on 2011-10-26
Did you boot into recovery console to repair your system?

> **mbuell said:**
> Update:

Manual methods, including chroot methods, failed. Chroot purge method failed due to lack of /var/lib/ files and folders - don't ask me, I'm just reporting, eh?

So, I think I will reinstall, but that requires some specific planning to protect all the user files on this computer's partitions. 

We will see. So far, no good. Manana, maybe.

---

### Post by wolfen69 on 2011-10-26
If you have more than 1 OS and hard disks, the BIOS may have gotten screwed up. Check that for your hard drive order.

---

### Post by mbuell on 2011-12-14
SOLVED. Late posting to report results.

I did reinstall, but it turns out the bios answer may have been closer. There were issues with the bios date, and with the boot order. There were also issues that had to be resolved because of Grub2 - you can't fix grub2 with Grub1 methods and tools. So, ultimately I am not sure which particular "fix" fixed it, but I suspect that the boot order and the Grub2 problems were the biggest culprits.

---

