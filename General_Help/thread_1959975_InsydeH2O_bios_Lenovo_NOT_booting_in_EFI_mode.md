---
title: "InsydeH2O bios Lenovo NOT booting in EFI mode"
date: 2012-04-16
forum: General Help
---

### Post by Yahoé on 2012-04-16
Hi,

So I have a brand new Lenovo G770 with a InsydeH2O bios V3.08 which is UEFI.
When booting from the latest 12.04 daily live (USB), Gparted doesn't offer me to format the ESP as a EFI start partition (fat32 with the boot flag), which would mean that I'm not booting into EFI mode. This kind of Bios doesn't offer any option even mentioning UEFI.

Does anyone have any experience with these InsydeH2O bioses.

Regards

---

### Post by Yahoé on 2012-04-17
Installation completed on the  the Lenovo G770 with InsydeH2O Bios. It was successful.
Here are the steps I followed:
The drive partition table is GPT. I created a fat32 partition in first  position and set the flag to boot (partition type is EFI, checked with  gdisk type ef00). Then an ext4 / , an ext4 /home and a swap. 
The installer warned me that with this partition table format in use I  should normally have a separate partition for the boot loader code, also  it nay still be possible to install the boot loader to a partition. I  ignored that,  did not create one and went one the installation process.
It completed nicely.  I then installed grub-efi-amd64 and all is working  perfectly on this laptop, the system now works just fine.

---

