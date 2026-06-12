---
title: "Installing linux-virtual breaks networking"
date: 2009-07-28
forum: General Help
---

### Post by sangandongo on 2009-07-28
Hiiiii everybody!

I've been issued a Lenovo Z61m as my work laptop. I've since patched its BIOS so that I can take advantage of the virtualization improvements on the hardware. 

On it I've installed 9.04: As the Title of the thread suggests, whenever I install linux-virtual metapackage, my networking goes bye-bye. I attempted to create a custom kernel to handle the virtualization but to no avail. Furthermore, I tried installing the -server kernel for grins and it too broke my networking. 

The devices are completely missing from /dev and I don't see them in dmesg. Its like they're just not getting loaded. 

This machine has an Intel Wireless 3945A/B/G and a Broadcom NetXtreme Gigabit Ethernet, both of which work when using -generic. 

I look forward to getting help. I truly don't want to run Windows on this silly thing since I only need to use it for work occassionally. 

Thanks!

--
John

---

