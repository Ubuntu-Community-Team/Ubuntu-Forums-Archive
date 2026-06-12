---
title: "Extremely Long Boot Time"
date: 2010-09-01
forum: General Help
---

### Post by spine5 on 2010-09-01
Hi, I have a Toshiba NB 305 netbook which I purchased recently.

I originally installed the regular Ubuntu OS (10.4) on it, and noticed it took a very long time to boot. By this I mean, it would be stuck on the blinking insert character in the top left for a good 8-12 minutes. It blinks throughout the process, with nothing else on the screen. Then it would get past that, say the typical stuff, and that would go fast and then it'd take me to the login screen.

I had been using it for a bit and then installed another Linux distro on another partition (this particular distro was based on an Ubuntu 8.0 version). I noticed this booted pretty much immediately.

During the process of installing the second distro, I ended up sort of ruining my GRUB, and ended up completely wiping all my Linux partitions and starting from scratch. This time I installed the second Linux distro first, then Ubuntu. This time, I decided to try Ubuntu Netbook edition, which I was unaware of when I initially installed Ubuntu.

Unfortunately, I was unable to boot into it initially. I was dropped to a BusyBox any time I tried to boot to it. It looked as follows (not the same UUID/version, this was copied via Google, but it was almost identical to this):


```
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
     -Check rootdelay= (did the system wait long enough?)
     -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/310147a9-f21c-4e7c-aeb0-18f31073da58 does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```I Googled around and was advised to add 120 or more seconds to my rootdelay in GRUB. I added it, and the issue resolved itself, however, my boot time once again became incredibly long, just like when I had Ubuntu originally. The other Linux distro, both before and after the wipe of my partitions, boots easily 10x faster.

Anyway, due to the fact that I had to add a rootdelay, I'm assuming my "root device" (I am not really sure what that means; hard drive, Linux image, partition, or what?) is taking a very long time to start. However, considering other Linux distros seem to boot very quickly, I don't really think it's a hardware issue.

Can anyone think of a way to resolve this? Thanks.

---

### Post by spine5 on 2010-09-01
Bump.

---

### Post by kerry_s on 2010-09-02
it's a toshiba problem, you have to add to the boot line.
do a search in the forum for "toshiba" as i can't remember the steps.

---

### Post by pastalavista on 2010-09-02
Check out this post. It's a BIOS thing...

[http://ubuntuforums.org/showthread.php?t=1501994]("http://ubuntuforums.org/showthread.php?t=1501994")

---

