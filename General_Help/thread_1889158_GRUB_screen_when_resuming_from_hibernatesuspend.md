---
title: "GRUB screen when resuming from hibernate/suspend"
date: 2011-11-30
forum: General Help
---

### Post by JadeMoonlight on 2011-11-30
Hello,

Experience level:
I would consider myself to be somewhere between beginner and intermediate with my Ubuntu experience. I have no aversions to using the Terminal to apply a fix or gather needed output for troubleshooting. However, I do ask that you provide me with the code for whatever output you'd like me to get from the Terminal.

Installation details:
My laptop has a multi-boot configuration with Windows 7 and several Ubuntu versions, each on a separate partition, all on the same hard drive.

sda1 Windows Recovery partition
sda2 Windows 7
sda3 Space for sharing files between partitions
sda4 Extended
sda5 Swap
sda6 Lucid - old
sda7 Natty - old
sda8 Oneiric - current

Output for [FONT=Courier New]fdisk -l[/FONT]
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5e7046ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    18782207     9390080   27  Hidden NTFS WinRE
/dev/sda2        18812115   166128164    73658025    7  HPFS/NTFS/exFAT
/dev/sda3       166385205   292206284    62910540    7  HPFS/NTFS/exFAT
/dev/sda4       292206590   488392064    98092737+   5  Extended
/dev/sda5       476078080   484466687     4194304   82  Linux swap / Solaris
/dev/sda6   *   292206592   377237503    42515456   83  Linux
/dev/sda7       377239552   395537047     9148748   83  Linux
/dev/sda8       395538432   476076031    40268800   83  Linux
```

Problem details:
My computer is currently having problems coming out of the Hibernate or Suspend state. For Suspend, the power light will blink to indicate that it is in a suspended state, but when I awaken the computer, it returns to the GRUB bootloader menu rather than a screen to enter my password and resume my session.

If anyone cold help me correct this, I would be very appreciative.

---

### Post by Toz on 2011-11-30
> **JadeMoonlight said:**
> For Suspend, the power light will blink to indicate that it is in a suspended state, but when I awaken the computer, it returns to the GRUB bootloader menu rather than a screen to enter my password and resume my session.

Here's a potential quick-fix. Try booting with the **acpi_sleep=nonvs** kernel parameter. Here are instructions on how to test this by editing the grub kernel command line: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot").

After you've booted with the kernel parameter, open a terminal window, execute and post back the results of:
```
cat /proc/cmdline
```
...then re-test the suspend/resume cycle.

If it still doesn't work, then some information about your system (make/model) and the contents of the log file **/var/log/pm-suspend.log** would be helpful.

---

### Post by JadeMoonlight on 2011-12-04
Here are the results from the terminal after I added to the boot

~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=5640e1e4-9c87-462d-ad73-ed50596079a2 ro quiet splash vt.handoff=7

The addition to the boot entry doesn't seem to be working, however. I actually put it in wrong the first time (acpi_sleep=novs instead of acpi_sleep=nonvs), and the output for cat /proc/cmdline was the same both times.

System info:

[Sony Vaio VGN-NS140E]("http://www.sonystyle.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&langId=-1&productId=8198552921665507471#specifications")

Intel® Core™ 2 Duo T5800 processor (2.0GHz) 
4GB PC2-6400 memory
Wi-Fi : Intel® WiFi Link 5100AGN (802.11a/b/g/n)3
Ethernet Protocol : 10Base-T/100Base-TX/1000Base-T
Modem Type : Integrated V.92/V.90 Modem (RJ-11

Contents of /var/log/pm-suspend.log:
```
Initial commandline parameters: 
Thu Dec  1 17:57:42 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux owner-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_codec_realtek   330769  1 
iptable_nat            13229  0 
nf_nat                 25890  1 iptable_nat
nf_conntrack_ipv4      19716  3 iptable_nat,nf_nat
nf_conntrack           82342  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
iptable_filter         12810  0 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  4 iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi           13324  0 
iwlagn                314213  0 
snd_rawmidi            30547  1 snd_seq_midi
mac80211              462092  1 iwlagn
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              199587  2 iwlagn,mac80211
psmouse                73882  0 
i915                  566711  3 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
sony_laptop            45393  0 
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    2400524    1493964          0     101376    1171052
-/+ buffers/cache:    1128096    2766392
Swap:      4194300          0    4194300

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Dec  1 17:57:44 EST 2011: performing suspend
Initial commandline parameters: 
Fri Dec  2 15:03:21 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux owner-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
iptable_nat            13229  0 
nf_nat                 25890  1 iptable_nat
nf_conntrack_ipv4      19716  3 iptable_nat,nf_nat
nf_conntrack           82342  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  0 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  4 iptable_nat,iptable_mangle,iptable_filter,ip_tables
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_codec_realtek   330769  1 
iwlagn                314213  0 
mac80211              462092  1 iwlagn
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
psmouse                73882  0 
cfg80211              199587  2 iwlagn,mac80211
serio_raw              13166  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sony_laptop            45393  0 
i915                  566711  2 
drm_kms_helper         42558  1 i915
drm                   236330  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488     571248    3323240          0      48492     287816
-/+ buffers/cache:     234940    3659548
Swap:      4194300          0    4194300

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:

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

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Dec  2 15:03:22 EST 2011: performing suspend
Initial commandline parameters: 
Fri Dec  2 18:43:09 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux owner-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_codec_realtek   330769  1 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
uvcvideo               72711  0 
snd_seq_midi           13324  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_rawmidi            30547  1 snd_seq_midi
iwlagn                314213  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              462092  1 iwlagn
snd_timer              29991  2 snd_pcm,snd_seq
psmouse                73882  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13166  0 
i915                  566711  3 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  2 iwlagn,mac80211
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
sony_laptop            45393  0 
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    1514084    2380404          0      63916     614976
-/+ buffers/cache:     835192    3059296
Swap:      4194300          0    4194300

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Dec  2 18:43:11 EST 2011: performing suspend
Initial commandline parameters: 
Sat Dec  3 23:22:48 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux owner-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
arc4                   12529  2 
iptable_mangle         12734  0 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
snd_seq_midi           13324  0 
v4l2_compat_ioctl32    17083  1 videodev
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
iwlagn                314213  0 
mac80211              462092  1 iwlagn
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
serio_raw              13166  0 
cfg80211              199587  2 iwlagn,mac80211
soundcore              12680  1 snd
i915                  566711  3 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sony_laptop            45393  0 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    1295008    2599480          0      67364     603272
-/+ buffers/cache:     624372    3270116
Swap:      4194300          0    4194300

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Dec  3 23:22:50 EST 2011: performing suspend
```

---

### Post by Toz on 2011-12-04
Make sure you are adding it (acpi_sleep=nonvs) correctly to the kernel boot line following the instructions linked above. After you boot with it, you should see it displayed with:
```
cat /proc/cmdline
```
It should look something like:
> BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=5640e1e4-9c87-462d-ad73-ed50596079a2 ro quiet splash vt.handoff=7 acpi_sleep=nonvs

Then you can test suspend/resume again to see if there is a difference.

---

### Post by Toz on 2011-12-04
Can you also post back the results of the following 2 commands:
```
dmesg
```
...and
```
cat /var/log/syslog | grep PM:
```

---

### Post by JadeMoonlight on 2011-12-04
The boot entry edit worked this time; I had been putting it in the wrong place/on the wrong line.

Here is the output you requested.

Results of dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-13-generic (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 (Ubuntu 3.0.0-13.22-generic 3.0.6)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=5640e1e4-9c87-462d-ad73-ed50596079a2 ro quiet splash vt.handoff=7 acpi_sleep=nonvs
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009bc00 (usable)
[    0.000000]  BIOS-e820: 000000000009bc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b5ea8000 (usable)
[    0.000000]  BIOS-e820: 00000000b5ea8000 - 00000000b5ed0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b5ed0000 - 00000000b5ee1000 (reserved)
[    0.000000]  BIOS-e820: 00000000b5ee1000 - 00000000b5ee2000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b5ee2000 - 00000000b5f0a000 (reserved)
[    0.000000]  BIOS-e820: 00000000b5f0a000 - 00000000b5f0b000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b5f0b000 - 00000000b5f0c000 (reserved)
[    0.000000]  BIOS-e820: 00000000b5f0c000 - 00000000b5f17000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b5f17000 - 00000000b5f1d000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b5f1d000 - 00000000b5f39000 (reserved)
[    0.000000]  BIOS-e820: 00000000b5f39000 - 00000000b6000000 (usable)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Sony Corporation VGN-NS140E/VAIO, BIOS R0190Y3 07/09/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E7FFF write-through
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0B8000000 mask FF8000000 uncachable
[    0.000000]   3 base 0B6000000 mask FFE000000 uncachable
[    0.000000]   4 base 100000000 mask FC0000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 2944MB, range: 128MB, type UC
[    0.000000] reg 3, base: 2912MB, range: 32MB, type UC
[    0.000000] reg 4, base: 4GB, range: 1GB, type WB
[    0.000000] total RAM covered: 3936M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 256M 	num_reg: 5  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 2912MB, range: 32MB, type UC
[    0.000000] reg 3, base: 2944MB, range: 128MB, type UC
[    0.000000] reg 4, base: 4GB, range: 1GB, type WB
[    0.000000] e820 update range: 00000000b6000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xb6000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fd650] fd650
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000b6000000
[    0.000000]  0000000000 - 00b6000000 page 2M
[    0.000000] kernel direct mapping tables up to b6000000 @ b5ffc000-b6000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ 13fffa000-140000000
[    0.000000] RAMDISK: 365b2000 - 372d1000
[    0.000000] ACPI: RSDP 00000000000f03b0 00024 (v02   Sony)
[    0.000000] ACPI: XSDT 00000000b5f15f10 0005C (v01   Sony     VAIO 20080709 MSFT 00010013)
[    0.000000] ACPI: FACP 00000000b5f0aa90 000F4 (v04   Sony     VAIO 20080709 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110413/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xB5F1CE40/0x00000000B5F1CD40, using 32 (20110413/tbfadt-489)
[    0.000000] ACPI: DSDT 00000000b5f0c010 07AFE (v01   Sony     VAIO 20080709 INTL 20051117)
[    0.000000] ACPI: FACS 00000000b5f1ce40 00040
[    0.000000] ACPI: APIC 00000000b5f14f10 0006C (v02   Sony     VAIO 20080709 MSFT 00010013)
[    0.000000] ACPI: MCFG 00000000b5f1bc90 0003C (v01   Sony     VAIO 20080709 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000b5f1bc10 00038 (v01   Sony     VAIO 20080709 MSFT 00010013)
[    0.000000] ACPI: SLIC 00000000b5f17c10 00176 (v01   Sony     VAIO 20080709 Sony 01000000)
[    0.000000] ACPI: SSDT 00000000b5ee1590 00505 (v01   Sony     VAIO 20080709 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000b5eccc10 002E4 (v01   Sony     VAIO 20080709 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [000000013fffb000 - 000000013fffffff]
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff88013b800000-ffff88013effffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x000b5ea8
[    0.000000]     0: 0x000b5f39 -> 0x000b6000
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1007354
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3918 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 726951 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000b5ea8000 - 00000000b5ed0000
[    0.000000] PM: Registered nosave memory: 00000000b5ed0000 - 00000000b5ee1000
[    0.000000] PM: Registered nosave memory: 00000000b5ee1000 - 00000000b5ee2000
[    0.000000] PM: Registered nosave memory: 00000000b5ee2000 - 00000000b5f0a000
[    0.000000] PM: Registered nosave memory: 00000000b5f0a000 - 00000000b5f0b000
[    0.000000] PM: Registered nosave memory: 00000000b5f0b000 - 00000000b5f0c000
[    0.000000] PM: Registered nosave memory: 00000000b5f0c000 - 00000000b5f17000
[    0.000000] PM: Registered nosave memory: 00000000b5f17000 - 00000000b5f1d000
[    0.000000] PM: Registered nosave memory: 00000000b5f1d000 - 00000000b5f39000
[    0.000000] PM: Registered nosave memory: 00000000b6000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000ffa00000
[    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at b6000000 (gap: b6000000:2a000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88013fc00000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 989429
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=5640e1e4-9c87-462d-ad73-ed50596079a2 ro quiet splash vt.handoff=7 acpi_sleep=nonvs
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3878652k/5242880k available (6105k kernel code, 1213464k absent, 150764k reserved, 4879k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 32505856 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1993.767 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3987.53 BogoMIPS (lpj=7975068)
[    0.004010] pid_max: default: 32768 minimum: 301
[    0.004044] Security Framework initialized
[    0.004064] AppArmor: AppArmor initialized
[    0.004066] Yama: becoming mindful.
[    0.008128] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.010333] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.011353] Mount-cache hash table entries: 256
[    0.011535] Initializing cgroup subsys cpuacct
[    0.011544] Initializing cgroup subsys memory
[    0.011555] Initializing cgroup subsys devices
[    0.011558] Initializing cgroup subsys freezer
[    0.011560] Initializing cgroup subsys net_cls
[    0.011563] Initializing cgroup subsys blkio
[    0.011571] Initializing cgroup subsys perf_event
[    0.011606] CPU: Physical Processor ID: 0
[    0.011608] CPU: Processor Core ID: 0
[    0.011611] mce: CPU supports 6 MCE banks
[    0.011621] CPU0: Thermal monitoring enabled (TM2)
[    0.011626] using mwait in idle threads.
[    0.014385] ACPI: Core revision 20110413
[    0.020037] ftrace: allocating 25656 entries in 101 pages
[    0.024367] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.064271] CPU0: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz stepping 0d
[    0.068003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.068003] PEBS disabled due to CPU errata.
[    0.068003] ... version:                2
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] Booting Node   0, Processors  #1
[    0.068003] smpboot cpu 1: start_ip = 96000
[    0.156027] Brought up 2 CPUs
[    0.156031] Total of 2 processors activated (7974.61 BogoMIPS).
[    0.156996] devtmpfs: initialized
[    0.156996] PM: Registering ACPI NVS region at b5ea8000 (163840 bytes)
[    0.156996] PM: Registering ACPI NVS region at b5ee1000 (4096 bytes)
[    0.156996] PM: Registering ACPI NVS region at b5f0a000 (4096 bytes)
[    0.156996] PM: Registering ACPI NVS region at b5f17000 (24576 bytes)
[    0.157585] print_constraints: dummy: 
[    0.157620] Time: 20:11:27  Date: 12/04/11
[    0.157663] NET: Registered protocol family 16
[    0.157696] Trying to unpack rootfs image as initramfs...
[    0.157811] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.157814] ACPI: bus type pci registered
[    0.157902] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.157906] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.228397] PCI: Using configuration type 1 for base access
[    0.229404] bio: create slab <bio-0> at 0
[    0.231480] ACPI: EC: Look up EC in DSDT
[    0.233344] ACPI: Executed 1 blocks of module-level executable AML code
[    0.264101] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.302572] ACPI: SSDT 00000000b5ee5c10 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.303042] ACPI: Dynamic OEM Table Load:
[    0.303045] ACPI: SSDT           (null) 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.303200] ACPI: SSDT 00000000b5ee3810 007A2 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.303649] ACPI: Dynamic OEM Table Load:
[    0.303652] ACPI: SSDT           (null) 007A2 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.352413] ACPI: SSDT 00000000b5ee4d90 000FD (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.352882] ACPI: Dynamic OEM Table Load:
[    0.352886] ACPI: SSDT           (null) 000FD (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.388178] ACPI: SSDT 00000000b5ee2f90 00047 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.388637] ACPI: Dynamic OEM Table Load:
[    0.388640] ACPI: SSDT           (null) 00047 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.459537] Freeing initrd memory: 13436k freed
[    0.612140] ACPI: Interpreter enabled
[    0.612147] ACPI: (supports S0 S3 S4 S5)
[    0.612175] ACPI: Using IOAPIC for interrupt routing
[    0.648588] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.648773] ACPI: No dock devices found.
[    0.648776] HEST: Table not found.
[    0.648779] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.649071] \_SB_.PCI0:_OSC invalid UUID
[    0.649073] _OSC request data:1 8 1f 
[    0.649078] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.649557] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.649560] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.649563] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.649566] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.649569] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.649572] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.649574] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.649577] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.649580] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.649583] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
[    0.649600] pci 0000:00:00.0: [8086:2a40] type 0 class 0x000600
[    0.649627] DMAR: Forcing write-buffer flush capability
[    0.649629] DMAR: Disabling IOMMU for graphics on this chipset
[    0.649654] pci 0000:00:02.0: [8086:2a42] type 0 class 0x000300
[    0.649669] pci 0000:00:02.0: reg 10: [mem 0xd0000000-0xd03fffff 64bit]
[    0.649679] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.649686] pci 0000:00:02.0: reg 20: [io  0xe140-0xe147]
[    0.649723] pci 0000:00:02.1: [8086:2a43] type 0 class 0x000380
[    0.649736] pci 0000:00:02.1: reg 10: [mem 0xd0400000-0xd04fffff 64bit]
[    0.649833] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
[    0.649896] pci 0000:00:1a.0: reg 20: [io  0xe0e0-0xe0ff]
[    0.649960] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
[    0.650023] pci 0000:00:1a.1: reg 20: [io  0xe0c0-0xe0df]
[    0.650088] pci 0000:00:1a.2: [8086:2939] type 0 class 0x000c03
[    0.650151] pci 0000:00:1a.2: reg 20: [io  0xe0a0-0xe0bf]
[    0.650231] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
[    0.650260] pci 0000:00:1a.7: reg 10: [mem 0xd4204c00-0xd4204fff]
[    0.650360] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.650366] pci 0000:00:1a.7: PME# disabled
[    0.650401] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.650424] pci 0000:00:1b.0: reg 10: [mem 0xd4200000-0xd4203fff 64bit]
[    0.650510] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.650515] pci 0000:00:1b.0: PME# disabled
[    0.650546] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
[    0.650634] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.650640] pci 0000:00:1c.0: PME# disabled
[    0.650673] pci 0000:00:1c.1: [8086:2942] type 1 class 0x000604
[    0.650761] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.650766] pci 0000:00:1c.1: PME# disabled
[    0.650799] pci 0000:00:1c.2: [8086:2944] type 1 class 0x000604
[    0.650888] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.650893] pci 0000:00:1c.2: PME# disabled
[    0.650934] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
[    0.650997] pci 0000:00:1d.0: reg 20: [io  0xe080-0xe09f]
[    0.651061] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
[    0.651124] pci 0000:00:1d.1: reg 20: [io  0xe060-0xe07f]
[    0.652079] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
[    0.652142] pci 0000:00:1d.2: reg 20: [io  0xe040-0xe05f]
[    0.652221] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
[    0.652250] pci 0000:00:1d.7: reg 10: [mem 0xd4204800-0xd4204bff]
[    0.652349] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.652355] pci 0000:00:1d.7: PME# disabled
[    0.652383] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.652472] pci 0000:00:1f.0: [8086:2919] type 0 class 0x000601
[    0.652638] pci 0000:00:1f.2: [8086:2929] type 0 class 0x000106
[    0.652669] pci 0000:00:1f.2: reg 10: [io  0xe130-0xe137]
[    0.652682] pci 0000:00:1f.2: reg 14: [io  0xe120-0xe123]
[    0.652695] pci 0000:00:1f.2: reg 18: [io  0xe110-0xe117]
[    0.652708] pci 0000:00:1f.2: reg 1c: [io  0xe100-0xe103]
[    0.652720] pci 0000:00:1f.2: reg 20: [io  0xe020-0xe03f]
[    0.652733] pci 0000:00:1f.2: reg 24: [mem 0xd4204000-0xd42047ff]
[    0.652788] pci 0000:00:1f.2: PME# supported from D3hot
[    0.652794] pci 0000:00:1f.2: PME# disabled
[    0.652820] pci 0000:00:1f.3: [8086:2930] type 0 class 0x000c05
[    0.652843] pci 0000:00:1f.3: reg 10: [mem 0xd4205000-0xd42050ff 64bit]
[    0.652876] pci 0000:00:1f.3: reg 20: [io  0xe000-0xe01f]
[    0.653151] pci 0000:01:00.0: [11ab:4363] type 0 class 0x000200
[    0.653324] pci 0000:01:00.0: reg 10: [mem 0xd2d20000-0xd2d23fff 64bit]
[    0.653418] pci 0000:01:00.0: reg 18: [io  0xd000-0xd0ff]
[    0.653781] pci 0000:01:00.0: reg 30: [mem 0xd2d00000-0xd2d1ffff pref]
[    0.654107] pci 0000:01:00.0: supports D1 D2
[    0.654109] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.654134] pci 0000:01:00.0: PME# disabled
[    0.654289] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.654295] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.654300] pci 0000:00:1c.0:   bridge window [mem 0xd2d00000-0xd40fffff]
[    0.654309] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.654373] pci 0000:00:1c.1: PCI bridge to [bus 02-03]
[    0.654378] pci 0000:00:1c.1:   bridge window [io  0xc000-0xcfff]
[    0.654384] pci 0000:00:1c.1:   bridge window [mem 0xd1900000-0xd2cfffff]
[    0.654392] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.654558] pci 0000:04:00.0: [8086:4232] type 0 class 0x000280
[    0.654673] pci 0000:04:00.0: reg 10: [mem 0xd0500000-0xd0501fff 64bit]
[    0.655042] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.655075] pci 0000:04:00.0: PME# disabled
[    0.655191] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.655197] pci 0000:00:1c.2:   bridge window [io  0xb000-0xbfff]
[    0.655202] pci 0000:00:1c.2:   bridge window [mem 0xd0500000-0xd18fffff]
[    0.655210] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.655265] pci 0000:05:03.0: [1180:0832] type 0 class 0x000c00
[    0.655292] pci 0000:05:03.0: reg 10: [mem 0xd4100000-0xd41007ff]
[    0.655383] pci 0000:05:03.0: PME# supported from D0 D3hot D3cold
[    0.655389] pci 0000:05:03.0: PME# disabled
[    0.655415] pci 0000:05:03.1: [1180:0822] type 0 class 0x000805
[    0.655438] pci 0000:05:03.1: reg 10: [mem 0xd4100900-0xd41009ff]
[    0.655530] pci 0000:05:03.1: supports D1 D2
[    0.655533] pci 0000:05:03.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.655538] pci 0000:05:03.1: PME# disabled
[    0.655561] pci 0000:05:03.2: [1180:0592] type 0 class 0x000880
[    0.655585] pci 0000:05:03.2: reg 10: [mem 0xd4100800-0xd41008ff]
[    0.655676] pci 0000:05:03.2: supports D1 D2
[    0.655679] pci 0000:05:03.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.655684] pci 0000:05:03.2: PME# disabled
[    0.655756] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.655762] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.655768] pci 0000:00:1e.0:   bridge window [mem 0xd4100000-0xd41fffff]
[    0.655776] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.655780] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.655782] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.655785] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.655788] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.655791] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.655794] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.655797] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.655800] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.655802] pci 0000:00:1e.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.655805] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    0.655836] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.655971] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.655998] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.656044] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.656080] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.656212] \_SB_.PCI0:_OSC invalid UUID
[    0.656214] _OSC request data:1 1f 1f 
[    0.656219]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.656259] \_SB_.PCI0:_OSC invalid UUID
[    0.656261] _OSC request data:1 0 1d 
[    0.656266]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    0.656268] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.662535] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.662589] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[    0.662639] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.662689] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.662739] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.662789] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.662838] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.662893] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.663016] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.663031] vgaarb: loaded
[    0.663032] vgaarb: bridge control possible 0000:00:02.0
[    0.663248] SCSI subsystem initialized
[    0.663266] libata version 3.00 loaded.
[    0.663266] usbcore: registered new interface driver usbfs
[    0.663266] usbcore: registered new interface driver hub
[    0.663266] usbcore: registered new device driver usb
[    0.663266] PCI: Using ACPI for IRQ routing
[    0.674777] PCI: pci_cache_line_size set to 64 bytes
[    0.674896] reserve RAM buffer: 000000000009bc00 - 000000000009ffff 
[    0.674899] reserve RAM buffer: 00000000b5ea8000 - 00000000b7ffffff 
[    0.674903] reserve RAM buffer: 00000000b6000000 - 00000000b7ffffff 
[    0.675022] NetLabel: Initializing
[    0.675024] NetLabel:  domain hash size = 128
[    0.675025] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.675040] NetLabel:  unlabeled traffic allowed by default
[    0.675085] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.675093] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.675098] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.680061] Switching to clocksource hpet
[    0.683942] Switched to NOHz mode on CPU #0
[    0.683992] Switched to NOHz mode on CPU #1
[    0.687853] AppArmor: AppArmor Filesystem Enabled
[    0.687892] pnp: PnP ACPI init
[    0.687911] ACPI: bus type pnp registered
[    0.688226] pnp 00:00: [bus 00-ff]
[    0.688229] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.688232] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.688234] pnp 00:00: [io  0x0d00-0xffff window]
[    0.688237] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.688239] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.688241] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.688244] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.688246] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.688249] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.688251] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.688254] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.688256] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.688258] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.688261] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.688263] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.688265] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.688268] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.688270] pnp 00:00: [mem 0xc0000000-0xfebfffff window]
[    0.688273] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.688352] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.688366] pnp 00:01: [io  0x0000-0x001f]
[    0.688368] pnp 00:01: [io  0x0081-0x0091]
[    0.688370] pnp 00:01: [io  0x0093-0x009f]
[    0.688372] pnp 00:01: [io  0x00c0-0x00df]
[    0.688374] pnp 00:01: [dma 4]
[    0.688402] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.688413] pnp 00:02: [mem 0xff000000-0xffffffff]
[    0.688435] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.688518] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.688584] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.688589] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.688601] pnp 00:04: [io  0x00f0]
[    0.688615] pnp 00:04: [irq 13]
[    0.688643] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.688659] pnp 00:05: [io  0x002e-0x002f]
[    0.688662] pnp 00:05: [io  0x004e-0x004f]
[    0.688664] pnp 00:05: [io  0x0061]
[    0.688665] pnp 00:05: [io  0x0063]
[    0.688667] pnp 00:05: [io  0x0065]
[    0.688669] pnp 00:05: [io  0x0067]
[    0.688671] pnp 00:05: [io  0x0070]
[    0.688673] pnp 00:05: [io  0x0080]
[    0.688674] pnp 00:05: [io  0x0092]
[    0.688676] pnp 00:05: [io  0x00b2-0x00b3]
[    0.688678] pnp 00:05: [io  0x0680-0x069f]
[    0.688680] pnp 00:05: [io  0x1000-0x100f]
[    0.688682] pnp 00:05: [io  0x0800-0x0803]
[    0.688684] pnp 00:05: [io  0x0400-0x047f]
[    0.688686] pnp 00:05: [io  0x0500-0x053f]
[    0.688688] pnp 00:05: [io  0x164e-0x164f]
[    0.688741] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.688745] system 00:05: [io  0x1000-0x100f] has been reserved
[    0.688747] system 00:05: [io  0x0800-0x0803] has been reserved
[    0.688750] system 00:05: [io  0x0400-0x047f] has been reserved
[    0.688753] system 00:05: [io  0x0500-0x053f] has been reserved
[    0.688756] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.688759] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.688770] pnp 00:06: [io  0x0070-0x0077]
[    0.688776] pnp 00:06: [irq 8]
[    0.688804] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.688816] pnp 00:07: [io  0x0060]
[    0.688818] pnp 00:07: [io  0x0064]
[    0.688824] pnp 00:07: [irq 1]
[    0.688850] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.688864] pnp 00:08: [irq 12]
[    0.688889] pnp 00:08: Plug and Play ACPI device, IDs SNY9008 PNP0f13 (active)
[    0.689087] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.689090] pnp 00:09: [mem 0xfed14000-0xfed17fff]
[    0.689092] pnp 00:09: [mem 0xfed18000-0xfed18fff]
[    0.689094] pnp 00:09: [mem 0xfed19000-0xfed19fff]
[    0.689097] pnp 00:09: [mem 0xe0000000-0xefffffff]
[    0.689099] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.689101] pnp 00:09: [mem 0xfeb00000-0xfeb03fff]
[    0.689103] pnp 00:09: [mem 0xfed45000-0xfed8ffff]
[    0.689173] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.689177] system 00:09: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.689180] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.689183] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.689186] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.689189] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.689192] system 00:09: [mem 0xfeb00000-0xfeb03fff] has been reserved
[    0.689195] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.689199] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.704602] pnp: PnP ACPI: found 10 devices
[    0.704604] ACPI: ACPI bus type pnp unregistered
[    0.710775] PCI: max bus depth: 1 pci_try_num: 2
[    0.710830] pci 0000:00:1c.2: BAR 15: assigned [mem 0xd4300000-0xd44fffff 64bit pref]
[    0.710837] pci 0000:00:1c.1: BAR 15: assigned [mem 0xd4500000-0xd46fffff 64bit pref]
[    0.710844] pci 0000:00:1c.0: BAR 15: assigned [mem 0xd4700000-0xd48fffff 64bit pref]
[    0.710848] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.710851] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.710859] pci 0000:00:1c.0:   bridge window [mem 0xd2d00000-0xd40fffff]
[    0.710864] pci 0000:00:1c.0:   bridge window [mem 0xd4700000-0xd48fffff 64bit pref]
[    0.710873] pci 0000:00:1c.1: PCI bridge to [bus 02-03]
[    0.710876] pci 0000:00:1c.1:   bridge window [io  0xc000-0xcfff]
[    0.710883] pci 0000:00:1c.1:   bridge window [mem 0xd1900000-0xd2cfffff]
[    0.710889] pci 0000:00:1c.1:   bridge window [mem 0xd4500000-0xd46fffff 64bit pref]
[    0.710897] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.710901] pci 0000:00:1c.2:   bridge window [io  0xb000-0xbfff]
[    0.710908] pci 0000:00:1c.2:   bridge window [mem 0xd0500000-0xd18fffff]
[    0.710913] pci 0000:00:1c.2:   bridge window [mem 0xd4300000-0xd44fffff 64bit pref]
[    0.710922] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.710924] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.710931] pci 0000:00:1e.0:   bridge window [mem 0xd4100000-0xd41fffff]
[    0.710937] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.710960] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.710966] pci 0000:00:1c.0: setting latency timer to 64
[    0.710979] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.710984] pci 0000:00:1c.1: setting latency timer to 64
[    0.710995] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.711001] pci 0000:00:1c.2: setting latency timer to 64
[    0.711010] pci 0000:00:1e.0: setting latency timer to 64
[    0.711014] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.711017] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.711020] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.711022] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.711025] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.711027] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.711030] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.711032] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.711035] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.711037] pci_bus 0000:00: resource 13 [mem 0xc0000000-0xfebfffff]
[    0.711040] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.711043] pci_bus 0000:01: resource 1 [mem 0xd2d00000-0xd40fffff]
[    0.711045] pci_bus 0000:01: resource 2 [mem 0xd4700000-0xd48fffff 64bit pref]
[    0.711048] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.711051] pci_bus 0000:02: resource 1 [mem 0xd1900000-0xd2cfffff]
[    0.711053] pci_bus 0000:02: resource 2 [mem 0xd4500000-0xd46fffff 64bit pref]
[    0.711056] pci_bus 0000:04: resource 0 [io  0xb000-0xbfff]
[    0.711059] pci_bus 0000:04: resource 1 [mem 0xd0500000-0xd18fffff]
[    0.711061] pci_bus 0000:04: resource 2 [mem 0xd4300000-0xd44fffff 64bit pref]
[    0.711064] pci_bus 0000:05: resource 1 [mem 0xd4100000-0xd41fffff]
[    0.711067] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.711069] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.711071] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.711074] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.711076] pci_bus 0000:05: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.711079] pci_bus 0000:05: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.711081] pci_bus 0000:05: resource 10 [mem 0x000dc000-0x000dffff]
[    0.711084] pci_bus 0000:05: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.711086] pci_bus 0000:05: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.711089] pci_bus 0000:05: resource 13 [mem 0xc0000000-0xfebfffff]
[    0.711132] NET: Registered protocol family 2
[    0.711313] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.712708] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.716747] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.717236] TCP: Hash tables configured (established 524288 bind 65536)
[    0.717238] TCP reno registered
[    0.717250] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.717292] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.717467] NET: Registered protocol family 1
[    0.717489] pci 0000:00:02.0: Boot video device
[    0.717916] PCI: CLS 64 bytes, default 64
[    0.717919] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.717922] Placing 64MB software IO TLB between ffff8800b1ea8000 - ffff8800b5ea8000
[    0.717925] software IO TLB at phys 0xb1ea8000 - 0xb5ea8000
[    0.718320] audit: initializing netlink socket (disabled)
[    0.718334] type=2000 audit(1323029486.712:1): initialized
[    0.751561] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.774612] VFS: Disk quotas dquot_6.5.2
[    0.774680] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.775344] fuse init (API version 7.16)
[    0.775435] msgmni has been set to 7601
[    0.775868] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.775901] io scheduler noop registered
[    0.775903] io scheduler deadline registered
[    0.775949] io scheduler cfq registered (default)
[    0.776089] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.776153] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.776240] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.776298] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.776379] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.776436] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.776535] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.776560] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.776607] intel_idle: MWAIT substates: 0x22220
[    0.776610] intel_idle: does not run on family 6 model 15
[    0.777876] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.778850] ACPI: AC Adapter [ADP1] (on-line)
[    0.778966] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.780772] ACPI: Lid Switch [LID0]
[    0.780815] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.780820] ACPI: Power Button [PWRB]
[    0.780854] ACPI: acpi_idle registered with cpuidle
[    0.781769] Monitor-Mwait will be used to enter C-1 state
[    0.781803] Monitor-Mwait will be used to enter C-2 state
[    0.781836] Monitor-Mwait will be used to enter C-3 state
[    0.781844] Marking TSC unstable due to TSC halts in idle
[    0.799057] thermal LNXTHERM:00: registered as thermal_zone0
[    0.799060] ACPI: Thermal Zone [TZ00] (56 C)
[    0.800066] ACPI: Invalid active0 threshold
[    0.801036] thermal LNXTHERM:01: registered as thermal_zone1
[    0.801039] ACPI: Thermal Zone [TZ01] (56 C)
[    0.801066] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.801083] ERST: Table is not found!
[    0.801153] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.843705] ACPI: Battery Slot [BAT0] (battery present)
[    0.861096] Linux agpgart interface v0.103
[    0.861208] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[    0.861403] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    0.862523] agpgart-intel 0000:00:00.0: detected 131072K stolen memory
[    0.862653] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    0.863817] brd: module loaded
[    0.864386] loop: module loaded
[    0.864857] Fixed MDIO Bus: probed
[    0.864883] PPP generic driver version 2.4.2
[    0.864924] tun: Universal TUN/TAP device driver, 1.6
[    0.864926] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.865002] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.865035] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.865054] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.865059] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.865092] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.865127] ehci_hcd 0000:00:1a.7: debug port 1
[    0.869027] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.869046] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xd4204c00
[    0.884017] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.884133] hub 1-0:1.0: USB hub found
[    0.884138] hub 1-0:1.0: 6 ports detected
[    0.884226] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.884239] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.884243] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.884279] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.884310] ehci_hcd 0000:00:1d.7: debug port 1
[    0.888193] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.888208] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd4204800
[    0.904018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.904116] hub 2-0:1.0: USB hub found
[    0.904120] hub 2-0:1.0: 6 ports detected
[    0.904199] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.904213] uhci_hcd: USB Universal Host Controller Interface driver
[    0.904236] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.904244] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.904248] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.904293] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.904337] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e0e0
[    0.904453] hub 3-0:1.0: USB hub found
[    0.904458] hub 3-0:1.0: 2 ports detected
[    0.904531] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.904539] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.904543] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.904576] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.904615] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e0c0
[    0.904739] hub 4-0:1.0: USB hub found
[    0.904744] hub 4-0:1.0: 2 ports detected
[    0.904813] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.904820] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.904824] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.904864] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.904894] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000e0a0
[    0.905012] hub 5-0:1.0: USB hub found
[    0.905016] hub 5-0:1.0: 2 ports detected
[    0.905087] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.905094] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.905098] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.905130] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.905161] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e080
[    0.905278] hub 6-0:1.0: USB hub found
[    0.905283] hub 6-0:1.0: 2 ports detected
[    0.905348] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.905355] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.905359] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.905398] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.905430] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e060
[    0.905551] hub 7-0:1.0: USB hub found
[    0.905556] hub 7-0:1.0: 2 ports detected
[    0.905624] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.905631] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.905635] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.905667] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.905707] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e040
[    0.905831] hub 8-0:1.0: USB hub found
[    0.905835] hub 8-0:1.0: 2 ports detected
[    0.905943] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.910472] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.910480] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.910600] mousedev: PS/2 mouse device common for all mice
[    0.910727] rtc_cmos 00:06: RTC can wake from S4
[    0.910846] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.910878] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.910983] device-mapper: uevent: version 1.0.3
[    0.911054] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.911118] cpuidle: using governor ladder
[    0.911211] cpuidle: using governor menu
[    0.911213] EFI Variables Facility v0.08 2004-May-17
[    0.911478] TCP cubic registered
[    0.911606] NET: Registered protocol family 10
[    0.912147] NET: Registered protocol family 17
[    0.912163] Registering the dns_resolver key type
[    0.912266] PM: Hibernation image not present or could not be loaded.
[    0.912278] registered taskstats version 1
[    0.930237]   Magic number: 7:76:194
[    0.930359] rtc_cmos 00:06: setting system clock to 2011-12-04 20:11:27 UTC (1323029487)
[    0.930910] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.930912] EDD information not available.
[    0.932963] Freeing unused kernel memory: 984k freed
[    0.933257] Write protecting the kernel read-only data: 10240k
[    0.933513] Freeing unused kernel memory: 20k freed
[    0.936357] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.938884] Freeing unused kernel memory: 1396k freed
[    0.958591] udevd[85]: starting version 173
[    1.017341] ahci 0000:00:1f.2: version 3.0
[    1.017359] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.017422] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.017492] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.017497] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc ems 
[    1.017503] ahci 0000:00:1f.2: setting latency timer to 64
[    1.027451] scsi0 : ahci
[    1.030276] scsi1 : ahci
[    1.033254] scsi2 : ahci
[    1.034915] scsi3 : ahci
[    1.035056] ata1: SATA max UDMA/133 abar m2048@0xd4204000 port 0xd4204100 irq 43
[    1.035061] ata2: SATA max UDMA/133 abar m2048@0xd4204000 port 0xd4204180 irq 43
[    1.035063] ata3: DUMMY
[    1.035065] ata4: DUMMY
[    1.042678] sdhci: Secure Digital Host Controller Interface driver
[    1.042682] sdhci: Copyright(c) Pierre Ossman
[    1.066465] sky2: driver version 1.28
[    1.066511] sky2 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.066526] sky2 0000:01:00.0: setting latency timer to 64
[    1.067817] sky2 0000:01:00.0: Yukon-2 EC Ultra chip revision 3
[    1.068739] sky2 0000:01:00.0: irq 44 for MSI/MSI-X
[    1.071715] sky2 0000:01:00.0: eth0: addr 00:1d:ba:84:64:26
[    1.196097] usb 1-2: new high speed USB device number 2 using ehci_hcd
[    1.352053] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.352874] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.352880] ata1.00: ATA-8: ST9250827AS, 3.AAB, max UDMA/133
[    1.352883] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.353812] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.353816] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.353822] ata1.00: configured for UDMA/133
[    1.353988] scsi 0:0:0:0: Direct-Access     ATA      ST9250827AS      3.AA PQ: 0 ANSI: 5
[    1.354177] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.354243] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.354344] sd 0:0:0:0: [sda] Write Protect is off
[    1.354348] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.354403] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.356084] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.368832] ata2.00: ATAPI: Optiarc DVD RW AD-7560S, SS03, max UDMA/100
[    1.382504] ata2.00: configured for UDMA/100
[    1.384195] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7560S  SS03 PQ: 0 ANSI: 5
[    1.387917] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.387921] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.388056] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.388120] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.420112]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 >
[    1.420593] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.421385] sdhci-pci 0000:05:03.1: SDHCI controller found [1180:0822] (rev 22)
[    1.421403] sdhci-pci 0000:05:03.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.421438] sdhci-pci 0000:05:03.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.421468] mmc0: no vmmc regulator found
[    1.421497] Registered led device: mmc0::
[    1.421549] mmc0: SDHCI controller on PCI [0000:05:03.1] using DMA
[    1.423828] firewire_ohci 0000:05:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.488121] firewire_ohci: Added fw-ohci device 0000:05:03.0, OHCI v1.0, 4 IR + 4 IT contexts, quirks 0x1
[    1.988146] firewire_core: created device fw0: GUID 0800460302da9714, S400
[    7.186696] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   26.066404] udevd[321]: starting version 173
[   26.105424] lp: driver loaded but no devices found
[   26.137922] Adding 4194300k swap on /dev/sda5.  Priority:-1 extents:1 across:4194300k 
[   26.209415] [drm] Initialized drm 1.1.0 20060810
[   26.290035] sony_laptop: Sony Notebook Control Driver v0.6
[   26.298967] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.298974] i915 0000:00:02.0: setting latency timer to 64
[   26.334594] cfg80211: Calling CRDA to update world regulatory domain
[   26.417270] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[   26.417278] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   26.417280] [drm] Driver supports precise vblank timestamp query.
[   26.417333] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   26.421855] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/SNY5001:00/input/input3
[   26.427971] input: Sony Vaio Jogdial as /devices/virtual/input/input4
[   26.429123] sony_laptop: brightness ignored, must be controlled by ACPI video driver
[   26.445150] type=1400 audit(1323047513.011:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=556 comm="apparmor_parser"
[   26.445431] type=1400 audit(1323047513.011:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=556 comm="apparmor_parser"
[   26.445623] type=1400 audit(1323047513.011:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=556 comm="apparmor_parser"
[   26.548379] fbcon: inteldrmfb (fb0) is primary device
[   26.548463] Console: switching to colour frame buffer device 160x50
[   26.548490] fb0: inteldrmfb frame buffer device
[   26.548492] drm: registered panic notifier
[   26.587681] acpi device:15: registered as cooling_device2
[   26.590204] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   26.590313] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   26.590435] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   26.590498] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   26.590585] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   26.590619] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   26.595607] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   26.595611] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   26.595703] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.595714] iwlagn 0000:04:00.0: setting latency timer to 64
[   26.595751] iwlagn 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   26.619077] iwlagn 0000:04:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   26.619081] iwlagn 0000:04:00.0: Device SKU: 0Xb
[   26.621432] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   26.621525] iwlagn 0000:04:00.0: irq 47 for MSI/MSI-X
[   26.653298] Linux video capture interface: v2.00
[   26.654105] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:18b3)
[   26.660368] input: UVC Camera (05ca:18b3) as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input6
[   26.660494] usbcore: registered new interface driver uvcvideo
[   26.660497] USB Video Class driver (v1.1.0)
[   26.675922] ip_tables: (C) 2000-2006 Netfilter Core Team
[   26.678486] hda_codec: ALC262: SKU not ready 0x411111f0
[   26.678567] hda_codec: ALC262: BIOS auto-probing.
[   26.696939] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   26.697782] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   26.725640] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   26.734367] cfg80211: World regulatory domain updated:
[   26.734372] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   26.734375] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.734378] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.734381] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.734384] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.734387] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.782219] iwlagn 0000:04:00.0: loaded firmware version 8.83.5.1 build 33692
[   26.782507] Registered led device: phy0-led
[   26.782540] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   26.811979] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   27.177902] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04711/0xa00000/0x20000
[   27.222619] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   28.091657] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro
[   29.003784] EXT4-fs (sda6): warning: maximal mount count reached, running e2fsck is recommended
[   29.004169] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   29.063221] EXT4-fs (sda7): warning: maximal mount count reached, running e2fsck is recommended
[   29.063505] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   29.245369] ppdev: user-space parallel port driver
[   29.257700] type=1400 audit(1323047515.823:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=982 comm="apparmor_parser"
[   29.261620] type=1400 audit(1323047515.827:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=982 comm="apparmor_parser"
[   29.274634] type=1400 audit(1323047515.839:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=992 comm="apparmor_parser"
[   29.281078] type=1400 audit(1323047515.847:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=992 comm="apparmor_parser"
[   29.281274] type=1400 audit(1323047515.847:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=992 comm="apparmor_parser"
[   29.282324] type=1400 audit(1323047515.847:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=991 comm="apparmor_parser"
[   29.314190] type=1400 audit(1323047515.879:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=998 comm="apparmor_parser"
[   29.397476] sky2 0000:01:00.0: eth0: enabling interface
[   29.398552] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.575368] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.656858] init: failsafe main process (924) killed by TERM signal
[   29.658969] init: apport pre-start process (1076) terminated with status 1
[   29.689523] init: apport post-stop process (1104) terminated with status 1
[   29.957998] Bluetooth: Core ver 2.16
[   29.958026] NET: Registered protocol family 31
[   29.958028] Bluetooth: HCI device and connection manager initialized
[   29.958031] Bluetooth: HCI socket layer initialized
[   29.958033] Bluetooth: L2CAP socket layer initialized
[   29.958080] Bluetooth: SCO socket layer initialized
[   29.963042] Bluetooth: RFCOMM TTY layer initialized
[   29.963050] Bluetooth: RFCOMM socket layer initialized
[   29.963052] Bluetooth: RFCOMM ver 1.11
[   29.979328] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.979332] Bluetooth: BNEP filters: protocol multicast
[   30.979744] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
[   30.982818] EXT4-fs (sda6): re-mounted. Opts: commit=0
[   30.986160] EXT4-fs (sda7): re-mounted. Opts: commit=0
[   31.416609] init: plymouth-stop pre-start process (1492) terminated with status 1
[   32.299088] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
[   32.308271] EXT4-fs (sda6): re-mounted. Opts: commit=0
[   32.313670] EXT4-fs (sda7): re-mounted. Opts: commit=0
[   37.243564] wlan0: authenticate with 00:1b:8f:89:a4:20 (try 1)
[   37.244935] wlan0: authenticated
[   37.249609] wlan0: associate with 00:1b:8f:89:a4:20 (try 1)
[   37.251914] wlan0: RX AssocResp from 00:1b:8f:89:a4:20 (capab=0x421 status=0 aid=229)
[   37.251920] wlan0: associated
[   37.255928] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   47.760088] wlan0: no IPv6 routers present
[   82.028441] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:07:eb:4c:e4:42:08:00 SRC=173.225.132.34 DST=172.16.130.22 LEN=46 TOS=0x00 PREC=0x00 TTL=48 ID=12282 DF PROTO=TCP SPT=443 DPT=59609 WINDOW=17680 RES=0x00 ACK PSH URGP=0 
[   82.029331] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:07:eb:4c:e4:42:08:00 SRC=173.225.132.34 DST=172.16.130.22 LEN=56 TOS=0x00 PREC=0x00 TTL=48 ID=12283 DF PROTO=TCP SPT=443 DPT=59609 WINDOW=17680 RES=0x00 ACK PSH URGP=0 
[   82.469336] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:07:eb:4c:e4:42:08:00 SRC=173.225.132.34 DST=172.16.130.22 LEN=62 TOS=0x00 PREC=0x00 TTL=48 ID=12284 DF PROTO=TCP SPT=443 DPT=59609 WINDOW=17680 RES=0x00 ACK PSH URGP=0 
[   82.995859] sky2 0000:01:00.0: eth0: disabling interface
[   83.204048] wlan0: deauthenticating from 00:1b:8f:89:a4:20 by local choice (reason=3)
[   83.221857] cfg80211: All devices are disconnected, going to restore regulatory settings
[   83.221866] cfg80211: Restoring regulatory settings
[   83.221872] cfg80211: Calling CRDA to update world regulatory domain
[   83.244110] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   83.244115] cfg80211: World regulatory domain updated:
[   83.244117] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   83.244121] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   83.244124] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   83.244127] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   83.244130] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   83.244133] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   84.923204] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
[   84.926279] EXT4-fs (sda6): re-mounted. Opts: commit=0
[   84.928893] EXT4-fs (sda7): re-mounted. Opts: commit=0
[   85.854962] init: anacron main process (1100) killed by TERM signal
[   86.493689] PM: Syncing filesystems ... done.
[   86.622614] PM: Preparing system for mem sleep
[   86.736350] Freezing user space processes ... (elapsed 0.01 seconds) done.
[   86.752140] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[   86.768125] PM: Entering mem sleep
[   86.768140] Suspending console(s) (use no_console_suspend to debug)
[   86.768931] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[   86.769754] sd 0:0:0:0: [sda] Stopping disk
[   86.818255] ACPI handle has no context!
[   86.818265] sdhci-pci 0000:05:03.1: PCI INT B disabled
[   86.818273] ACPI handle has no context!
[   86.818446] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[   86.818460] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[   86.818472] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[   86.818483] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[   86.818556] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[   86.818568] uhci_hcd 0000:00:1a.2: PCI INT C disabled
[   86.818582] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[   86.818595] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[   86.824056] ACPI handle has no context!
[   87.145193] PM: suspend of drv:sd dev:0:0:0:0 complete after 376.266 msecs
[   87.145210] PM: suspend of drv:scsi dev:target0:0:0 complete after 376.251 msecs
[   87.145223] PM: suspend of drv:scsi dev:host0 complete after 376.218 msecs
[   87.160024] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 341.634 msecs
[   87.228127] HDA Intel 0000:00:1b.0: PCI INT A disabled
[   87.244023] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 425.521 msecs
[   87.244042] PM: suspend of drv: dev:pci0000:00 complete after 424.953 msecs
[   87.244053] PM: suspend of devices complete after 475.384 msecs
[   87.244056] PM: suspend devices took 0.476 seconds
[   87.416101] PM: late suspend of drv:sky2 dev:0000:01:00.0 complete after 156.050 msecs
[   87.448269] PM: late suspend of devices complete after 204.209 msecs
[   87.448496] ACPI: Preparing to enter system sleep state S3
[   87.449199] PM: Saving platform NVS memory
[   87.449202] Disabling non-boot CPUs ...
[   87.552037] CPU 1 is now offline
[   87.552442] Extended CMOS year: 2000
[   87.552442] ACPI: Low-level resume complete
[   87.552442] PM: Restoring platform NVS memory
[   87.552442] Extended CMOS year: 2000
[   87.552442] Enabling non-boot CPUs ...
[   87.552442] Booting Node 0 Processor 1 APIC 0x1
[   87.552442] smpboot cpu 1: start_ip = 96000
[   87.644126] Switched to NOHz mode on CPU #1
[   87.644756] CPU1 is up
[   87.645728] ACPI: Waking up from system sleep state S3
[   87.852274] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[   87.852304] pci 0000:00:02.1: restoring config space at offset 0x4 (was 0x4, writing 0xd0400004)
[   87.852309] pci 0000:00:02.1: restoring config space at offset 0x1 (was 0x900000, writing 0x900007)
[   87.852326] uhci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[   87.852341] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x8 (was 0x1, writing 0xe0e1)
[   87.852355] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
[   87.852378] uhci_hcd 0000:00:1a.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[   87.852392] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x8 (was 0x1, writing 0xe0c1)
[   87.852407] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
[   87.852429] uhci_hcd 0000:00:1a.2: restoring config space at offset 0xf (was 0x300, writing 0x305)
[   87.852443] uhci_hcd 0000:00:1a.2: restoring config space at offset 0x8 (was 0x1, writing 0xe0a1)
[   87.852458] uhci_hcd 0000:00:1a.2: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
[   87.852487] ehci_hcd 0000:00:1a.7: restoring config space at offset 0xf (was 0x300, writing 0x305)
[   87.852508] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x4 (was 0x0, writing 0xd4204c00)
[   87.852517] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[   87.852553] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x103)
[   87.852574] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xc0000004, writing 0xd4200004)
[   87.852579] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[   87.852587] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[   87.852621] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[   87.852634] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x1fff1, writing 0xd481d471)
[   87.852646] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[   87.852653] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[   87.852708] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[   87.852721] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x1fff1, writing 0xd461d451)
[   87.852733] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[   87.852741] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[   87.852794] pcieport 0000:00:1c.2: restoring config space at offset 0xf (was 0x300, writing 0x30b)
[   87.852807] pcieport 0000:00:1c.2: restoring config space at offset 0x9 (was 0x1fff1, writing 0xd441d431)
[   87.852820] pcieport 0000:00:1c.2: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[   87.852827] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[   87.852874] uhci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[   87.852888] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x8 (was 0x1, writing 0xe081)
[   87.852903] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
[   87.852925] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x205)
[   87.852939] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x8 (was 0x1, writing 0xe061)
[   87.852954] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
[   87.852976] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x30b)
[   87.852990] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x8 (was 0x1, writing 0xe041)
[   87.853005] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
[   87.853034] ehci_hcd 0000:00:1d.7: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[   87.853055] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x4 (was 0x0, writing 0xd4204800)
[   87.853063] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[   87.853112] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[   87.853214] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[   87.853330] sky2 0000:01:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[   87.853341] sky2 0000:01:00.0: restoring config space at offset 0xc (was 0x0, writing 0xd2d00000)
[   87.853359] sky2 0000:01:00.0: restoring config space at offset 0x6 (was 0x1, writing 0xd001)
[   87.853368] sky2 0000:01:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xd2d20004)
[   87.853375] sky2 0000:01:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[   87.853384] sky2 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[   87.853505] iwlagn 0000:04:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[   87.853542] iwlagn 0000:04:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xd0500004)
[   87.853550] iwlagn 0000:04:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[   87.853562] iwlagn 0000:04:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[   87.853639] firewire_ohci 0000:05:03.0: restoring config space at offset 0xf (was 0x4020100, writing 0x402010b)
[   87.853661] firewire_ohci 0000:05:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xd4100000)
[   87.853667] firewire_ohci 0000:05:03.0: restoring config space at offset 0x3 (was 0x800000, writing 0x802010)
[   87.853675] firewire_ohci 0000:05:03.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[   87.853700] sdhci-pci 0000:05:03.1: restoring config space at offset 0xf (was 0x200, writing 0x204)
[   87.853722] sdhci-pci 0000:05:03.1: restoring config space at offset 0x4 (was 0x0, writing 0xd4100900)
[   87.853728] sdhci-pci 0000:05:03.1: restoring config space at offset 0x3 (was 0x800000, writing 0x802010)
[   87.853735] sdhci-pci 0000:05:03.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[   87.853761] pci 0000:05:03.2: restoring config space at offset 0xf (was 0x200, writing 0x204)
[   87.853783] pci 0000:05:03.2: restoring config space at offset 0x4 (was 0x0, writing 0xd4100800)
[   87.853788] pci 0000:05:03.2: restoring config space at offset 0x3 (was 0x800000, writing 0x802010)
[   87.853796] pci 0000:05:03.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[   87.854371] PM: early resume of devices complete after 2.263 msecs
[   87.854475] i915 0000:00:02.0: setting latency timer to 64
[   87.859805] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   87.859813] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[   87.859842] usb usb3: root hub lost power or was reset
[   87.859859] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   87.859866] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[   87.859893] usb usb4: root hub lost power or was reset
[   87.859908] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[   87.859915] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[   87.859942] usb usb5: root hub lost power or was reset
[   87.859959] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[   87.859966] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[   87.860038] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   87.860044] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   87.860096] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   87.860154] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   87.860161] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   87.860188] usb usb6: root hub lost power or was reset
[   87.860203] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   87.860209] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   87.860236] usb usb7: root hub lost power or was reset
[   87.860251] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   87.860257] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[   87.860285] usb usb8: root hub lost power or was reset
[   87.860301] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   87.860308] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   87.860356] pci 0000:00:1e.0: setting latency timer to 64
[   87.860376] ahci 0000:00:1f.2: setting latency timer to 64
[   87.860508] sdhci-pci 0000:05:03.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   87.860512] sdhci-pci 0000:05:03.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   87.861243] sd 0:0:0:0: [sda] Starting disk
[   87.906705] Extended CMOS year: 2000
[   87.924133] firewire_core: skipped bus generations, destroying all nodes
[   87.980132] PM: resume of drv:hub dev:3-0:1.0 complete after 119.460 msecs
[   87.980140] PM: resume of drv: dev:ep_00 complete after 119.433 msecs
[   87.980147] PM: resume of drv:hub dev:8-0:1.0 complete after 119.083 msecs
[   87.980151] PM: resume of drv:hub dev:4-0:1.0 complete after 119.398 msecs
[   87.980156] PM: resume of drv: dev:ep_00 complete after 119.054 msecs
[   87.980160] PM: resume of drv: dev:ep_00 complete after 119.376 msecs
[   87.980163] PM: resume of drv:hub dev:7-0:1.0 complete after 119.178 msecs
[   87.980167] PM: resume of drv:hub dev:5-0:1.0 complete after 119.338 msecs
[   87.980171] PM: resume of drv: dev:ep_00 complete after 119.150 msecs
[   87.980175] PM: resume of drv: dev:ep_00 complete after 119.310 msecs
[   87.980178] PM: resume of drv:hub dev:6-0:1.0 complete after 119.272 msecs
[   87.980181] PM: resume of drv: dev:ep_81 complete after 119.492 msecs
[   87.980186] PM: resume of drv: dev:ep_00 complete after 119.242 msecs
[   87.980188] PM: resume of drv: dev:ep_81 complete after 119.106 msecs
[   87.980192] PM: resume of drv: dev:ep_81 complete after 119.190 msecs
[   87.980195] PM: resume of drv: dev:ep_81 complete after 119.427 msecs
[   87.980198] PM: resume of drv: dev:ep_81 complete after 119.273 msecs
[   87.980201] PM: resume of drv: dev:ep_81 complete after 119.354 msecs
[   87.996657] PM: resume of drv:i915 dev:0000:00:02.0 complete after 142.189 msecs
[   88.188047] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   88.214712] ata2.00: configured for UDMA/100
[   88.424085] firewire_core: rediscovered device fw0
[   89.524078] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   89.577349] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[   89.577353] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[   89.577356] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[   89.578178] ACPI Error: Field [CMDX] at 224 exceeds Buffer [SCBF] size 168 (bits) (20110413/dsopcode-236)
[   89.578185] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SATA.GTFB] (Node ffff8801391616b8), AE_AML_BUFFER_LIMIT (20110413/psparse-536)
[   89.578194] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SATA.SPT0._SDD] (Node ffff880139161578), AE_AML_BUFFER_LIMIT (20110413/psparse-536)
[   89.578203] ata1.00: ACPI _SDD failed (AE 0x300a)
[   89.578206] ata1.00: revalidation failed (errno=-5)
[   94.844080] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   94.844525] ACPI Error: Field [CMDX] at 224 exceeds Buffer [SCBF] size 168 (bits) (20110413/dsopcode-236)
[   94.844532] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SATA.GTFB] (Node ffff8801391616b8), AE_AML_BUFFER_LIMIT (20110413/psparse-536)
[   94.844539] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SATA.SPT0._SDD] (Node ffff880139161578), AE_AML_BUFFER_LIMIT (20110413/psparse-536)
[   94.844549] ata1.00: ACPI _SDD failed (AE 0x300a)
[   94.844550] ata1.00: ACPI: failed the second time, disabled
[   94.844997] ata1.00: configured for UDMA/133
[   94.897472] PM: resume of drv:sd dev:0:0:0:0 complete after 7036.228 msecs
[   94.897502] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 6990.654 msecs
[   94.899382] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 7038.099 msecs
[   94.899537] PM: resume of devices complete after 7045.098 msecs
[   94.899788] PM: resume devices took 7.044 seconds
[   94.899829] PM: Finishing wakeup.
[   94.899831] Restarting tasks ... done.
[   94.947484] video LNXVIDEO:00: Restoring backlight state
[   96.504232] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
[   96.507581] EXT4-fs (sda6): re-mounted. Opts: commit=0
[   96.510345] EXT4-fs (sda7): re-mounted. Opts: commit=0
[   96.545754] sky2 0000:01:00.0: eth0: enabling interface
[   96.546549] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   96.598395] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  104.360756] wlan0: authenticate with 00:1b:8f:89:a4:20 (try 1)
[  104.362132] wlan0: authenticated
[  104.363297] wlan0: associate with 00:1b:8f:89:a4:20 (try 1)
[  104.364814] wlan0: RX AssocResp from 00:1b:8f:89:a4:20 (capab=0x421 status=0 aid=230)
[  104.364819] wlan0: associated
[  104.369627] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  114.680050] wlan0: no IPv6 routers present
[  371.750844] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=12174 PROTO=UDP SPT=137 DPT=137 LEN=58 
[  372.394294] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=12215 PROTO=UDP SPT=137 DPT=137 LEN=58 
[  372.425360] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=12221 PROTO=UDP SPT=137 DPT=137 LEN=58 
[  374.042364] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=12266 PROTO=UDP SPT=137 DPT=137 LEN=58 
[  377.141448] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=12327 PROTO=UDP SPT=137 DPT=137 LEN=58 
[  378.507891] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=12368 PROTO=UDP SPT=137 DPT=137 LEN=58 
[  378.510187] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=12372 PROTO=UDP SPT=137 DPT=137 LEN=58 
[  379.940533] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=12401 PROTO=UDP SPT=137 DPT=137 LEN=58 
[  379.971994] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=12407 PROTO=UDP SPT=137 DPT=137 LEN=58 
[  381.820426] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=12448 DF PROTO=TCP SPT=49836 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[  384.470412] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=12514 DF PROTO=TCP SPT=49831 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[  384.499521] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=12519 DF PROTO=TCP SPT=49836 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[  390.595878] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=12604 DF PROTO=TCP SPT=49836 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[  402.675656] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=12669 PROTO=UDP SPT=52569 DPT=161 LEN=49 
[  405.135936] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=12697 PROTO=UDP SPT=52569 DPT=161 LEN=49 
[  427.045633] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=12985 DF PROTO=TCP SPT=49882 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[  430.132321] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13032 DF PROTO=TCP SPT=49881 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[  430.141653] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13031 DF PROTO=TCP SPT=49882 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[  436.089039] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=13126 DF PROTO=TCP SPT=49882 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[  448.045168] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13219 DF PROTO=TCP SPT=49881 DPT=8080 WINDOW=8192 RES=0x00 SYN URGP=0 
[  448.045683] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13220 DF PROTO=TCP SPT=49882 DPT=8080 WINDOW=8192 RES=0x00 SYN URGP=0 
[  451.256123] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13246 DF PROTO=TCP SPT=49881 DPT=8080 WINDOW=8192 RES=0x00 SYN URGP=0 
[  457.170795] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=13283 DF PROTO=TCP SPT=49881 DPT=8080 WINDOW=8192 RES=0x00 SYN URGP=0 
[  469.292528] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13424 DF PROTO=TCP SPT=49881 DPT=139 WINDOW=8192 RES=0x00 SYN URGP=0 
[  472.055651] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13508 DF PROTO=TCP SPT=49882 DPT=139 WINDOW=8192 RES=0x00 SYN URGP=0 
[  472.059056] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13506 DF PROTO=TCP SPT=49881 DPT=139 WINDOW=8192 RES=0x00 SYN URGP=0 
[  478.052334] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=13550 DF PROTO=TCP SPT=49881 DPT=139 WINDOW=8192 RES=0x00 SYN URGP=0 
[  478.054890] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=13552 DF PROTO=TCP SPT=49882 DPT=139 WINDOW=8192 RES=0x00 SYN URGP=0 
[  490.137352] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13617 DF PROTO=TCP SPT=49881 DPT=445 WINDOW=8192 RES=0x00 SYN URGP=0 
[  493.056819] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13635 DF PROTO=TCP SPT=49882 DPT=445 WINDOW=8192 RES=0x00 SYN URGP=0 
[  493.057003] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13636 DF PROTO=TCP SPT=49881 DPT=445 WINDOW=8192 RES=0x00 SYN URGP=0 
[  499.172370] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=13689 DF PROTO=TCP SPT=49882 DPT=445 WINDOW=8192 RES=0x00 SYN URGP=0 
[  511.427090] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13733 DF PROTO=TCP SPT=49882 DPT=3389 WINDOW=8192 RES=0x00 SYN URGP=0 
[  514.056822] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13754 DF PROTO=TCP SPT=49882 DPT=3389 WINDOW=8192 RES=0x00 SYN URGP=0 
[  514.057028] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13753 DF PROTO=TCP SPT=49881 DPT=3389 WINDOW=8192 RES=0x00 SYN URGP=0 
[  520.237389] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=13800 DF PROTO=TCP SPT=49882 DPT=3389 WINDOW=8192 RES=0x00 SYN URGP=0 
[  532.112000] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13979 DF PROTO=TCP SPT=49882 DPT=5900 WINDOW=8192 RES=0x00 SYN URGP=0 
[  535.095594] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13997 DF PROTO=TCP SPT=49882 DPT=5900 WINDOW=8192 RES=0x00 SYN URGP=0 
[  535.095741] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=13995 DF PROTO=TCP SPT=49881 DPT=5900 WINDOW=8192 RES=0x00 SYN URGP=0 
[  541.124032] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=14235 DF PROTO=TCP SPT=49882 DPT=5900 WINDOW=8192 RES=0x00 SYN URGP=0 
[  553.245501] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=14289 DF PROTO=TCP SPT=49882 DPT=40080 WINDOW=8192 RES=0x00 SYN URGP=0 
[  556.290288] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=14309 DF PROTO=TCP SPT=49881 DPT=40080 WINDOW=8192 RES=0x00 SYN URGP=0 
[  562.088897] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=14411 DF PROTO=TCP SPT=49881 DPT=40080 WINDOW=8192 RES=0x00 SYN URGP=0 
[  562.088998] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:22:fb:38:89:b4:08:00 SRC=172.16.130.177 DST=172.16.130.22 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=14410 DF PROTO=TCP SPT=49882 DPT=40080 WINDOW=8192 RES=0x00 SYN URGP=0 
```

Results of cat /var/log/syslog | grep PM:
```
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ea8000 - 00000000b5ed0000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ed0000 - 00000000b5ee1000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ee1000 - 00000000b5ee2000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ee2000 - 00000000b5f0a000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0a000 - 00000000b5f0b000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0b000 - 00000000b5f0c000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0c000 - 00000000b5f17000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f17000 - 00000000b5f1d000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f1d000 - 00000000b5f39000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b6000000 - 00000000e0000000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000ffa00000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.165465] PM: Registering ACPI NVS region at b5ea8000 (163840 bytes)
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.165465] PM: Registering ACPI NVS region at b5ee1000 (4096 bytes)
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.165465] PM: Registering ACPI NVS region at b5f0a000 (4096 bytes)
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    0.165465] PM: Registering ACPI NVS region at b5f17000 (24576 bytes)
Dec  3 21:07:24 owner-VGN-NS140E kernel: [    1.510708] PM: Hibernation image not present or could not be loaded.
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ea8000 - 00000000b5ed0000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ed0000 - 00000000b5ee1000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ee1000 - 00000000b5ee2000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ee2000 - 00000000b5f0a000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0a000 - 00000000b5f0b000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0b000 - 00000000b5f0c000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0c000 - 00000000b5f17000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f17000 - 00000000b5f1d000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f1d000 - 00000000b5f39000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b6000000 - 00000000e0000000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000ffa00000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.156997] PM: Registering ACPI NVS region at b5ea8000 (163840 bytes)
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.156997] PM: Registering ACPI NVS region at b5ee1000 (4096 bytes)
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.156997] PM: Registering ACPI NVS region at b5f0a000 (4096 bytes)
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    0.156997] PM: Registering ACPI NVS region at b5f17000 (24576 bytes)
Dec  3 21:34:12 owner-VGN-NS140E kernel: [    1.412298] PM: Hibernation image not present or could not be loaded.
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ea8000 - 00000000b5ed0000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ed0000 - 00000000b5ee1000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ee1000 - 00000000b5ee2000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ee2000 - 00000000b5f0a000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0a000 - 00000000b5f0b000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0b000 - 00000000b5f0c000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0c000 - 00000000b5f17000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f17000 - 00000000b5f1d000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f1d000 - 00000000b5f39000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b6000000 - 00000000e0000000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000ffa00000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5ea8000 (163840 bytes)
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5ee1000 (4096 bytes)
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5f0a000 (4096 bytes)
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5f17000 (24576 bytes)
Dec  3 23:24:34 owner-VGN-NS140E kernel: [    1.892457] PM: Hibernation image not present or could not be loaded.
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ea8000 - 00000000b5ed0000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ed0000 - 00000000b5ee1000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ee1000 - 00000000b5ee2000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ee2000 - 00000000b5f0a000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0a000 - 00000000b5f0b000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0b000 - 00000000b5f0c000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0c000 - 00000000b5f17000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f17000 - 00000000b5f1d000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f1d000 - 00000000b5f39000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b6000000 - 00000000e0000000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000ffa00000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5ea8000 (163840 bytes)
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5ee1000 (4096 bytes)
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5f0a000 (4096 bytes)
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5f17000 (24576 bytes)
Dec  3 23:28:07 owner-VGN-NS140E kernel: [    1.424040] PM: Hibernation image not present or could not be loaded.
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ea8000 - 00000000b5ed0000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ed0000 - 00000000b5ee1000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ee1000 - 00000000b5ee2000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ee2000 - 00000000b5f0a000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0a000 - 00000000b5f0b000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0b000 - 00000000b5f0c000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0c000 - 00000000b5f17000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f17000 - 00000000b5f1d000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f1d000 - 00000000b5f39000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b6000000 - 00000000e0000000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000ffa00000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.165465] PM: Registering ACPI NVS region at b5ea8000 (163840 bytes)
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.165465] PM: Registering ACPI NVS region at b5ee1000 (4096 bytes)
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.165465] PM: Registering ACPI NVS region at b5f0a000 (4096 bytes)
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    0.165465] PM: Registering ACPI NVS region at b5f17000 (24576 bytes)
Dec  4 19:58:22 owner-VGN-NS140E kernel: [    1.514605] PM: Hibernation image not present or could not be loaded.
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ea8000 - 00000000b5ed0000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ed0000 - 00000000b5ee1000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ee1000 - 00000000b5ee2000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ee2000 - 00000000b5f0a000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0a000 - 00000000b5f0b000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0b000 - 00000000b5f0c000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0c000 - 00000000b5f17000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f17000 - 00000000b5f1d000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f1d000 - 00000000b5f39000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b6000000 - 00000000e0000000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000ffa00000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5ea8000 (163840 bytes)
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5ee1000 (4096 bytes)
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5f0a000 (4096 bytes)
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5f17000 (24576 bytes)
Dec  4 20:11:55 owner-VGN-NS140E kernel: [    0.912266] PM: Hibernation image not present or could not be loaded.
Dec  4 20:12:53 owner-VGN-NS140E kernel: [   86.493689] PM: Syncing filesystems ... done.
Dec  4 20:12:53 owner-VGN-NS140E kernel: [   86.622614] PM: Preparing system for mem sleep
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   86.768125] PM: Entering mem sleep
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.145193] PM: suspend of drv:sd dev:0:0:0:0 complete after 376.266 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.145210] PM: suspend of drv:scsi dev:target0:0:0 complete after 376.251 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.145223] PM: suspend of drv:scsi dev:host0 complete after 376.218 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.160024] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 341.634 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.244023] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 425.521 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.244042] PM: suspend of drv: dev:pci0000:00 complete after 424.953 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.244053] PM: suspend of devices complete after 475.384 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.244056] PM: suspend devices took 0.476 seconds
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.416101] PM: late suspend of drv:sky2 dev:0000:01:00.0 complete after 156.050 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.448269] PM: late suspend of devices complete after 204.209 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.449199] PM: Saving platform NVS memory
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.552442] PM: Restoring platform NVS memory
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.854371] PM: early resume of devices complete after 2.263 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.980132] PM: resume of drv:hub dev:3-0:1.0 complete after 119.460 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.980140] PM: resume of drv: dev:ep_00 complete after 119.433 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.980147] PM: resume of drv:hub dev:8-0:1.0 complete after 119.083 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.980151] PM: resume of drv:hub dev:4-0:1.0 complete after 119.398 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.980156] PM: resume of drv: dev:ep_00 complete after 119.054 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.980160] PM: resume of drv: dev:ep_00 complete after 119.376 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.980163] PM: resume of drv:hub dev:7-0:1.0 complete after 119.178 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.980167] PM: resume of drv:hub dev:5-0:1.0 complete after 119.338 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.980171] PM: resume of drv: dev:ep_00 complete after 119.150 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.980175] PM: resume of drv: dev:ep_00 complete after 119.310 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.980178] PM: resume of drv:hub dev:6-0:1.0 complete after 119.272 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.980181] PM: resume of drv: dev:ep_81 complete after 119.492 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.980186] PM: resume of drv: dev:ep_00 complete after 119.242 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.980188] PM: resume of drv: dev:ep_81 complete after 119.106 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.980192] PM: resume of drv: dev:ep_81 complete after 119.190 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.980195] PM: resume of drv: dev:ep_81 complete after 119.427 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.980198] PM: resume of drv: dev:ep_81 complete after 119.273 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.980201] PM: resume of drv: dev:ep_81 complete after 119.354 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   87.996657] PM: resume of drv:i915 dev:0000:00:02.0 complete after 142.189 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   94.897472] PM: resume of drv:sd dev:0:0:0:0 complete after 7036.228 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   94.897502] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 6990.654 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   94.899382] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 7038.099 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   94.899537] PM: resume of devices complete after 7045.098 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   94.899788] PM: resume devices took 7.044 seconds
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   94.899829] PM: Finishing wakeup.
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ea8000 - 00000000b5ed0000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ed0000 - 00000000b5ee1000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ee1000 - 00000000b5ee2000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ee2000 - 00000000b5f0a000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0a000 - 00000000b5f0b000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0b000 - 00000000b5f0c000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0c000 - 00000000b5f17000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f17000 - 00000000b5f1d000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f1d000 - 00000000b5f39000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b6000000 - 00000000e0000000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000ffa00000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.156995] PM: Registering ACPI NVS region at b5ea8000 (163840 bytes)
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.156995] PM: Registering ACPI NVS region at b5ee1000 (4096 bytes)
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.156995] PM: Registering ACPI NVS region at b5f0a000 (4096 bytes)
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    0.156995] PM: Registering ACPI NVS region at b5f17000 (24576 bytes)
Dec  4 20:37:55 owner-VGN-NS140E kernel: [    1.404290] PM: Hibernation image not present or could not be loaded.
```

---

### Post by Toz on 2011-12-05
Did suspend/resume work this time? According to the log file:
> Dec  4 20:13:06 owner-VGN-NS140E kernel: [   94.899537] PM: resume of devices complete after 7045.098 msecs
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   94.899788] PM: resume devices took 7.044 seconds
Dec  4 20:13:06 owner-VGN-NS140E kernel: [   94.899829] PM: Finishing wakeup.
...it did.

---

### Post by JadeMoonlight on 2011-12-05
Yes, adding acpi_sleep=nonvs made resuming from a Suspended state work properly that time. 

How do I permanently fix this problem?

---

### Post by Toz on 2011-12-05
Edit the file **/etc/default/grub** as root:
```
gksudo gedit /etc/default/grub
```
..and add *acpi_sleep=nonvs* to the **GRUB_CMDLINE_LINUX_DEFAULT** so that it looks something like:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_sleep=nonvs"
...(make sure you just add acpi_sleep to the end of you're existing line)

Save the file then re-generate grub via:
```
sudo update-grub
```

It will then be run at every boot.

---

### Post by JadeMoonlight on 2011-12-11
Okay. Thank you, Toz.

That fixes my problem with the Suspend feature, but my laptop still has problems with the Hibernate feature.

Are you able to help me with this issue as well?

When my computer tries to hibernate, it displays this or a similar message before powering down:

```
[ 7175.169955] ata1.00: revalidation failed (errno=-5)
```

---

### Post by Toz on 2011-12-11
Can you post back the contents of **/var/log/pm-suspend.log** and the results of ```
cat /var/log/syslog | grep PM:
```..._after_ a hibernate attempt?

Also useful might be:
```
dmesg
```
```
cat /etc/fstab
```
```
sudo blkid
```
```
cat /etc/initramfs-tools/conf.d/resume
```

Is your home directory and/or swap file encrypted?

---

### Post by JadeMoonlight on 2011-12-11
> Is your home directory and/or swap file encrypted? 
If my home and/or swap directory is encrypted, its not something that I intentionally meant to do. Is there a way for me to check whether these are encrypted?

I do have Storage Device Manager installed and there is a possibility that I could have messed something up with that. I think this might still have been a problem even before I started using Storage Device Manager, but I'm not sure.

**/var/log/pm-suspend.log** contains:
```
Initial commandline parameters: 
Thu Dec  1 17:57:42 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_codec_realtek   330769  1 
iptable_nat            13229  0 
nf_nat                 25890  1 iptable_nat
nf_conntrack_ipv4      19716  3 iptable_nat,nf_nat
nf_conntrack           82342  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
iptable_filter         12810  0 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  4 iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi           13324  0 
iwlagn                314213  0 
snd_rawmidi            30547  1 snd_seq_midi
mac80211              462092  1 iwlagn
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              199587  2 iwlagn,mac80211
psmouse                73882  0 
i915                  566711  3 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
sony_laptop            45393  0 
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    2400524    1493964          0     101376    1171052
-/+ buffers/cache:    1128096    2766392
Swap:      4194300          0    4194300

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Dec  1 17:57:44 EST 2011: performing suspend
Initial commandline parameters: 
Fri Dec  2 15:03:21 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
iptable_nat            13229  0 
nf_nat                 25890  1 iptable_nat
nf_conntrack_ipv4      19716  3 iptable_nat,nf_nat
nf_conntrack           82342  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  0 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  4 iptable_nat,iptable_mangle,iptable_filter,ip_tables
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_codec_realtek   330769  1 
iwlagn                314213  0 
mac80211              462092  1 iwlagn
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
psmouse                73882  0 
cfg80211              199587  2 iwlagn,mac80211
serio_raw              13166  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sony_laptop            45393  0 
i915                  566711  2 
drm_kms_helper         42558  1 i915
drm                   236330  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488     571248    3323240          0      48492     287816
-/+ buffers/cache:     234940    3659548
Swap:      4194300          0    4194300

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:

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

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Dec  2 15:03:22 EST 2011: performing suspend
Initial commandline parameters: 
Fri Dec  2 18:43:09 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_codec_realtek   330769  1 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
uvcvideo               72711  0 
snd_seq_midi           13324  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_rawmidi            30547  1 snd_seq_midi
iwlagn                314213  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              462092  1 iwlagn
snd_timer              29991  2 snd_pcm,snd_seq
psmouse                73882  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13166  0 
i915                  566711  3 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  2 iwlagn,mac80211
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
sony_laptop            45393  0 
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    1514084    2380404          0      63916     614976
-/+ buffers/cache:     835192    3059296
Swap:      4194300          0    4194300

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Dec  2 18:43:11 EST 2011: performing suspend
Initial commandline parameters: 
Sat Dec  3 23:22:48 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
arc4                   12529  2 
iptable_mangle         12734  0 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
snd_seq_midi           13324  0 
v4l2_compat_ioctl32    17083  1 videodev
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
iwlagn                314213  0 
mac80211              462092  1 iwlagn
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
serio_raw              13166  0 
cfg80211              199587  2 iwlagn,mac80211
soundcore              12680  1 snd
i915                  566711  3 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sony_laptop            45393  0 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    1295008    2599480          0      67364     603272
-/+ buffers/cache:     624372    3270116
Swap:      4194300          0    4194300

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Dec  3 23:22:50 EST 2011: performing suspend
Initial commandline parameters: 
Sun Dec  4 20:12:50 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
snd_hda_codec_realtek   330769  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
iwlagn                314213  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
mac80211              462092  1 iwlagn
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
psmouse                73882  0 
serio_raw              13166  0 
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              199587  2 iwlagn,mac80211
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
sony_laptop            45393  0 
i915                  566711  3 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
sky2                   58674  0 
crc_itu_t              12707  1 firewire_core
sdhci                  32166  1 sdhci_pci
ahci                   26002  7 
libahci                26861  1 ahci
             total       used       free     shared    buffers     cached
Mem:       3894488    1042164    2852324          0      60776     406104
-/+ buffers/cache:     575284    3319204
Swap:      4194300          0    4194300

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

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Dec  4 20:12:52 EST 2011: performing suspend
Sun Dec  4 20:13:06 EST 2011: Awake.
Sun Dec  4 20:13:06 EST 2011: Running hooks for resume
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
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

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
Sun Dec  4 20:13:08 EST 2011: Finished.
Initial commandline parameters: 
Mon Dec  5 01:19:42 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
uvcvideo               72711  0 
snd_hda_codec_realtek   330769  1 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_intel          33390  4 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
iwlagn                314213  0 
mac80211              462092  1 iwlagn
psmouse                73882  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
serio_raw              13166  0 
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              199587  2 iwlagn,mac80211
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sony_laptop            45393  0 
i915                  566711  4 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         42558  1 i915
drm                   236330  5 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    1627072    2267416          0      81748     807084
-/+ buffers/cache:     738240    3156248
Swap:      4194300          0    4194300

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

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Mon Dec  5 01:19:44 EST 2011: performing suspend
Initial commandline parameters: 
Mon Dec  5 12:20:32 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
snd_hda_codec_realtek   330769  1 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_hda_intel          33390  4 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_intel,snd_hda_codec
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
iwlagn                314213  0 
snd_timer              29991  2 snd_pcm,snd_seq
psmouse                73882  0 
mac80211              462092  1 iwlagn
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13166  0 
snd                    68266  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  2 iwlagn,mac80211
sony_laptop            45393  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    1407856    2486632          0      63816     628828
-/+ buffers/cache:     715212    3179276
Swap:      4194300          0    4194300

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

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Mon Dec  5 12:20:34 EST 2011: performing suspend
Initial commandline parameters: 
Mon Dec  5 22:20:40 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_realtek   330769  1 
arc4                   12529  2 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
uvcvideo               72711  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
videodev               93004  1 uvcvideo
snd_hwdep              13668  1 snd_hda_codec
v4l2_compat_ioctl32    17083  1 videodev
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
iwlagn                314213  0 
mac80211              462092  1 iwlagn
snd_seq_midi           13324  0 
cfg80211              199587  2 iwlagn,mac80211
snd_rawmidi            30547  1 snd_seq_midi
psmouse                73882  0 
serio_raw              13166  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
sony_laptop            45393  0 
i915                  566711  3 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
sky2                   58674  0 
ahci                   26002  7 
libahci                26861  1 ahci
             total       used       free     shared    buffers     cached
Mem:       3894488    1040632    2853856          0      60764     411644
-/+ buffers/cache:     568224    3326264
Swap:      4194300          0    4194300

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Mon Dec  5 22:20:42 EST 2011: performing suspend
Mon Dec  5 22:20:58 EST 2011: Awake.
Mon Dec  5 22:20:58 EST 2011: Running hooks for resume
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
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

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
Mon Dec  5 22:21:00 EST 2011: Finished.
Initial commandline parameters: 
Mon Dec  5 22:23:39 EST 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
btrfs                 648895  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
ufs                    75303  0 
qnx4                   17677  0 
hfsplus                88963  0 
hfs                    54782  0 
minix                  36322  0 
ntfs                  101885  0 
vfat                   17585  0 
msdos                  17332  0 
fat                    61475  2 vfat,msdos
jfs                   186662  0 
xfs                   831526  0 
reiserfs              248828  0 
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_realtek   330769  1 
arc4                   12529  2 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
uvcvideo               72711  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
videodev               93004  1 uvcvideo
snd_hwdep              13668  1 snd_hda_codec
v4l2_compat_ioctl32    17083  1 videodev
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
iwlagn                314213  0 
mac80211              462092  1 iwlagn
snd_seq_midi           13324  0 
cfg80211              199587  2 iwlagn,mac80211
snd_rawmidi            30547  1 snd_seq_midi
psmouse                73882  0 
serio_raw              13166  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
sony_laptop            45393  0 
i915                  566711  3 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
sky2                   58674  0 
ahci                   26002  7 
libahci                26861  1 ahci
             total       used       free     shared    buffers     cached
Mem:       3894488    1229872    2664616          0      59140     510628
-/+ buffers/cache:     660104    3234384
Swap:      4194300          4    4194296

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Mon Dec  5 22:23:41 EST 2011: performing hibernate
Initial commandline parameters: 
Mon Dec  5 22:30:27 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi           13324  0 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
uvcvideo               72711  0 
snd_rawmidi            30547  1 snd_seq_midi
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
iptable_mangle         12734  0 
iptable_filter         12810  1 
snd_seq_midi_event     14899  1 snd_seq_midi
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
iwlagn                314213  0 
i915                  566711  3 
psmouse                73882  0 
mac80211              462092  1 iwlagn
serio_raw              13166  0 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  2 iwlagn,mac80211
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
sony_laptop            45393  0 
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    1402836    2491652          0      71992     646040
-/+ buffers/cache:     684804    3209684
Swap:      4194300          0    4194300

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Mon Dec  5 22:30:29 EST 2011: performing suspend
Initial commandline parameters: 
Mon Dec  5 23:04:13 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
snd_hda_codec_realtek   330769  1 
iptable_mangle         12734  0 
iptable_filter         12810  1 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                73882  0 
serio_raw              13166  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
iwlagn                314213  0 
sony_laptop            45393  0 
mac80211              462092  1 iwlagn
cfg80211              199587  2 iwlagn,mac80211
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
firewire_ohci          40722  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  7 
sky2                   58674  0 
libahci                26861  1 ahci
             total       used       free     shared    buffers     cached
Mem:       3894488    1152568    2741920          0      72520     511392
-/+ buffers/cache:     568656    3325832
Swap:      4194300          0    4194300

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Mon Dec  5 23:04:15 EST 2011: performing suspend
Initial commandline parameters: 
Tue Dec  6 16:45:04 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
snd_hda_codec_realtek   330769  1 
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
iwlagn                314213  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
mac80211              462092  1 iwlagn
psmouse                73882  0 
serio_raw              13166  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
sony_laptop            45393  0 
i915                  566711  2 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              199587  2 iwlagn,mac80211
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         42558  1 i915
soundcore              12680  1 snd
drm                   236330  3 i915,drm_kms_helper
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488     571848    3322640          0      48508     287228
-/+ buffers/cache:     236112    3658376
Swap:      4194300          0    4194300

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Dec  6 16:45:05 EST 2011: performing suspend
Tue Dec  6 16:45:20 EST 2011: Awake.
Tue Dec  6 16:45:20 EST 2011: Running hooks for resume
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
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

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

/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: Returned exit code 1.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Initial commandline parameters: 
Tue Dec  6 16:49:44 EST 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
snd_hda_codec_realtek   330769  1 
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
iwlagn                314213  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
mac80211              462092  1 iwlagn
psmouse                73882  0 
serio_raw              13166  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
sony_laptop            45393  0 
i915                  566711  3 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              199587  2 iwlagn,mac80211
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         42558  1 i915
soundcore              12680  1 snd
drm                   236330  4 i915,drm_kms_helper
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    1186516    2707972          0      61196     496824
-/+ buffers/cache:     628496    3265992
Swap:      4194300          0    4194300

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Tue Dec  6 16:49:48 EST 2011: performing hibernate
Initial commandline parameters: 
Tue Dec  6 16:53:54 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlagn                314213  0 
psmouse                73882  0 
serio_raw              13166  0 
mac80211              462092  1 iwlagn
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              199587  2 iwlagn,mac80211
sony_laptop            45393  0 
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
firewire_ohci          40722  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    1249712    2644776          0      68740     513100
-/+ buffers/cache:     667872    3226616
Swap:      4194300          0    4194300

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Dec  6 16:53:56 EST 2011: performing suspend
Tue Dec  6 17:54:54 EST 2011: Awake.
Tue Dec  6 17:54:54 EST 2011: Running hooks for resume
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
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

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
Tue Dec  6 17:54:56 EST 2011: Finished.
Initial commandline parameters: 
Tue Dec  6 20:00:05 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlagn                314213  0 
psmouse                73882  0 
serio_raw              13166  0 
mac80211              462092  1 iwlagn
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              199587  2 iwlagn,mac80211
sony_laptop            45393  0 
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
firewire_ohci          40722  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    1823816    2070672          0      89044     671064
-/+ buffers/cache:    1063708    2830780
Swap:      4194300         12    4194288

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Dec  6 20:00:06 EST 2011: performing suspend
Tue Dec  6 21:22:03 EST 2011: Awake.
Tue Dec  6 21:22:03 EST 2011: Running hooks for resume
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
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

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
Tue Dec  6 21:22:04 EST 2011: Finished.
Initial commandline parameters: 
Wed Dec  7 03:29:12 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
usb_storage            57901  0 
uas                    18027  0 
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlagn                314213  0 
psmouse                73882  0 
serio_raw              13166  0 
mac80211              462092  1 iwlagn
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              199587  2 iwlagn,mac80211
sony_laptop            45393  0 
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
firewire_ohci          40722  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    1630864    2263624          0      93588     555952
-/+ buffers/cache:     981324    2913164
Swap:      4194300         68    4194232

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

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Wed Dec  7 03:29:15 EST 2011: performing suspend
Wed Dec  7 08:09:46 EST 2011: Awake.
Wed Dec  7 08:09:46 EST 2011: Running hooks for resume
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
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

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
Wed Dec  7 08:09:48 EST 2011: Finished.
Initial commandline parameters: 
Wed Dec  7 08:51:14 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
usb_storage            57901  0 
uas                    18027  0 
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  4 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_pcm                96755  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlagn                314213  0 
psmouse                73882  0 
serio_raw              13166  0 
mac80211              462092  1 iwlagn
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              199587  2 iwlagn,mac80211
sony_laptop            45393  0 
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
firewire_ohci          40722  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    1794664    2099824          0     100760     638768
-/+ buffers/cache:    1055136    2839352
Swap:      4194300         68    4194232

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

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Wed Dec  7 08:51:15 EST 2011: performing suspend
Wed Dec  7 10:12:14 EST 2011: Awake.
Wed Dec  7 10:12:14 EST 2011: Running hooks for resume
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
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

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
Wed Dec  7 10:12:16 EST 2011: Finished.
Initial commandline parameters: 
Wed Dec  7 10:58:05 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nls_utf8               12557  1 
udf                    93640  1 
usb_storage            57901  0 
uas                    18027  0 
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  4 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_pcm                96755  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlagn                314213  0 
psmouse                73882  0 
serio_raw              13166  0 
mac80211              462092  1 iwlagn
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              199587  2 iwlagn,mac80211
sony_laptop            45393  0 
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
firewire_ohci          40722  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  2 udf,firewire_core
ahci                   26002  9 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    2602184    1292304          0     699500     750116
-/+ buffers/cache:    1152568    2741920
Swap:      4194300         68    4194232

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Wed Dec  7 10:58:06 EST 2011: performing suspend
Wed Dec  7 11:46:26 EST 2011: Awake.
Wed Dec  7 11:46:26 EST 2011: Running hooks for resume
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
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

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
Wed Dec  7 11:46:29 EST 2011: Finished.
Initial commandline parameters: 
Wed Dec  7 13:10:58 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nls_utf8               12557  1 
udf                    93640  1 
usb_storage            57901  0 
uas                    18027  0 
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  4 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_pcm                96755  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlagn                314213  0 
psmouse                73882  0 
serio_raw              13166  0 
mac80211              462092  1 iwlagn
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              199587  2 iwlagn,mac80211
sony_laptop            45393  0 
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
firewire_ohci          40722  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  2 udf,firewire_core
ahci                   26002  10 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    2363360    1531128          0     469588     743956
-/+ buffers/cache:    1149816    2744672
Swap:      4194300         68    4194232

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Wed Dec  7 13:10:59 EST 2011: performing suspend
Wed Dec  7 17:01:51 EST 2011: Awake.
Wed Dec  7 17:01:51 EST 2011: Running hooks for resume
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
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

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
Wed Dec  7 17:01:54 EST 2011: Finished.
Initial commandline parameters: 
Wed Dec  7 17:47:12 EST 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nls_utf8               12557  1 
udf                    93640  1 
usb_storage            57901  0 
uas                    18027  0 
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  4 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_pcm                96755  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlagn                314213  0 
psmouse                73882  0 
serio_raw              13166  0 
mac80211              462092  1 iwlagn
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              199587  2 iwlagn,mac80211
sony_laptop            45393  0 
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
firewire_ohci          40722  0 
sdhci                  32166  1 sdhci_pci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  2 udf,firewire_core
ahci                   26002  10 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    2396560    1497928          0     474352     748252
-/+ buffers/cache:    1173956    2720532
Swap:      4194300         72    4194228

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Wed Dec  7 17:47:14 EST 2011: performing hibernate
Initial commandline parameters: 
Wed Dec  7 18:49:17 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nls_utf8               12557  1 
udf                    93640  1 
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
uvcvideo               72711  0 
snd_hda_codec_realtek   330769  1 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
snd_hda_intel          33390  2 
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
iptable_filter         12810  1 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
iwlagn                314213  0 
mac80211              462092  1 iwlagn
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
serio_raw              13166  0 
cfg80211              199587  2 iwlagn,mac80211
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
sony_laptop            45393  0 
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  2 udf,firewire_core
ahci                   26002  8 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    1470856    2423632          0     107040     704828
-/+ buffers/cache:     658988    3235500
Swap:      4194300          0    4194300

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Wed Dec  7 18:49:18 EST 2011: performing suspend
Wed Dec  7 21:42:48 EST 2011: Awake.
Wed Dec  7 21:42:49 EST 2011: Running hooks for resume
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
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

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
Wed Dec  7 21:42:51 EST 2011: Finished.
Initial commandline parameters: 
Wed Dec  7 21:53:30 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nls_utf8               12557  1 
udf                    93640  1 
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
uvcvideo               72711  0 
snd_hda_codec_realtek   330769  1 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
snd_hda_intel          33390  2 
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
iptable_filter         12810  1 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
iwlagn                314213  0 
mac80211              462092  1 iwlagn
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
serio_raw              13166  0 
cfg80211              199587  2 iwlagn,mac80211
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
sony_laptop            45393  0 
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  2 udf,firewire_core
ahci                   26002  8 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    1684132    2210356          0     103508     868352
-/+ buffers/cache:     712272    3182216
Swap:      4194300         12    4194288

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Wed Dec  7 21:53:31 EST 2011: performing suspend
Thu Dec  8 10:23:03 EST 2011: Awake.
Thu Dec  8 10:23:03 EST 2011: Running hooks for resume
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
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

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
Thu Dec  8 10:23:12 EST 2011: Finished.
Initial commandline parameters: 
Thu Dec  8 10:56:34 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nls_utf8               12557  1 
udf                    93640  1 
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_realtek   330769  1 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  2 
iptable_mangle         12734  0 
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_seq_midi           13324  0 
uvcvideo               72711  0 
snd_rawmidi            30547  1 snd_seq_midi
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73882  0 
serio_raw              13166  0 
iwlagn                314213  0 
i915                  566711  3 
mac80211              462092  1 iwlagn
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  2 iwlagn,mac80211
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sony_laptop            45393  0 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  2 udf,firewire_core
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
ahci                   26002  8 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    2069844    1824644          0     655032     721284
-/+ buffers/cache:     693528    3200960
Swap:      4194300          0    4194300

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

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Dec  8 10:56:36 EST 2011: performing suspend
Thu Dec  8 12:01:49 EST 2011: Awake.
Thu Dec  8 12:01:49 EST 2011: Running hooks for resume
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
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

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
Thu Dec  8 12:01:51 EST 2011: Finished.
Initial commandline parameters: 
Thu Dec  8 12:54:42 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nls_utf8               12557  1 
udf                    93640  1 
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_realtek   330769  1 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  2 
iptable_mangle         12734  0 
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_seq_midi           13324  0 
uvcvideo               72711  0 
snd_rawmidi            30547  1 snd_seq_midi
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73882  0 
serio_raw              13166  0 
iwlagn                314213  0 
i915                  566711  3 
mac80211              462092  1 iwlagn
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  2 iwlagn,mac80211
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sony_laptop            45393  0 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  2 udf,firewire_core
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
ahci                   26002  8 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    2494736    1399752          0    1037332     712944
-/+ buffers/cache:     744460    3150028
Swap:      4194300          0    4194300

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Dec  8 12:54:44 EST 2011: performing suspend
Thu Dec  8 16:51:17 EST 2011: Awake.
Thu Dec  8 16:51:17 EST 2011: Running hooks for resume
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
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

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
Thu Dec  8 16:51:20 EST 2011: Finished.
Initial commandline parameters: 
Thu Dec  8 17:28:47 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nls_utf8               12557  0 
udf                    93640  0 
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_realtek   330769  1 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  2 
iptable_mangle         12734  0 
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_seq_midi           13324  0 
uvcvideo               72711  0 
snd_rawmidi            30547  1 snd_seq_midi
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73882  0 
serio_raw              13166  0 
iwlagn                314213  0 
i915                  566711  3 
mac80211              462092  1 iwlagn
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  2 iwlagn,mac80211
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sony_laptop            45393  0 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  2 udf,firewire_core
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    1804256    2090232          0      72504     845488
-/+ buffers/cache:     886264    3008224
Swap:      4194300         12    4194288

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Dec  8 17:28:48 EST 2011: performing suspend
Fri Dec  9 18:44:41 EST 2011: Awake.
Fri Dec  9 18:44:41 EST 2011: Running hooks for resume
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
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

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
Fri Dec  9 18:44:44 EST 2011: Finished.
Initial commandline parameters: 
Sat Dec 10 14:24:06 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
usb_storage            57901  0 
uas                    18027  0 
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
iwlagn                314213  0 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              462092  1 iwlagn
soundcore              12680  1 snd
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
cfg80211              199587  2 iwlagn,mac80211
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
v4l2_compat_ioctl32    17083  1 videodev
joydev                 17693  0 
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
psmouse                73882  0 
serio_raw              13166  0 
sony_laptop            45393  0 
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sky2                   58674  0 
ahci                   26002  7 
libahci                26861  1 ahci
             total       used       free     shared    buffers     cached
Mem:       3894488    1332684    2561804          0      49000     528952
-/+ buffers/cache:     754732    3139756
Swap:      4194300          0    4194300

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Dec 10 14:24:08 EST 2011: performing suspend
Sat Dec 10 19:05:29 EST 2011: Awake.
Sat Dec 10 19:05:29 EST 2011: Running hooks for resume
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
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

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
Sat Dec 10 19:05:31 EST 2011: Finished.
Initial commandline parameters: 
Sat Dec 10 21:06:27 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
usb_storage            57901  0 
uas                    18027  0 
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_codec_realtek   330769  1 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
iwlagn                314213  0 
psmouse                73882  0 
serio_raw              13166  0 
sony_laptop            45393  0 
mac80211              462092  1 iwlagn
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  2 iwlagn,mac80211
i915                  566711  3 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  3 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    2740884    1153604          0     629628    1174108
-/+ buffers/cache:     937148    2957340
Swap:      4194300         28    4194272

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Dec 10 21:06:30 EST 2011: performing suspend
Sun Dec 11 12:23:20 EST 2011: Awake.
Sun Dec 11 12:23:20 EST 2011: Running hooks for resume
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
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

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
Sun Dec 11 12:23:22 EST 2011: Finished.
Initial commandline parameters: 
Sun Dec 11 12:41:44 EST 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
usb_storage            57901  0 
uas                    18027  0 
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_codec_realtek   330769  1 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
iwlagn                314213  0 
psmouse                73882  0 
serio_raw              13166  0 
sony_laptop            45393  0 
mac80211              462092  1 iwlagn
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  2 iwlagn,mac80211
i915                  566711  3 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
ahci                   26002  3 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    2761440    1133048          0     630236    1176160
-/+ buffers/cache:     955044    2939444
Swap:      4194300         28    4194272

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Sun Dec 11 12:41:45 EST 2011: performing hibernate
Initial commandline parameters: 
Sun Dec 11 13:24:32 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_realtek   330769  1 
uvcvideo               72711  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  2 
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
snd_seq_midi           13324  0 
iptable_filter         12810  1 
snd_rawmidi            30547  1 snd_seq_midi
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
iwlagn                314213  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              462092  1 iwlagn
i915                  566711  3 
psmouse                73882  0 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  2 iwlagn,mac80211
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
sony_laptop            45393  0 
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
sky2                   58674  0 
crc_itu_t              12707  1 firewire_core
ahci                   26002  7 
libahci                26861  1 ahci
             total       used       free     shared    buffers     cached
Mem:       3894488    1998784    1895704          0     161736     980168
-/+ buffers/cache:     856880    3037608
Swap:      4194300          0    4194300

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Dec 11 13:24:34 EST 2011: performing suspend
Sun Dec 11 13:27:43 EST 2011: Awake.
Sun Dec 11 13:27:43 EST 2011: Running hooks for resume
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
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128

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
Sun Dec 11 13:27:45 EST 2011: Finished.
Initial commandline parameters: 
Sun Dec 11 13:59:00 EST 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_realtek   330769  1 
uvcvideo               72711  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  2 
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
snd_seq_midi           13324  0 
iptable_filter         12810  1 
snd_rawmidi            30547  1 snd_seq_midi
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
iwlagn                314213  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              462092  1 iwlagn
i915                  566711  3 
psmouse                73882  0 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  2 iwlagn,mac80211
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
sony_laptop            45393  0 
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
sky2                   58674  0 
crc_itu_t              12707  1 firewire_core
ahci                   26002  7 
libahci                26861  1 ahci
             total       used       free     shared    buffers     cached
Mem:       3894488    2036224    1858264          0     156204    1012444
-/+ buffers/cache:     867576    3026912
Swap:      4194300         16    4194284

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Sun Dec 11 13:59:02 EST 2011: performing hibernate
Initial commandline parameters: 
Sun Dec 11 15:45:54 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_realtek   330769  1 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
arc4                   12529  2 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
i915                  566711  3 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
iwlagn                314213  0 
psmouse                73882  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42558  1 i915
mac80211              462092  1 iwlagn
drm                   236330  4 i915,drm_kms_helper
serio_raw              13166  0 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  2 iwlagn,mac80211
i2c_algo_bit           13423  1 i915
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sony_laptop            45393  0 
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    1807332    2087156          0     138572     745704
-/+ buffers/cache:     923056    2971432
Swap:      4194300          0    4194300

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Dec 11 15:45:56 EST 2011: performing suspend
Sun Dec 11 15:46:06 EST 2011: Awake.
Sun Dec 11 15:46:06 EST 2011: Running hooks for resume
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
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

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
Sun Dec 11 15:46:08 EST 2011: Finished.
Initial commandline parameters: 
Sun Dec 11 17:53:07 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_realtek   330769  1 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
arc4                   12529  2 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
i915                  566711  3 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
iwlagn                314213  0 
psmouse                73882  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42558  1 i915
mac80211              462092  1 iwlagn
drm                   236330  4 i915,drm_kms_helper
serio_raw              13166  0 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  2 iwlagn,mac80211
i2c_algo_bit           13423  1 i915
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sony_laptop            45393  0 
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    2700748    1193740          0     550332    1188688
-/+ buffers/cache:     961728    2932760
Swap:      4194300         16    4194284

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Dec 11 17:53:08 EST 2011: performing suspend
Sun Dec 11 19:10:20 EST 2011: Awake.
Sun Dec 11 19:10:21 EST 2011: Running hooks for resume
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
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

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
Sun Dec 11 19:10:23 EST 2011: Finished.
Initial commandline parameters: 
Sun Dec 11 19:29:42 EST 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux naomi-VGN-NS140E 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xt_limit               12711  8 
xt_tcpudp              12603  10 
ipt_LOG                12919  8 
ipt_MASQUERADE         12759  0 
xt_DSCP                12629  0 
ipt_REJECT             12576  1 
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  0 
xt_state               12578  6 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_realtek   330769  1 
iptable_nat            13229  0 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  9 iptable_nat,nf_nat
nf_conntrack           82342  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_mangle         12734  0 
iptable_filter         12810  1 
ip_tables              27473  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               29846  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
arc4                   12529  2 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
i915                  566711  3 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
iwlagn                314213  0 
psmouse                73882  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42558  1 i915
mac80211              462092  1 iwlagn
drm                   236330  4 i915,drm_kms_helper
serio_raw              13166  0 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199587  2 iwlagn,mac80211
i2c_algo_bit           13423  1 i915
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sony_laptop            45393  0 
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
ahci                   26002  7 
libahci                26861  1 ahci
sky2                   58674  0 
             total       used       free     shared    buffers     cached
Mem:       3894488    2393348    1501140          0     541356    1153916
-/+ buffers/cache:     698076    3196412
Swap:      4194300         16    4194284

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Sun Dec 11 19:29:44 EST 2011: performing hibernate
```

**cat /var/log/syslog | grep PM:** returns:
```
Dec 11 13:24:35 naomi-VGN-NS140E kernel: [ 2527.397024] PM: Syncing filesystems ... done.
Dec 11 13:24:35 naomi-VGN-NS140E kernel: [ 2527.508241] PM: Preparing system for mem sleep
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2527.724135] PM: Entering mem sleep
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.087692] PM: suspend of drv:sd dev:0:0:0:0 complete after 362.754 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.087709] PM: suspend of drv:scsi dev:target0:0:0 complete after 362.766 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.087723] PM: suspend of drv:scsi dev:host0 complete after 362.651 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.100028] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 325.782 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.200017] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 425.618 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.200037] PM: suspend of drv: dev:pci0000:00 complete after 425.022 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.200049] PM: suspend of devices complete after 475.366 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.200051] PM: suspend devices took 0.476 seconds
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.372038] PM: late suspend of drv:sky2 dev:0000:01:00.0 complete after 155.993 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.404264] PM: late suspend of devices complete after 204.209 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.405202] PM: Saving platform NVS memory
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.508445] PM: Restoring platform NVS memory
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.810852] PM: early resume of devices complete after 2.733 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.936062] PM: resume of drv:hub dev:8-0:1.0 complete after 117.131 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.936074] PM: resume of drv: dev:ep_00 complete after 117.093 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.936082] PM: resume of drv: dev:ep_81 complete after 117.129 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.936116] PM: resume of drv:hub dev:6-0:1.0 complete after 117.420 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.936127] PM: resume of drv: dev:ep_00 complete after 117.377 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.936136] PM: resume of drv: dev:ep_81 complete after 117.414 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.936168] PM: resume of drv:hub dev:7-0:1.0 complete after 117.358 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.936179] PM: resume of drv: dev:ep_00 complete after 117.313 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.936188] PM: resume of drv: dev:ep_81 complete after 117.351 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.936219] PM: resume of drv:hub dev:5-0:1.0 complete after 117.635 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.936231] PM: resume of drv: dev:ep_00 complete after 117.593 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.936239] PM: resume of drv: dev:ep_81 complete after 117.630 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.936272] PM: resume of drv:hub dev:4-0:1.0 complete after 117.799 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.936283] PM: resume of drv: dev:ep_00 complete after 117.755 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.936292] PM: resume of drv: dev:ep_81 complete after 117.791 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.936326] PM: resume of drv:hub dev:3-0:1.0 complete after 117.968 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.936336] PM: resume of drv: dev:ep_00 complete after 117.925 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2528.936345] PM: resume of drv: dev:ep_81 complete after 117.962 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2529.072717] PM: resume of drv:i915 dev:0000:00:02.0 complete after 261.742 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2536.134782] PM: resume of drv:sd dev:0:0:0:0 complete after 7315.601 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2536.134819] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 7263.888 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2536.136080] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 7316.842 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2536.136400] PM: resume of devices complete after 7325.463 msecs
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2536.136761] PM: resume devices took 7.328 seconds
Dec 11 13:27:43 naomi-VGN-NS140E kernel: [ 2536.136830] PM: Finishing wakeup.
Dec 11 13:59:02 naomi-VGN-NS140E kernel: [ 4415.441160] PM: Marking nosave pages: 000000000009b000 - 0000000000100000
Dec 11 13:59:02 naomi-VGN-NS140E kernel: [ 4415.441171] PM: Marking nosave pages: 00000000b5ea8000 - 00000000b5f39000
Dec 11 13:59:02 naomi-VGN-NS140E kernel: [ 4415.441182] PM: Marking nosave pages: 00000000b6000000 - 0000000100000000
Dec 11 13:59:02 naomi-VGN-NS140E kernel: [ 4415.443164] PM: Basic memory bitmaps created
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ea8000 - 00000000b5ed0000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ed0000 - 00000000b5ee1000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ee1000 - 00000000b5ee2000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ee2000 - 00000000b5f0a000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0a000 - 00000000b5f0b000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0b000 - 00000000b5f0c000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0c000 - 00000000b5f17000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f17000 - 00000000b5f1d000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f1d000 - 00000000b5f39000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b6000000 - 00000000e0000000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000ffa00000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5ea8000 (163840 bytes)
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5ee1000 (4096 bytes)
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5f0a000 (4096 bytes)
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5f17000 (24576 bytes)
Dec 11 14:00:33 naomi-VGN-NS140E kernel: [    0.908468] PM: Hibernation image not present or could not be loaded.
Dec 11 15:45:56 naomi-VGN-NS140E kernel: [ 6365.221189] PM: Syncing filesystems ... done.
Dec 11 15:45:56 naomi-VGN-NS140E kernel: [ 6365.310374] PM: Preparing system for mem sleep
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6365.568126] PM: Entering mem sleep
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6365.949337] PM: suspend of drv:sd dev:0:0:0:0 complete after 380.416 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6365.949355] PM: suspend of drv:scsi dev:target0:0:0 complete after 380.399 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6365.949367] PM: suspend of drv:scsi dev:host0 complete after 380.285 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6365.964018] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 346.610 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.044017] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 426.473 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.044036] PM: suspend of drv: dev:pci0000:00 complete after 426.369 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.044048] PM: suspend of devices complete after 475.376 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.044051] PM: suspend devices took 0.476 seconds
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.216037] PM: late suspend of drv:sky2 dev:0000:01:00.0 complete after 155.992 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.248262] PM: late suspend of devices complete after 204.207 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.249202] PM: Saving platform NVS memory
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.352437] PM: Restoring platform NVS memory
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.654351] PM: early resume of devices complete after 2.272 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.780087] PM: resume of drv: dev:ep_00 complete after 119.277 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.780095] PM: resume of drv:hub dev:3-0:1.0 complete after 119.324 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.780104] PM: resume of drv: dev:ep_81 complete after 119.315 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.780128] PM: resume of drv: dev:ep_00 complete after 119.162 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.780135] PM: resume of drv:hub dev:5-0:1.0 complete after 119.207 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.780143] PM: resume of drv: dev:ep_00 complete after 119.254 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.780149] PM: resume of drv:hub dev:4-0:1.0 complete after 119.298 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.780157] PM: resume of drv: dev:ep_81 complete after 119.211 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.780163] PM: resume of drv: dev:ep_81 complete after 119.294 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.780176] PM: resume of drv: dev:ep_00 complete after 119.057 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.780182] PM: resume of drv:hub dev:7-0:1.0 complete after 119.099 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.780189] PM: resume of drv:hub dev:6-0:1.0 complete after 119.180 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.780192] PM: resume of drv: dev:ep_00 complete after 119.146 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.780198] PM: resume of drv:hub dev:8-0:1.0 complete after 119.038 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.780201] PM: resume of drv: dev:ep_81 complete after 119.097 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.780206] PM: resume of drv: dev:ep_00 complete after 119.009 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.780212] PM: resume of drv: dev:ep_81 complete after 119.033 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.780223] PM: resume of drv: dev:ep_81 complete after 119.198 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6366.816659] PM: resume of drv:i915 dev:0000:00:02.0 complete after 162.209 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6373.203697] PM: resume of drv:sd dev:0:0:0:0 complete after 6542.359 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6373.203726] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 6485.949 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6373.205370] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 6543.989 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6373.205594] PM: resume of devices complete after 6551.172 msecs
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6373.205851] PM: resume devices took 6.552 seconds
Dec 11 15:46:06 naomi-VGN-NS140E kernel: [ 6373.205893] PM: Finishing wakeup.
Dec 11 17:53:08 naomi-VGN-NS140E kernel: [13995.186267] PM: Syncing filesystems ... done.
Dec 11 17:53:08 naomi-VGN-NS140E kernel: [13995.252867] PM: Preparing system for mem sleep
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13995.416108] PM: Entering mem sleep
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13995.790507] PM: suspend of drv:sd dev:0:0:0:0 complete after 358.070 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13995.790524] PM: suspend of drv:scsi dev:target0:0:0 complete after 358.053 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13995.790536] PM: suspend of drv:scsi dev:host0 complete after 357.948 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13995.804028] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 322.374 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13995.804038] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 322.247 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13995.804050] PM: suspend of drv: dev:pci0000:00 complete after 322.130 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13995.804056] PM: suspend of devices complete after 371.870 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13995.804059] PM: suspend devices took 0.388 seconds
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13995.976039] PM: late suspend of drv:sky2 dev:0000:01:00.0 complete after 155.985 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.008267] PM: late suspend of devices complete after 204.204 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.009201] PM: Saving platform NVS memory
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.112432] PM: Restoring platform NVS memory
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.414355] PM: early resume of devices complete after 2.274 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.540112] PM: resume of drv:hub dev:3-0:1.0 complete after 118.673 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.540121] PM: resume of drv: dev:ep_00 complete after 118.646 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.540128] PM: resume of drv:hub dev:4-0:1.0 complete after 118.614 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.540135] PM: resume of drv: dev:ep_00 complete after 118.585 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.540142] PM: resume of drv: dev:ep_00 complete after 118.280 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.540150] PM: resume of drv:hub dev:8-0:1.0 complete after 118.324 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.540157] PM: resume of drv: dev:ep_81 complete after 118.701 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.540165] PM: resume of drv: dev:ep_81 complete after 118.632 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.540169] PM: resume of drv:hub dev:7-0:1.0 complete after 118.419 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.540172] PM: resume of drv: dev:ep_00 complete after 118.464 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.540178] PM: resume of drv: dev:ep_00 complete after 118.394 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.540180] PM: resume of drv: dev:ep_81 complete after 118.336 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.540184] PM: resume of drv:hub dev:6-0:1.0 complete after 118.514 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.540187] PM: resume of drv: dev:ep_00 complete after 118.557 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.540192] PM: resume of drv:hub dev:5-0:1.0 complete after 118.602 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.540195] PM: resume of drv: dev:ep_81 complete after 118.428 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.540200] PM: resume of drv: dev:ep_81 complete after 118.513 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.540203] PM: resume of drv: dev:ep_81 complete after 118.591 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13996.572692] PM: resume of drv:i915 dev:0000:00:02.0 complete after 158.239 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13998.330564] PM: resume of drv:sd dev:0:0:0:0 complete after 1908.561 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13998.330592] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 1860.132 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13998.331923] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 1909.880 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13998.331951] PM: resume of devices complete after 1917.525 msecs
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13998.332219] PM: resume devices took 1.920 seconds
Dec 11 19:10:20 naomi-VGN-NS140E kernel: [13998.332254] PM: Finishing wakeup.
Dec 11 19:29:44 naomi-VGN-NS140E kernel: [15161.715162] PM: Marking nosave pages: 000000000009b000 - 0000000000100000
Dec 11 19:29:44 naomi-VGN-NS140E kernel: [15161.715170] PM: Marking nosave pages: 00000000b5ea8000 - 00000000b5f39000
Dec 11 19:29:44 naomi-VGN-NS140E kernel: [15161.715177] PM: Marking nosave pages: 00000000b6000000 - 0000000100000000
Dec 11 19:29:44 naomi-VGN-NS140E kernel: [15161.716397] PM: Basic memory bitmaps created
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ea8000 - 00000000b5ed0000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ed0000 - 00000000b5ee1000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ee1000 - 00000000b5ee2000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5ee2000 - 00000000b5f0a000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0a000 - 00000000b5f0b000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0b000 - 00000000b5f0c000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f0c000 - 00000000b5f17000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f17000 - 00000000b5f1d000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b5f1d000 - 00000000b5f39000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000b6000000 - 00000000e0000000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000ffa00000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5ea8000 (163840 bytes)
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5ee1000 (4096 bytes)
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5f0a000 (4096 bytes)
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.156996] PM: Registering ACPI NVS region at b5f17000 (24576 bytes)
Dec 11 19:31:04 naomi-VGN-NS140E kernel: [    0.932716] PM: Hibernation image not present or could not be loaded.
```

**dmesg** returns:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-13-generic (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 (Ubuntu 3.0.0-13.22-generic 3.0.6)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=5640e1e4-9c87-462d-ad73-ed50596079a2 ro quiet splash acpi_sleep=nonvs vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009bc00 (usable)
[    0.000000]  BIOS-e820: 000000000009bc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b5ea8000 (usable)
[    0.000000]  BIOS-e820: 00000000b5ea8000 - 00000000b5ed0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b5ed0000 - 00000000b5ee1000 (reserved)
[    0.000000]  BIOS-e820: 00000000b5ee1000 - 00000000b5ee2000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b5ee2000 - 00000000b5f0a000 (reserved)
[    0.000000]  BIOS-e820: 00000000b5f0a000 - 00000000b5f0b000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b5f0b000 - 00000000b5f0c000 (reserved)
[    0.000000]  BIOS-e820: 00000000b5f0c000 - 00000000b5f17000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b5f17000 - 00000000b5f1d000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b5f1d000 - 00000000b5f39000 (reserved)
[    0.000000]  BIOS-e820: 00000000b5f39000 - 00000000b6000000 (usable)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Sony Corporation VGN-NS140E/VAIO, BIOS R0190Y3 07/09/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E7FFF write-through
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0B8000000 mask FF8000000 uncachable
[    0.000000]   3 base 0B6000000 mask FFE000000 uncachable
[    0.000000]   4 base 100000000 mask FC0000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 2944MB, range: 128MB, type UC
[    0.000000] reg 3, base: 2912MB, range: 32MB, type UC
[    0.000000] reg 4, base: 4GB, range: 1GB, type WB
[    0.000000] total RAM covered: 3936M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 256M 	num_reg: 5  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 2912MB, range: 32MB, type UC
[    0.000000] reg 3, base: 2944MB, range: 128MB, type UC
[    0.000000] reg 4, base: 4GB, range: 1GB, type WB
[    0.000000] e820 update range: 00000000b6000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xb6000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fd650] fd650
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000b6000000
[    0.000000]  0000000000 - 00b6000000 page 2M
[    0.000000] kernel direct mapping tables up to b6000000 @ b5ffc000-b6000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ 13fffa000-140000000
[    0.000000] RAMDISK: 365b2000 - 372d1000
[    0.000000] ACPI: RSDP 00000000000f03b0 00024 (v02   Sony)
[    0.000000] ACPI: XSDT 00000000b5f15f10 0005C (v01   Sony     VAIO 20080709 MSFT 00010013)
[    0.000000] ACPI: FACP 00000000b5f0aa90 000F4 (v04   Sony     VAIO 20080709 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110413/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xB5F1CE40/0x00000000B5F1CD40, using 32 (20110413/tbfadt-489)
[    0.000000] ACPI: DSDT 00000000b5f0c010 07AFE (v01   Sony     VAIO 20080709 INTL 20051117)
[    0.000000] ACPI: FACS 00000000b5f1ce40 00040
[    0.000000] ACPI: APIC 00000000b5f14f10 0006C (v02   Sony     VAIO 20080709 MSFT 00010013)
[    0.000000] ACPI: MCFG 00000000b5f1bc90 0003C (v01   Sony     VAIO 20080709 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000b5f1bc10 00038 (v01   Sony     VAIO 20080709 MSFT 00010013)
[    0.000000] ACPI: SLIC 00000000b5f17c10 00176 (v01   Sony     VAIO 20080709 Sony 01000000)
[    0.000000] ACPI: SSDT 00000000b5ee1590 00505 (v01   Sony     VAIO 20080709 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000b5eccc10 002E4 (v01   Sony     VAIO 20080709 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [000000013fffb000 - 000000013fffffff]
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff88013b800000-ffff88013effffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x000b5ea8
[    0.000000]     0: 0x000b5f39 -> 0x000b6000
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1007354
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3918 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 726951 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000b5ea8000 - 00000000b5ed0000
[    0.000000] PM: Registered nosave memory: 00000000b5ed0000 - 00000000b5ee1000
[    0.000000] PM: Registered nosave memory: 00000000b5ee1000 - 00000000b5ee2000
[    0.000000] PM: Registered nosave memory: 00000000b5ee2000 - 00000000b5f0a000
[    0.000000] PM: Registered nosave memory: 00000000b5f0a000 - 00000000b5f0b000
[    0.000000] PM: Registered nosave memory: 00000000b5f0b000 - 00000000b5f0c000
[    0.000000] PM: Registered nosave memory: 00000000b5f0c000 - 00000000b5f17000
[    0.000000] PM: Registered nosave memory: 00000000b5f17000 - 00000000b5f1d000
[    0.000000] PM: Registered nosave memory: 00000000b5f1d000 - 00000000b5f39000
[    0.000000] PM: Registered nosave memory: 00000000b6000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000ffa00000
[    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at b6000000 (gap: b6000000:2a000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88013fc00000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 989429
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=5640e1e4-9c87-462d-ad73-ed50596079a2 ro quiet splash acpi_sleep=nonvs vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3878652k/5242880k available (6105k kernel code, 1213464k absent, 150764k reserved, 4879k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 32505856 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1993.771 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3987.54 BogoMIPS (lpj=7975084)
[    0.004010] pid_max: default: 32768 minimum: 301
[    0.004045] Security Framework initialized
[    0.004065] AppArmor: AppArmor initialized
[    0.004068] Yama: becoming mindful.
[    0.004588] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.009459] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010474] Mount-cache hash table entries: 256
[    0.010655] Initializing cgroup subsys cpuacct
[    0.010663] Initializing cgroup subsys memory
[    0.010674] Initializing cgroup subsys devices
[    0.010677] Initializing cgroup subsys freezer
[    0.010679] Initializing cgroup subsys net_cls
[    0.010681] Initializing cgroup subsys blkio
[    0.010690] Initializing cgroup subsys perf_event
[    0.010725] CPU: Physical Processor ID: 0
[    0.010727] CPU: Processor Core ID: 0
[    0.010730] mce: CPU supports 6 MCE banks
[    0.010740] CPU0: Thermal monitoring enabled (TM2)
[    0.010745] using mwait in idle threads.
[    0.013490] ACPI: Core revision 20110413
[    0.020025] ftrace: allocating 25656 entries in 101 pages
[    0.024355] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.066767] CPU0: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz stepping 0d
[    0.068003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.068003] PEBS disabled due to CPU errata.
[    0.068003] ... version:                2
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] Booting Node   0, Processors  #1
[    0.068003] smpboot cpu 1: start_ip = 96000
[    0.156028] Brought up 2 CPUs
[    0.156031] Total of 2 processors activated (7974.63 BogoMIPS).
[    0.156996] devtmpfs: initialized
[    0.156996] PM: Registering ACPI NVS region at b5ea8000 (163840 bytes)
[    0.156996] PM: Registering ACPI NVS region at b5ee1000 (4096 bytes)
[    0.156996] PM: Registering ACPI NVS region at b5f0a000 (4096 bytes)
[    0.156996] PM: Registering ACPI NVS region at b5f17000 (24576 bytes)
[    0.157585] print_constraints: dummy: 
[    0.157620] Time: 19:30:22  Date: 12/11/11
[    0.157663] NET: Registered protocol family 16
[    0.157697] Trying to unpack rootfs image as initramfs...
[    0.157813] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.157816] ACPI: bus type pci registered
[    0.157903] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.157907] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.228174] PCI: Using configuration type 1 for base access
[    0.229191] bio: create slab <bio-0> at 0
[    0.231265] ACPI: EC: Look up EC in DSDT
[    0.233130] ACPI: Executed 1 blocks of module-level executable AML code
[    0.264100] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.303039] ACPI: SSDT 00000000b5ee5c10 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.303507] ACPI: Dynamic OEM Table Load:
[    0.303511] ACPI: SSDT           (null) 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.303665] ACPI: SSDT 00000000b5ee3810 007A2 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.304125] ACPI: Dynamic OEM Table Load:
[    0.304129] ACPI: SSDT           (null) 007A2 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.372404] ACPI: SSDT 00000000b5ee4d90 000FD (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.372873] ACPI: Dynamic OEM Table Load:
[    0.372877] ACPI: SSDT           (null) 000FD (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.392189] ACPI: SSDT 00000000b5ee2f90 00047 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.392649] ACPI: Dynamic OEM Table Load:
[    0.392652] ACPI: SSDT           (null) 00047 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.460055] Freeing initrd memory: 13436k freed
[    0.628139] ACPI: Interpreter enabled
[    0.628147] ACPI: (supports S0 S3 S4 S5)
[    0.628174] ACPI: Using IOAPIC for interrupt routing
[    0.664574] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.664763] ACPI: No dock devices found.
[    0.664765] HEST: Table not found.
[    0.664768] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.665060] \_SB_.PCI0:_OSC invalid UUID
[    0.665062] _OSC request data:1 8 1f 
[    0.665067] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.665545] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.665549] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.665552] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.665555] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.665557] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.665560] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.665563] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.665565] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.665568] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.665571] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
[    0.665588] pci 0000:00:00.0: [8086:2a40] type 0 class 0x000600
[    0.665614] DMAR: Forcing write-buffer flush capability
[    0.665616] DMAR: Disabling IOMMU for graphics on this chipset
[    0.665642] pci 0000:00:02.0: [8086:2a42] type 0 class 0x000300
[    0.665657] pci 0000:00:02.0: reg 10: [mem 0xd0000000-0xd03fffff 64bit]
[    0.665667] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.665674] pci 0000:00:02.0: reg 20: [io  0xe140-0xe147]
[    0.665710] pci 0000:00:02.1: [8086:2a43] type 0 class 0x000380
[    0.665724] pci 0000:00:02.1: reg 10: [mem 0xd0400000-0xd04fffff 64bit]
[    0.665821] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
[    0.665884] pci 0000:00:1a.0: reg 20: [io  0xe0e0-0xe0ff]
[    0.665949] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
[    0.666012] pci 0000:00:1a.1: reg 20: [io  0xe0c0-0xe0df]
[    0.666076] pci 0000:00:1a.2: [8086:2939] type 0 class 0x000c03
[    0.666139] pci 0000:00:1a.2: reg 20: [io  0xe0a0-0xe0bf]
[    0.666218] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
[    0.666247] pci 0000:00:1a.7: reg 10: [mem 0xd4204c00-0xd4204fff]
[    0.666346] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.666353] pci 0000:00:1a.7: PME# disabled
[    0.666387] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.666411] pci 0000:00:1b.0: reg 10: [mem 0xd4200000-0xd4203fff 64bit]
[    0.666497] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.666502] pci 0000:00:1b.0: PME# disabled
[    0.666532] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
[    0.666621] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.666627] pci 0000:00:1c.0: PME# disabled
[    0.666660] pci 0000:00:1c.1: [8086:2942] type 1 class 0x000604
[    0.666748] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.666753] pci 0000:00:1c.1: PME# disabled
[    0.666787] pci 0000:00:1c.2: [8086:2944] type 1 class 0x000604
[    0.666875] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.666880] pci 0000:00:1c.2: PME# disabled
[    0.666922] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
[    0.666985] pci 0000:00:1d.0: reg 20: [io  0xe080-0xe09f]
[    0.667050] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
[    0.667113] pci 0000:00:1d.1: reg 20: [io  0xe060-0xe07f]
[    0.667177] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
[    0.667240] pci 0000:00:1d.2: reg 20: [io  0xe040-0xe05f]
[    0.667319] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
[    0.667348] pci 0000:00:1d.7: reg 10: [mem 0xd4204800-0xd4204bff]
[    0.667446] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.667452] pci 0000:00:1d.7: PME# disabled
[    0.667481] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.668112] pci 0000:00:1f.0: [8086:2919] type 0 class 0x000601
[    0.668278] pci 0000:00:1f.2: [8086:2929] type 0 class 0x000106
[    0.668309] pci 0000:00:1f.2: reg 10: [io  0xe130-0xe137]
[    0.668322] pci 0000:00:1f.2: reg 14: [io  0xe120-0xe123]
[    0.668335] pci 0000:00:1f.2: reg 18: [io  0xe110-0xe117]
[    0.668347] pci 0000:00:1f.2: reg 1c: [io  0xe100-0xe103]
[    0.668360] pci 0000:00:1f.2: reg 20: [io  0xe020-0xe03f]
[    0.668373] pci 0000:00:1f.2: reg 24: [mem 0xd4204000-0xd42047ff]
[    0.668428] pci 0000:00:1f.2: PME# supported from D3hot
[    0.668433] pci 0000:00:1f.2: PME# disabled
[    0.668459] pci 0000:00:1f.3: [8086:2930] type 0 class 0x000c05
[    0.668483] pci 0000:00:1f.3: reg 10: [mem 0xd4205000-0xd42050ff 64bit]
[    0.668516] pci 0000:00:1f.3: reg 20: [io  0xe000-0xe01f]
[    0.668792] pci 0000:01:00.0: [11ab:4363] type 0 class 0x000200
[    0.668960] pci 0000:01:00.0: reg 10: [mem 0xd2d20000-0xd2d23fff 64bit]
[    0.669060] pci 0000:01:00.0: reg 18: [io  0xd000-0xd0ff]
[    0.669422] pci 0000:01:00.0: reg 30: [mem 0xd2d00000-0xd2d1ffff pref]
[    0.669732] pci 0000:01:00.0: supports D1 D2
[    0.669734] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.669760] pci 0000:01:00.0: PME# disabled
[    0.669912] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.669918] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.669923] pci 0000:00:1c.0:   bridge window [mem 0xd2d00000-0xd40fffff]
[    0.669932] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.669996] pci 0000:00:1c.1: PCI bridge to [bus 02-03]
[    0.670002] pci 0000:00:1c.1:   bridge window [io  0xc000-0xcfff]
[    0.670007] pci 0000:00:1c.1:   bridge window [mem 0xd1900000-0xd2cfffff]
[    0.670015] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.670111] pci 0000:04:00.0: [8086:4232] type 0 class 0x000280
[    0.670154] pci 0000:04:00.0: reg 10: [mem 0xd0500000-0xd0501fff 64bit]
[    0.670318] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.670326] pci 0000:04:00.0: PME# disabled
[    0.670379] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.670384] pci 0000:00:1c.2:   bridge window [io  0xb000-0xbfff]
[    0.670390] pci 0000:00:1c.2:   bridge window [mem 0xd0500000-0xd18fffff]
[    0.670398] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.670452] pci 0000:05:03.0: [1180:0832] type 0 class 0x000c00
[    0.670478] pci 0000:05:03.0: reg 10: [mem 0xd4100000-0xd41007ff]
[    0.670570] pci 0000:05:03.0: PME# supported from D0 D3hot D3cold
[    0.670576] pci 0000:05:03.0: PME# disabled
[    0.670601] pci 0000:05:03.1: [1180:0822] type 0 class 0x000805
[    0.670624] pci 0000:05:03.1: reg 10: [mem 0xd4100900-0xd41009ff]
[    0.670714] pci 0000:05:03.1: supports D1 D2
[    0.670716] pci 0000:05:03.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.670722] pci 0000:05:03.1: PME# disabled
[    0.670745] pci 0000:05:03.2: [1180:0592] type 0 class 0x000880
[    0.670768] pci 0000:05:03.2: reg 10: [mem 0xd4100800-0xd41008ff]
[    0.670858] pci 0000:05:03.2: supports D1 D2
[    0.670861] pci 0000:05:03.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.670866] pci 0000:05:03.2: PME# disabled
[    0.670939] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.670945] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.670950] pci 0000:00:1e.0:   bridge window [mem 0xd4100000-0xd41fffff]
[    0.670959] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.670962] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.670965] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.670968] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.670970] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.670973] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.670976] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.670979] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.670982] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.670985] pci 0000:00:1e.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.670988] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    0.671017] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.671153] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.671180] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.671215] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.671250] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.671382] \_SB_.PCI0:_OSC invalid UUID
[    0.671384] _OSC request data:1 1f 1f 
[    0.671389]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.671429] \_SB_.PCI0:_OSC invalid UUID
[    0.671431] _OSC request data:1 0 1d 
[    0.671436]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    0.671438] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.677716] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.677769] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[    0.677820] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.677870] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.677920] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.677971] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.678020] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.678076] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.678199] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.678214] vgaarb: loaded
[    0.678216] vgaarb: bridge control possible 0000:00:02.0
[    0.678431] SCSI subsystem initialized
[    0.678448] libata version 3.00 loaded.
[    0.678448] usbcore: registered new interface driver usbfs
[    0.678448] usbcore: registered new interface driver hub
[    0.678448] usbcore: registered new device driver usb
[    0.678448] PCI: Using ACPI for IRQ routing
[    0.689939] PCI: pci_cache_line_size set to 64 bytes
[    0.690057] reserve RAM buffer: 000000000009bc00 - 000000000009ffff 
[    0.690061] reserve RAM buffer: 00000000b5ea8000 - 00000000b7ffffff 
[    0.690064] reserve RAM buffer: 00000000b6000000 - 00000000b7ffffff 
[    0.690180] NetLabel: Initializing
[    0.690182] NetLabel:  domain hash size = 128
[    0.690184] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.690198] NetLabel:  unlabeled traffic allowed by default
[    0.690243] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.690250] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.690256] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.696062] Switching to clocksource hpet
[    0.699942] Switched to NOHz mode on CPU #0
[    0.699994] Switched to NOHz mode on CPU #1
[    0.703855] AppArmor: AppArmor Filesystem Enabled
[    0.703893] pnp: PnP ACPI init
[    0.703913] ACPI: bus type pnp registered
[    0.704228] pnp 00:00: [bus 00-ff]
[    0.704232] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.704234] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.704236] pnp 00:00: [io  0x0d00-0xffff window]
[    0.704239] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.704241] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.704244] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.704246] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.704248] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.704251] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.704253] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.704256] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.704258] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.704261] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.704263] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.704265] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.704268] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.704270] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.704273] pnp 00:00: [mem 0xc0000000-0xfebfffff window]
[    0.704275] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.704354] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.704369] pnp 00:01: [io  0x0000-0x001f]
[    0.704371] pnp 00:01: [io  0x0081-0x0091]
[    0.704373] pnp 00:01: [io  0x0093-0x009f]
[    0.704375] pnp 00:01: [io  0x00c0-0x00df]
[    0.704377] pnp 00:01: [dma 4]
[    0.704405] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.704415] pnp 00:02: [mem 0xff000000-0xffffffff]
[    0.704438] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.704520] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.704586] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.704590] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.704602] pnp 00:04: [io  0x00f0]
[    0.704617] pnp 00:04: [irq 13]
[    0.704645] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.704662] pnp 00:05: [io  0x002e-0x002f]
[    0.704664] pnp 00:05: [io  0x004e-0x004f]
[    0.704666] pnp 00:05: [io  0x0061]
[    0.704668] pnp 00:05: [io  0x0063]
[    0.704670] pnp 00:05: [io  0x0065]
[    0.704671] pnp 00:05: [io  0x0067]
[    0.704673] pnp 00:05: [io  0x0070]
[    0.704675] pnp 00:05: [io  0x0080]
[    0.704677] pnp 00:05: [io  0x0092]
[    0.704679] pnp 00:05: [io  0x00b2-0x00b3]
[    0.704681] pnp 00:05: [io  0x0680-0x069f]
[    0.704683] pnp 00:05: [io  0x1000-0x100f]
[    0.704684] pnp 00:05: [io  0x0800-0x0803]
[    0.704686] pnp 00:05: [io  0x0400-0x047f]
[    0.704688] pnp 00:05: [io  0x0500-0x053f]
[    0.704690] pnp 00:05: [io  0x164e-0x164f]
[    0.704744] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.704748] system 00:05: [io  0x1000-0x100f] has been reserved
[    0.704751] system 00:05: [io  0x0800-0x0803] has been reserved
[    0.704754] system 00:05: [io  0x0400-0x047f] has been reserved
[    0.704756] system 00:05: [io  0x0500-0x053f] has been reserved
[    0.704759] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.704763] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.704773] pnp 00:06: [io  0x0070-0x0077]
[    0.704779] pnp 00:06: [irq 8]
[    0.704807] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.704819] pnp 00:07: [io  0x0060]
[    0.704821] pnp 00:07: [io  0x0064]
[    0.704827] pnp 00:07: [irq 1]
[    0.704853] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.704867] pnp 00:08: [irq 12]
[    0.704893] pnp 00:08: Plug and Play ACPI device, IDs SNY9008 PNP0f13 (active)
[    0.705089] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.705092] pnp 00:09: [mem 0xfed14000-0xfed17fff]
[    0.705094] pnp 00:09: [mem 0xfed18000-0xfed18fff]
[    0.705096] pnp 00:09: [mem 0xfed19000-0xfed19fff]
[    0.705099] pnp 00:09: [mem 0xe0000000-0xefffffff]
[    0.705101] pnp 00:09: [mem 0xfed20000-0xfed3ffff]
[    0.705103] pnp 00:09: [mem 0xfeb00000-0xfeb03fff]
[    0.705105] pnp 00:09: [mem 0xfed45000-0xfed8ffff]
[    0.705176] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.705179] system 00:09: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.705182] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.705185] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.705188] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.705191] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.705194] system 00:09: [mem 0xfeb00000-0xfeb03fff] has been reserved
[    0.705197] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.705201] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.720839] pnp: PnP ACPI: found 10 devices
[    0.720841] ACPI: ACPI bus type pnp unregistered
[    0.727023] PCI: max bus depth: 1 pci_try_num: 2
[    0.727078] pci 0000:00:1c.2: BAR 15: assigned [mem 0xd4300000-0xd44fffff 64bit pref]
[    0.727085] pci 0000:00:1c.1: BAR 15: assigned [mem 0xd4500000-0xd46fffff 64bit pref]
[    0.727091] pci 0000:00:1c.0: BAR 15: assigned [mem 0xd4700000-0xd48fffff 64bit pref]
[    0.727095] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.727099] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.727106] pci 0000:00:1c.0:   bridge window [mem 0xd2d00000-0xd40fffff]
[    0.727111] pci 0000:00:1c.0:   bridge window [mem 0xd4700000-0xd48fffff 64bit pref]
[    0.727120] pci 0000:00:1c.1: PCI bridge to [bus 02-03]
[    0.727124] pci 0000:00:1c.1:   bridge window [io  0xc000-0xcfff]
[    0.727130] pci 0000:00:1c.1:   bridge window [mem 0xd1900000-0xd2cfffff]
[    0.727136] pci 0000:00:1c.1:   bridge window [mem 0xd4500000-0xd46fffff 64bit pref]
[    0.727145] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.727148] pci 0000:00:1c.2:   bridge window [io  0xb000-0xbfff]
[    0.727155] pci 0000:00:1c.2:   bridge window [mem 0xd0500000-0xd18fffff]
[    0.727160] pci 0000:00:1c.2:   bridge window [mem 0xd4300000-0xd44fffff 64bit pref]
[    0.727169] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.727171] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.727178] pci 0000:00:1e.0:   bridge window [mem 0xd4100000-0xd41fffff]
[    0.727183] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.727208] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.727214] pci 0000:00:1c.0: setting latency timer to 64
[    0.727226] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.727232] pci 0000:00:1c.1: setting latency timer to 64
[    0.727243] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.727248] pci 0000:00:1c.2: setting latency timer to 64
[    0.727257] pci 0000:00:1e.0: setting latency timer to 64
[    0.727262] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.727265] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.727267] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.727270] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.727272] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.727275] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.727277] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.727280] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.727282] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.727285] pci_bus 0000:00: resource 13 [mem 0xc0000000-0xfebfffff]
[    0.727288] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.727290] pci_bus 0000:01: resource 1 [mem 0xd2d00000-0xd40fffff]
[    0.727293] pci_bus 0000:01: resource 2 [mem 0xd4700000-0xd48fffff 64bit pref]
[    0.727296] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.727298] pci_bus 0000:02: resource 1 [mem 0xd1900000-0xd2cfffff]
[    0.727301] pci_bus 0000:02: resource 2 [mem 0xd4500000-0xd46fffff 64bit pref]
[    0.727304] pci_bus 0000:04: resource 0 [io  0xb000-0xbfff]
[    0.727306] pci_bus 0000:04: resource 1 [mem 0xd0500000-0xd18fffff]
[    0.727309] pci_bus 0000:04: resource 2 [mem 0xd4300000-0xd44fffff 64bit pref]
[    0.727312] pci_bus 0000:05: resource 1 [mem 0xd4100000-0xd41fffff]
[    0.727314] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.727317] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.727319] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.727322] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.727324] pci_bus 0000:05: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.727327] pci_bus 0000:05: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.727329] pci_bus 0000:05: resource 10 [mem 0x000dc000-0x000dffff]
[    0.727332] pci_bus 0000:05: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.727334] pci_bus 0000:05: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.727337] pci_bus 0000:05: resource 13 [mem 0xc0000000-0xfebfffff]
[    0.727380] NET: Registered protocol family 2
[    0.727558] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.728956] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.732986] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.733482] TCP: Hash tables configured (established 524288 bind 65536)
[    0.733484] TCP reno registered
[    0.733496] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.733539] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.733714] NET: Registered protocol family 1
[    0.733737] pci 0000:00:02.0: Boot video device
[    0.734157] PCI: CLS 64 bytes, default 64
[    0.734160] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.734163] Placing 64MB software IO TLB between ffff8800b1ea8000 - ffff8800b5ea8000
[    0.734166] software IO TLB at phys 0xb1ea8000 - 0xb5ea8000
[    0.734562] audit: initializing netlink socket (disabled)
[    0.734575] type=2000 audit(1323631821.728:1): initialized
[    0.767824] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.790863] VFS: Disk quotas dquot_6.5.2
[    0.790932] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.791598] fuse init (API version 7.16)
[    0.791694] msgmni has been set to 7601
[    0.792140] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.792174] io scheduler noop registered
[    0.792177] io scheduler deadline registered
[    0.792221] io scheduler cfq registered (default)
[    0.792348] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.792413] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.792500] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.792560] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.792640] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.792696] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.792797] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.792821] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.792868] intel_idle: MWAIT substates: 0x22220
[    0.792870] intel_idle: does not run on family 6 model 15
[    0.793647] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.794493] ACPI: AC Adapter [ADP1] (on-line)
[    0.794609] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.796385] ACPI: Lid Switch [LID0]
[    0.796428] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.796434] ACPI: Power Button [PWRB]
[    0.796462] ACPI: acpi_idle registered with cpuidle
[    0.797394] Monitor-Mwait will be used to enter C-1 state
[    0.797428] Monitor-Mwait will be used to enter C-2 state
[    0.797459] Monitor-Mwait will be used to enter C-3 state
[    0.797467] Marking TSC unstable due to TSC halts in idle
[    0.814668] thermal LNXTHERM:00: registered as thermal_zone0
[    0.814671] ACPI: Thermal Zone [TZ00] (55 C)
[    0.815672] ACPI: Invalid active0 threshold
[    0.816553] thermal LNXTHERM:01: registered as thermal_zone1
[    0.816556] ACPI: Thermal Zone [TZ01] (55 C)
[    0.816583] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.816604] ERST: Table is not found!
[    0.816678] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.859853] ACPI: Battery Slot [BAT0] (battery present)
[    0.880762] Linux agpgart interface v0.103
[    0.880875] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[    0.881069] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    0.882188] agpgart-intel 0000:00:00.0: detected 131072K stolen memory
[    0.882321] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    0.883483] brd: module loaded
[    0.884046] loop: module loaded
[    0.884514] Fixed MDIO Bus: probed
[    0.884540] PPP generic driver version 2.4.2
[    0.884577] tun: Universal TUN/TAP device driver, 1.6
[    0.884579] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.884657] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.884690] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.884709] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.884714] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.884747] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.884780] ehci_hcd 0000:00:1a.7: debug port 1
[    0.888656] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.888674] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xd4204c00
[    0.904017] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.904139] hub 1-0:1.0: USB hub found
[    0.904144] hub 1-0:1.0: 6 ports detected
[    0.904232] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.904245] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.904250] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.904289] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.904319] ehci_hcd 0000:00:1d.7: debug port 1
[    0.908217] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.908232] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd4204800
[    0.924019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.924114] hub 2-0:1.0: USB hub found
[    0.924118] hub 2-0:1.0: 6 ports detected
[    0.924197] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.924211] uhci_hcd: USB Universal Host Controller Interface driver
[    0.924234] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.924242] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.924245] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.924284] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.924326] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e0e0
[    0.924444] hub 3-0:1.0: USB hub found
[    0.924449] hub 3-0:1.0: 2 ports detected
[    0.924522] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.924530] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.924533] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.924569] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.924609] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e0c0
[    0.924727] hub 4-0:1.0: USB hub found
[    0.924732] hub 4-0:1.0: 2 ports detected
[    0.924800] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.924807] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.924811] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.924853] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.924882] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000e0a0
[    0.925001] hub 5-0:1.0: USB hub found
[    0.925006] hub 5-0:1.0: 2 ports detected
[    0.925075] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.925082] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.925086] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.925118] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.925147] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e080
[    0.925265] hub 6-0:1.0: USB hub found
[    0.925269] hub 6-0:1.0: 2 ports detected
[    0.925334] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.925341] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.925345] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.925390] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.925420] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e060
[    0.925542] hub 7-0:1.0: USB hub found
[    0.925546] hub 7-0:1.0: 2 ports detected
[    0.925615] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.925622] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.925625] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.925660] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.925701] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e040
[    0.925824] hub 8-0:1.0: USB hub found
[    0.925829] hub 8-0:1.0: 2 ports detected
[    0.925937] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.930928] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.930937] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.931047] mousedev: PS/2 mouse device common for all mice
[    0.931168] rtc_cmos 00:06: RTC can wake from S4
[    0.931293] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.931325] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.931431] device-mapper: uevent: version 1.0.3
[    0.931504] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.931567] cpuidle: using governor ladder
[    0.931660] cpuidle: using governor menu
[    0.931662] EFI Variables Facility v0.08 2004-May-17
[    0.931930] TCP cubic registered
[    0.932075] NET: Registered protocol family 10
[    0.932601] NET: Registered protocol family 17
[    0.932617] Registering the dns_resolver key type
[    0.932716] PM: Hibernation image not present or could not be loaded.
[    0.932729] registered taskstats version 1
[    0.950604]   Magic number: 7:357:546
[    0.950637] tty ttyS22: hash matches
[    0.950665] mem null: hash matches
[    0.950733] rtc_cmos 00:06: setting system clock to 2011-12-11 19:30:22 UTC (1323631822)
[    0.951282] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.951284] EDD information not available.
[    0.953349] Freeing unused kernel memory: 984k freed
[    0.953654] Write protecting the kernel read-only data: 10240k
[    0.953910] Freeing unused kernel memory: 20k freed
[    0.959264] Freeing unused kernel memory: 1396k freed
[    0.965372] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.978157] udevd[86]: starting version 173
[    1.048687] sky2: driver version 1.28
[    1.048734] sky2 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.048749] sky2 0000:01:00.0: setting latency timer to 64
[    1.048786] sky2 0000:01:00.0: Yukon-2 EC Ultra chip revision 3
[    1.048923] sky2 0000:01:00.0: irq 43 for MSI/MSI-X
[    1.053244] sky2 0000:01:00.0: eth0: addr 00:1d:ba:84:64:26
[    1.072508] firewire_ohci 0000:05:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.073470] sdhci: Secure Digital Host Controller Interface driver
[    1.073473] sdhci: Copyright(c) Pierre Ossman
[    1.076980] ahci 0000:00:1f.2: version 3.0
[    1.076998] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.077063] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.077139] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.077143] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc ems 
[    1.077149] ahci 0000:00:1f.2: setting latency timer to 64
[    1.084818] scsi0 : ahci
[    1.085012] scsi1 : ahci
[    1.085104] scsi2 : ahci
[    1.085189] scsi3 : ahci
[    1.085297] ata1: SATA max UDMA/133 abar m2048@0xd4204000 port 0xd4204100 irq 44
[    1.085302] ata2: SATA max UDMA/133 abar m2048@0xd4204000 port 0xd4204180 irq 44
[    1.085304] ata3: DUMMY
[    1.085306] ata4: DUMMY
[    1.140149] firewire_ohci: Added fw-ohci device 0000:05:03.0, OHCI v1.0, 4 IR + 4 IT contexts, quirks 0x1
[    1.140228] sdhci-pci 0000:05:03.1: SDHCI controller found [1180:0822] (rev 22)
[    1.140246] sdhci-pci 0000:05:03.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.140288] sdhci-pci 0000:05:03.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.140315] mmc0: no vmmc regulator found
[    1.140347] Registered led device: mmc0::
[    1.140393] mmc0: SDHCI controller on PCI [0000:05:03.1] using DMA
[    1.216096] usb 1-2: new high speed USB device number 2 using ehci_hcd
[    1.408075] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.408102] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.408907] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.408913] ata1.00: ATA-8: ST9250827AS, 3.AAB, max UDMA/133
[    1.408916] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.409477] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.409482] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.409488] ata1.00: configured for UDMA/133
[    1.409654] scsi 0:0:0:0: Direct-Access     ATA      ST9250827AS      3.AA PQ: 0 ANSI: 5
[    1.409818] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.409828] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.409872] sd 0:0:0:0: [sda] Write Protect is off
[    1.409876] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.409903] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.421027] ata2.00: ATAPI: Optiarc DVD RW AD-7560S, SS03, max UDMA/100
[    1.434479] ata2.00: configured for UDMA/100
[    1.436448] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7560S  SS03 PQ: 0 ANSI: 5
[    1.440160] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.440164] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.440265] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.440330] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.494368]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 >
[    1.494800] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.640213] firewire_core: created device fw0: GUID 0800460302da9714, S400
[    7.409703] EXT4-fs (sda8): INFO: recovery required on readonly filesystem
[    7.409707] EXT4-fs (sda8): write access will be enabled during recovery
[   14.720961] EXT4-fs (sda8): orphan cleanup on readonly fs
[   14.720971] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 2231856
[   14.721031] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 2231971
[   14.721051] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 2231965
[   14.721102] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 2227263
[   14.721120] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 2231957
[   14.721138] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 2228128
[   14.721175] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 2359841
[   14.721219] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 2359837
[   14.721236] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 2231937
[   14.721287] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 2231860
[   14.721305] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 2231938
[   14.721322] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 2231851
[   14.721340] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 1832415
[   14.721358] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 1832382
[   14.721383] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 2228303
[   14.721400] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 2231853
[   14.721416] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 2227264
[   14.721433] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 2228127
[   14.721450] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 262448
[   14.721462] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 2236204
[   14.721480] EXT4-fs (sda8): ext4_orphan_cleanup: deleting unreferenced inode 2236263
[   14.721496] EXT4-fs (sda8): 21 orphan inodes deleted
[   14.721499] EXT4-fs (sda8): recovery complete
[   15.090862] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   31.727465] udevd[307]: starting version 173
[   31.767853] lp: driver loaded but no devices found
[   31.811264] Adding 4194300k swap on /dev/sda5.  Priority:-1 extents:1 across:4194300k 
[   32.329308] sony_laptop: Sony Notebook Control Driver v0.6
[   32.361553] cfg80211: Calling CRDA to update world regulatory domain
[   32.376710] [drm] Initialized drm 1.1.0 20060810
[   32.412836] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/SNY5001:00/input/input3
[   32.413904] input: Sony Vaio Jogdial as /devices/virtual/input/input4
[   32.414159] sony_laptop: brightness ignored, must be controlled by ACPI video driver
[   32.417167] type=1400 audit(1323649853.963:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=546 comm="apparmor_parser"
[   32.417452] type=1400 audit(1323649853.963:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=546 comm="apparmor_parser"
[   32.417638] type=1400 audit(1323649853.963:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=546 comm="apparmor_parser"
[   32.432229] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   32.432233] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   32.432326] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   32.432337] iwlagn 0000:04:00.0: setting latency timer to 64
[   32.432374] iwlagn 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   32.437430] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   32.437443] i915 0000:00:02.0: setting latency timer to 64
[   32.455816] iwlagn 0000:04:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   32.455819] iwlagn 0000:04:00.0: Device SKU: 0Xb
[   32.468464] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   32.468555] iwlagn 0000:04:00.0: irq 45 for MSI/MSI-X
[   32.620157] ip_tables: (C) 2000-2006 Netfilter Core Team
[   32.631092] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[   32.631100] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   32.631102] [drm] Driver supports precise vblank timestamp query.
[   32.631154] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   32.663973] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   32.738439] cfg80211: World regulatory domain updated:
[   32.738443] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   32.738446] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   32.738450] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   32.738453] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   32.738456] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   32.738459] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   32.750222] Linux video capture interface: v2.00
[   32.752649] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:18b3)
[   32.756535] input: UVC Camera (05ca:18b3) as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input5
[   32.756721] usbcore: registered new interface driver uvcvideo
[   32.756724] USB Video Class driver (v1.1.0)
[   32.767721] iwlagn 0000:04:00.0: loaded firmware version 8.83.5.1 build 33692
[   32.768052] Registered led device: phy0-led
[   32.768083] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   32.768509] fbcon: inteldrmfb (fb0) is primary device
[   32.768617] Console: switching to colour frame buffer device 160x50
[   32.768644] fb0: inteldrmfb frame buffer device
[   32.768646] drm: registered panic notifier
[   32.770571] acpi device:15: registered as cooling_device2
[   32.770711] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   32.770765] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   32.770854] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   32.770949] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   32.771028] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   32.771063] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   32.774336] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   32.810399] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro
[   32.837029] hda_codec: ALC262: SKU not ready 0x411111f0
[   32.837092] hda_codec: ALC262: BIOS auto-probing.
[   32.847195] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   32.847314] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   33.283036] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04711/0xa00000/0x20000
[   33.327558] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   34.647753] EXT4-fs (sda6): warning: maximal mount count reached, running e2fsck is recommended
[   34.648152] EXT4-fs (sda6): recovery complete
[   34.648291] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   34.706059] EXT4-fs (sda7): warning: maximal mount count reached, running e2fsck is recommended
[   34.706531] EXT4-fs (sda7): recovery complete
[   34.706689] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   43.125609] ppdev: user-space parallel port driver
[   43.153581] type=1400 audit(1323649864.699:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=978 comm="apparmor_parser"
[   43.157373] type=1400 audit(1323649864.703:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=976 comm="apparmor_parser"
[   43.164967] type=1400 audit(1323649864.711:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=976 comm="apparmor_parser"
[   43.166344] type=1400 audit(1323649864.711:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=977 comm="apparmor_parser"
[   43.173218] type=1400 audit(1323649864.719:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=978 comm="apparmor_parser"
[   43.173410] type=1400 audit(1323649864.719:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=978 comm="apparmor_parser"
[   43.188149] type=1400 audit(1323649864.735:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=979 comm="apparmor_parser"
[   43.198929] type=1400 audit(1323649864.743:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=984 comm="apparmor_parser"
[   43.202531] type=1400 audit(1323649864.747:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=979 comm="apparmor_parser"
[   43.203108] type=1400 audit(1323649864.747:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=984 comm="apparmor_parser"
[   43.320973] sky2 0000:01:00.0: eth0: enabling interface
[   43.332084] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   43.363949] init: failsafe main process (906) killed by TERM signal
[   43.367834] init: apport pre-start process (1059) terminated with status 1
[   43.402419] init: apport post-stop process (1089) terminated with status 1
[   43.538630] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.623238] Bluetooth: Core ver 2.16
[   43.623279] NET: Registered protocol family 31
[   43.623281] Bluetooth: HCI device and connection manager initialized
[   43.623284] Bluetooth: HCI socket layer initialized
[   43.623286] Bluetooth: L2CAP socket layer initialized
[   43.623896] Bluetooth: SCO socket layer initialized
[   43.627385] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   43.627389] Bluetooth: BNEP filters: protocol multicast
[   43.628859] Bluetooth: RFCOMM TTY layer initialized
[   43.628865] Bluetooth: RFCOMM socket layer initialized
[   43.628867] Bluetooth: RFCOMM ver 1.11
[   43.762621] init: plymouth-upstart-bridge main process (939) killed by TERM signal
[   44.532619] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
[   44.537130] EXT4-fs (sda6): re-mounted. Opts: commit=0
[   44.539408] EXT4-fs (sda7): re-mounted. Opts: commit=0
[   44.857811] init: plymouth-stop pre-start process (1394) terminated with status 1
[   47.560757] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
[   47.563879] EXT4-fs (sda6): re-mounted. Opts: commit=0
[   47.567044] EXT4-fs (sda7): re-mounted. Opts: commit=0
[   51.217411] wlan0: authenticate with 00:1c:0e:41:26:00 (try 1)
[   51.219494] wlan0: authenticated
[   51.220544] wlan0: associate with 00:1c:0e:41:26:00 (try 1)
[   51.223697] wlan0: RX AssocResp from 00:1c:0e:41:26:00 (capab=0x421 status=0 aid=62)
[   51.223703] wlan0: associated
[   51.231173] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   59.944772] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:07:eb:4c:e4:42:08:00 SRC=199.47.217.144 DST=172.16.130.197 LEN=219 TOS=0x00 PREC=0x00 TTL=52 ID=34162 DF PROTO=TCP SPT=80 DPT=49428 WINDOW=26800 RES=0x00 ACK PSH URGP=0 
[   61.744075] wlan0: no IPv6 routers present
[  175.685413] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:07:eb:4c:e4:42:08:00 SRC=173.225.132.34 DST=172.16.130.197 LEN=46 TOS=0x00 PREC=0x00 TTL=48 ID=9695 DF PROTO=TCP SPT=443 DPT=33098 WINDOW=19040 RES=0x00 ACK PSH URGP=0 
[  175.686140] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:07:eb:4c:e4:42:08:00 SRC=173.225.132.34 DST=172.16.130.197 LEN=41 TOS=0x00 PREC=0x00 TTL=48 ID=9696 DF PROTO=TCP SPT=443 DPT=33098 WINDOW=19040 RES=0x00 ACK PSH URGP=0 
[  175.919745] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:07:eb:4c:e4:42:08:00 SRC=173.225.132.34 DST=172.16.130.197 LEN=47 TOS=0x00 PREC=0x00 TTL=48 ID=9697 DF PROTO=TCP SPT=443 DPT=33098 WINDOW=19040 RES=0x00 ACK PSH URGP=0 
[  176.397277] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:07:eb:4c:e4:42:08:00 SRC=173.225.132.34 DST=172.16.130.197 LEN=47 TOS=0x00 PREC=0x00 TTL=48 ID=9698 DF PROTO=TCP SPT=443 DPT=33098 WINDOW=19040 RES=0x00 ACK PSH URGP=0 
[  177.357431] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:07:eb:4c:e4:42:08:00 SRC=173.225.132.34 DST=172.16.130.197 LEN=47 TOS=0x00 PREC=0x00 TTL=48 ID=9699 DF PROTO=TCP SPT=443 DPT=33098 WINDOW=19040 RES=0x00 ACK PSH URGP=0 
[  179.286111] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:07:eb:4c:e4:42:08:00 SRC=173.225.132.34 DST=172.16.130.197 LEN=47 TOS=0x00 PREC=0x00 TTL=48 ID=9700 DF PROTO=TCP SPT=443 DPT=33098 WINDOW=19040 RES=0x00 ACK PSH URGP=0 
[  183.134831] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:07:eb:4c:e4:42:08:00 SRC=173.225.132.34 DST=172.16.130.197 LEN=47 TOS=0x00 PREC=0x00 TTL=48 ID=9701 DF PROTO=TCP SPT=443 DPT=33098 WINDOW=19040 RES=0x00 ACK PSH URGP=0 
[  190.820971] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:07:eb:4c:e4:42:08:00 SRC=173.225.132.34 DST=172.16.130.197 LEN=47 TOS=0x00 PREC=0x00 TTL=48 ID=9702 DF PROTO=TCP SPT=443 DPT=33098 WINDOW=19040 RES=0x00 ACK PSH URGP=0 
[  206.212953] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:07:eb:4c:e4:42:08:00 SRC=173.225.132.34 DST=172.16.130.197 LEN=47 TOS=0x00 PREC=0x00 TTL=48 ID=9703 DF PROTO=TCP SPT=443 DPT=33098 WINDOW=19040 RES=0x00 ACK PSH URGP=0 
[  236.956980] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:07:eb:4c:e4:42:08:00 SRC=173.225.132.34 DST=172.16.130.197 LEN=47 TOS=0x00 PREC=0x00 TTL=48 ID=9704 DF PROTO=TCP SPT=443 DPT=33098 WINDOW=19040 RES=0x00 ACK PSH URGP=0 
[  298.527879] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:07:eb:4c:e4:42:08:00 SRC=173.225.132.34 DST=172.16.130.197 LEN=47 TOS=0x00 PREC=0x00 TTL=48 ID=9705 DF PROTO=TCP SPT=443 DPT=33098 WINDOW=19040 RES=0x00 ACK PSH URGP=0 
[  350.746892] wlan0: authenticate with 00:1b:8f:89:a4:20 (try 1)
[  350.748812] wlan0: authenticated
[  350.769874] wlan0: associate with 00:1b:8f:89:a4:20 (try 1)
[  350.771486] wlan0: RX ReassocResp from 00:1b:8f:89:a4:20 (capab=0x421 status=0 aid=238)
[  350.771495] wlan0: associated
[  418.626865] Inbound IN=wlan0 OUT= MAC=00:21:5d:00:d8:bc:00:07:eb:4c:e4:42:08:00 SRC=173.225.132.34 DST=172.16.130.197 LEN=47 TOS=0x00 PREC=0x00 TTL=48 ID=9706 DF PROTO=TCP SPT=443 DPT=33098 WINDOW=19040 RES=0x00 ACK PSH URGP=0 
```

**cat /etc/fstab** returns:
```
proc                                       /proc        proc  nodev,noexec,nosuid                                             0  0  
UUID=5640e1e4-9c87-462d-ad73-ed50596079a2  /            ext4  errors=remount-ro                                               0  1  
UUID=36924278-77a5-40db-9966-ac3bcfd9be54  none         swap  sw                                                              0  0  
/dev/sda1                                  /media/sda1  ntfs  defaults                                                        0  0  
/dev/sda2                                  /media/sda2  ntfs  defaults                                                        0  0  
/dev/sda3                                  /media/sda3  ntfs  nls=iso8859-1,group=naomi,users,umask=000,user,owner,uid=naomi  0  0  
/dev/sda5                                  /media/sda5  swap  defaults                                                        0  0  
/dev/sda6                                  /media/sda6  ext4  defaults                                                        0  0  
/dev/sda7                                  /media/sda7  ext4  defaults                                                        0  0  
/dev/sdb1                                  /media/sdb1  ntfs  nls=iso8859-1,ro,users,umask=000                                0  0  
```

**sudo blkid** returns:
```
/dev/sda1: LABEL="Recovery" UUID="F8EE666BEE6621DC" TYPE="ntfs" 
/dev/sda2: LABEL="Win7 OS" UUID="C452D9DD52D9D470" TYPE="ntfs" 
/dev/sda3: LABEL="Data Files" UUID="80FA0C3BFA0C2FC8" TYPE="ntfs" 
/dev/sda5: UUID="1453748c-adaf-4e18-b468-41e847d0705e" TYPE="swap" 
/dev/sda6: UUID="62f3010c-d5c0-4aad-ad78-a23494d36f85" TYPE="ext4" 
/dev/sda7: UUID="35c96824-9b36-4def-b0cb-34841506a146" TYPE="ext4" 
/dev/sda8: UUID="5640e1e4-9c87-462d-ad73-ed50596079a2" TYPE="ext4" 
```

**cat /etc/initramfs-tools/conf.d/resume** returns:
```
RESUME=UUID=36924278-77a5-40db-9966-ac3bcfd9be54
```

---

### Post by drs305 on 2011-12-12
One thing I notice is that the swap UUID in fstab and RESUME is not the same as the actual swap partition UUID, which is: 
UUID="1453748c-adaf-4e18-b468-41e847d0705e"

The easiest way to fix this, since no other partitions are using the 'bad' swap UUID, is to change the actual UUID to what fstab and RESUME think it should be. It's a bit backward, but it's the easiest method to fix it and once accomplished everything will be normal again.
```

sudo tune2fs -U 36924278-77a5-40db-9966-ac3bcfd9be54 /dev/sda5
gksu gedit /etc/fstab &
sudo mount -a

```
You have two entries for swap in fstab. Remove the one referenced by /media/sda5, as two swaps are not necessary and they both will reference the same partition.

After saving the change in fstab the "mount" command should return no error messages.

---

### Post by Toz on 2011-12-12
> **drs305 said:**
> One thing I notice is that the swap UUID in fstab and RESUME is not the same as the actual swap partition UUID, which is: 
UUID="1453748c-adaf-4e18-b468-41e847d0705e"

The easiest way to fix this, since no other partitions are using the 'bad' swap UUID, is to change the actual UUID to what fstab and RESUME think it should be. It's a bit backward, but it's the easiest method to fix it and once accomplished everything will be normal again.
```

sudo tune2fs -U 36924278-77a5-40db-9966-ac3bcfd9be54 /dev/sda5
gksu gedit /etc/fstab &
sudo mount -a

```
You have two entries for swap in fstab. Remove the one referenced by /media/sda5, as two swaps are not necessary and they both will reference the same partition.

After saving the change in fstab the "mount" command should return no error messages.

+1
The UUID value in /etc/initramfs-tools/conf.d/resume should match the results of the swap UUID from blkid and the entry in fstab.

Your swap drive is not encrypted.

---

### Post by JadeMoonlight on 2011-12-12
About a month ago, I installed Oneiric to a new partition and was expecting it to recognize and use my existing swap partition. Apparently I did something wrong and a second swap partition was made during setup.

Some time after making this new Oneiric partition I upgraded my RAM, deleted **UUID="36924278-77a5-40db-9966-ac3bcfd9be54"**, which had likely been assigned to /dev/sda9 at the time, and resized **/dev/sda5: UUID="1453748c-adaf-4e18-b468-41e847d0705e" TYPE="swap"** to be a size appropriate to the RAM upgrade.

> **drs305 said:**
> 
```

sudo tune2fs -U 36924278-77a5-40db-9966-ac3bcfd9be54 /dev/sda5

```


This command returns:
```
tune2fs 1.41.14 (22-Dec-2010)
tune2fs: Bad magic number in super-block while trying to open /dev/sda5
Couldn't find valid filesystem superblock.

```
And I'm unsure whether it's safe to proceed from there, or how to proceed properly.
Does this output mean that **UUID="36924278-77a5-40db-9966-ac3bcfd9be54"** no longer exists, because I deleted it as mentioned earlier?


> **Toz said:**
> 
The UUID value in /etc/initramfs-tools/conf.d/resume should match the results of the swap UUID from blkid and the entry in fstab.


Would it make sense for me to physically change the UUID in **/etc/initramfs-tools/conf.d/resume** to the UUID listed as swap in **blkid** (UUID="1453748c-adaf-4e18-b468-41e847d0705e"), or am I not understanding that file's purpose correctly and would potentially break something even further by doing this?

---

### Post by drs305 on 2011-12-12
You can do it the normal way. 

Run the "sudo blkid -c /dev/null" command and note the UUID of the swap partition.
Put that UUID on the swap entry of fstab and in the RESUME file. Save both files.
Run the following to make sure the OS knows which partition is the swap:

```

gksu gedit /etc/initramfs-tools/conf.d/resume /etc/fstab
sudo update-initramfs -v -u -k all 
```

You should then be able to check if swap is ok with the following:
```
free -m  # Probably shows 0's for all swap entries
sudo swapoff -a
sudo swapon
free -m # Should now show values for swap. If not, reboot and run this command again.

```

---

### Post by JadeMoonlight on 2011-12-12
Okay, it all seems to be working as I would like it to now. Thank you both very much for all of your help!

I'm going to chalk the **ata1.00: revalidation failed (errno=-5)** message as an issue unrelated to power management problems.

Marking the thread as solved now.

P.S. I had to leave out the **/dev/null** of **sudo blkid /dev/null** for it to give me any output. ;)

---

### Post by drs305 on 2011-12-12
> **JadeMoonlight said:**
> P.S. I had to leave out the **/dev/null** of **sudo blkid /dev/null** for it to give me any output. ;)

My bad - thanks for pointing this out.

I dropped the **-c** switch. That switch forces the system to reread the partitions and ensures it doesn't provide an outdated listing. It's not common for that to happen, but it can. I've edited my previous post.

---

