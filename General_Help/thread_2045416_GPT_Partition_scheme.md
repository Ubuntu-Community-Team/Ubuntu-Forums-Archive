---
title: "GPT Partition scheme"
date: 2012-08-21
forum: General Help
---

### Post by rickm1945 on 2012-08-21
Can Ubuntu or Mint be installed on a drive that is setup with GPT paritions. If not, what is, if possible, the easiest way to set the drive up as MBR?

---

### Post by drmrgd on 2012-08-21
I don't know about Mint (although I don't see why it wouldn't be the same), but Ubuntu can definitely be installed to a GPT formatted drive.

---

### Post by oldfred on 2012-08-22
If a BIOS system, then with gpt you need a bios_grub partition for grub2 to install correctly.

I have BIOS and converted one drive to gpt with 9.10. I also used gpt on a 16GB flash drive just to see if it works & it does again with bios_grub partition. 

For SSDs gpt is suggested, but if BIOS and you want to dual boot with Windows you have to use MBR unless you can boot with UEFI. Windows only boots from gpt partition drives with UEFI. Windows 7 will read gpt partitioned drives with  NTFS formated partitions from a MBR drive, but XP will not.

---

