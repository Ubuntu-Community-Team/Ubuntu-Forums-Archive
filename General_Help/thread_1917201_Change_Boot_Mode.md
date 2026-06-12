---
title: "Change Boot Mode"
date: 2012-01-29
forum: General Help
---

### Post by Tk007LwZFJW5ej on 2012-01-29
I´m using boot repair, and it gave me the message:

```

The boot of your PC is in EFI mode. Please change it to BIOS mode. Do you want to continue?

```
How do I change from efi to BIOS mode?

---

### Post by oldfred on 2012-01-29
I am not sure you should change it.

From boot repair post the link to boot_info script and use the git/beta version as it has been updated to also parse efi partitions.

New systems seem to be UEFI/BIOS but if you have an efi partition then that is how you boot.

---

### Post by Tk007LwZFJW5ej on 2012-01-29
Not sure where to get the correct version. Is it the first three files here?

[https://launchpad.net/boot-repair/+download](https://launchpad.net/boot-repair/+download)

---

### Post by Tk007LwZFJW5ej on 2012-01-29
I was able to get the system to boot correctly by adding 

```

nomodeset

```

at boottime, so it looks like this is a graphics problem rather than a boot problem.

---

