---
title: "Rescheduling Interrupts Powertop-1.13"
date: 2012-06-13
forum: General Help
---

### Post by WBMachinery on 2012-06-13
Using powertop-1.13 to print list of top wakeup offenders I get some high numbers on [Rescheduling Interrupts] <kernel ipi>.
I already investigated a little and tried what was on this link [https://help.ubuntu.com/community/ReschedulingInterrupts](https://help.ubuntu.com/community/ReschedulingInterrupts), but didn't get results when i tried changing the kernel parameters,and Im not sure if I did it correctly, I changed them in the /etc/default/grub file.

This is the output of powertop:

```
Wakeups-from-idle per second : 177.6	interval: 60.0s
Power usage (ACPI estimate): 8.3W (5.8 hours) 
Top causes for wakeups:
  39.0% (345.8)   [Rescheduling interrupts] <kernel IPI>
  10.2% ( 90.9)   PS/2 keyboard/mouse/touchpad interrupt
  10.2% ( 90.5)   swapper/0
   7.5% ( 66.4)   [i915] <interrupt>
   5.8% ( 51.8)   [ahci] <interrupt>
   5.6% ( 49.5)   swapper/1
   4.9% ( 43.1)   [TLB shootdowns] <kernel IPI>
   4.4% ( 39.1)   [iwlwifi] <interrupt>
   3.5% ( 30.6)   swapper/3
   2.9% ( 26.1)   swapper/2
   0.5% (  4.3)D  chrome
   0.0% (  0.0)D  Chrome_CacheThr
   0.0% (  0.0)D  Chrome_DBThread
   1.8% ( 16.2)   compiz
   0.0% (  0.1)D  Chrome_HistoryT
   0.0% (  0.0)D  zeitgeist-fts
   0.0% (  0.0)D  Chrome_FileThre
   0.9% (  7.6)   [Thermal event interrupts] <kernel IPI>
   0.6% (  5.0)   syndaemon
   0.3% (  3.1)   Xorg
   0.3% (  3.0)   Chrome_IOThread
   0.3% (  2.5)   SignalSender
   0.0% (  0.0)D  powertop-1.13
   0.2% (  1.6)   kworker/1:1
   0.2% (  1.6)   pool
   0.1% (  1.0)   gvfs-afc-volume
   0.0% (  0.0)D  ubuntuone-login
   0.0% (  0.0)D  WorkerPool/2493
   0.1% (  0.6)   kworker/0:3
   0.1% (  0.6)   [acpi] <interrupt>
   0.1% (  0.6)   kworker/u:5
   0.1% (  0.6)   dnsmasq
   0.1% (  0.5)   Watchdog
   0.0% (  0.3)   gnome-settings-
   0.0% (  0.3)   unity-applicati
   0.0% (  0.2)   zeitgeist-datah
   0.0% (  0.2)   accounts-daemon
   0.0% (  0.2)   avahi-daemon
   0.0% (  0.2)   python
   0.0% (  0.2)   WorkerPool/2417
   0.0% (  0.2)   NetworkManager
   0.0% (  0.2)   unity-panel-ser
   0.0% (  0.2)   WorkerPool/2418
   0.0% (  0.1)   nautilus
   0.0% (  0.1)   update-notifier
   0.0% (  0.1)   aptd
   0.0% (  0.1)   rtkit-daemon
   0.0% (  0.1)   watchdog/0
   0.0% (  0.1)   WorkerPool/2414
   0.0% (  0.1)   wpa_supplicant

```

What else can I do to get those numbers down? 
And also I've noticed that my touchpad produces relatively high number of wakeups,is that a normal number or was it configured wrongly?

Im runnign ubuntu 12.04 LTS 64-bit 3.2.0-24-generic on an ASUS U56E-BBL6

---

### Post by vedovatti on 2012-07-29
Hi I have the same problem. I have a Lenovo e420s and the powertop indicates the same to causes of the causes of the wakeups.

I try this weak to see if the ACPI parameter helps to reduce them and report a feedback as soon as I can.

But for me is a big problem it reduced a lot the battery life of my laptop.

---

### Post by vedovatti on 2012-07-30
Hi,

My laptop is wasting too much energy. Normaly it supposed to last 5 hours and in Ubuntu is reduced to 2,5 hours.

I have tried all the ACPI options in the documentation: [https://help.ubuntu.com/community/ReschedulingInterrupts](https://help.ubuntu.com/community/ReschedulingInterrupts) and no help. 

The same as you too many wakeup:
[PHP]Power usage (ACPI estimate): 19.0W (1.9 hours) 
Top causes for wakeups:
  46.2% (744.3)   [Rescheduling interrupts] <kernel IPI>
   0.7% ( 10.7)D  firefox
  17.2% (277.1)   PS/2 keyboard/mouse/touchpad interrupt
   6.0% ( 96.7)   [TLB shootdowns] <kernel IPI>
   1.4% ( 22.7)D  thunderbird
   4.9% ( 79.2)   [i915] <interrupt>
   4.2% ( 66.9)   [ahci] <interrupt>
   4.0% ( 64.5)   swapper/0
   3.7% ( 59.1)   [iwlwifi] <interrupt>
   3.2% ( 51.1)   swapper/2
   1.9% ( 30.0)   Xorg
   1.7% ( 27.1)   swapper/3
   1.7% ( 26.9)   swapper/1
   1.2% ( 19.9)   compiz
   0.0% (  0.0)D  desktopcouch-se
   0.5% (  7.9)   [ehci_hcd:usb1] <interrupt>
   0.0% (  0.1)D  gconfd-2
   0.3% (  5.0)   syndaemon
   0.0% (  0.0)D  zeitgeist-fts
   0.0% (  0.0)D  touch
   0.2% (  2.5)   [acpi] <interrupt>
   0.1% (  2.0)   nautilus
   0.1% (  2.0)   [ehci_hcd:usb2] <interrupt>
   0.0% (  0.6)D  pool
   0.1% (  1.1)   hp-systray
   0.0% (  0.2)D  beam.smp
   0.1% (  1.0)   gvfs-afc-volume
   0.1% (  1.0)   tor
   0.1% (  1.0)   /sys/bus/usb/devices/2-1.2
   0.1% (  1.0)   kworker/u:4
   0.1% (  0.9)   kworker/0:2
   0.1% (  0.8)   avahi-daemon
   0.0% (  0.6)   watchdog/0
   0.0% (  0.5)   kworker/1:1
   0.0% (  0.5)   blueman-mechani
   0.0% (  0.5)   kworker/3:1
   0.0% (  0.4)   [Non-maskable interrupts] <kernel IPI>
   0.0% (  0.3)   dnsmasq
   0.0% (  0.3)   zeitgeist-datah
   0.0% (  0.3)   gnome-settings-
   0.0% (  0.2)   accounts-daemon
   0.0% (  0.2)   unity-applicati
   0.0% (  0.2)   watchdog/1
   0.0% (  0.2)   watchdog/2
   0.0% (  0.2)   watchdog/3
   0.0% (  0.2)   NetworkManager
   0.0% (  0.2)   update-notifier
   0.0% (  0.2)   unity-panel-ser
   0.0% (  0.2)   /sys/bus/usb/devices/1-1
   0.0% (  0.1)   rtkit-daemon[/PHP]

I checked the file /proc/interrupts

[PHP]           CPU0       CPU1       CPU2       CPU3       
  0:         49          0          0          0   IO-APIC-edge      timer
  1:         34          0       1539          0   IO-APIC-edge      i8042
  8:          1          0          0          0   IO-APIC-edge      rtc0
  9:       3445          0          0          0   IO-APIC-fasteoi   acpi
 12:     201500          0       2945          0   IO-APIC-edge      i8042
 16:       2429          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb1
 18:          0          0          0          0   IO-APIC-fasteoi   mmc0
 23:       1917          0       1361          0   IO-APIC-fasteoi   ehci_hcd:usb2
 41:      23381          0          0          0   PCI-MSI-edge      ahci
 42:          0          0          0          0   PCI-MSI-edge      eth1
 43:     103032          0      11299          0   PCI-MSI-edge      i915
 44:         15          0          0          0   PCI-MSI-edge      mei
 45:      38193          0          0          0   PCI-MSI-edge      iwlwifi
 46:        345          0          0          0   PCI-MSI-edge      snd_hda_intel
NMI:         69         25         56         24   Non-maskable interrupts
LOC:      63796      42040      67068      40969   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:         69         25         56         24   Performance monitoring interrupts
IWI:          0          0          0          0   IRQ work interrupts
RES:     169330      52609     200678      49513   Rescheduling interrupts
CAL:        642        749        669        669   Function call interrupts
TLB:       4623      10322      13790       5250   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:          5          5          5          5   Machine check polls
ERR:          0
MIS:          0[/PHP]

The driver i8042 wakeups even more often the CPU as the Graphic driver. Seems to be a misconfigured hardware. i8042 seems a driver for the keyboard.

Any idea how to solve it?

---

### Post by vedovatti on 2012-07-31
I just reported a bug: [https://bugs.launchpad.net/linux/+bug/1031459](https://bugs.launchpad.net/linux/+bug/1031459)

---

