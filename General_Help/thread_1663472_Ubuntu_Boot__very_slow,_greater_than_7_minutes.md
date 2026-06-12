---
title: "Ubuntu Boot  very slow, greater than 7 minutes"
date: 2011-01-09
forum: General Help
---

### Post by TrevorCampbell on 2011-01-09
My Ubuntu 10.10 is now very slow to boot.  I have run bootchart and there is a 'find' process running for many minutes, but I have no idea how to work out where or why this is being run.

All help would be really appreciated.

---

### Post by oldfred on 2011-01-09
I do not know how to read boot chart.

But some users have had issues with cd's left in the cd player and the system trying to run filecheck on the cd. Some have had issues where BIOS was configured for a floppy but one does not exist, so it goes searching for floppy (or other device).

So check BIOS for settings.

I also saved comments from others with strange issues:
Some issues on booting install:
BIOS settings need USB mouse & keyboard
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility 
BIOS should be set for IDE compatibility mode
So then I tried disabling "IDE DMA Transfer Access" which had no explanation in the BIOS as to what it did. Restarted the computer and Ubuntu booted up no problem. According to the motherboard manual "This item is used to enable or disable the DMA transfer function of the IDE hard drive."
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
BIOS setting, Keyboard response in grub really slow

---

### Post by hawkmage on 2011-01-09
Do you have a mount of a remote filesystem in your /etc/fstab?  Unavailable or slow responding mounts can cause delayed boot times.

---

### Post by cascade9 on 2011-01-09
> **oldfred said:**
> I also saved comments from others with strange issues:

Change SATA controller mode from AHCI to Compatibility 
BIOS should be set for IDE compatibility mode
So then I tried disabling "IDE DMA Transfer Access" which had no explanation in the BIOS as to what it did. Restarted the computer and Ubuntu booted up no problem. According to the motherboard manual "This item is used to enable or disable the DMA transfer function of the IDE hard drive."


SATA mode should stay in AHCI  unless you are getting nasty issues (which shouldnt happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI withotu loadign the drivers..and you need a floppy drive to laod the drivers, which most newer computers dont have (and lots of people are lazy anyway).

'IDE DMA tansfer' is the newer system to access IDE discs. By 'newer' I mean 'anything newer than 1997/1998 or so'. Disabling this setting forces the IDE drive to use 'PIO' mode, which is super slow. 

Running PIO mode for a DMA HDD is a major performance hit. Running SATA HDDs in 'compatibility' (or 'IDE') mode is less of a hit, but still a hit. 

Maybe I should get of my butt and make a 'how to love you BIOS' blog post, or even a post here.

---

### Post by TrevorCampbell on 2011-01-09
> **hawkmage said:**
> Do you have a mount of a remote filesystem in  your /etc/fstab?  Unavailable or slow responding mounts can cause  delayed boot times.

No nothing like that at all:
~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6564407e-3317-4bb4-b253-c7d8f7e43457 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=53eaa6ad-94ea-4177-b1be-1d39ad147fdb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Synapsi on 2011-01-09
Your doomed.  just kidding :KS

---

