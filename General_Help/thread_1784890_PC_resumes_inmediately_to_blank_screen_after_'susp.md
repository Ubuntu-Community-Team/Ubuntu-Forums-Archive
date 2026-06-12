---
title: "PC resumes inmediately to blank screen after 'suspend'"
date: 2011-06-17
forum: General Help
---

### Post by jmborr on 2011-06-17
Dear Ubuntu users,

It seems 'suspend' (to RAM) does not work in my PC. After pressing the button this is what happens:

1- PC switches off monitor and hard drive
2- PC resumes hard drive activity inmediately after
3- PC switches on monitor to a blank screen

I can't bring any image in the monitor, I don't know if the keyboard works at all. The typical commands to bring a prompt or kill the X-server are not working.
Pressing & releasing the power button doesn't change things, either.
My only 'solution' is to press the power button for a while to completely switch off the computer and then reboot it.

Any ideas where to start checking things, please ? :confused:

- Jose

---

### Post by Toz on 2011-06-17
Have a look at /var/log/pm-suspend.log. It might give a clue as to what the problem is. Feel free to post the file here if you require further assistance.

---

### Post by collisionystm on 2011-06-17
That happens time to time in my Natty install. Although it hasn't happened in a while. Seems that updates have fixed it.

---

### Post by jmborr on 2011-06-17
> **Toz said:**
> Have a look at /var/log/pm-suspend.log. It might give a clue as to what the problem is. Feel free to post the file here if you require further assistance.

Here it goes. I don't know how to interpret it. I highlighted the 'Failed' messages:

Initial commandline parameters: 
Fri Jun 17 00:29:27 EDT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux bean 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
binfmt_misc            13213  1 
vesafb                 13449  1 
nvidia               7098106  24 
arc4                   12473  2 
snd_intel8x0           33213  3 
snd_ac97_codec        105614  1 snd_intel8x0
vmnet                  50337  10 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  3 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
vmblock                18374  1 
rtl8180                35687  0 
snd_rawmidi            25269  1 snd_seq_midi
mac80211              257001  1 rtl8180
vsock                  42319  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
vmci                   58429  1 vsock
vmmon                  74792  0 
ppdev                  12849  0 
eeprom_93cx6           12653  1 rtl8180
snd_timer              28659  2 snd_pcm,snd_seq
usblp                  17827  0 
cfg80211              156212  2 rtl8180,mac80211
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  12 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 12872  0 
parport_pc             32111  1 
soundcore              12600  1 snd
i2c_ali15x3            12878  0 
shpchp                 32345  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_ali1535            12777  0 
i2c_ali1563            12891  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  1 
uas                    17676  0 
floppy                 60032  0 
sata_uli               12693  2 
pata_ali               13564  3 
uli526x                22364  0 
             total       used       free     shared    buffers     cached
Mem:       2060336    1947388     112948          0     223400     842284
-/+ buffers/cache:     881704    1178632
Swap:      2095100      47988    2047112

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

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
**Having NetworkManager put all interaces to sleep...Failed.**

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
**Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory**

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Fri Jun 17 00:29:34 EDT 2011: performing suspend
Fri Jun 17 00:29:53 EDT 2011: Awake.
Fri Jun 17 00:29:53 EDT 2011: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdc:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdc:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
**Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory**

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...method return sender=:1.2 -> dest=:1.147 reply_serial=2
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
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Jun 17 00:29:59 EDT 2011: Finished.
Initial commandline parameters: 
Fri Jun 17 14:41:27 EDT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux bean 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux
Module                  Size  Used by
binfmt_misc            13213  1 
vesafb                 13449  1 
vmnet                  50337  10 
arc4                   12473  2 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
vmblock                18374  1 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
vsock                  42319  0 
vmci                   58429  1 vsock
vmmon                  74792  0 
rtl8180                35687  0 
nvidia               7098106  24 
snd_seq_midi           13132  0 
mac80211              257001  1 rtl8180
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
eeprom_93cx6           12653  1 rtl8180
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
cfg80211              156212  2 rtl8180,mac80211
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32111  1 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_ali15x3            12878  0 
soundcore              12600  1 snd
shpchp                 32345  0 
k8temp                 12872  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_ali1563            12891  0 
i2c_ali1535            12777  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
pata_ali               13564  2 
floppy                 60032  0 
uli526x                22364  0 
sata_uli               12693  0 
             total       used       free     shared    buffers     cached
Mem:       2060336     974628    1085708          0      99772     392440
-/+ buffers/cache:     482416    1577920
Swap:      2095100          0    2095100

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

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
**Having NetworkManager put all interaces to sleep...Failed.**

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
**Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory**

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Fri Jun 17 14:41:31 EDT 2011: performing suspend
Fri Jun 17 14:41:51 EDT 2011: Awake.
Fri Jun 17 14:41:51 EDT 2011: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
**Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory**

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...method return sender=:1.3 -> dest=:1.77 reply_serial=2
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
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Jun 17 14:41:57 EDT 2011: Finished.

---

### Post by DirtyPC on 2011-06-17
try to start in recovery mode.
from the terminal then run:
sudo pm-suspend

---

### Post by Toz on 2011-06-17
What make/model is your computer?

Can you post back the results of:```
lspci -vvv
sudo lshw
```

And can you try the following to see if it will suspend your computer:```
sudo bash -c "echo shutdown > /sys/power/disk"
sudo bash -c "echo mem > /sys/power/state"
``` (you may need to press the power button to awaken it)

---

### Post by wildmanne39 on 2011-06-18
Hi, I had this problem, I just went to the screensaver and disabled screensaver and in power management I set it not to spin down or go into sleep. I used the sleep in the last ubuntu and I liked having it but it does not work for me in natty, if the screen goes black I have to reatart.

---

### Post by jmborr on 2011-06-18
I took the following steps but the problem continued the same (goes to standby for ~1sec and then resumes to a dead screen):

1 disabled screensaver
2 in power management I set it not to spin down or go into sleep
3 reboot to recovery mode and ran a failsafeX session
4 sudo pm-suspend

Other attempts:

sudo bash -c "echo mem > /sys/power/state" sent the computer to standby and **stayed there**. I resumed the session by pressing the keyboard but I got no signal to the screen

sudo bash -c "echo shutdown > /sys/power/disk"
 did nothing. Here are the contents of file /sys/power/disk
*platform test testproc [shutdown] reboot*

It seems that the PC has problems resuming the screen or the X-server because sudo bash -c "echo mem > /sys/power/state" seems to correctly send the computer to standby, but when I resume I get a **no signal** message in the screen.

Here's the output of **sudo lshw**
bean
    description: Desktop Computer
    version: System Version
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=30768E5B-D854-DC11-8A0D-BF429D60139F
  *-core
       description: Motherboard
       product: K8U-X
       vendor: ASUSTeK Computer INC.
       physical id: 0
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1001
          date: 08/17/2006
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3200+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.12.2
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2213MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 32
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: M1689 K8 Northbridge [Super K8 Single Chip]
          vendor: ALi Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-amd64
          resources: irq:0 memory:e0000000-efffffff
        *-pci:0
             description: PCI bridge
             product: AGP8X Controller
             vendor: ALi Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:fa000000-fbefffff memory:f0000000-f8ffffff
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5500]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=64 maxlatency=1 mingnt=5
                resources: irq:16 memory:fa000000-faffffff memory:f0000000-f7ffffff memory:fbee0000-fbefffff
        *-pci:1
             description: PCI bridge
             product: M5249 HTT to PCI Bridge
             vendor: ALi Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:e000(size=4096) memory:fbf00000-fbffffff
           *-network
                description: Wireless interface
                product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: wlan0
                version: 20
                serial: 00:08:54:95:94:56
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8180 driverversion=2.6.38-8-generic firmware=N/A latency=64 link=no maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
                resources: irq:21 ioport:e800(size=256) memory:fbfffc00-fbfffdff
        *-isa
             description: ISA bridge
             product: M1563 HyperTransport South Bridge
             vendor: ALi Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 70
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=ali1563_smbus latency=0 maxlatency=24 mingnt=1
             resources: irq:0
        *-bridge UNCLAIMED
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: M5455 PCI AC-Link Controller Audio Device
             vendor: ALi Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=64 mingnt=64
             resources: irq:18 ioport:c800(size=256) memory:f9fff000-f9ffffff
        *-network
             description: Ethernet interface
             product: ULi 1689,1573 integrated ethernet.
             vendor: ALi Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             logical name: eth0
             version: 40
             serial: 00:1d:60:50:80:12
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=uli526x driverversion=0.9.3 duplex=full ip=192.168.1.100 latency=64 link=yes maxlatency=40 mingnt=20 multicast=yes port=MII speed=100Mbit/s
             resources: irq:17 ioport:c400(size=256) memory:f9ffec00-f9ffecff
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: e
             bus info: pci@0000:00:0e.0
             logical name: scsi0
             logical name: scsi1
             version: c7
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_ali latency=32
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-cdrom
                description: DVD writer
                product: DVD-RW  DVR-112D
                vendor: PIONEER
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.21
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
           *-disk:0
                description: ATA Disk
                product: Maxtor 6L300R0
                vendor: Maxtor
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: BAH4
                serial: L60E0ERH
                size: 279GiB (300GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a00bdb06
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 88c1a11d-4a8c-9143-b50c-26db1d115284
                   size: 279GiB
                   capacity: 279GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-10-15 17:31:15 filesystem=ntfs state=clean
           *-disk:1
                description: ATA Disk
                product: ST3400832A
                vendor: Seagate
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/sdb
                version: 3.03
                serial: 3NF160ZA
                size: 372GiB (400GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=c896595c
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: f430ce29-80aa-407e-93e9-ec0997c45fb9
                   size: 370GiB
                   capacity: 370GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-06-13 07:20:48 filesystem=ext4 lastmountpoint=/ modified=2011-06-13 10:59:48 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-06-18 10:26:13 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.1.0,2
                   logical name: /dev/sdb2
                   size: 2046MiB
                   capacity: 2046MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 2046MiB
                      capabilities: nofs
        *-storage
             description: Mass storage controller
             product: ULi 5289 SATA
             vendor: ALi Corporation
             physical id: e.1
             bus info: pci@0000:00:0e.1
             logical name: scsi2
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master emulated
             configuration: driver=sata_uli latency=128
             resources: irq:19 ioport:cc00(size=8) ioport:c080(size=4) ioport:c000(size=8) ioport:bc00(size=4) ioport:b880(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG HD204UI
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdc
                version: 1AQ1
                serial: S2H7J1BZC14794
                size: 1863GiB (2TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=f4d28a5d
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdc1
                   version: 3.1
                   serial: 803e8990-f6c0-bc45-8610-3f2855bfe6f1
                   size: 512GiB
                   capacity: 512GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2007-07-06 16:37:24 filesystem=ntfs state=clean
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sdc2
                   version: 1.0
                   serial: ba3c4801-70e0-4044-ae18-bb1c0ae6e16d
                   size: 1351GiB
                   capacity: 1351GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-06-13 11:24:17 filesystem=ext4 label=samsung_ubuntu lastmountpoint=/projects modified=2011-06-15 09:23:26 mounted=2011-06-15 09:23:26 state=clean
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:20 memory:f9ff3000-f9ff3fff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:21 memory:f9ffc000-f9ffcfff
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: f.2
             bus info: pci@0000:00:0f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:22 memory:f9ffd000-f9ffdfff
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: ALi Corporation
             physical id: f.3
             bus info: pci@0000:00:0f.3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=32 mingnt=16
             resources: irq:23 memory:f9ffe800-f9ffe8ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0


Here's the output of **lspci -vvv**:
00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-amd64
	Kernel modules: ali-agp

00:01.0 PCI bridge: ALi Corporation AGP8X Controller (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fa000000-fbefffff
	Prefetchable memory behind bridge: f0000000-f8ffffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity+ SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Kernel modules: shpchp

00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbf00000-fbffffff
	Prefetchable memory behind bridge: fff00000-000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR+
	BridgeCtl: Parity+ SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Kernel modules: shpchp

00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
	Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (250ns min, 6000ns max)
	Kernel driver in use: ali1563_smbus
	Kernel modules: i2c-ali1563

00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
	Subsystem: ALi Corporation M7101 Power Management Controller [PMU]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel modules: alim7101_wdt, i2c-ali15x3, i2c-ali1535

00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
	Subsystem: ASUSTeK Computer Inc. Device 810d
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (16000ns min), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at c800 [size=256]
	Region 1: Memory at f9fff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:0d.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
	Subsystem: ASUSTeK Computer Inc. Device 816a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (5000ns min, 10000ns max)
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at c400 [size=256]
	Region 1: Memory at f9ffec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: uli526x
	Kernel modules: uli526x

00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7) (prog-if fa)
	Subsystem: ALi Corporation M5229 IDE
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin A routed to IRQ 19
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	Region 4: I/O ports at ff00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_ali
	Kernel modules: pata_ali

00:0e.1 Mass storage controller: ALi Corporation ULi 5289 SATA (rev 10) (prog-if 8f)
	Subsystem: ASUSTeK Computer Inc. Device 816b
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 128, Cache Line Size: 512 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: I/O ports at cc00 [size=8]
	Region 1: I/O ports at c080 [size=4]
	Region 2: I/O ports at c000 [size=8]
	Region 3: I/O ports at bc00 [size=4]
	Region 4: I/O ports at b880 [size=16]
	Kernel driver in use: sata_uli
	Kernel modules: sata_uli

00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Device 816b
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
	Latency: 64 (20000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at f9ff3000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Device 816b
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
	Latency: 64 (20000ns max), Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 21
	Region 0: Memory at f9ffc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Device 816b
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
	Latency: 64 (20000ns max), Cache Line Size: 64 bytes
	Interrupt: pin C routed to IRQ 22
	Region 0: Memory at f9ffd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 816b
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (4000ns min, 8000ns max), Cache Line Size: 64 bytes
	Interrupt: pin D routed to IRQ 23
	Region 0: Memory at f9ffe800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1) (prog-if 00 [VGA controller])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (1250ns min, 250ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Expansion ROM at fbee0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nouveau, nvidiafb

02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (8000ns min, 16000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: I/O ports at e800 [size=256]
	Region 1: Memory at fbfffc00 (32-bit, non-prefetchable) [size=512]
	Capabilities: <access denied>
	Kernel driver in use: rtl8180
	Kernel modules: rtl8180

---

### Post by Toz on 2011-06-18
A few things we can try. 

First off, open a terminal window, type in the following, and then try to suspend the normal way:
```
sudo touch /etc/pm/sleep.d/60_wpa_supplicant
```

If that doesn't solve the same problem, then 
```
gksudo /etc/pm/config.d/defaults
```
and add the following to this file:
```
SUSPEND_MODULES="rtl8180 uli526x"
```
save the file, reboot and try again.

If still not working, post back **/var/log/pm-suspend.log**.
When you post back these file contents, please enclose them in ```
 
``` blocks.

---

### Post by jmborr on 2011-06-19
Attempt 1:```
sudo touch /etc/pm/sleep.d/60_wpa_supplicant
```
It did not solve the problem :(

Attempt 2:```
gksudo /etc/pm/config.d/defaults
```
and add the following to this file:
```
SUSPEND_MODULES="rtl8180 uli526x"
```
save the file, reboot and try again.
File **/etc/pm/config.d/defaults** didn't exists. I created this file with the single line.

It didn't solve the problem :(

I think the computer successfully go to suspend mode. The problem shows up when trying to resume activity. The hard-disk does spin, but the screen is dead. Keyboard is dead because LEDs "caps lock" and "scroll lock" stay iluminated. 

Is there a way to recover some information of what goes on when resuming activity?

Contents of /var/log/pm-suspend.log:
```
Initial commandline parameters: 
Fri Jun 17 00:29:27 EDT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux bean 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
binfmt_misc            13213  1 
vesafb                 13449  1 
nvidia               7098106  24 
arc4                   12473  2 
snd_intel8x0           33213  3 
snd_ac97_codec        105614  1 snd_intel8x0
vmnet                  50337  10 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  3 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
vmblock                18374  1 
rtl8180                35687  0 
snd_rawmidi            25269  1 snd_seq_midi
mac80211              257001  1 rtl8180
vsock                  42319  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
vmci                   58429  1 vsock
vmmon                  74792  0 
ppdev                  12849  0 
eeprom_93cx6           12653  1 rtl8180
snd_timer              28659  2 snd_pcm,snd_seq
usblp                  17827  0 
cfg80211              156212  2 rtl8180,mac80211
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  12 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 12872  0 
parport_pc             32111  1 
soundcore              12600  1 snd
i2c_ali15x3            12878  0 
shpchp                 32345  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_ali1535            12777  0 
i2c_ali1563            12891  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  1 
uas                    17676  0 
floppy                 60032  0 
sata_uli               12693  2 
pata_ali               13564  3 
uli526x                22364  0 
             total       used       free     shared    buffers     cached
Mem:       2060336    1947388     112948          0     223400     842284
-/+ buffers/cache:     881704    1178632
Swap:      2095100      47988    2047112

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

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Fri Jun 17 00:29:34 EDT 2011: performing suspend
Fri Jun 17 00:29:53 EDT 2011: Awake.
Fri Jun 17 00:29:53 EDT 2011: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdc:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdc:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...method return sender=:1.2 -> dest=:1.147 reply_serial=2
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
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Jun 17 00:29:59 EDT 2011: Finished.
Initial commandline parameters: 
Fri Jun 17 14:41:27 EDT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux bean 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux
Module                  Size  Used by
binfmt_misc            13213  1 
vesafb                 13449  1 
vmnet                  50337  10 
arc4                   12473  2 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
vmblock                18374  1 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
vsock                  42319  0 
vmci                   58429  1 vsock
vmmon                  74792  0 
rtl8180                35687  0 
nvidia               7098106  24 
snd_seq_midi           13132  0 
mac80211              257001  1 rtl8180
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
eeprom_93cx6           12653  1 rtl8180
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
cfg80211              156212  2 rtl8180,mac80211
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32111  1 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_ali15x3            12878  0 
soundcore              12600  1 snd
shpchp                 32345  0 
k8temp                 12872  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_ali1563            12891  0 
i2c_ali1535            12777  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
pata_ali               13564  2 
floppy                 60032  0 
uli526x                22364  0 
sata_uli               12693  0 
             total       used       free     shared    buffers     cached
Mem:       2060336     974628    1085708          0      99772     392440
-/+ buffers/cache:     482416    1577920
Swap:      2095100          0    2095100

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

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Fri Jun 17 14:41:31 EDT 2011: performing suspend
Fri Jun 17 14:41:51 EDT 2011: Awake.
Fri Jun 17 14:41:51 EDT 2011: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...method return sender=:1.3 -> dest=:1.77 reply_serial=2
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
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Jun 17 14:41:57 EDT 2011: Finished.
Initial commandline parameters: 
Sat Jun 18 10:07:43 EDT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux bean 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux
Module                  Size  Used by
vesafb                 13449  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
arc4                   12473  2 
nvidia               7098106  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
rtl8180                35687  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
mac80211              257001  1 rtl8180
snd_timer              28659  2 snd_pcm,snd_seq
ppdev                  12849  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
eeprom_93cx6           12653  1 rtl8180
cfg80211              156212  2 rtl8180,mac80211
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32111  1 
shpchp                 32345  0 
i2c_ali15x3            12878  0 
soundcore              12600  1 snd
k8temp                 12872  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_ali1563            12891  0 
i2c_ali1535            12777  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
floppy                 60032  0 
pata_ali               13564  2 
sata_uli               12693  0 
uli526x                22364  0 
             total       used       free     shared    buffers     cached
Mem:       2060336     445220    1615116          0      29980     194212
-/+ buffers/cache:     221028    1839308
Swap:      2095100          0    2095100

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

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...method return sender=:1.3 -> dest=:1.62 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sat Jun 18 10:07:47 EDT 2011: performing suspend
Initial commandline parameters: 
Sun Jun 19 11:56:31 EDT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux bean 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux
Module                  Size  Used by
vesafb                 13449  1 
nvidia               7098106  0 
arc4                   12473  2 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
rtl8180                35687  0 
snd_rawmidi            25269  1 snd_seq_midi
mac80211              257001  1 rtl8180
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
eeprom_93cx6           12653  1 rtl8180
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  2 rtl8180,mac80211
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32111  1 
soundcore              12600  1 snd
i2c_ali15x3            12878  0 
k8temp                 12872  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_ali1563            12891  0 
shpchp                 32345  0 
i2c_ali1535            12777  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
floppy                 60032  0 
sata_uli               12693  0 
pata_ali               13564  2 
uli526x                22364  0 
             total       used       free     shared    buffers     cached
Mem:       2060336     458972    1601364          0      41992     191892
-/+ buffers/cache:     225088    1835248
Swap:      2095100          0    2095100

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

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /etc/pm/sleep.d/60_wpa.supplicant suspend suspend:

/etc/pm/sleep.d/60_wpa.supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sun Jun 19 11:56:35 EDT 2011: performing suspend
Initial commandline parameters: 
Sun Jun 19 12:17:42 EDT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux bean 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
nvidia               7098106  0 
rtl8180                35687  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              257001  1 rtl8180
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
eeprom_93cx6           12653  1 rtl8180
ppdev                  12849  0 
cfg80211              156212  2 rtl8180,mac80211
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32111  1 
k8temp                 12872  0 
soundcore              12600  1 snd
i2c_ali15x3            12878  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_ali1535            12777  0 
i2c_ali1563            12891  0 
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
floppy                 60032  0 
uli526x                22364  0 
sata_uli               12693  0 
pata_ali               13564  2 
             total       used       free     shared    buffers     cached
Mem:       2060336     472784    1587552          0      46908     199596
-/+ buffers/cache:     226280    1834056
Swap:      2095100          0    2095100

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

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /etc/pm/sleep.d/60_wpa.supplicant suspend suspend:

/etc/pm/sleep.d/60_wpa.supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module rt18180...Done.
Unloading kernel module uli526x...Done.

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sun Jun 19 12:17:44 EDT 2011: performing suspend

```

---

### Post by Toz on 2011-06-19
Okay. Since that didn't work, lets undo what we did in the last step.
```
sudo rm /etc/pm/sleep.d/60_wpa_supplicant
sudo rm /etc/pm/config.d/defaults
```

Everything should log to /var/log/pm-suspend, but as you can see from the last two attempts, there is nothing being logged for the wakeup.

There is another suspend/hibernate module that can be used. I've used it successfully in the past for systems that had trouble with suspend/resume. Its called **uswsusp**.

Install it from the Software Centre or:```
sudo apt-get install uswsusp
```

Once installed, give it a go:```
sudo s2ram
```
If you get a message about the system not being recognized or not in the database, then try:```
sudo s2ram -f
```

Let us know if it works.

---

### Post by jmborr on 2011-06-20
I installed uswsusp. Command **s2ram** did not recognize my machine. I did several combinations of flags for s2ram, as suggested in [http://tr.opensuse.org/S2ram#How_to_use_it.3F](http://tr.opensuse.org/S2ram#How_to_use_it.3F).

PC awakes to dead screen with either of the following commands:
```
s2ram -f
s2ram -f -a 2
s2ram -f -p -s
s2ram -f -s
s2ram -f -p

```

PC awakes to a dead start with either of the following commands (screen showed the first message I always get when I boot the PC, then nothing more). this is the first message:
[i]PNY Verto GeForce FX 5500 AGP
Version 4.34.20.69.51
Copyright (C) 1996-2003 NVIDIA Corp.
128.0MB RAM[/i]

```
s2ram -f -a 1
s2ram -f -a 3
s2ram -f -a 1 -s
s2ram -f -a 1 -p

```

---

### Post by Toz on 2011-06-20
In that link that you referenced, in the background section, it suggests a number of dirty tricks to get the backlight back on (which is what I think is happening with the first set of s2ram commands that awaken as you say to a dead screen). Specifically, the acpi_sleep commands.

What does:```
cat /proc/sys/kernel/acpi_video_flags
```return?

If it is 0, you can also try with values 1,2 or 3. You can do this from the command line like:```
echo 1 | sudo tee -a /proc/sys/kernel/acpi_video_flags
```and then run the s2ram commands that led to a dead screen. If still no return of the screen, try the other values. Remember that 0, 1, 2, and 3 are the only valid entries.

---

### Post by jmborr on 2011-06-21
> **Toz said:**
> In that link that you referenced, in the background section, it suggests a number of dirty tricks to get the backlight back on (which is what I think is happening with the first set of s2ram commands that awaken as you say to a dead screen). Specifically, the acpi_sleep commands.

What does:```
cat /proc/sys/kernel/acpi_video_flags
```return?

If it is 0, you can also try with values 1,2 or 3. You can do this from the command line like:```
echo 1 | sudo tee -a /proc/sys/kernel/acpi_video_flags
```and then run the s2ram commands that led to a dead screen. If still no return of the screen, try the other values. Remember that 0, 1, 2, and 3 are the only valid entries.

If I understand correctly, flag **-a** does what you're suggesting. Here's a quote from [http://powersave.sourceforge.net/powersave/Suspend2Ram.html:](http://powersave.sourceforge.net/powersave/Suspend2Ram.html:) "The *acpi_sleep* parameter can also be set at runtime in /proc/sys/kernel/acpi_video_flags, or with the s2ram tool" (this *acpi_sleep* parameter is set with flag **-a**)

---

### Post by Toz on 2011-06-21
The -a parameter belongs to the tee command. The end result of this command is to put another value into /proc/sys/kernel/acpi_video_flags for the purposes of testing those "dirty tricks". After changing the value, you should run those s2ram commands that generated the blank screen to see if you can get the screen to come back. If one of the values 0,1,2 or 3 work, then we can script something that will work for you.

---

### Post by jmborr on 2011-06-22
> **Toz said:**
> The -a parameter belongs to the tee command. The end result of this command is to put another value into /proc/sys/kernel/acpi_video_flags for the purposes of testing those "dirty tricks". After changing the value, you should run those s2ram commands that generated the blank screen to see if you can get the screen to come back. If one of the values 0,1,2 or 3 work, then we can script something that will work for you.

I didn't explain myself. I meant the **-a** flag in command **s2ram -f -a *X***, where *X* is either 1, 2, or 3. These values correspond to the different values that you can store in file *acpi_video_flags*.
Thus, storing values in file *acpi_video_flags* amounts to trying the different **s2ram -f -a *X*** commands which I already did, and unfortunately didn't solve the problem.

---

### Post by Toz on 2011-06-22
Oh, yes. It appears it does the same. I've got one more thing you can try. Try purging the package vbetool (in case its interfering with s2ram) and trying those commands again:```
sudo apt-get purge vbetool
```

---

### Post by Toz on 2011-06-22
Just came across this link: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug"). Suspend/resume issues related to usb controllers affecting many. Maybe worth a try?

---

### Post by jmborr on 2011-06-23
> **Toz said:**
> Oh, yes. It appears it does the same. I've got one more thing you can try. Try purging the package vbetool (in case its interfering with s2ram) and trying those commands again:```
sudo apt-get purge vbetool
```

I removed **vbetool** and issue a series of **s2ram** commands with various flags, but the PC still did not awoke successfully. Thus, I reinstalled **vbetool** back.

---

### Post by jmborr on 2011-06-23
> **Toz said:**
> Just came across this link: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug"). Suspend/resume issues related to usb controllers affecting many. Maybe worth a try?

I tried, but with no result ](*,)

---

### Post by Toz on 2011-06-23
I'm afraid I am running out of ideas. 

Post #5 suggested you boot into recovery mode and run pm-suspend. If this works, then there is a good chance that it is your video card that's preventing the suspend function from working properly. If thats the case, you could try unloading the nvidia module prior to suspend.
```
gksudo /etc/pm/config.d/defaults
```
with contents:
```
SUSPEND_MODULES="nvidia"
```

Use the regular suspend functions (not s2ram) to test.

---

### Post by jmborr on 2011-06-24
I've been doing all my trials in recovery mode. The "nvidia" module is loaded in this mode, although not in use
```
lsmod|grep nvidia
nvidia      7098106  0
```
Thus, I introduced suspension of nvidia module in /etc/pm/config.d/defaults and ran **pm-suspend** with different **quirk** options:
```
pm-suspend
pm-suspend --quirk-save-pci
pm-suspend --quirk-dpms-on
pm-suspend --quirk-radeon-off
pm-suspend --quirk-s3-bios
pm-suspend --quirk-save-pci --quirk-s3-bios 
pm-suspend --quirk-s3-mode
pm-suspend --quirk-save-pci --quirk-s3-mode
pm-suspend --quirk-vbe-post
pm-suspend --quirk-save-pci --quirk-vbe-post

```
None of the worked :mad: I'm going to have to give up with the suspend option in my PC.

---

### Post by chayzer on 2011-07-19
I realize this is a few weeks old but I'm having similar problems and stumbled upon [this thread]("http://ubuntuforums.org/showthread.php?t=1746045").

---

### Post by jmborr on 2011-07-20
> **chayzer said:**
> I realize this is a few weeks old but I'm having similar problems and stumbled upon [this thread]("http://ubuntuforums.org/showthread.php?t=1746045").

Good luck! I was never able to solve the issue :frown: Let me know if you succeed to see how you did it!

---

### Post by chayzer on 2011-07-20
I installed the tuxonice enabled kernels because I was just going to use hibernate instead but these kernels seem to have resolved it in suspend as well!

```
sudo add-apt-repository ppa:tuxonice/ppa
sudo apt-get update

sudo apt-get install tuxonice-userui linux-generic-tuxonice linux-headers-generic-tuxonice

or if you're using the PAE kernels

sudo apt-get install tuxonice-userui linux-generic-pae-tuxonice linux-headers-generic-pae-tuxonice

```

Suspend and Hibernate working great! Maybe it'll help you as well.

---

### Post by jmborr on 2011-07-20
> **chayzer said:**
> I installed the tuxonice enabled kernels because I was just going to use hibernate instead but these kernels seem to have resolved it in suspend as well!

```
sudo add-apt-repository ppa:tuxonice/ppa
sudo apt-get update

sudo apt-get install tuxonice-userui linux-generic-tuxonice linux-headers-generic-tuxonice

or if you're using the PAE kernels

sudo apt-get install tuxonice-userui linux-generic-pae-tuxonice linux-headers-generic-pae-tuxonice

```

Suspend and Hibernate working great! Maybe it'll help you as well.

No luck. What's worse, my nvidia drivers are not working now because I compiled them with the previous kernel.
Do you now how do I recover the old kernels? Will:
```
sudo apt-get remove tuxonice-userui linux-generic-tuxonice linux-headers-generic-tuxonice
```
do the trick?

---

### Post by jmborr on 2011-07-20
Just to be sure tuxonice does not solve my problem, I recompiled the NVIDIA driver against  the new kernels. Now I can boot normally with the tuxonice kernels, but the 'suspend' and 'hibernate' options still don't work. I always end up with a blank screen after restarting the PC :-k

---

### Post by teeedubb on 2012-01-07
> **jmborr said:**
> Dear Ubuntu users,

It seems 'suspend' (to RAM) does not work in my PC. After pressing the button this is what happens:

1- PC switches off monitor and hard drive
2- PC resumes hard drive activity inmediately after
3- PC switches on monitor to a blank screen

I can't bring any image in the monitor, I don't know if the keyboard works at all. The typical commands to bring a prompt or kill the X-server are not working.
Pressing & releasing the power button doesn't change things, either.
My only 'solution' is to press the power button for a while to completely switch off the computer and then reboot it.

Any ideas where to start checking things, please ? :confused:

- Jose

I started having the exact same issues after adding powertop suggestions to my /etc/rc.local file. Removing these fixed suspend resuming to a blank screen...

---

### Post by jmborr on 2012-01-09
> **teeedubb said:**
> I started having the exact same issues after adding powertop suggestions to my /etc/rc.local file. Removing these fixed suspend resuming to a blank screen...

Thanks for the tip, but I don't have Ubuntu in my home PC anymore :D

---

### Post by Pilot6 on 2012-01-09
The problem is fixed in kernel 3.2
I fixed all my problems.
1. Blank screen after resume. Fixed by a new kernel
2. Artifacts on boot. Installed Nvidia 295 drivers.
3. Problems with window placement under the panel randomly when there are 2 x screens connected. Fixed by compiling unity 5.0

This means that all will be fixed in 12.04, but you can do it now.

---

### Post by tanoloco on 2012-05-14
> **Pilot6 said:**
> The problem is fixed in kernel 3.2
I fixed all my problems.
1. Blank screen after resume. Fixed by a new kernel
2. Artifacts on boot. Installed Nvidia 295 drivers.
3. Problems with window placement under the panel randomly when there are 2 x screens connected. Fixed by compiling unity 5.0

This means that all will be fixed in 12.04, but you can do it now.

For old cards, the nvidia-173 driver is not currently working
please see
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053")
so we don't know now if this is solved in 12.04

---

