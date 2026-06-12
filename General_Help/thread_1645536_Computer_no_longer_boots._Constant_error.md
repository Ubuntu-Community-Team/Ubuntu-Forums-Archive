---
title: "Computer no longer boots. Constant error"
date: 2010-12-14
forum: General Help
---

### Post by Vulpes_Fortis on 2010-12-14
I have tried to keep away from posting this seeing how many have had the same problem but this is getting to the point of me just selling my computer out of shear frustration. Ive got Windows XP and Ubuntu 10.04lts. For a while they all ran fine together till my Windows drive gave out and ever since I tried to remove the drive GRUB recovery has been popping up. I even tried to put the drive back in and the computer still wont boot anything. Ive got 4 different live boots and neither one works, Ive tried to boot with my internal dvd drive and a usb one, there is always a Grub error. When I put in the ls command and find my only non"unknown filesystem" it still says "bad filename". I guess where im getting at is grub wont even let me reformat my computer or boot from anything without saying "no such device: 32d98-e0b3-451b-809b-ae6562ccb701"

My computer information:
AMD 64 2800
2gb ram
ati 9250 vid card
2gb ddr ram
hdd- 160gb maxtor (master drive, tried making slave and linux boot master but is what caused the problem. changed back and did nothing. bad drive and windows drive)
320gb wd blue (slave drive with linux)
1tb wd black (only sata drive).

Once again, it all ran well together till I tried to make my 160gb a slave and 320 master. I changed it back and it still says grub recovery. Ive got one live boot to ever work and when I reset my computer it said no such device again.

Sorry for posting this but its really getting frustrating and Ive tried everything I could find that has been suggested to people either on this forum or many others.

---

### Post by Quackers on 2010-12-14
It is likely that you can fix this, but the only way I know of is by booting a Live cd or Live usb. In order to do this your boot priority must be set to boot from cd/dvd or usb flash first. If you can't get a live cd/usb to boot you won't be able to fix it.

---

### Post by mr clark25 on 2010-12-14
it sounds like you need to change the boot order in your BIOS.

---

### Post by oldfred on 2010-12-15
Does your BIOS let you choose boot drive. Some have it as part of the device menu, where hard disk has  a submenu. Others have it as a totally different menu item. 

Older IDE BIOS do not select drive but rely on jumpers on hard drive for master/slave or jumper with cable select and the newer 80 wire cables. If it is an older BIOS (over about 5 years ago) it probalbly does not even have a BIOS boot. But my new system that had many USB boot options would not boot my flash drive. But then one day with flash plugged in, I was changing boot on hard drives and flash drive was listed. It was not a USB device but a hard drive.

---

