---
title: "MTRR allocation failed"
date: 2010-12-31
forum: General Help
---

### Post by waltersch on 2010-12-31
After every boot, there are the following three lines in /var/log/messages:

Dec 31 13:25:46 cardo2 kernel: [   14.760994] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
Dec 31 13:25:46 cardo2 kernel: [   14.760997] [drm] MTRR allocation failed.  Graphics performance may suffer.
Dec 31 13:25:46 cardo2 kernel: [   14.762929] [drm] set up 31M of stolen space

I have 4 GB RAM, and the result of   cat /proc/mtrr  is:
reg00: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg01: base=0x0dde00000 ( 3550MB), size=    2MB, count=1: uncachable
reg02: base=0x0de000000 ( 3552MB), size=   32MB, count=1: uncachable
reg03: base=0x0e0000000 ( 3584MB), size=  512MB, count=1: uncachable
reg04: base=0x100000000 ( 4096MB), size=  512MB, count=1: write-back

I've read nearly all threads about "MTRR allocation failed" and have tried a lot (see below). For other people, who had the same MTRR allocation message, one of the measures I describe below, was the solution. But not for me. I have found no thread which proposed an additional solution.

I am using Ubuntu 10.04.1 with the latest updates. Kernel 2.6.32-27-generic-pae

First try:
I have added "enable_mtrr_cleanup mtrr_spare_reg_nr=1" to /etc/default/grub in variable GRUB_CMDLINE_LINUX.
Then update-grub and reboot.
Had no effect.

Second try:
I have added "nopat" to /etc/default/grub in variable GRUB_CMDLINE_LINUX.
Then update-grub and reboot.
Had no effect. Combined it with the parameters of the 1st try, but also had no effect.

Third try:
With a script (see below) that is executed during boot as early as possible, the automatically (wrong) set contents of mtrr are disabled and overwritten by new settings.
The script is put in /etc/init.d and referenced (ln -s) by S02fix_mtrr in /etc/rcS.d/
During testing, I had many situations when my system was not bootable or extremely slow. This script is EXTREMELY DANGEROUS!!
But now it works in the way, that the result of   cat /proc/mtrr  is now:
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size=  512MB, count=1: write-back
reg03: base=0x0e0000000 ( 3584MB), size=  256MB, count=1: write-combining
reg04: base=0x100000000 ( 4096MB), size=  512MB, count=1: write-back
reg05: base=0x0dde00000 ( 3550MB), size=    2MB, count=1: uncachable
reg06: base=0x0de000000 ( 3552MB), size=   32MB, count=1: uncachable

So, after the third try (which is no solution, but a very ugly work-around), I think I have no more graphics performance problem. But the three lines in /var/log/messages still come on every boot. The error still appears and I don't know why.

This is the script, that is VERY DANGEROUS and CAN MAKE YOUR SYSTEM UNUSABLE!
Be sure to adapt it to the conditions of your system.
Be sure that you have an additional possibility to delete it from /etc/init.d/ rsp. /etc/rcS.d/ if your system won't boot anymore.

# ------------------------

#!/bin/sh
# Fix wrong MTRR setting

# This program as it is only works for 4GB RAM and 32Bit Linux and
# 256 MB write-combining space starting at 0x0e0000000.
# Must be adapted to other conditions.
# VERY DANGEROUS to run it without matching the conditions. 

# remember old contents, only during testing.
echo "---  before  -----------" >>/root/mtrr.txt
cat /proc/mtrr >>/root/mtrr.txt

# Disabling seems to be valid only when done in a certain sequence
# that is not linear. To meet all possibilities, disabling of all
# registers is done in a linear sequence, but multiple times.
echo -n "Fixing MTRR ... "
for X in $(cat /proc/mtrr | cut -c 5 | sort -rn)
do
echo "disable=$X" >| /proc/mtrr
done
for X in $(cat /proc/mtrr | cut -c 5 | sort -rn)
do
echo "disable=$X" >| /proc/mtrr
done
for X in $(cat /proc/mtrr | cut -c 5 | sort -rn)
do
echo "disable=$X" >| /proc/mtrr
done
for X in $(cat /proc/mtrr | cut -c 5 | sort -rn)
do
echo "disable=$X" >| /proc/mtrr
done

#Set Correct settings:
# Important: sizes must be powers of 2, otherwise the statement is rejected.

# Main memory 3.5 of 4 GB: Must be in multiple lines with size in powers of 2.
echo "base=0x000000000 size=0x080000000 type=write-back" >| /proc/mtrr
echo "base=0x080000000 size=0x040000000 type=write-back" >| /proc/mtrr
echo "base=0x0c0000000 size=0x020000000 type=write-back" >| /proc/mtrr
# write-combining space
echo "base=0x0e0000000 size=0x010000000 type=write-combining" >| /proc/mtrr
# The rest of main memory (when Memory Remap Feature in BIOS-setup is active).
echo "base=0x100000000 size=0x020000000 type=write-back" >| /proc/mtrr
# Don't know for what that is. The same as shown by  cat /proc/mtrr
echo "base=0x0dde00000 size=0x000200000 type=uncachable" >| /proc/mtrr
echo "base=0x0de000000 size=0x002000000 type=uncachable" >| /proc/mtrr

# save new contents, only during testing.
echo "---  after  -----------" >>/root/mtrr.txt
cat /proc/mtrr >>/root/mtrr.txt

echo "Done"

# ------------------------

---

### Post by dcstar on 2010-12-31
> **waltersch said:**
> After every boot, there are the following three lines in /var/log/messages:

Dec 31 13:25:46 cardo2 kernel: [   14.760994] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
Dec 31 13:25:46 cardo2 kernel: [   14.760997] [drm] MTRR allocation failed.  Graphics performance may suffer.
Dec 31 13:25:46 cardo2 kernel: [   14.762929] [drm] set up 31M of stolen space

I have 4 GB RAM, and the result of   cat /proc/mtrr  is:
reg00: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg01: base=0x0dde00000 ( 3550MB), size=    2MB, count=1: uncachable
reg02: base=0x0de000000 ( 3552MB), size=   32MB, count=1: uncachable
reg03: base=0x0e0000000 ( 3584MB), size=  512MB, count=1: uncachable
reg04: base=0x100000000 ( 4096MB), size=  512MB, count=1: write-back

I've read nearly all threads about "MTRR allocation failed" and have tried a lot (see below). For other people, who had the same MTRR allocation message, one of the measures I describe below, was the solution. But not for me. I have found no thread which proposed an additional solution.

I am using Ubuntu 10.04.1 with the latest updates. Kernel **2.6.32-27-generic-pae**
........

You are using 32-bit with 4GB RAM, even with PAE it is still problematic that things will be able to use all available address space.

Check you BIOS settings that any advanced option is set to still be <4GB or try 64-bit Ubuntu.

---

### Post by waltersch on 2011-01-01
Can't see any options in my BIOS setup that relate to 4 GB - except "Memory Remap Feature", which I have tried with both possibilities Enabled and Disabled.

If I only had 2 GB RAM, there would be no conflict between main memory and the write-combining space.
If I have 32-bit-Linux installed and then enlarge my RAM to the amount of 4 GB, it should be possible to continue using this system without errors on every boot.

I don't understand the mechanisms for allocating main memory with respect to the needed write-combining space. But, suppose that during the process of allocating main memory, there is a reliable way to check which space must stay free for write-combining space. Then the allocation of main memory could act like the scipt above does (and has helped other users as I can see from other threads).
Allocation of main memory with the corresponding line in   cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
is obviously wrong. But that is what my kernel does.
Allocation of main memory with the corresponding lines in   cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size=  512MB, count=1: write-back
seems to be correct, if the start address for write-combining space is 0x0e0000000 ( 3584MB).

Regarding the fact that many 32-bit-linux users will enlarge their RAM in the coming time:
Is there a possibility to enable the 32-bit kernels to allocate mtrr in a less simple way, so that 4 GB RAM are treated correctly? If the use of 3 or 4 mtrr registers for main memory can cause problems in some cases, it could be a boot option to limit the number of registers for main memory (and have parts of memory unused). And if there is no reliable way to check the needed space for write-combining space, there could be an additional boot option for that.

I can't yet fully believe that the kernel developers did not enable such a possiblility ...

---

### Post by bartverm on 2011-01-06
I'm getting the same error on a 64bit system with 8Gb of memory

---

### Post by aktiwers on 2011-12-08
Me too

---

