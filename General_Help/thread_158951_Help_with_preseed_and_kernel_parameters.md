---
title: "Help with preseed and kernel parameters"
date: 2006-04-12
forum: General Help
---

### Post by Brendon Rogers on 2006-04-12
I am working on an unattended deployment of 5.10 Server. At this stage I have the computer booting correctly off PXE and accessing the menu screens provided by netboot. 

In my default file I pass the kernel the following parameters **debian-installer/locale=en_UK kbd-chooser/method=uk** (amongst others). These parameters definitely work because with them I am not prompted to select language and keyboard at the beginning part of the install.

In my preseed file I have **base-config config/choose_country_zone_single      boolean true**. The preseed file is correctly formatted  and does work because other options in the file are passed to the install. However, towards the end of the installation I am prompted to choose my timezone. How do I get around this?

Additionally, I am trying to make the preseed file automatically partition the entire disk and have the following in my preseed file:
[B]# Automatically partion disk
d-i	partman/confirm_write_new_label	boolean true
d-i	partman/choose_partition	select Finish partitioning and write changes to disk
d-i	partman/confirm	boolean true[/B]

I am still prompted to hit enter when the install gets to the disk partition screen; from there it does the rest automatically. How do I avoid any input at the disk screen?

Thanks in advance for any assistance.

---

