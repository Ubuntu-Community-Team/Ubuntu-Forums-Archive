---
title: "slow boot after adding new drive"
date: 2011-01-07
forum: General Help
---

### Post by smeggs on 2011-01-07
I've had Ubuntu for about 8 months now, and haven't really had any serious problems with it, or problems I couldn't find a solution for. This one is kind of weird and is really driving me crazy.

There were two Seagate Barracuda's in my computer, and I added a third a couple days ago. At first, I was getting a grub 22 error, because they were in the wrong sata socket order, but now they're all in the order they were before, save for the third which is in SATA port 3. 

After the GRUB2 display, I receive a blinking cursor on a black screen. I can type whatever I want into it and nothing happens, and if I wait a few minutes it will eventually show a graphical login screen, then displays an exception and then boots to the graphical plymouth screen. Here's a section from my kern.log that shows the bit the login screen displays as well as the rest of the errors. 

```

scsi 2:0:0:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
Jan  5 20:34:07 klendathu kernel: [   16.712112] sd 2:0:0:0: Attached scsi generic sg1 type 0
Jan  5 20:34:07 klendathu kernel: [   16.712118] sd 2:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Jan  5 20:34:07 klendathu kernel: [   16.712202] scsi 3:0:0:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
Jan  5 20:34:07 klendathu kernel: [   16.712204] sd 2:0:0:0: [sda] Write Protect is off
Jan  5 20:34:07 klendathu kernel: [   16.712207] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan  5 20:34:07 klendathu kernel: [   16.712229] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan  5 20:34:07 klendathu kernel: [   16.712308] sd 3:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Jan  5 20:34:07 klendathu kernel: [   16.712312] sd 3:0:0:0: Attached scsi generic sg2 type 0
Jan  5 20:34:07 klendathu kernel: [   16.712359] sd 3:0:0:0: [sdb] Write Protect is off
Jan  5 20:34:07 klendathu kernel: [   16.712361] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Jan  5 20:34:07 klendathu kernel: [   16.712374]  sda:
Jan  5 20:34:07 klendathu kernel: [   16.712376] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan  5 20:34:07 klendathu kernel: [   16.712398] scsi 4:0:0:0: Direct-Access     ATA      ST31000340NS     SN06 PQ: 0 ANSI: 5
Jan  5 20:34:07 klendathu kernel: [   16.712482] sd 4:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Jan  5 20:34:07 klendathu kernel: [   16.712494] sd 4:0:0:0: Attached scsi generic sg3 type 0
Jan  5 20:34:07 klendathu kernel: [   16.712496]  sdb:
Jan  5 20:34:07 klendathu kernel: [   16.712521] sd 4:0:0:0: [sdc] Write Protect is off
Jan  5 20:34:07 klendathu kernel: [   16.712523] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Jan  5 20:34:07 klendathu kernel: [   16.712567] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan  5 20:34:07 klendathu kernel: [   16.712679]  sdc: sda1 sda2 < sdb1
Jan  5 20:34:07 klendathu kernel: [   16.741981] sd 3:0:0:0: [sdb] Attached SCSI disk
Jan  5 20:34:07 klendathu kernel: [   16.758618]  sda5 >
Jan  5 20:34:07 klendathu kernel: [   16.758875] sd 2:0:0:0: [sda] Attached SCSI disk
Jan  5 20:34:07 klendathu kernel: [   16.773736] ldm_parse_tocblock(): Cannot find TOCBLOCK, database may be corrupt.
Jan  5 20:34:07 klendathu kernel: [   16.773738] ldm_parse_tocblock(): Cannot find TOCBLOCK, database may be corrupt.
Jan  5 20:34:07 klendathu kernel: [   16.826689]  [LDM] sdc1
Jan  5 20:34:07 klendathu kernel: [   16.826938] sd 4:0:0:0: [sdc] Attached SCSI disk
Jan  5 20:34:07 klendathu kernel: [   23.980090] ata1: lost interrupt (Status 0x58)
Jan  5 20:34:07 klendathu kernel: [   23.980110] ata1: drained 2 bytes to clear DRQ.
Jan  5 20:34:07 klendathu kernel: [   23.980113] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jan  5 20:34:07 klendathu kernel: [   23.980116] sr 0:0:0:0: [sr0] CDB: Inquiry: 12 00 00 00 fe 00
Jan  5 20:34:07 klendathu kernel: [   23.980122] ata1.00: cmd a0/01:00:00:fe:00/00:00:00:00:00/a0 tag 0 dma 16640 in
Jan  5 20:34:07 klendathu kernel: [   23.980123]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jan  5 20:34:07 klendathu kernel: [   23.980125] ata1.00: status: { DRDY }
Jan  5 20:34:07 klendathu kernel: [   29.020082] ata1: link is slow to respond, please be patient (ready=0)
Jan  5 20:34:07 klendathu kernel: [   31.840096] ata1: soft resetting link
Jan  5 20:34:07 klendathu kernel: [   32.060550] ata1.00: configured for UDMA/66
Jan  5 20:34:07 klendathu kernel: [   32.060887] ata1: EH complete

```

Here's my /etc/default/grub:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap"


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_GFXMODE=1680x1050

```
I don't know what else to post, if anyone has any tips or questions about my set up let me know. Thanks in advance. :D

---

### Post by dcstar on 2011-01-07
> **smeggs said:**
> I've had Ubuntu for about 8 months now, and haven't really had any serious problems with it, or problems I couldn't find a solution for. This one is kind of weird and is really driving me crazy.

There were two Seagate Barracuda's in my computer, and I added a third a couple days ago. At first, I was getting a grub 22 error, because they were in the wrong sata socket order, but now they're all in the order they were before, save for the third which is in SATA port 3. 
.........
I don't know what else to post, if anyone has any tips or questions about my set up let me know. Thanks in advance. :D

Check your BIOS settings and specifically the Boot order of the drives.

If your system is trying to boot off non-system drives first then you will have to wait for it to time out before going to the next drive in the list.

---

### Post by smeggs on 2011-01-07
Thanks for the reply. I tried that and I didn't realize there were two settings in the BIOS for storage information. One was boot order (and it lists the serials of the drives, two of which are the same), and one was boot devices. I removed everything but my primary from the boot devices list and it worked.

---

