---
title: "Does Ubuntu 10.04 boot from GPT?"
date: 2010-08-12
forum: General Help
---

### Post by TrieBr on 2010-08-12
I'm about to switch one of my hard drives from Master boot record to GUID partition table.
This may be an obvious/idiotic question but I would like to find out before installing and finding out that it wont boot.

Also, I'm not sure exactly the differences between the two, but I know GPT is better. Are there any other difficulties I may run into?

Thanks in advance :)

---

### Post by Ocxic on 2010-08-12
Doing that WILL DELETE ALL EXISTING PARTITIONS AND DATA!!!!! Make sure you backup first!!!

I think it will considering you can dual boot with Apple's OS X. on a MAC and OS X requires a GUID partition table(there's no getting around that).

---

### Post by TrieBr on 2010-08-12
> Doing that WILL DELETE ALL EXISTING PARTITIONS AND DATA!!!!! Make sure you backup first!!!
Yup, There is only 35GB on the drive which I've already backed up :)

> I think it will considering you can dual boot with Apple's OS X. on a  MAC and OS X requires a GUID partition table(there's no getting around  that).
Yea I'm going to attempt to triple boot Win7/OSX/Ubuntu and the GPT is required for OSX and I would like to install Ubuntu on the same drive as OSX.

Thanks, I'll post back here if I have any problems :)

---

### Post by jerenept on 2010-08-12
AFAIK, you can only boot with GPT (GUID) if you are using an EFI based system (most common, apple computers)

Yeah, though, it does work quite fine.

---

