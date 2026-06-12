---
title: "Please help! (Error: no such partition)"
date: 2009-12-12
forum: General Help
---

### Post by super noob on 2009-12-12
So I just uninstalled ubuntu on my hp tx2, I decided I was going to do a clean install and run ubuntu inside of windows instead of having 2 seperate partitions. I after I uninstalled ubuntu I deleted the empty partition. I just turned on my computer again and it says-

grub loading.
Error: no such partition
grub rescue>

what the heck is going on! Somone please help me get back into windows

---

### Post by justin_guerin on 2009-12-12
The problem is that part of grub (your boot loader) lives in the master boot record, but part of it lives in the Ubuntu partition.  Since you deleted the Ubuntu partition, grub can't find the rest of the files it needs to boot.

To properly back out of this situation, boot from the live CD.  If you have an option to boot into installed OS, try that.  If you get into Windows, then use a Windows utility to restore the master boot record.  "fdisk /mbr" used to be the command to do this, but I don't think that works in newer versions of Windows.

If the live CD doesn't boot you into Windows, you could edit the boot options on the live CD to execute a chainloader and boot into Windows.

If you're not sure how to do that, then just go ahead and install Ubuntu again.  When it finishes installing, it should allow you to boot into your Windows system.  Do that, and then fix the master boot record as above.

Once you have fixed the master boot record, you should boot directly to Windows.  Only then will it be safe to completely remove the Linux partition.

Hope that helps,
Justin

---

### Post by super noob on 2009-12-12
Thanks,  worked perfectly.

---

