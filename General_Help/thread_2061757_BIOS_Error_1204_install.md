---
title: "BIOS Error 1204 install"
date: 2012-09-23
forum: General Help
---

### Post by ub45 on 2012-09-23
I've just installed ubuntu 1204 and everything went fine but once I downloaded the updates and restarted the computer all I got was a black screen and later on I find
out that the bios is corrupted or missing. Does anybody know how to fix this.

---

### Post by oldfred on 2012-09-23
Very much doubt that it is a BIOS error. Do you get a BIOS screen when you turn power on?

It may be some update did not complete correctly. And then it can be a boot issue, a video issue or some driver preventing booting. If you hold shift key from BIOS do you get a grub menu?

Lets start with boot issues. From BIOS change to boot CD (or USB) that you used to install or liveCD. Assumes you did not use alternative installer as it is not a liveCD.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

