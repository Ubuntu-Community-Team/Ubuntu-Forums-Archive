---
title: "Grub - problem - windows 7 and two ubuntu"
date: 2009-08-02
forum: General Help
---

### Post by fbu90 on 2009-08-02
Hello. 
I had installed Windows 7 and Ubuntu 9.04 on my laptop. 
I needed more space for the Windows partition and free space, I wanted to draw but could not lift the board and set up the free space partition linux ntfs partitions. 
after the operation started after the reboot, grub error batter 17. I tried to restore grub from a Live CD but without effect. 
I wanted to delete the NTFS partition, which previously made but not in gparted so sformatowa&#322;&#281;m council gave it to ext3, cause your computer to the same, no change. 
Suggested on another forum podpowiedziami applied to 


```
fsck-tpCy / dev/sda5 
```
Program after a few minutes, you need repaired, then when you try to restore grub odnajdywa&#322;o not hatalogu / bin / bash 
I did not know what to do now, nothing worked, so I decided to install ubuntu again (I wanted to put on yourself, (no data loss) but unfortunately the board was not so. 
Install Ubuntu next to (for free space) 

He added on an old ubuntu to the menu.lst but it wants to enter into your old Ubuntu pops up to error15 

I would like to use the old ubuntu, (spent on the configuration of nice niechcia&#322;bym a few weeks and that all the work went to waste) 

Here is the result of fdisk-l 

```
Disk / dev / sda: 120.0 GB, 120034123776 bytes 
255 heads, 63 sectors / track, 14593 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x2527a2c7 

    Device Boot Start End Blocks Id System 
/ dev/sda1 * 11072 14267 25671870 7 HPFS / NTFS 
/ dev/sda2 2 11071 88919775 5 Extended 
/ dev/sda3 14268 14593 2618595 b W95 FAT32 
/ dev/sda5 * 2 5952 47801344 + 83 Linux 
/ dev/sda6 5953 9441 28025361 83 Linux 
/ dev/sda7 10746 11071 2618563 + 82 Linux swap / Solaris 
/ dev/sda8 9442 10683 9976333 + 83 Linux 
/ dev/sda9 10684 10745 497983 + 82 Linux swap / Solaris 

Partition table entries are not in disk order 
```

And menu.lst 

```
# Menu.lst - See: grub (8), info grub, update-grub (8) 
# Grub-install (8), grub-floppy (8), 
# Grub-md5-crypt, / usr / share / doc / grub 
# And / usr / share / doc / grub-doc /. 

# # Default num 
# Set the default entry to the entry number NUM. Numbering starts from 0, and 
# The entry number 0 is the default if the command is not used. 
# 
# You can specify 'saved' instead of a number. In this case, the default entry 
# Is the entry saved with the command 'savedefault'. 
# WARNING: If you are using dmraid do not use 'savedefault' or your 
# Array will desync and will not let you boot your system. 
default 0 

# # Timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (Normally the first entry defined). 
timeout 10 

# # Hiddenmenu 
# Hides the menu by default (press ESC to see the menu) 
# hiddenmenu 

# Pretty colors 
# color cyan / blue white / blue 

# # Password [ '- md5'] passwd 
# If used in the first section of a menu file, disable all interactive editing 
# Control (menu entry editor and command-line) and entries protected by the 
# Command 'lock' 
# E.g. password topsecret 
# Password - md5 $ 1 $ gLhU0 / $ aW78kHK1QfV3P2b2znUoe / 
# Password topsecret 

# 
# Examples 
# 
# Title Windows 95/98/NT/2000 
# Root (hd0, 0) 
# Makeactive 
# Chainloader +1 
# 
# Title Linux 
# Root (hd0, 1) 
# Kernel / vmlinuz root = / dev/hda2 ro 
# 

# 
# Put static boot stanzas before and / or after Automagic KERNEL LIST 

# # # BEGIN Automagic Kernels LIST 
# # Lines between the kernels Automagic LIST markers will be modified 
# # By the debian update-grub script except for the default options below 

# # DO NOT uncomment THEM, Just edit them to your needs 

# # # # Start Default Options # # 
# # Default kernel options 
# # Default kernel options for Automagic boot options 
# # If you want special options for specific kernels use kopt_x_y_z 
X.y.z where # # is the kernel version. Minor versions can be omitted. 
# # E.g. kopt = root = / dev/hda1 ro 
# # Kopt_2_6_8 = root = / dev/hdc1 ro 
# # Kopt_2_6_8_2_686 = root = / ro dev/hdc2 
# Kopt = root = UUID = 822d5c90-3fcb-4f6a-92b8-edaad0e615b0 ro 

# # Default grub root device 
# # E.g. groot = (hd0, 0) 
# Groot = 822d5c90-3fcb-4f6a-92b8-edaad0e615b0 

# # Should update-grub create alternative Automagic boot options 
# # E.g. alternative = true 
# # Alternative = false 
# Alternative = true 

# # Should update-grub lock alternative boot options Automagic 
# # E.g. lockalternative = true 
# # Lockalternative = false 
# Lockalternative = false 

# # Additional options to use with the default boot option, but not with the 
# # Alternatives 
# # E.g. defoptions = vga = 791 resume = / dev/hda5 
# Defoptions = quiet splash 

# # Should update-grub lock old Automagic boot options 
# # E.g. lockold = false 
# # Lockold = true 
# Lockold = false 

# # Xen hypervisor options to use with the default Xen boot option 
# = Xenhopt 

# # Xen Linux kernel options to use with the default Xen boot option 
# Xenkopt = console = tty0 

# # Altoption boot targets option 
# # Multiple altoptions lines are allowed 
# # E.g. altoptions = (extra menu suffix) extra boot options 
# # Altoptions = (recovery) single 
# Altoptions = (recovery mode) single 

# # Controls how many kernels should be put into the menu.lst 
# # Only counts the first occurrence of a kernel, not the 
# # Alternative kernel options 
# # E.g. howmany = all 
# # Howmany = 7 
# Howmany = all 

# # Specify if Xen running in the house or have grub automatically detect 
# # Update-grub will ignore non-xen kernels when running in the house and vice versa 
# # E.g. indomU = detect 
# # IndomU = true 
# # IndomU = false 
IndomU detect = # 

# # Should update-grub create memtest86 boot option 
# # E.g. memtest86 = true 
# # Memtest86 = false 
# Memtest86 = true 

# # Should update-grub adjust the value of the default booted system 
# # Can be true or false 
# Updatedefaultentry = false 

# # Should update-grub add savedefault to the default options 
# # Can be true or false 
# Savedefault = false 

# # # # End Default Options # # 

title Ubuntu 9.04, kernel 2.6.28-11-generic 
uuid 822d5c90-3fcb-4f6a-92b8-edaad0e615b0 
kernel / boot/vmlinuz-2.6.28-11-generic root = UUID = 822d5c90-3fcb-4f6a-92b8-edaad0e615b0 ro quiet splash 
initrd / boot/initrd.img-2.6.28-11-generic 
quiet 

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) 
uuid 822d5c90-3fcb-4f6a-92b8-edaad0e615b0 
kernel / boot/vmlinuz-2.6.28-11-generic root = UUID = 822d5c90-3fcb-4f6a-92b8-ro single edaad0e615b0 
initrd / boot/initrd.img-2.6.28-11-generic 

title Ubuntu 9.04, memtest86 + 
uuid 822d5c90-3fcb-4f6a-92b8-edaad0e615b0 
kernel / boot/memtest86 +. bin 
quiet 

# # # END DEBIAN Automagic Kernels LIST 

# This is a divider, added to separate the menu items below from the Debian 
# Ones. 
title Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# On / dev/sda1 
title Windows Vista (loader) 
rootnoverify (hd0, 0) 
savedefault 
makeactive 
chainloader +1 


# This entry automatically added by the Debian installer for an existing 
# Linux installation on / dev/sda5. 
title Ubuntu 9.04 (9.04) (on / dev/sda5) 
root (hd0, 4) 
kernel / boot/vmlinuz-2.6.28-11-generic 
initrd / boot/initrd.img-2.6.28-11-generic 
savedefault 
boot 
```
Please help.

---

