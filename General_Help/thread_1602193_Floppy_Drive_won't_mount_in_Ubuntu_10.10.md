---
title: "Floppy Drive won't mount in Ubuntu 10.10"
date: 2010-10-21
forum: General Help
---

### Post by iownall555 on 2010-10-21
My floppies won't show up or mount in Ubuntu 10.10. I also had this problem in Ubuntu 10.04 and none of the workarounds worked. I am running Ubuntu in a VMWare Virtual Machine. Could this be a reason why it doesn't work? Please post a way to fix it. I really need to use floppy disks.
EDIT: Forgot to mention it said that there was no media in the drive when i tried to access it.

---

### Post by dcstar on 2010-10-21
> **iownall555 said:**
> My floppies won't show up or mount in Ubuntu 10.10. I also had this problem in Ubuntu 10.04 and none of the workarounds worked. I am running Ubuntu in a VMWare Virtual Machine. Could this be a reason why it doesn't work? Please post a way to fix it. I really need to use floppy disks.
EDIT: Forgot to mention it said that there was no media in the drive when i tried to access it.

VM issues belong in the Virtualization forum.

---

### Post by iownall555 on 2010-10-21
Oh ok sorry. I am still wondering why it doesn't work. Any help would be appreciated.
EDIT: I am not sure if i should make a new thread and let this one die or ask a moderator to move it. Maybe i should make a new one.

---

### Post by plucky on 2010-10-21
> VM issues belong in the Virtualization forum. 

Is this a VM issue?

Floppies stopped working in 10.04 with the udisks upgrade and everyone had to downgrade udisks to get them to work.
The work around I found was to use a command in the terminal to mount the floppy.
```
udisks --mount /dev/fd0
```

I don't know if this will help in VMware,but there is no harm in trying.
You also have to have the line ```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
``` in /etc/fstab.

Good Luck

---

### Post by iownall555 on 2010-10-21
Mount failed: Error mounting: mount exited with exit code 1: helper failed with:
mount: you must specify the filesystem type
I got that error when i tried it. The line is also in /etc/fstab.
I might have to downgrade udisks if i can't get it to work.

---

### Post by ZeroFossilFuel on 2011-03-28
> **plucky said:**
> Is this a VM issue?

Floppies stopped working in 10.04 with the udisks upgrade and everyone had to downgrade udisks to get them to work.
The work around I found was to use a command in the terminal to mount the floppy.
```
udisks --mount /dev/fd0
```I don't know if this will help in VMware,but there is no harm in trying.
You also have to have the line ```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
``` in /etc/fstab.

Good LuckLook, I know floppies are passer but I just had a need to upgrade the BIOS on a Dell L400 that has been repurposed for my ham station. Bootable FDD was the only way.

I ended up booting to my windoze partition (which I HATE doing) to write the boot disk to upgrade the bios. That's before I found this neat little trick, which works for me BTW, so thank you. Maybe I'll get to use it again.

But I sure would like to see that basic functionality restored. :|

And yes, I did say L400 (PIII-700/256MB RAM). Maverick runs fine on it. In fact, better than fine. Awesome.

---

### Post by AllGamer on 2011-08-13
> **plucky said:**
> 
```
udisks --mount /dev/fd0
```


thank you very much!!

this worked

and same here, i'm stuck using a FDD drive to update the Firmware / BIOS of some RAID controllers that can only be done in DOS in a FDD

really wish hardware manufactures payed more attention to Linux and made utilities to flash BIOS from within linux.

most manufacture only focuses on Windows, and worse case is DOS only, that's soooo old school

not many PCs have floppy drives anymore.

some motherboards don't even come with the floppy port anymore

yet their bios can only be upgraded in DOS if you have no windows installed

booting DOS from a USB is quite a nuisance, not many USB + Motherboard combination works properly

---

### Post by summaries on 2012-03-17
I am running 10.04 LTS and updated / upgraded to 10.04.04 today.

My floppy drive stopped working after the upgrade.  
This thread has directions at the bottom
to FORCE the reinstallation of a previous version of udisks. 

That is the only way I was able to get it working again. :KS Thankyou

[URL="http://ubuntuforums.org/showthread.php?t=1772291&highlight=mount+floppy+stopped+working"]http://ubuntuforums.org/showthread.php?t=1772291&highlight=mount+floppy+stopped+working


[/URL]

---

