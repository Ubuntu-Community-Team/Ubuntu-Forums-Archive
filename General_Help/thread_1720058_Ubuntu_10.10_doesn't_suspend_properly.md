---
title: "Ubuntu 10.10 doesn't suspend properly"
date: 2011-04-02
forum: General Help
---

### Post by b.schelberg on 2011-04-02
Occasionally when I suspend my laptop (HP Pavilion dv6) it begins the suspend process, but then the fan goes to full speed and my laptop remains in that state until I press and hold the power button to turn it off.

The end of the messages log is:
```
Apr  2 21:20:44 Morpheus kernel: [31276.709647] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Apr  2 21:20:44 Morpheus kernel: [31276.714084] EXT4-fs (sda9): re-mounted. Opts: commit=0
Apr  2 21:20:44 Morpheus kernel: [31276.776358] EXT4-fs (sda6): re-mounted. Opts: commit=0
Apr  2 21:20:44 Morpheus kernel: [31276.782068] EXT4-fs (sda8): re-mounted. Opts: commit=0
Apr  2 21:20:45 Morpheus kernel: [31278.068874] cfg80211: Calling CRDA to update world regulatory domain
Apr  2 21:20:45 Morpheus kernel: [31278.076137] cfg80211: World regulatory domain updated:
Apr  2 21:20:45 Morpheus kernel: [31278.076145]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  2 21:20:45 Morpheus kernel: [31278.076155]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 21:20:45 Morpheus kernel: [31278.076165]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 21:20:45 Morpheus kernel: [31278.076174]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 21:20:45 Morpheus kernel: [31278.076182]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 21:20:45 Morpheus kernel: [31278.076191]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
```

pm-suspend.log shows:
```
Sat Apr  2 21:20:44 EST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Morpheus 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux
Module                  Size  Used by
ipt_MASQUERADE          1919  1 
iptable_nat             4593  1 
nf_nat                 20067  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      13143  3 iptable_nat,nf_nat
nf_conntrack           75238  4 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1569  1 nf_conntrack_ipv4
ip_tables              19139  1 iptable_nat
x_tables               24423  3 ipt_MASQUERADE,iptable_nat,ip_tables
binfmt_misc             7984  1 
rfcomm                 40787  4 
sco                     9986  2 
bnep                   11985  2 
l2cap                  42304  16 rfcomm,bnep
vboxnetadp              5267  0 
vboxnetflt             14966  1 
vboxdrv              1792856  3 vboxnetadp,vboxnetflt
kvm_intel              49279  0 
kvm                   299345  1 kvm_intel
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_atihdmi     3079  1 
snd_hda_codec_idt      64699  1 
snd_hda_intel          26147  2 
snd_hda_codec         100951  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_seq_midi            5932  0 
snd_hwdep               6660  1 snd_hda_codec
joydev                 11395  0 
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_rawmidi            22207  1 snd_seq_midi
arc4                    1497  2 
snd_seq_midi_event      7291  1 snd_seq_midi
hp_accel               14304  0 
lis3lv02d              10384  1 hp_accel
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
input_polldev           4527  1 lis3lv02d
snd_timer              23850  2 snd_pcm,snd_seq
ath9k                 101858  0 
ath9k_common            6874  1 ath9k
ath9k_hw              314731  2 ath9k,ath9k_common
ath                    10413  2 ath9k,ath9k_hw
video                  22176  0 
mac80211              267099  2 ath9k,ath9k_common
cdc_ether               4920  0 
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              170485  4 ath9k,ath9k_common,ath,mac80211
btusb                  12929  2 
led_class               3393  2 hp_accel,ath9k
lp                     10201  0 
uvcvideo               62379  0 
output                  2527  1 video
videodev               49359  1 uvcvideo
psmouse                62080  0 
cdc_subset              3101  0 
serio_raw               4910  0 
usbnet                 20985  2 cdc_ether,cdc_subset
i7core_edac            18122  0 
edac_core              46822  1 i7core_edac
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev
snd                    64181  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hp_wmi                  6467  0 
fglrx                2523725  249 
soundcore               1240  1 snd
parport                37032  3 parport_pc,ppdev,lp
bluetooth              59245  9 rfcomm,sco,bnep,l2cap,btusb
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
usbhid                 42030  0 
hid                    84710  1 usbhid
ahci                   22210  6 
r8169                  42254  0 
libahci                26148  1 ahci
mii                     5261  2 usbnet,r8169
nbd                     9959  0 
             total       used       free     shared    buffers     cached
Mem:       3991576    3565884     425692          0     189344    1451396
-/+ buffers/cache:    1925144    2066432
Swap:      2321356       1824    2319532

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
Having NetworkManager put all interaces to sleep...method return sender=:1.4 -> dest=:1.237 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend:

/usr/lib/pm-utils/sleep.d/70action_wpa suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Runn
```
(that's not a cut'n'paste error - the last line is cut off in the log)

syslog shows:
```
Apr  2 21:20:44 Morpheus anacron[29884]: Anacron 2.3 started on 2011-04-02
Apr  2 21:20:44 Morpheus anacron[29884]: Normal exit (0 jobs run)
Apr  2 21:20:44 Morpheus kernel: [31276.709647] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Apr  2 21:20:44 Morpheus kernel: [31276.714084] EXT4-fs (sda9): re-mounted. Opts: commit=0
Apr  2 21:20:44 Morpheus kernel: [31276.776358] EXT4-fs (sda6): re-mounted. Opts: commit=0
Apr  2 21:20:44 Morpheus kernel: [31276.782068] EXT4-fs (sda8): re-mounted. Opts: commit=0
Apr  2 21:20:45 Morpheus NetworkManager[1236]: <info> sleep requested (sleeping: no  enabled: yes)
Apr  2 21:20:45 Morpheus NetworkManager[1236]: <info> sleeping or disabling...
Apr  2 21:20:45 Morpheus NetworkManager[1236]: <info> (wlan0): now unmanaged
Apr  2 21:20:45 Morpheus NetworkManager[1236]: <info> (wlan0): device state change: 8 -> 1 (reason 37)
Apr  2 21:20:45 Morpheus NetworkManager[1236]: <info> (wlan0): deactivating device (reason: 37).
Apr  2 21:20:45 Morpheus NetworkManager[1236]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 28903
Apr  2 21:20:45 Morpheus kernel: [31277.742488] wlan0: deauthenticating from 00:1b:11:d4:f7:1c by local choice (reason=3)
Apr  2 21:20:45 Morpheus avahi-daemon[1213]: Withdrawing address record for 10.1.1.11 on wlan0.
Apr  2 21:20:45 Morpheus avahi-daemon[1213]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.1.1.11.
Apr  2 21:20:45 Morpheus avahi-daemon[1213]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr  2 21:20:45 Morpheus NetworkManager[1236]: <info> (wlan0): cleaning up...
Apr  2 21:20:45 Morpheus NetworkManager[1236]: <info> (wlan0): taking down device.
Apr  2 21:20:45 Morpheus avahi-daemon[1213]: Interface wlan0.IPv6 no longer relevant for mDNS.
Apr  2 21:20:45 Morpheus avahi-daemon[1213]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::c646:19ff:fe2a:24b8.
Apr  2 21:20:45 Morpheus avahi-daemon[1213]: Withdrawing address record for fe80::c646:19ff:fe2a:24b8 on wlan0.
Apr  2 21:20:45 Morpheus wpa_supplicant[1346]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr  2 21:20:45 Morpheus NetworkManager[1236]: <info> (eth0): now unmanaged
Apr  2 21:20:45 Morpheus NetworkManager[1236]: <info> (eth0): device state change: 2 -> 1 (reason 37)
Apr  2 21:20:45 Morpheus NetworkManager[1236]: <info> (eth0): cleaning up...
Apr  2 21:20:45 Morpheus NetworkManager[1236]: <info> (eth0): taking down device.
Apr  2 21:20:45 Morpheus kernel: [31278.068856] cfg80211: All devices are disconnected, going to restore regulatory settings
Apr  2 21:20:45 Morpheus kernel: [31278.068867] cfg80211: Restoring regulatory settings
Apr  2 21:20:45 Morpheus kernel: [31278.068874] cfg80211: Calling CRDA to update world regulatory domain
Apr  2 21:20:45 Morpheus kernel: [31278.076137] cfg80211: World regulatory domain updated:
Apr  2 21:20:45 Morpheus kernel: [31278.076145]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  2 21:20:45 Morpheus kernel: [31278.076155]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 21:20:45 Morpheus kernel: [31278.076165]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 21:20:45 Morpheus kernel: [31278.076174]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  2 21:20:45 Morpheus kernel: [31278.076182]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 21:20:45 Morpheus kernel: [31278.076191]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  2 21:20:46 Morpheus NetworkManager[1236]: <info> (eth2): now unmanaged
Apr  2 21:20:46 Morpheus NetworkManager[1236]: <info> (eth2): device state change: 8 -> 1 (reason 37)
Apr  2 21:20:46 Morpheus NetworkManager[1236]: <iApr  3 08:53:14 Morpheus kernel: imklog 4.2.0, log source = /proc/kmsg started.
```
(again, note the last line not written to the log properly)

Any help in helping me track down what's happening here would be much appreciated.

Thanks,
Bernie

---

### Post by gordintoronto on 2011-04-02
How long did you give it? I've got an HP G62, and it has taken as long as 10 minutes to suspend -- but it did suspend properly.

---

### Post by b.schelberg on 2011-04-02
One time I gave it an hour. I don't like giving it too long, as it gets very hot - the fan spins up for a reason!
I have observed it taking a long time other times - sometimes it seems like it decides to write to swap instead of simply suspending to RAM. But that's not a CPU intensive operation, and the fan doesn't spin up. I can also see the hard disk activity light flashing, so I can see what's happening.
When the problem occurs, there's no hard disk activity.

---

### Post by gordintoronto on 2011-04-03
I usually end a session by simply closing the lid. If I'm connected to power, it suspends to RAM, but if I'm running on batteries it hibernates to swap. It's actually the hibernate which sometimes takes a long time, with the fan running at full speed, blowing hot air out the side.

---

### Post by b.schelberg on 2011-04-03
Yes, I usually suspend by closing the lid also. I always suspend before disconnecting power, as disconnecting power sometimes screws up my video display. Actually, my system is configured to suspend to RAM even if running on battery power - if I need to hibernate I do it manually.

---

