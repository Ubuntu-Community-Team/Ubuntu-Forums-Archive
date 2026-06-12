---
title: "Is Grub2 automatically installed in all RAID drives using alternate CD?"
date: 2010-06-27
forum: General Help
---

### Post by jones.79 on 2010-06-27
Hello!

I am going to setup a new Ubuntu 10.04 using RAID 1 soon.

Installation will be via the alternate CD.

Older distributions required manually installing Grub to the second drive,
to boot if the first drive fails.

I found different statements about how this is handled since 9.10.

e.g.
> Install GRUB boot-loader on second drive (this step is not need if you use Ubuntu 9.10) or
> installing GRUB to second hard drive depending on your distribution
 
> grub-install /dev/md0
or
> grub-install /dev/sda
> grub-install /dev/sdb
So my question, is Grub2 automatically installed in all RAID drives using alternate CD 10.04
like executing sort of "grub-install /dev/md0" during the installation ??

Kind regards,
jones

---

### Post by dcstar on 2010-06-28
> **jones.79 said:**
> 
........
So my question, is Grub2 automatically installed in all RAID drives using alternate CD 10.04
like executing sort of "grub-install /dev/md0" during the installation ??

Kind regards,
jones

[LIST=1]
[*]Do not "quote" data, "quote" is for previous posts.
[*]Select the "Advanced" options at the end of the install questions and select what Grub install options are offered.
[/LIST]

---

### Post by jones.79 on 2010-06-28
Hi!


[LIST=1]
[*]Thanks for your answer.
[*] Sorry for the wrong quoting, thought it was for quotes from other websites, too.
[*] I found that the "Advanced"-button does not exist using the AlternateCD. Immediately after partitioning and configuring two disks as RAID1 Ubuntu is installed. But after copying all files that GRUB-config-part appears. Well, you can not configure much, but you are asked to install into the MBR of the first hdd. And when you select "Yes" one can see that ```
grub-install /dev/sda /dev/sdb
``` is executed. So, yes, grub is installed automatically into all RAID disks.
[/LIST]
Kind regards,
jones

---

