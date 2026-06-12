---
title: "grub-pc (1.98-1ubuntu6) from 10.04 locks GX1 when configuring serial then gfxterm"
date: 2010-06-25
forum: General Help
---

### Post by joephi on 2010-06-25
Before filing a bug report, I'd like to ask if anyone else may have seen this behavior, know how to find it in launchpad/these forums better than I could, or has any suggestions.

I'm working on a Dell OptiPlex GX1 350MHz with A10 BIOS, 4M video RAM, 384M main RAM, 20G PATA disk (I could give more details if you need them).  This was installed via the alternate CD, first as MBR partitions, and later manually converted using GNU parted to GPT (single user mode, one terminal with fdisk listing, the other with parted to reenter sector numbers).  Using aptitude, all the installed packages are up-to-date ("u", "U", "g", "g" keystrokes).

I started experimenting with the gfxterm module.  I added a shell script at 08_serial_setup which puts code in to load the serial module, initialize the 0 port, and use ```
terminal_(in|out)put console serial
``` After this was working fine, I hit "c", and started experimenting with ```
set gfxmode=1024x768x16
insmod gfxterm
insmod vbe
terminal_output gfxterm
```Unfortunately, on hitting that last instruction, the screen cleared to all black, and the (PS/2) keyboard was non-responsive; not even Ctrl-Alt-Del would reboot.  I had to reach over and hard-reset the computer.

After several experiments, all ending in freezing, I renamed grub.cfg to not-grub.cfg so that NO configuration (other than grub-mkimage/grub-setup may have done, like set prefix=(hd0,2)/grub and such) would have effect.  I boiled it down to this: one can insmod the serial module, and that's no problem.  I can set a gfxmode, insmod the other two modules, and all is OK.  **But** if I do```
serial --unit=0 --speed=57600
```and **then** try to set up the gfxterm, it will consistently lock the system, requiring either the reset button or powercycle (doesn't really matter which; both will work fine).  It doesn't seem to matter what resolution strings I try (the system is capable up to 1280x1024x16).

FWIW, I noticed the serial driver module sometimes can't keep up.  I have a "null modem" cable between it and another Linux computer, and if I copy/paste more than about 20 characers of text into an XTerm (happens to use ckermit to talk to the serial port), at 57600bps characters will be dropped (hmmm...15 octet serial chip FIFO capacity?  maybe).

I just thought, here is some more disk detail:```

ttyS0 20:11:17 root@rootin2:~ 127# parted /dev/sda
GNU Parted 2.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p                                                                
Model: ATA Maxtor 2B020H1 (scsi)
Disk /dev/sda: 20.5GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name           Flags
 1      32.3kB  8225kB  8193kB                  GPTbootPart    bios_grub
 2      8225kB  510MB   502MB   ext3            LinuxBootPart  boot
 3      510MB   2007MB  1497MB  ext4            rootpart
 4      2007MB  2772MB  765MB   linux-swap(v1)  swappart
 5      2772MB  3035MB  263MB   ext4            varlogpart
 6      3035MB  20.5GB  17.5GB                  logicalvols    lvm

(parted) q                                                                
ttyS0 20:12:07 root@rootin2:~ 0# 
```
(You might be thinking, why use such a wimpy machine?  It's going to be a broadband home router :-) )

---

