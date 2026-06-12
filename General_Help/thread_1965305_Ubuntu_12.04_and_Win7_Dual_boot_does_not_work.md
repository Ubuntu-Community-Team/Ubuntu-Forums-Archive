---
title: "Ubuntu 12.04 and Win7 Dual boot does not work"
date: 2012-04-25
forum: General Help
---

### Post by armq on 2012-04-25
Hey all,

I recently installed Ubuntu 12.04 alongside Windows 7, and first dual boot was working fine, but for last 2 weeks I have
"error: out of partition" for trying Ubuntu
and
"A Disk read error occurred"

I can access ubuntu through Rescue partition -> "resume" and it's boots Ubuntu, but I need to do it every time. And I cant access windows7, is there any way to deal with this problem?

Thanks,
Aram

---

### Post by techsupport on 2012-04-25
> **armq said:**
> Hey all,

I recently installed Ubuntu 12.04 alongside Windows 7, and first dual boot was working fine, but for last 2 weeks I have
"error: out of partition" for trying Ubuntu
and
"A Disk read error occurred"

I can access ubuntu through Rescue partition -> "resume" and it's boots Ubuntu, but I need to do it every time. And I cant access windows7, is there any way to deal with this problem?

Thanks,
Aram

Sounds like you might be out of disk space. Have you created a live bootable usb of Ubuntu to boot from to check the condition of your hard drive?

---

### Post by oldfred on 2012-04-25
Post the bootinfoscript results link that this creates. You may be able to reinstall grub2's boot loader also which may fix it, but it may be a partition issue.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

You can download Boot Repair into the Ubuntu liveCD/USB or it has liveCD that you can download.

---

### Post by kc1di on 2012-04-25
try boot repair 
you can get it here 
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

Oldfred beat me too it :)

---

