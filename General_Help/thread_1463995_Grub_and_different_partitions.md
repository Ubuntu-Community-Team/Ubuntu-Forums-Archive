---
title: "Grub and different partitions"
date: 2010-04-27
forum: General Help
---

### Post by Proxin on 2010-04-27
Hi all,
Here is my situation. I have a removable harddrive (sdb) that I installed Ubuntu on. However, I want to have Grub boot from my laptop's Internal harddrive (sda). I installed Grub to /dev/sda when I was in the Live session installing Ubuntu.

However, Grub gives an error upon booting without the secondary harddrive (sdb with Ubuntu installed) plugged in, and displays a grub rescue prompt. I want to be able to boot up from Grub from sda, without having my sdb plugged in. Is there any way to do this?

I asked on #grub on IRC and got the following response:
grub needs to be able to read /boot to work... Create a /boot partition on your internal drive, set it up to mount as /boot in /etc/fstab, then re-run grub-install and "update-grub".

I'm new to Ubuntu so I am not certain, at all, how to do the fstab and /boot stuff... I made an ext3 partition on my internal harddrive (sda) to use for boot though. Can someone please help me out here?

---

### Post by oldfred on 2010-04-27
What do you have installed on your internal drive that you will be booting? You should also have grub installed in the external to boot the external ( just in case even if you do not use it normally). You can choose in BIOS which drive boots first to control which grub boots as default.

Is this grub legacy or grub2?

Grub legacy:
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition_")

Grub2:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition")

---

