---
title: "No ACPI data available???"
date: 2010-06-26
forum: General Help
---

### Post by oxf on 2010-06-26
Hi
I installed Powertop after reading a number of threads of threads about power consumption issues in Lucid. Though it would be good to know what I was doing. But when I run Powertop it tells me "now ACPI power usage estimate available" Any ideas why?

Thanks

---

### Post by happyhamster on 2010-06-26
Likely because ACPI isn't used at the moment (system isn't in powersave mode). If it's a laptop, make sure it's unplugged (running on batteries).

---

### Post by oxf on 2010-06-26
> **happyhamster said:**
> Likely because ACPI isn't used at the moment (system isn't in powersave mode). If it's a laptop, make sure it's unplugged (running on batteries).

OMG Duuuuh!    :redface:
Yes a laptop

---

### Post by oxf on 2010-06-26
Well its the same result "no ACPI..... estimate available" on battery as well! :confused:

---

### Post by happyhamster on 2010-06-26
> **oxf said:**
> Well its the same result "no ACPI..... estimate available" on battery as well! :confused:
- Perhaps it's using apm instead. Try:

dmesg | grep apm -i

dmesg | grep acpi -i

dmesg | grep power -i

- To see the relevant messages in your log. Also make sure you run powertop as root.

---

### Post by oxf on 2010-06-26
> **happyhamster said:**
> - Perhaps it's using apm instead. Try:

dmesg | grep apm -i

dmesg | grep acpi -i

dmesg | grep power -i

- To see the relevant messages in your log. Also make sure you run powertop as root.

apm returns nothing. Definately running ACPI!

---

### Post by happyhamster on 2010-06-26
- Do you only get the "no ACPI power usage estimate available" message and nothing else?

- Take a look in the folder: /proc/acpi/battery/ It should contain files that describe the current state of the laptop's battery. For example, on my laptop:

cat /proc/acpi/battery/BAT1/state

- gives all info about the current battery status. If the folder's empty, then perhaps these features aren't supported for the hardware. Is there a battery-icon in the top panel? And if so, does it show the remaining discharge time?

---

### Post by oxf on 2010-06-26
> **happyhamster said:**
> - Do you only get the "no ACPI power usage estimate available" message and nothing else?

- Take a look in the folder: /proc/acpi/battery/ It should contain files that describe the current state of the laptop's battery. For example, on my laptop:

cat /proc/acpi/battery/BAT1/state

- gives all info about the current battery status. If the folder's empty, then perhaps these features aren't supported for the hardware. Is there a battery-icon in the top panel? And if so, does it show the remaining discharge time?

OK this looks a little more complicated than I first thought. May be linked to something else? maybe not?. Here goes...

Yes there is a battery icon on top panel. Sometimes it shows remaining discharge time and sometimes not. e.g. right now just an empty icon and " battery discharging... 0%". (Its fully charged though) BUT the battery is not good, doesnt last long and needs replacing! I questioned this once before and no one was sure but theory was "perhaps bad cell prevents you from getting ACPI info" I never got to the bottom of this (and not yet got around to replacing the battery)

Terminal shows much the same:
```
mbdb@M2000:~$ cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            unknown
remaining capacity:      unknown
present voltage:         unknown
mbdb@M2000:~$ 

```So yes I do have an old battery but whether theres something else going on I dont know. I always felt that my previous issue with battery state was never answered though.

---

### Post by happyhamster on 2010-06-26
- So ACPI does know there is a battery, but probably has no info on its type, or is unable to get any readings from it. What's the output of:

cat /proc/acpi/battery/BAT1/info

- Can you also show the output of:

dmesg | grep acpi -i

- And:

cat /etc/default/acpid

- (It will show which modules are being loaded at acpid's startup.)

---

### Post by oxf on 2010-06-26
> **happyhamster said:**
> - So ACPI does know there is a battery, but probably has no info on its type, or is unable to get any readings from it. What's the output of:

cat /proc/acpi/battery/BAT1/info

- Can you also show the output of:

dmesg | grep acpi -i

- And:

cat /etc/default/acpid

- (It will show which modules are being loaded at acpid's startup.)

Well I just pulled the power plug out and it now showing "batter discharging 57%". Anyway...
Oh and thanks for helping ;)

```
mbdb@M2000:~$ sudo cat /proc/acpi/battery/BAT1/info
[sudo] password for mbdb: 
present:                 yes
design capacity:         6000 mAh
last full capacity:      unknown
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 250 mAh
design capacity low:     150 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            JM-6
serial number:           5001413129
battery type:            LION
OEM info:                Hewlett-Packard
mbdb@M2000:~$ 
```

```
mbdb@M2000:~$ dmesg | grep acpi -i
[    0.000000]  BIOS-e820: 0000000037ef0000 - 0000000037eff000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037eff000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  modified: 0000000037ef0000 - 0000000037eff000 (ACPI data)
[    0.000000]  modified: 0000000037eff000 - 0000000037f00000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000f8080 00014 (v00 HP    )
[    0.000000] ACPI: RSDT 37ef8c12 00034 (v01 HP     3096     20041019  LTP 00000000)
[    0.000000] ACPI: FACP 37efee4b 00074 (v01 HP     3096     20041019 PTL  0000005F)
[    0.000000] ACPI: DSDT 37ef8c46 06205 (v01 HP     3091     20041019 MSFT 0100000E)
[    0.000000] ACPI: FACS 37efffc0 00040
[    0.000000] ACPI: SSDT 37efeebf 000B5 (v01 PTLTD  POWERNOW 20041019  LTP 00000001)
[    0.000000] ACPI: APIC 37efef74 00050 (v01 PTLTD  ? 3096   20041019  LTP 00000000)
[    0.000000] ACPI: MCFG 37efefc4 0003C (v01 PTLTD    MCFG   20041019  LTP 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.028389] ACPI: Core revision 20090903
[    0.088001] ACPI: bus type pci registered
[    0.088001] ACPI: EC: Look up EC in DSDT
[    0.089955] ACPI: Interpreter enabled
[    0.089966] ACPI: (supports S0 S3 S4 S5)
[    0.089990] ACPI: Using IOAPIC for interrupt routing
[    0.090776] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.096595] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.096742] ACPI: No dock devices found.
[    0.097935] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.101118] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.101231] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.101319] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.103666] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.103773] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.103878] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.103984] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.104098] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.104204] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.104311] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.104416] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.105013] ACPI: WMI: Mapper loaded
[    0.105015] PCI: Using ACPI for IRQ routing
[    0.107728] pnp: PnP ACPI init
[    0.107739] ACPI: bus type pnp registered
[    0.109323] pnp: PnP ACPI: found 10 devices
[    0.109326] ACPI: ACPI bus type pnp unregistered
[    0.109331] PnPBIOS: Disabled by ACPI PNP
[    0.845589] ACPI: AC Adapter [ACAD] (on-line)
[    0.845670] ACPI: Power Button [PWRB]
[    0.845729] ACPI: Sleep Button [SLPB]
[    0.846424] ACPI: Lid Switch [LID]
[    0.846504] ACPI: Power Button [PWRF]
[    0.849815] Switching to clocksource acpi_pm
[    0.850474] ACPI: Thermal Zone [THRM] (44 C)
[    0.857146] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.857211] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.049191] ACPI: Battery Slot [BAT1] (battery present)
[   16.019770] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   16.278667] radeon 0000:01:05.0: power state changed by ACPI to D0


```

```
mbdb@M2000:~$ sudo cat /etc/default/acpid
# Options to pass to acpid
#
# OPTIONS are appended to the acpid command-line
#OPTIONS=""

# Linux kernel modules to load before starting acpid
#
# MODULES is a space seperated list of modules to load, or "all" to load all
# acpi drivers, or commented out to load no module
#MODULES="battery ac processor button fan thermal video"
#MODULES="all"
mbdb@M2000:~$ 


```

---

### Post by happyhamster on 2010-06-26
> Well I just pulled the power plug out and it now showing "batter discharging 57%". Anyway...
Wait, do you mean the icon does show a time estimate, while "cat /proc/acpi/battery/BAT1/state" doesn't? That's weird. BTW. don't run such commands as root (don't use 'sudo').

What version of ubuntu are you using?

Anyway, the output you showed looked fine except for:
```

last full capacity:      unknown

```
ACPI doesn't know the value for a charged battery, so it can't calculate an estimate based on the current discharge rate. This could be a kernel (BIOS) issue. There's no easy fix for this (if at all).

I did a search for the battery model, and soon found:
[http://ubuntuforums.org/showthread.php?t=1035411](http://ubuntuforums.org/showthread.php?t=1035411)
Which doesn't look good. There are also lots of bugreports on launchpad on this.

---

### Post by oxf on 2010-06-26
> **happyhamster said:**
> Wait, do you mean the icon does show a time estimate, while "cat /proc/acpi/battery/BAT1/state" doesn't? That's weird. BTW. don't run such commands as root (don't use 'sudo').

What version of ubuntu are you using?

Anyway, the output you showed looked fine except for:
```

last full capacity:      unknown

```ACPI doesn't know the value for a charged battery, so it can't calculate an estimate based on the current discharge rate. This could be a kernel (BIOS) issue. There's no easy fix for this (if at all).

I did a search for the battery model, and soon found:
[http://ubuntuforums.org/showthread.php?t=1035411](http://ubuntuforums.org/showthread.php?t=1035411)
Which doesn't look good. There are also lots of bugreports on launchpad on this.

I'm using 10.04 now but had the same battery issue on Karmic and I think before that, so its not new. 
Come to think of I don't ever remember getting an accurate battery reading since I started using Ubuntu.

Right now clicking on the battery icon gives "discharging 56%" and then terminal gives:
 ```
mbdb@M2000:~$ cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            unknown
remaining capacity:      3360 mAh
present voltage:         unknown
mbdb@M2000:~$ 

```If it's a known bug I guess I can live with it if need be. I'll read through the thread tomorrow, thanks for the link..

---

