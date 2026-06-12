---
title: "Sometimes can't wake from suspend, in Ubuntu 11.10"
date: 2011-12-05
forum: General Help
---

### Post by pretty_whistle on 2011-12-05
[SIZE=3]The title says it.

I have it set to suspend when I close the lid.   This is when it happens.

It doesn't do it every time.

Sometimes I can login despite it (I can click-through it), as if the logon screen is there and is only out of view!  Weird......

Other times if I can't login I have to shut down the power and start it back up or I can't reach the desktop.

Is there any way to fix this?

Thanks ahead of time for any help provided.


[/SIZE]

---

### Post by 2F4U on 2011-12-05
Is there any pattern behind the failures (or successes)? Suspend and resume actions are recorded in log files located in /var/log:
- pm-powersave.log
- pm-suspend.log

So, when it fails, look into the log files and maybe publish them here so that we can look at them. In addition, you should provide detailed information about your hardware.

---

### Post by Diametric on 2011-12-05
This may not be helpful, but this happens to me all the time with my 10.04 install on my laptop.  I recall seeing several discussions on this forum regarding the issue - it might be worth searching the site to get some info from those discussion.

---

### Post by pretty_whistle on 2011-12-05
> **2F4U said:**
> Is there any pattern behind the failures (or successes)? Suspend and resume actions are recorded in log files located in /var/log:
- pm-powersave.log
- pm-suspend.log

So, when it fails, look into the log files and maybe publish them here so that we can look at them. In addition, you should provide detailed information about your hardware.
[SIZE=3]Here are the 2 logs (1st is the powersave.log):[/SIZE]
```

Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host2 to max_performance...Done.
Setting SATA APLM on host3 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host2 to max_performance...Done.
Setting SATA APLM on host3 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host0 to max_performance...Done.
Setting SATA APLM on host1 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host0 to max_performance...Done.
Setting SATA APLM on host1 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host0 to max_performance...Done.
Setting SATA APLM on host1 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host0 to max_performance...Done.
Setting SATA APLM on host1 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.
Setting journal commit time for /media/Dubbins to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.
Setting readahead for /dev/sda3 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host0 to max_performance...Done.
Setting SATA APLM on host1 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:
start: Job is already running: anacron

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.
Setting journal commit time for /media/Dubbins to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.
Setting readahead for /dev/sda3 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host0 to max_performance...Done.
Setting SATA APLM on host1 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host2 to max_performance...Done.
Setting SATA APLM on host3 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host2 to max_performance...Done.
Setting SATA APLM on host3 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm true:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/usr/lib/pm-utils/power.d/95hdparm-apm true: success.
Running hook /usr/lib/pm-utils/power.d/anacron true:
stop: Unknown instance: 

/usr/lib/pm-utils/power.d/anacron true: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol true:

/usr/lib/pm-utils/power.d/disable_wol true: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling true:

/usr/lib/pm-utils/power.d/hal-cd-polling true: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave true:
Setting power savings for snd_hda_intel to 1...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave true: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit true:
Setting journal commit time for / to 600...Done.
Setting journal commit time for /media/Dubbins to 600...Done.

/usr/lib/pm-utils/power.d/journal-commit true: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode true:
Laptop mode enabled.

/usr/lib/pm-utils/power.d/laptop-mode true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:

/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/readahead true:
Setting readahead for /dev/sda1 to 3072...Done.
Setting readahead for /dev/sda3 to 3072...Done.

/usr/lib/pm-utils/power.d/readahead true: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm true:

/usr/lib/pm-utils/power.d/sata_alpm true: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave true:
**sched policy powersave ON

/usr/lib/pm-utils/power.d/sched-powersave true: success.
Running hook /usr/lib/pm-utils/power.d/wireless true:
Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless true: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer true:

/usr/lib/pm-utils/power.d/xfs_buffer true: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.
Setting journal commit time for /media/Dubbins to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.
Setting readahead for /dev/sda3 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host2 to max_performance...Done.
Setting SATA APLM on host3 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm true:

/usr/lib/pm-utils/power.d/95hdparm-apm true: success.
Running hook /usr/lib/pm-utils/power.d/anacron true:
stop: Unknown instance: 

/usr/lib/pm-utils/power.d/anacron true: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol true:

/usr/lib/pm-utils/power.d/disable_wol true: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling true:

/usr/lib/pm-utils/power.d/hal-cd-polling true: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave true:
Setting power savings for snd_hda_intel to 1...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave true: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit true:
Setting journal commit time for / to 600...Done.

/usr/lib/pm-utils/power.d/journal-commit true: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode true:
Laptop mode enabled.

/usr/lib/pm-utils/power.d/laptop-mode true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:

/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/readahead true:
Setting readahead for /dev/sda1 to 3072...Done.

/usr/lib/pm-utils/power.d/readahead true: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm true:

/usr/lib/pm-utils/power.d/sata_alpm true: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave true:
**sched policy powersave ON

/usr/lib/pm-utils/power.d/sched-powersave true: success.
Running hook /usr/lib/pm-utils/power.d/wireless true:
Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless true: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer true:

/usr/lib/pm-utils/power.d/xfs_buffer true: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm true:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/usr/lib/pm-utils/power.d/95hdparm-apm true: success.
Running hook /usr/lib/pm-utils/power.d/anacron true:
stop: Unknown instance: 

/usr/lib/pm-utils/power.d/anacron true: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol true:

/usr/lib/pm-utils/power.d/disable_wol true: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling true:

/usr/lib/pm-utils/power.d/hal-cd-polling true: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave true:
Setting power savings for snd_hda_intel to 1...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave true: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit true:
Setting journal commit time for / to 600...Done.

/usr/lib/pm-utils/power.d/journal-commit true: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode true:
Laptop mode enabled.

/usr/lib/pm-utils/power.d/laptop-mode true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:

/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/readahead true:
Setting readahead for /dev/sda1 to 3072...Done.

/usr/lib/pm-utils/power.d/readahead true: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm true:

/usr/lib/pm-utils/power.d/sata_alpm true: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave true:
**sched policy powersave ON

/usr/lib/pm-utils/power.d/sched-powersave true: success.
Running hook /usr/lib/pm-utils/power.d/wireless true:
Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless true: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer true:

/usr/lib/pm-utils/power.d/xfs_buffer true: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host2 to max_performance...Done.
Setting SATA APLM on host3 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host2 to max_performance...Done.
Setting SATA APLM on host3 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:
start: Job is already running: anacron

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host2 to max_performance...Done.
Setting SATA APLM on host3 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.
Setting journal commit time for /media/Dubbins to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.
Setting readahead for /dev/sda3 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host2 to max_performance...Done.
Setting SATA APLM on host3 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:
start: Job is already running: anacron

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.
Setting journal commit time for /media/Dubbins to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.
Setting readahead for /dev/sda3 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host2 to max_performance...Done.
Setting SATA APLM on host3 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.
Setting journal commit time for /media/Dubbins to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.
Setting readahead for /dev/sda3 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host2 to max_performance...Done.
Setting SATA APLM on host3 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:
start: Job is already running: anacron

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.
Setting journal commit time for /media/Dubbins to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.
Setting readahead for /dev/sda3 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host2 to max_performance...Done.
Setting SATA APLM on host3 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.
Setting journal commit time for /media/Dubbins to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.
Setting readahead for /dev/sda3 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host2 to max_performance...Done.
Setting SATA APLM on host3 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.
Setting journal commit time for /media/Dubbins to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda1 to 256...Done.
Setting readahead for /dev/sda3 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA APLM on host2 to max_performance...Done.
Setting SATA APLM on host3 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.

--------------------------

Initial commandline parameters: 
Thu Dec  1 21:31:46 MST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux nutin 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 athlon i386 GNU/Linux
Module                  Size  Used by
usb_storage            44173  0 
uas                    17699  0 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
bnep                   17923  2 
snd_hda_codec_hdmi     31426  1 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
binfmt_misc            17292  1 
arc4                   12473  2 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_seq_midi           13132  0 
nvidia               7098131  36 
joydev                 17393  0 
snd_rawmidi            25241  1 snd_seq_midi
ath5k                 145100  0 
ath                    19387  1 ath5k
mac80211              393459  1 ath5k
psmouse                73673  0 
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              172392  3 ath5k,ath,mac80211
video                  18908  0 
k10temp                12990  0 
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
shpchp                 32356  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  1 hp_wmi
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
forcedeth              58103  0 
pata_amd               13753  0 
ahci                   21634  3 
libahci                25727  1 ahci
             total       used       free     shared    buffers     cached
Mem:       1802056     887304     914752          0      64656     393204
-/+ buffers/cache:     429444    1372612
Swap:      1831932          0    1831932

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Dec  1 21:31:55 MST 2011: performing suspend
Fri Dec  2 07:23:35 MST 2011: Awake.
Fri Dec  2 07:23:35 MST 2011: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Dec  2 07:23:35 MST 2011: Finished.
Initial commandline parameters: 
Fri Dec  2 18:23:44 MST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux nutin 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 athlon i386 GNU/Linux
Module                  Size  Used by
usb_storage            44173  0 
uas                    17699  0 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
binfmt_misc            17292  1 
arc4                   12473  2 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
nvidia               7098131  36 
joydev                 17393  0 
ath5k                 145100  0 
snd_seq_midi           13132  0 
ath                    19387  1 ath5k
snd_rawmidi            25241  1 snd_seq_midi
mac80211              393459  1 ath5k
psmouse                73673  0 
serio_raw              12990  0 
k10temp                12990  0 
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              172392  3 ath5k,ath,mac80211
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 32356  0 
soundcore              12600  1 snd
video                  18908  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
wmi                    18744  1 hp_wmi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  3 
forcedeth              58103  0 
pata_amd               13753  0 
libahci                25727  1 ahci
             total       used       free     shared    buffers     cached
Mem:       1802056    1303956     498100          0      91476     621548
-/+ buffers/cache:     590932    1211124
Swap:      1831932          0    1831932

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Dec  2 18:23:53 MST 2011: performing suspend
Initial commandline parameters: 
Fri Dec  2 21:01:29 MST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux nutin 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 athlon i386 GNU/Linux
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
nvidia               7098131  36 
binfmt_misc            17292  1 
arc4                   12473  2 
joydev                 17393  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                73673  0 
ath5k                 145100  0 
k10temp                12990  0 
serio_raw              12990  0 
ath                    19387  1 ath5k
mac80211              393459  1 ath5k
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
cfg80211              172392  3 ath5k,ath,mac80211
video                  18908  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
shpchp                 32356  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  1 hp_wmi
i2c_nforce2            12906  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  2 
libahci                25727  1 ahci
forcedeth              58103  0 
pata_amd               13753  0 
             total       used       free     shared    buffers     cached
Mem:       1802056    1260192     541864          0      88528     589148
-/+ buffers/cache:     582516    1219540
Swap:      1831932          0    1831932

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Dec  2 21:01:36 MST 2011: performing suspend
Sat Dec  3 07:20:22 MST 2011: Awake.
Sat Dec  3 07:20:22 MST 2011: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sat Dec  3 07:20:22 MST 2011: Finished.
Initial commandline parameters: 
Sat Dec  3 21:37:56 MST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux nutin 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 athlon i386 GNU/Linux
Module                  Size  Used by
usb_storage            44173  0 
uas                    17699  0 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
nvidia               7098131  40 
binfmt_misc            17292  1 
arc4                   12473  2 
joydev                 17393  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                73673  0 
ath5k                 145100  0 
k10temp                12990  0 
serio_raw              12990  0 
ath                    19387  1 ath5k
mac80211              393459  1 ath5k
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
cfg80211              172392  3 ath5k,ath,mac80211
video                  18908  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
shpchp                 32356  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  1 hp_wmi
i2c_nforce2            12906  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  3 
libahci                25727  1 ahci
forcedeth              58103  0 
pata_amd               13753  0 
             total       used       free     shared    buffers     cached
Mem:       1802056    1627416     174640          0     128888     716648
-/+ buffers/cache:     781880    1020176
Swap:      1831932        252    1831680

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Dec  3 21:38:04 MST 2011: performing suspend
Sun Dec  4 07:11:00 MST 2011: Awake.
Sun Dec  4 07:11:00 MST 2011: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sun Dec  4 07:11:01 MST 2011: Finished.
Initial commandline parameters: 
Sun Dec  4 21:54:18 MST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux nutin 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 athlon i386 GNU/Linux
Module                  Size  Used by
usb_storage            44173  0 
uas                    17699  0 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
nvidia               7098131  36 
binfmt_misc            17292  1 
arc4                   12473  2 
joydev                 17393  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                73673  0 
ath5k                 145100  0 
k10temp                12990  0 
serio_raw              12990  0 
ath                    19387  1 ath5k
mac80211              393459  1 ath5k
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
cfg80211              172392  3 ath5k,ath,mac80211
video                  18908  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
shpchp                 32356  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  1 hp_wmi
i2c_nforce2            12906  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  3 
libahci                25727  1 ahci
forcedeth              58103  0 
pata_amd               13753  0 
             total       used       free     shared    buffers     cached
Mem:       1802056    1347976     454080          0     126896     649584
-/+ buffers/cache:     571496    1230560
Swap:      1831932       2000    1829932

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Dec  4 21:54:26 MST 2011: performing suspend
Mon Dec  5 07:48:57 MST 2011: Awake.
Mon Dec  5 07:48:57 MST 2011: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Mon Dec  5 07:48:58 MST 2011: Finished.
Initial commandline parameters: 
Mon Dec  5 12:17:39 MST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux nutin 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 athlon i386 GNU/Linux
Module                  Size  Used by
usb_storage            44173  0 
uas                    17699  0 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
nvidia               7098131  40 
binfmt_misc            17292  1 
arc4                   12473  2 
joydev                 17393  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                73673  0 
ath5k                 145100  0 
k10temp                12990  0 
serio_raw              12990  0 
ath                    19387  1 ath5k
mac80211              393459  1 ath5k
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
cfg80211              172392  3 ath5k,ath,mac80211
video                  18908  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
shpchp                 32356  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  1 hp_wmi
i2c_nforce2            12906  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  3 
libahci                25727  1 ahci
forcedeth              58103  0 
pata_amd               13753  0 
             total       used       free     shared    buffers     cached
Mem:       1802056    1631276     170780          0     225856     583748
-/+ buffers/cache:     821672     980384
Swap:      1831932      11028    1820904

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Mon Dec  5 12:17:48 MST 2011: performing suspend
Mon Dec  5 12:18:50 MST 2011: Awake.
Mon Dec  5 12:18:50 MST 2011: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Mon Dec  5 12:18:51 MST 2011: Finished.

```-----------------------------------------
[SIZE=3]As far as what hardware I have, I don't know where to look to get that info.  All I know is that my laptop is a 160GB Compaq Presario CQ50 210US, 2GB RAM, Dual core.

And there's no pattern to it and it's happening every time as opposed to just sometimes.


[/SIZE]

---

### Post by pretty_whistle on 2011-12-05
[SIZE=3]I found this on this problem:

[http://askubuntu.com/questions/14289/laptop-does-not-wake-up-after-sleep](http://askubuntu.com/questions/14289/laptop-does-not-wake-up-after-sleep)


[/SIZE]

---

### Post by pretty_whistle on 2011-12-05
[SIZE=3]Well, at least I can treat the screen as a click-through by assuming the cursor is in the password field, enter my password in, and reach the desktop.

This way I don't have to do a hard shutdown.

One more thing:
I have auto login set up but suspend is acting otherwise.  At least I can click-through it.


[/SIZE]

---

