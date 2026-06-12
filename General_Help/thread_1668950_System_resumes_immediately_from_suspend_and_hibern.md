---
title: "System resumes immediately from suspend and hibernate after hardware upgrade"
date: 2011-01-17
forum: General Help
---

### Post by pr0grammer1 on 2011-01-17
I just upgraded from a Q6600 and XFX 680i LT SLI to a 2500k and Asus P8P67 PRO. Suspend and hibernate used to both work fine, but after the upgrade, either one resumes immediately after I start it.

Here's the relevant info from pm-suspend.log:
```
Initial commandline parameters: 
Sun Jan 16 23:02:17 PST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux alex-desktop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux
Module                  Size  Used by
snd_seq_dummy           1806  0 
nls_utf8                1453  0 
udf                    86514  0 
rfcomm                 40787  4 
binfmt_misc             7984  1 
sco                     9986  2 
bnep                   11985  2 
l2cap                  42304  16 rfcomm,bnep
vboxnetadp              5267  0 
vboxnetflt             14966  0 
vboxdrv              1792856  2 vboxnetadp,vboxnetflt
parport_pc             30086  0 
ppdev                   6804  0 
btusb                  12929  2 
bluetooth              59245  9 rfcomm,sco,bnep,l2cap,btusb
coretemp                6442  0 
snd_hda_codec_realtek   299844  1 
ath3k                   2799  0 
nvidia              10221046  58 
snd_hda_intel          26019  3 
snd_hda_codec         100919  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
max6650                 8900  0 
snd_seq                57512  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 11395  0 
snd                    64181  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
adt7475                26161  0 
hwmon_vid               3154  1 adt7475
eeepc_wmi               3571  0 
sparse_keymap           3837  1 eeepc_wmi
psmouse                62080  0 
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
xhci_hcd               58578  0 
intel_agp              32462  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42062  0 
hid                    84710  1 usbhid
dm_raid45              75026  0 
firewire_ohci          24615  0 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  2 udf,firewire_core
xor                     4709  1 dm_raid45
ahci                   22210  9 
libahci                26052  1 ahci
e1000e                151787  0 
             total       used       free     shared    buffers     cached
Mem:       8174488    1420556    6753932          0      28024     226428
-/+ buffers/cache:    1166104    7008384
Swap:      8385924     918236    7467688

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.2 -> dest=:1.132 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module ehci_hcd...Done.

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sun Jan 16 23:02:19 PST 2011: performing suspend
Sun Jan 16 23:02:19 PST 2011: Awake.
Sun Jan 16 23:02:19 PST 2011: Running hooks for resume
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
Having NetworkManager wake interfaces back up...method return sender=:1.2 -> dest=:1.134 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sun Jan 16 23:02:20 PST 2011: Finished.
```

Is there anything I can do to fix this, or do I need to wait for a patch (since the hardware was only just released)?

---

### Post by pr0grammer1 on 2011-01-18
Bump.

---

### Post by pr0grammer1 on 2011-01-18
Here's /proc/acpi/wakeup:

```
Device	S-state	  Status   Sysfs node
UAR1	  S4	*disabled  pnp:00:08
BR20	  S3	*disabled  
USBE	  S4	*disabled  pci:0000:00:1a.0
P0P3	  S4	*disabled  
P0P4	  S4	*disabled  
P0P1	  S4	*disabled  pci:0000:00:01.0
P0P2	  S4	*disabled  
PEX0	  S4	*disabled  pci:0000:00:1c.0
PEX1	  S4	*disabled  pci:0000:00:1c.1
PEX2	  S4	*disabled  pci:0000:00:1c.2
PEX3	  S4	*disabled  pci:0000:00:1c.3
PEX4	  S4	*disabled  pci:0000:00:1c.4
PEX5	  S4	*disabled  
PEX6	  S4	*disabled  pci:0000:00:1c.6
BR24	  S4	*disabled  pci:0000:07:00.0
PEX7	  S4	*disabled  pci:0000:00:1c.7
GBE	  S4	*disabled  pci:0000:00:19.0
EUSB	  S4	*disabled  pci:0000:00:1d.0
PWRB	  S4	*enabled   
```

Unless I'm reading that incorrectly, shouldn't the power button be the only thing that should wake the computer?

---

### Post by pr0grammer1 on 2011-01-19
Bump again.

---

### Post by pr0grammer1 on 2011-01-28
Bump.

---

### Post by VCoolio on 2011-01-28
Check your bios settings, there should be something there about suspending. I have a p7p55d-e pro, same issue, had to change something. If I remember correctly, something in the power tab. But for me only suspend works, not hibernate; not sure what the issue is. I can live with suspend.

---

### Post by pr0grammer1 on 2011-01-29
I tried all of the available options there and none made any difference.

---

### Post by pr0grammer1 on 2011-01-29
Bump.

---

### Post by pr0grammer1 on 2011-01-29
Fixed. Run:
```
echo blacklist xhci_hcd | sudo tee -a /etc/modprobe.d/blacklist.conf >/dev/null
```
and reboot.

The issue was the USB3 module.

---

### Post by xdevnull on 2011-01-29
Hey - I have USB 3 too - and having trouble - with the asus p7p55d-e pro.  Same thing happening.  Did that disable your usb3 capabilities or the plugs?

---

### Post by xxaarrgg on 2011-03-15
I had the same problem as OP, and blacklisting xhci_hcd also worked for me :D.

Ubuntu Maverick 10.10
Gigabyte GA-890GPA-UD3H 890GX

---

### Post by bobharvey on 2011-04-28
My Server 10.04 based system was obeying pm-suspend-hyrbid reliably every time until last week, and now 3 times out of 4 it resumes immediately.  it always did that with pm-hibernate, but I wasn't using that.

I've removed the wifi card (not used) in case it was that, and have tried the blacklist trick described here with a clean boot, and it is no better.

I am at my wits end.

---

