---
title: "Cloning Boot partition and Grub, Media Server IBMA50"
date: 2010-06-23
forum: General Help
---

### Post by wannabegeek on 2010-06-23
Hi folks,

I have seen a lot of threads on how to backup a root partition assuming that the current
/sda will be the target for the files. 

I have an existing 20GB HD I use for my OS and want to upgrade to a newer faster 20GB HD I have sitting around.

I have an enclosure  for the drive and tried to rsync the root directory to the new hard drive. I keep all my documents and pertitent files on other parititions, so I only excluded  /proc and  /lost+found. I unmounted the other partitions to avoid accidentitly modifying them.

I think it worked, but of course I need to copy my Grub to the new boot partition.
I don't know how to confirm the location of my external-drive/new-boot-partition 
in Grub syntax.

thanks for any clarification you can offer,
wbg

---

### Post by dcstar on 2010-06-24
> **wannabegeek said:**
> Hi folks,

I have seen a lot of threads on how to backup a root partition assuming that the current
/sda will be the target for the files. 

I have an existing 20GB HD I use for my OS and want to upgrade to a newer faster 20GB HD I have sitting around.

I have an enclosure  for the drive and tried to rsync the root directory to the new hard drive. I keep all my documents and pertitent files on other parititions, so I only excluded  /proc and  /lost+found. I unmounted the other partitions to avoid accidentitly modifying them.

I think it worked, but of course I need to copy my Grub to the new boot partition.
I don't know how to confirm the location of my external-drive/new-boot-partition 
in Grub syntax.

thanks for any clarification you can offer,
wbg

Boot off a Live CD, do not mount the drives, then:

```
dd if=dev/old-drive-whatever of=/dev/new-drive
```

---

### Post by wannabegeek on 2010-06-24
hi dcstar

I'll try that...I suppose I shouldn't have to do anything with grub if I just copy the entire drive eh?

I have not seen this use of dd beofre. I used it once to make an ISO out of a cdrom...

will try tonight
wbg

---

