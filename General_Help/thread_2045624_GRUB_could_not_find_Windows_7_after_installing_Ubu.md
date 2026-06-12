---
title: "GRUB could not find Windows 7 after installing Ubuntu - RAID 0"
date: 2012-08-21
forum: General Help
---

### Post by iihavetoes26 on 2012-08-21
I just purchased a new computer with two 256 GB SSDs configured in RAID 0.  It came pre-installed with Windows 7, but I wanted at least one Linux distribution installed as well.  So, I tried installing Ubuntu through the LiveCD.

In the LiveCD, I first created a few partitions for Ubuntu.  The first was a 12GB swap and the next, about 88GB formatted ext4 (gparted wouldn't let me create an extended partition, so both of there were primary partitions).  The extra space came from shrinking the Windows 7 partition.

While installing Ubuntu, I selected the master RAID controller for the boot loader.  After the installer was finished, everything booted fine, but GRUB didn't have an entry for the Windows 7 loader (even though it had one for the Windows 7 Recovery loader).

To fix this, I tried manually editing the /boot/grub/grub.cfg file by adding these lines to the 30_os-prober section:

```
    menuentry "Windows 7 (loader) (on /dev/mapper/isw_bhcibcaafd_Volume0p5)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(hd2,msdos3)'
        search --no-floppy --fs-uuid --set=root 6A92977992974889
        drivemap -s (hd0) ${root}
        chainloader +1
    }
```

After rebooting, GRUB didn't load and all I got was a blinking cursor in the top left of the screen.  So, I tried taking that section out (through the Ubuntu LiveCD) and after doing so, I still couldn't boot anything.  Could someone please help me out? Thanks!

Here is a copy of my BootInfo Summary: [http://paste.ubuntu.com/1159385/](http://paste.ubuntu.com/1159385/)

P.S. I have a copy of the grub.cfg if someone needs it for finding a solution

---

### Post by oldfred on 2012-08-21
I do not know RAID, but you seem to have gpt partitions inside your RAID. Windows only installs to gpt partitions with UEFI not BIOS.

You must install Ubuntu in UEFI mode also to have it work with Windows, but I do not know how the RAID changes things. How you boot the installer determines how it installs. You have to use the 64bit version, but the desktop version does not have the RAID drivers and I do not know enough about alternate version which has the RAID drivers to know if it has UEFI as an option.

Drives with gpt partitioning do not have extended partition nor any logicals. All partitions are primary.

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

I do not know if you can chain from BIOS boot in Ubuntu to efi in Windows, but these are chain to efi partition examples:

```
Chainload entry:
https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383
https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801
http://ubuntuforums.org/showthread.php?t=1934773
menuentry "Windows 7 UEFI" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='(hd0,gpt2)'
  search --fs-uuid --no-floppy --set=root 4f84-ee2e
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

http://www.insanelymac.com/forum/lofiversion/index.php/t186440
menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}
```

---

### Post by YannBuntu on 2012-08-23
Hello
I confirm that your Windows was pre-installed in EFI mode. So now you just need to **convert your Ubuntu into EFI mode.**
For this:
1) Boot your installed Ubuntu
2) Run Boot-Repair
3) click "advanced options"
4) go to the "GRUB location" tab
5) tick the "Separate /boot/efi partition: isw_bhcibcaafd_Volume0p3" option
6) click the "Apply" button
7) indicate us the new URL that will appear
8.) If you had disabled EFI in your BIOS, you need to re-activate it.
9) reboot and tell us what you observe.

---

