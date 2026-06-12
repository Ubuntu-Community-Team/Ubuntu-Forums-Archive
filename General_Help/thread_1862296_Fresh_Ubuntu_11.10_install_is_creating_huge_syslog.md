---
title: "Fresh Ubuntu 11.10 install is creating huge syslog &amp; kern.log"
date: 2011-10-16
forum: General Help
---

### Post by AnotherMuggle on 2011-10-16
I just upgraded to Ubuntu 11.10 on my netbook and desktop.  Netbook is fine, everything works great.  The desktop seems to be having a problem and I have syslog and kern.log files >1.5GB in under 1hr use.

The following messages are just repeatedly being spammed into the log files.  Can anyone help me out?

```
Oct 16 19:42:40 ubupc kernel: [ 3293.247019] bad: scheduling from the idle thread!
Oct 16 19:42:40 ubupc kernel: [ 3293.247026] Pid: 0, comm: swapper Tainted: G         C  3.0.0-12-generic #20-Ubuntu
Oct 16 19:42:40 ubupc kernel: [ 3293.247031] Call Trace:
Oct 16 19:42:40 ubupc kernel: [ 3293.247039]  [<ffffffff8104e529>] dequeue_task_idle+0x39/0x50
Oct 16 19:42:40 ubupc kernel: [ 3293.247046]  [<ffffffff81049143>] dequeue_task+0x93/0xb0
Oct 16 19:42:40 ubupc kernel: [ 3293.247053]  [<ffffffff8104918e>] deactivate_task+0x2e/0x40
Oct 16 19:42:40 ubupc kernel: [ 3293.247062]  [<ffffffff815e7b69>] schedule+0x589/0x770
Oct 16 19:42:40 ubupc kernel: [ 3293.247070]  [<ffffffff81009243>] cpu_idle+0xe3/0x100
Oct 16 19:42:40 ubupc kernel: [ 3293.247079]  [<ffffffff815b803e>] rest_init+0x72/0x74
Oct 16 19:42:40 ubupc kernel: [ 3293.247085]  [<ffffffff81ad0c2b>] start_kernel+0x3d4/0x3df
Oct 16 19:42:40 ubupc kernel: [ 3293.247094]  [<ffffffff81ad0388>] x86_64_start_reservations+0x132/0x136
Oct 16 19:42:40 ubupc kernel: [ 3293.247103]  [<ffffffff81ad0140>] ? early_idt_handlers+0x140/0x140
Oct 16 19:42:40 ubupc kernel: [ 3293.247111]  [<ffffffff81ad0459>] x86_64_start_kernel+0xcd/0xdc
Oct 16 19:42:40 ubupc kernel: [ 3293.252339] bad: scheduling from the idle thread!
Oct 16 19:42:40 ubupc kernel: [ 3293.252346] Pid: 0, comm: swapper Tainted: G         C  3.0.0-12-generic #20-Ubuntu
Oct 16 19:42:40 ubupc kernel: [ 3293.252350] Call Trace:
Oct 16 19:42:40 ubupc kernel: [ 3293.252358]  [<ffffffff8104e529>] dequeue_task_idle+0x39/0x50
Oct 16 19:42:40 ubupc kernel: [ 3293.252363]  [<ffffffff81049143>] dequeue_task+0x93/0xb0
Oct 16 19:42:40 ubupc kernel: [ 3293.252368]  [<ffffffff8104918e>] deactivate_task+0x2e/0x40
Oct 16 19:42:40 ubupc kernel: [ 3293.252374]  [<ffffffff815e7b69>] schedule+0x589/0x770
Oct 16 19:42:40 ubupc kernel: [ 3293.252380]  [<ffffffff81009243>] cpu_idle+0xe3/0x100
Oct 16 19:42:40 ubupc kernel: [ 3293.252387]  [<ffffffff815b803e>] rest_init+0x72/0x74
Oct 16 19:42:40 ubupc kernel: [ 3293.252391]  [<ffffffff81ad0c2b>] start_kernel+0x3d4/0x3df
Oct 16 19:42:40 ubupc kernel: [ 3293.252398]  [<ffffffff81ad0388>] x86_64_start_reservations+0x132/0x136
Oct 16 19:42:40 ubupc kernel: [ 3293.252404]  [<ffffffff81ad0140>] ? early_idt_handlers+0x140/0x140
Oct 16 19:42:40 ubupc kernel: [ 3293.252409]  [<ffffffff81ad0459>] x86_64_start_kernel+0xcd/0xdc
Oct 16 19:42:40 ubupc kernel: [ 3293.254093] bad: scheduling from the idle thread!
Oct 16 19:42:40 ubupc kernel: [ 3293.254101] Pid: 0, comm: swapper Tainted: G         C  3.0.0-12-generic #20-Ubuntu
Oct 16 19:42:40 ubupc kernel: [ 3293.254104] Call Trace:
Oct 16 19:42:40 ubupc kernel: [ 3293.254112]  [<ffffffff8104e529>] dequeue_task_idle+0x39/0x50
Oct 16 19:42:40 ubupc kernel: [ 3293.254118]  [<ffffffff81049143>] dequeue_task+0x93/0xb0
Oct 16 19:42:40 ubupc kernel: [ 3293.254122]  [<ffffffff8104918e>] deactivate_task+0x2e/0x40
Oct 16 19:42:40 ubupc kernel: [ 3293.254128]  [<ffffffff815e7b69>] schedule+0x589/0x770
Oct 16 19:42:40 ubupc kernel: [ 3293.254135]  [<ffffffff81009243>] cpu_idle+0xe3/0x100
Oct 16 19:42:40 ubupc kernel: [ 3293.254141]  [<ffffffff815b803e>] rest_init+0x72/0x74
Oct 16 19:42:40 ubupc kernel: [ 3293.254146]  [<ffffffff81ad0c2b>] start_kernel+0x3d4/0x3df
Oct 16 19:42:40 ubupc kernel: [ 3293.254152]  [<ffffffff81ad0388>] x86_64_start_reservations+0x132/0x136
Oct 16 19:42:40 ubupc kernel: [ 3293.254158]  [<ffffffff81ad0140>] ? early_idt_handlers+0x140/0x140
Oct 16 19:42:40 ubupc kernel: [ 3293.254164]  [<ffffffff81ad0459>] x86_64_start_kernel+0xcd/0xdc

```

Cheers,
Tom

Update: I was using the 64bit version on both machines.  I am now trying the 32bit version on the desktop and the error message appears to have gone away.

---

### Post by jonnan on 2011-10-31
After the second time I've added a gig to the var partition I found the exact same issue - the kernal log and sys log are 1.2 Gig apiece (*Minutes* ago they were ~850 Meg apiece) and there's a kern.log.2 backup that's 1.5 Gig.

Just the same error as the previous poster, over and over, evidently from the 23rd on.

Does anyone know what's going on here?

---

### Post by quan2m on 2011-11-15
Same issue. It seems to actually lock my machine when I use compositing... Without compositing, I have gotten 1.5GB of logs in 34 mins.

Nov 15 21:50:44 thur kernel: [ 3396.303016] bad: scheduling from the idle thread!
Nov 15 21:50:44 thur kernel: [ 3396.303019] Pid: 0, comm: swapper Tainted: P            3.0.0-12-generic #20-Ubuntu
Nov 15 21:50:44 thur kernel: [ 3396.303020] Call Trace:
Nov 15 21:50:44 thur kernel: [ 3396.303023]  [<ffffffff8104e529>] dequeue_task_idle+0x39/0x50
Nov 15 21:50:44 thur kernel: [ 3396.303026]  [<ffffffff81049143>] dequeue_task+0x93/0xb0
Nov 15 21:50:44 thur kernel: [ 3396.303028]  [<ffffffff8104918e>] deactivate_task+0x2e/0x40
Nov 15 21:50:44 thur kernel: [ 3396.303031]  [<ffffffff815e7b69>] schedule+0x589/0x770
Nov 15 21:50:44 thur kernel: [ 3396.303034]  [<ffffffff81009243>] cpu_idle+0xe3/0x100
Nov 15 21:50:44 thur kernel: [ 3396.303037]  [<ffffffff815b803e>] rest_init+0x72/0x74
Nov 15 21:50:44 thur kernel: [ 3396.303040]  [<ffffffff81ad0c2b>] start_kernel+0x3d4/0x3df
Nov 15 21:50:44 thur kernel: [ 3396.303043]  [<ffffffff81ad0388>] x86_64_start_reservations+0x132/0x136
Nov 15 21:50:44 thur kernel: [ 3396.303046]  [<ffffffff81ad0140>] ? early_idt_handlers+0x140/0x140^C

---

### Post by quan2m on 2011-11-15
I am also using 64bit.

Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric

@thur:~$ cat /proc/version_signature 
Ubuntu 3.0.0-12.20-generic 3.0.4


@thur:~$ cat /proc/version
Linux version 3.0.0-12-generic (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011



@thur:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
vesafb                 13809  1 
binfmt_misc            17540  1 
joydev                 17693  0 
nvidia              11713772  40 
ppdev                  17113  0 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  0 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
arc4                   12529  2 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
rt2500pci              27646  0 
rt2x00pci              14578  1 rt2500pci
rt2x00lib              50325  2 rt2500pci,rt2x00pci
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              310872  2 rt2x00pci,rt2x00lib
parport_pc             36962  1 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
asus_atk0110           18078  0 
cfg80211              199587  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2500pci
k10temp                13166  0 
snd                    68266  9 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_core              53746  0 
edac_mce_amd           23709  0 
psmouse                73882  0 
serio_raw              13166  0 
wmi                    19256  0 
sp5100_tco             13791  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_piix4              13301  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
firewire_ohci          40722  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
floppy                 70365  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_atiixp            13164  1 
ahci                   26002  2 
libahci                26861  1 ahci

---

### Post by AnotherMuggle on 2011-11-16
If our problem is the same, you will find that blacklisting the rt2500pci driver stops the error messages from being generated.

I am currently using a USB wifi adapter without experiencing these errors.  I need to choose a PCI card which has good Linux compatibility but I can't tell which is a good choice.

---

