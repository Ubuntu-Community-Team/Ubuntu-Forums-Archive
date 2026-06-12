---
title: "Suspends OK but resumes after a few seconds!"
date: 2011-11-25
forum: General Help
---

### Post by Rebelli0us on 2011-11-25
I want to enable keyboard to wake the machine from S3. The keyboard is on USB2 so I did this:

```
echo USB2 > /proc/acpi/wakeup
```

And I got this:

```
cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
PCI0	  S5	*disabled  no-bus:pci0000:00
USB0	  S3	*enabled   pci:0000:00:12.0
USB1	  S3	*enabled   pci:0000:00:12.2
USB2	  S3	*enabled   pci:0000:00:13.0
USB3	  S3	*enabled   pci:0000:00:13.2
USB4	  S3	*enabled   pci:0000:00:16.0
USB5	  S3	*enabled   pci:0000:00:16.2
USB6	  S3	*enabled   pci:0000:00:14.5
SBAZ	  S4	*disabled  pci:0000:00:14.2
PEX0	  S5	*disabled  pci:0000:00:15.0
PEX1	  S5	*disabled  
PEX2	  S5	*disabled  
PEX3	  S5	*disabled  
P2P	  S5	*disabled  pci:0000:00:14.4
PCE2	  S4	*disabled  
PCE3	  S4	*disabled  
PCE4	  S4	*disabled  
PCE5	  S4	*disabled  
PCE6	  S4	*disabled  
PCE7	  S4	*disabled  pci:0000:00:07.0
PCE9	  S4	*disabled  
PCEA	  S4	*disabled  pci:0000:00:0a.0
PCEB	  S4	*disabled  
PCEC	  S4	*disabled  

```


Now the machine suspends S3 but then it resumes after about 30 seconds. It doesn’t stay in S3. How do I fix this?

.

---

### Post by Rebelli0us on 2011-12-02
Any ideas?

---

### Post by matt_symes on 2011-12-02
Hi

As opposed to using /proc/acpi which, i think, is deprecated, have you considered using sysfs.

```
echo enabled | sudo tee /sys/bus/usb/devices/**usb2**/power/wakeup
```This assumes the keyboard is attached to USB 2 as highlighted above.

I think it's the wakeup file you need. If it works then you need to make it permanent.

Kind regards

---

### Post by Rebelli0us on 2011-12-02
> **matt_symes said:**
> Hi

As opposed to using /proc/acpi which, i think, is deprecated, have you considered using sysfs.

```
echo enabled | sudo tee /sys/bus/usb/devices/**usb2**/power/wakeup
```This assumes the keyboard is attached to USB 2 as highlighted above.

I think it's the wakeup file you need. If it works then you need to make it permanent.

Kind regards

Thank you. I don't know what sysfs is, but I looked up the ".../wakeup" file and it already says "enabled". What does that mean?

---

### Post by matt_symes on 2011-12-03
Hi

> **Rebelli0us said:**
> Thank you. I don't know what sysfs is, but I looked up the ".../wakeup" file and it already says "enabled". What does that mean?

It means that it should wakeup for the USB keyboard already. It is the new way to do it though; not using procfs but sysfs.

Can you try to suspend you PC. After it attempts to suspend, open a terminal and type
[FONT=monospace]
[/FONT]```
cat /sys/bus/usb/devices/usb2/power/wakeup_hit_count

```

Post the results back here. Can you also post the results from (just the last suspend/ resume attempt)

```
cat /var/log/pm-suspend.log
```

Kind regards

---

### Post by Rebelli0us on 2011-12-03
> **matt_symes said:**
> Hi



It means that it should wakeup for the USB keyboard already. It is the new way to do it though; not using procfs but sysfs.

Can you try to suspend you PC. After it attempts to suspend, open a terminal and type
[FONT=monospace]
[/FONT]```
cat /sys/bus/usb/devices/usb2/power/wakeup_hit_count

```

Post the results back here. Can you also post the results from (just the last suspend/ resume attempt)

```
cat /var/log/pm-suspend.log
```

Kind regards



Thank you. I'm not sure what you mean, it **does** suspend ok but resumes after 30 sec or so. Windows will do that too if wake-on-lan isn't setup properly, because resume is triggered by internet noise. Regardless, I'll try your solution in a few minutes and post back.

I'm on a different machine right now and it has suspend problems as well: Suspend **works only once**, then the mouse/keyboard device no longer wakes the machine from S3.

in /etc/rc.local I added:

echo UHC4 >> /proc/acpi/wakeup

That seems to enable **all** usb devices for wakeup:

```
cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
PCE2	  S4	 disabled  
PCE3	  S4	 disabled  
PCE4	  S4	 disabled  pci:0000:00:04.0
PCE5	  S4	 disabled  
PCE7	  S4	 disabled  
PCE9	  S4	 disabled  
PCEA	  S4	 disabled  
SBAZ	  S4	 disabled  pci:0000:00:14.2
P0PC	  S4	 disabled  pci:0000:00:14.4
UHC1	  S4	 enabled   pci:0000:00:12.0
UHC2	  S4	 enabled   pci:0000:00:12.2
USB3	  S4	 enabled   pci:0000:00:13.0
UHC4	  S4	 enabled   pci:0000:00:13.2
USB5	  S4	 enabled   pci:0000:00:16.0
UHC6	  S4	 enabled   pci:0000:00:16.2
UHC7	  S4	 enabled   pci:0000:00:14.5
PE20	  S4	 disabled  
PE21	  S4	 disabled  
PE22	  S4	 disabled  
PE23	  S4	 disabled  
GEC	  S4	 disabled  
PS2K	  S3	 disabled  pnp:00:09
PCE6	  S4	 disabled  pci:0000:00:06.0
PWRB	  S3	*enabled   

```




How do I enable this device for wakeup permanently?

---

### Post by Rebelli0us on 2011-12-03
ok I'm at the 1st machine now, the one that suspends but resumes after 30sec.

```
cat /sys/bus/usb/devices/usb2/power/wakeup_hit_count
cat: /sys/bus/usb/devices/usb2/power/wakeup_hit_count: No such file or directory
```

The second command
```
cat /var/log/pm-suspend.log
```
prints out more lines than the terminal buffer will hold. What am I looking for there?

So it looks like Linux doesn't have the dreaded "Registry", instead config data is kept in a million little files. I prefer that.

---

### Post by Rebelli0us on 2011-12-26
Trying again:

```
cat /var/log/pm-suspend.log
```

This seems to be the last resume event, I mark in **bold** the start of resume from S3:

```
Mon Dec 26 07:49:30 EST 2011: Finished.
Initial commandline parameters: 
Mon Dec 26 07:59:50 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux A17N-U 2.6.35-31-generic #63-Ubuntu SMP Mon Nov 28 19:29:10 UTC 2011 x86_64 GNU/Linux
Module                  Size  Used by
xhci_hcd               62016  0 
cryptd                  8140  0 
aes_x86_64              7936  1 
aes_generic            27631  1 aes_x86_64
binfmt_misc             7984  1 
rfcomm                 40819  4 
sco                     9986  2 
bnep                   11985  2 
l2cap                  42336  18 rfcomm,bnep
pci_stub                1622  1 
vboxpci                15608  0 
vboxnetadp              5838  0 
vboxnetflt             16638  0 
vboxdrv              1854941  4 vboxpci,vboxnetadp,vboxnetflt
parport_pc             30086  0 
ppdev                   6804  0 
joydev                 11395  0 
snd_hda_codec_atihdmi     3079  1 
snd_hda_codec_realtek   300109  1 
arc4                    1497  2 
snd_seq_midi            5932  0 
snd_hda_intel          26147  4 
snd_rawmidi            22207  1 snd_seq_midi
radeon                910771  2 
ath9k                 101858  0 
ath9k_common            6874  1 ath9k
ath9k_hw              314654  2 ath9k,ath9k_common
ath                    10413  2 ath9k,ath9k_hw
snd_hda_codec         100919  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi_event      7291  1 snd_seq_midi
snd_hwdep               6660  1 snd_hda_codec
ttm                    68212  1 radeon
drm_kms_helper         32836  1 radeon
snd_pcm                89104  3 snd_hda_intel,snd_hda_codec
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              23850  2 snd_seq,snd_pcm
mac80211              267099  2 ath9k,ath9k_common
drm                   206198  4 radeon,ttm,drm_kms_helper
i2c_algo_bit            6208  1 radeon
edac_core              46822  0 
shpchp                 34910  0 
edac_mce_amd            9387  0 
snd                    64277  16 snd_hda_codec_realtek,snd_hda_intel,snd_rawmidi,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
cfg80211              170581  4 ath9k,ath9k_common,ath,mac80211
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
led_class               3393  1 ath9k
i2c_piix4              10047  0 
btusb                  12961  2 
bluetooth              59245  9 rfcomm,sco,bnep,l2cap,btusb
serio_raw               4910  0 
k10temp                 3535  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42030  0 
hid                    84710  1 usbhid
firewire_ohci          24839  0 
r8169                  42286  0 
ahci                   22370  5 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
libahci                26148  1 ahci
mii                     5261  1 r8169
pata_jmicron            2771  0 
             total       used       free     shared    buffers     cached
Mem:       3537712    3238700     299012          0     264212    1609896
-/+ buffers/cache:    1364592    2173120
Swap:            0          0          0

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk suspend suspend:

/usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/45bluetooth-service suspend suspend:

/usr/lib/pm-utils/sleep.d/45bluetooth-service suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.5 -> dest=:1.182 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module xhci-hcd...Done.

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Mon Dec 26 07:59:52 EST 2011: performing suspend
**Mon Dec 26 08:00:12 EST 2011: Awake.**
Mon Dec 26 08:00:12 EST 2011: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa resume suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...method return sender=:1.5 -> dest=:1.184 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/45bluetooth-service resume suspend:

/usr/lib/pm-utils/sleep.d/45bluetooth-service resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk resume suspend:

/usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
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
Mon Dec 26 08:00:13 EST 2011: Finished.

```


So what's waking up the machine?

---

### Post by matt_symes on 2011-12-28
Hi

Open a terminal and type

```
echo -n mem | sudo tee /sys/power/state
```

Does it suspend successfully them ?

Kind regards

---

### Post by Rebelli0us on 2011-12-28
```
echo -n mem | sudo tee /sys/power/state
memtee: /sys/power/state: No such file or directory
```

Machine suspends just fine, BUT if USB2 (keyboard) is enabled for wakeup then it resumes about 1 min later.

---

### Post by matt_symes on 2011-12-30
Hi
[FONT=monospace]
[/FONT]> /sys/power/state: No such file or directory

On my machine
```

matthew@matthew-Aspire-7540:~$ ls /sys/power
disk  image_size  pm_async  pm_test  pm_trace  pm_trace_dev_match  reserved_size  resume  state  wakeup_count
matthew@matthew-Aspire-7540:~$
```

What version of Ubuntu are you using ? Do you not have swsusp ?

Do you not have a /sys/power directory ?

What's  the output of 

```
ls -d /sys/p*
```

and 

```
ls /sys/p*
```

Kind regards

---

### Post by Rebelli0us on 2011-12-31
I'm running Ubu 10.10, swsusp is not installed.

I just looked, there is a file /sys/power/state and it has a one-liner "mem disk".

---

### Post by donaldt on 2011-12-31
OK, this is probably in the wrong place, but if so someone please re-direct.

The IMAC used elsewhere in our office has a very nice feature for suspending and re-start.  You set the time for it to shut down and wake-up.  After that, it does that daily, awaking at 0800 and shutting down at 2200.  

No further human intervention required.  Now, all the Ubuntu users and programmers are obviously more clever and smarter than Apple, so there must be something similar for Ubuntu.  Right?  or Wrong?

Thanks for the indulgence.

donaldt

---

### Post by matt_symes on 2012-01-03
Hi

@donaldt. 

Take a look at the shutdown command to shutdown your PC or pm-suspend and pm-hibernate to suspend or hibernate.

To wake it up look at the rtcwake command.

That may take you closer.

Kind regards

---

### Post by Rebelli0us on 2012-01-03
> **donaldt said:**
> OK, this is probably in the wrong place, but if so someone please re-direct.

The IMAC used elsewhere in our office has a very nice feature for suspending and re-start.  You set the time for it to shut down and wake-up.  After that, it does that daily, awaking at 0800 and shutting down at 2200.  

No further human intervention required.  Now, all the Ubuntu users and programmers are obviously more clever and smarter than Apple, so there must be something similar for Ubuntu.  Right?  or Wrong?

Thanks for the indulgence.

donaldt

Ubuntu has "Scheduled tasks" that claims to be similar to Windows' Task Scheduler. It's not installed by default but you can find it in Ubuntu Software Center.

---

