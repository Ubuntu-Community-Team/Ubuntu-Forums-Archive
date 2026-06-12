---
title: "Unable to boot off Plextor PX-740A Loading Hard. Drivers"
date: 2006-03-15
forum: General Help
---

### Post by steve31783 on 2006-03-15
I am unable to boot when my Plextor PX-740A drive is plugged in. I currently have it set as slave, with an HP DVD/CD-RW combo as Master. With just the HP drive plugged in, the PC boots fine. I have tried booting with the Plextor as a single master, and got the same issue. I started with Kubuntu 5.10 Breezy installed, have tried upgrading to Dapper (kernel 2.6.15.18 386) and continue to get the same issue. I am now running a clean install of Breezy again.  The plextor drive runs off a Phillips chipset that had a known issue with Ubuntu, but the problem was "resolved" in bugzilla. I have updated the firmware on the drive to 1.02 ([http://www.plextor.com/ENGLISH/support/support_downloads.html#firm](http://www.plextor.com/ENGLISH/support/support_downloads.html#firm))

I have taken advice from the following websites/bugzilla/posts:

[http://kudos.berlios.de/kf/kisimlar/fixes.html#probnodma](http://kudos.berlios.de/kf/kisimlar/fixes.html#probnodma)
[http://www.ubuntuforums.org/archive/index.php/t-82017.html](http://www.ubuntuforums.org/archive/index.php/t-82017.html)
[http://www.ubuntuforums.org/showthread.php?t=72056&page=2](http://www.ubuntuforums.org/showthread.php?t=72056&page=2)

With the HP as master, it is obviously hda, so I'm assuming with the Plextor as slave, it will become hdb.

Here is my current hdparm.conf:

## This is the default configuration for hdparm for Debian.  It is a 
## rather simple script, so please follow the following guidelines :)
## Any line that begins with a comment is ignored - add as many as you 
## like.  Note that an in-line comment is not supported.  If a line 
## consists of whitespace only (tabs, spaces, carriage return), it will be
## ignored, so you can space control fields as you like.  ANYTHING ELSE
## IS PARSED!!  This means that lines with stray characters or lines that 
## use non # comment characters will be interpreted by the initscript.  
## This has probably minor, but potentially serious, side effects for your 
## hard drives, so please follow the guidelines.  Patches to improve 
## flexibilty welcome.  Please read /usr/share/doc/hdparm/README.Debian for 
## notes about known issues, especially if you have an MD array.
##
## Note that if the init script causes boot problems, you can pass 'nohdparm' 
## on the kernel command line, and the script will not be run.

# -q be quiet
quiet 
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
#apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
#dma = off
# -D enable/disable the on-drive defect management
#defect_mana = off
# -E cdrom speed
#cd_speed = 16
# -k disable/enable the "keep_settings_over_reset" flag for this drive
#keep_settings_over_reset = off
# -K disable/enable the drive's "keep_features_over_reset" flag
#keep_features_over_reset = on
# -m sector count for multiple sector I/O
#mult_sect_io = 32
# -P maximum sector count for the drive's internal prefetch mechanism
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode

## New note - you can use straight hdparm commands in this config file 
## as well - the set up is ugly, but it keeps backwards compatibility
## Additionally, it should be noted that any blocks that begin with 
## the keyword 'command_line' are not run until after the root filesystem
## is mounted.  This is done to avoid running blocks twice.  If you need 
## to run hdparm to set parameters for your root disk, please use the 
## standard format.

#Samples follow:
#First three are good for devfs systems, fourth one for systems that do 
#not use devfs.  The fifth example uses straight hdparm command line
#syntax.  Any of the blocks that use command line syntax must begin with
#the keyword 'command_line', and no attempt is made to validate syntax.  
#It is provided for those more comfortable with hdparm syntax. 

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

#/dev/cdroms/cdrom1 {
#       dma = on
#       interrupt_unmask = on
#       io32_support = 0
#}

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}

# Addition by kudos unofficial kubuntu faq
command_line {
	hdparm -c3 -d1 -m16 /dev/hdb
}



Could someone please post a copy of their hdparm.conf from a clean dapper install?

Also, please offer any suggestions to help fix this problem. I just converted to kubuntu yesterday from Mepis Linux. So far I really like Kubuntu, but need my DVD burner to work. This setup has worked fine in all other distros I have tried.

---

### Post by steve31783 on 2006-03-16
After plugging in both cdroms and walking away from the pc overnight, it finally did boot, but neither cd rom is functioning.

Dmesg:

[4295750.488000] hdb: lost interrupt
[4295810.688000] ide-cd: cmd 0x3 timed out
[4295810.688000] hdb: lost interrupt
[4295870.891000] ide-cd: cmd 0x25 timed out
[4295870.891000] hdb: irq timeout: status=0x51 { DriveReady SeekComplete Error }
[4295870.891000] hdb: irq timeout: error=0x24 { AbortedCommand LastFailedSense=0x02 }
[4295870.891000] ide: failed opcode was: unknown
[4295930.892000] ide-cd: cmd 0x3 timed out
[4295930.892000] hdb: lost interrupt
[4295930.892000] ATAPI device hdb:
[4295930.892000]   Error: Not ready -- (Sense key=0x02)
[4295930.892000]   (vendor-specific error) -- (asc=0xff, ascq=0xff)
[4295930.892000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295930.892000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295990.894000] ide-cd: cmd 0x3 timed out
[4295990.894000] hdb: lost interrupt
[4296050.894000] ide-cd: cmd 0x3 timed out
[4296050.894000] hdb: lost interrupt
[4296110.894000] ide-cd: cmd 0x1e timed out
[4296110.894000] hdb: lost interrupt
[4296445.439000] APIC error on CPU0: 00(40)

---

### Post by steve31783 on 2006-03-17
After a little bit of research, trial and error, I have solved the issue for anyone who cares...

Added:
"irqpoll" to the kernel line in grub menu.list

Added: 
/dev/hdb {
       mult_sect_io = 16
       write_cache = off
       dma = on
}

in hdparm.conf to turn DMA on for the plextor...

Both drives now mount and function fine.

---

