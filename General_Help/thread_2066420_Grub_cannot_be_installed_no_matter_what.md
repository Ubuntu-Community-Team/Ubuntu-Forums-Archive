---
title: "Grub cannot be installed no matter what"
date: 2012-10-04
forum: General Help
---

### Post by Roflcopterofl on 2012-10-04
I am currently trying to get my grub back. I have tried  everything from reinstalling, to boot-repair, and even super boot  manager. Nothing seems to work.
  I have created a log with boot-repair:
  paste.ubuntu.com/1259258
  Any ideas?
  Thanks!

---

### Post by piddewest on 2012-10-04
Well i am no expert...but the logfile contains a warning, maybe that is the error?

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted

---

### Post by Roflcopterofl on 2012-10-04
> **piddewest said:**
> Well i am no expert...but the logfile contains a warning, maybe that is the error?

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted
You may be onto something. The GPT was mentioned in the windows install disc. Is it possible to change the GPT to the right Partition table (MBR I believe)?

Edit: I know it is possible, but could it be done without losing data?

---

### Post by piddewest on 2012-10-05
Sorry. That i can not anwser....

---

### Post by oldfred on 2012-10-06
If you have gpt are you booting in UEFI mode? Then you do not want MBR.

You did have grub installed to MBR, but it looks like Boot-Repair fixed it and added it to the efi boot menu. 

Are you booting in UEFI mode not in BIOS mode. Boot files look like they are in efi partition. From UEFI/BIOS what boot choices do you have?

I do not see Boot-Repair offering to add the correct efi chainload entries. Was Windows in efi mode originally?

---

