---
title: "Laptop does not suspend"
date: 2012-10-09
forum: General Help
---

### Post by PrinceNo1 on 2012-10-09
I realise lately that my laptop does not go into suspend mode when i close its lid. I use windows 7 x64 Home Premium, dual booting Precise Pangolin 12.04.1 with all updates installed under Gnome 3.4 shell. Currently i do not have any issues about my system. I can use "suspend" command manually from the user drop down menu and it works. I already got "suspend when lid is closed" option set in power options but this doesnt work. Anything wrong?

---

### Post by PrinceNo1 on 2012-10-10
Anyone got an idea?

---

### Post by Toz on 2012-10-10
What is the make and model of your laptop? There are a number of lid sensing bugs around. 

Also, it might be helpful if you posted the results of this command (run from a terminal window) to see if there are any issues with acpi:
```
cat /var/log/dmesg | grep ACPI
```

---

### Post by PrinceNo1 on 2012-10-10
Thanks for the response. It is a compal nblb2 system with corei7 720qm, AMD Radeon 5650M, 4 GB DDR3, 400GB HDD and a 19x10 screen and i am not sure of the chipset but i can learn if that matters much. Here is what that command returned: 
> [    0.000000]  BIOS-e820: 00000000bf6bf000 - 00000000bf7bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf7bf000 - 00000000bf7ff000 (ACPI data)
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 Datate)
[    0.000000] ACPI: XSDT bf7fe120 000AC (v01 Datate Diamond1 00000001      01000013)
[    0.000000] ACPI: FACP bf7fb000 000F4 (v04 Datate Diamond1 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT bf7ef000 080ED (v02 Datate Diamond1 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS bf759000 00040
[    0.000000] ACPI: TCPA bf7fd000 00032 (v00                 00000000      00000000)
[    0.000000] ACPI: ASF! bf7fc000 000A5 (v32 Datate Diamond1 00000001 MSFT 01000013)
[    0.000000] ACPI: HPET bf7fa000 00038 (v01 Datate Diamond1 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC bf7f9000 0008C (v02 Datate Diamond1 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG bf7f8000 0003C (v01 Datate Diamond1 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC bf7ee000 00176 (v01 Datate Diamond1 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT bf7ed000 0073D (v01 TrmRef PtidDevc 00001000 INTL 20051117)
[    0.000000] ACPI: SSDT bf7ec000 00172 (v01  VaRef  Va_Acpi 00003000 INTL 20051117)
[    0.000000] ACPI: BOOT bf7eb000 00028 (v01 Datate Diamond1 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT bf7ea000 00C39 (v01 INTEL   SataPri 00001000 INTL 20051117)
[    0.000000] ACPI: SSDT bf7e9000 006C5 (v01 INTEL   SataSec 00001000 INTL 20051117)
[    0.000000] ACPI: SPCR bf7e8000 00050 (v01 Datate Diamond1 00000000 MSFT 01000013)
[    0.000000] ACPI: ASPT bf7e7000 00034 (v04 Datate Diamond1 00000001 MSFT 01000013)
[    0.000000] ACPI: WDRT bf7e6000 00047 (v01 Datate Diamond1 00000000 MSFT 01000013)
[    0.000000] ACPI: DMAR bf7e5000 00068 (v01 INTEL  CP_FIELD 00000001 INTL 00000001)
[    0.000000] ACPI: SSDT bf7e4000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.002730] ACPI: Core revision 20110623
[    1.051688] PM: Registering ACPI NVS region at bf6bf000 (1048576 bytes)
[    1.053207] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    1.053210] ACPI: bus type pci registered
[    1.054659] ACPI: Added _OSI(Module Device)
[    1.054662] ACPI: Added _OSI(Processor Device)
[    1.054664] ACPI: Added _OSI(3.0 _SCP Extensions)
[    1.054667] ACPI: Added _OSI(Processor Aggregator Device)
[    1.057892] ACPI: EC: Look up EC in DSDT
[    1.061091] ACPI: Executed 1 blocks of module-level executable AML code
[    1.124613] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.125197] ACPI: SSDT bf691a98 002DA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    1.125984] ACPI: Dynamic OEM Table Load:
[    1.125988] ACPI: SSDT   (null) 002DA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    1.126180] ACPI: SSDT bf690618 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    1.126928] ACPI: Dynamic OEM Table Load:
[    1.126931] ACPI: SSDT   (null) 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    1.180957] ACPI: SSDT bf691718 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    1.181824] ACPI: Dynamic OEM Table Load:
[    1.181828] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    1.212731] ACPI: SSDT bf68fd98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.213547] ACPI: Dynamic OEM Table Load:
[    1.213551] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.280816] ACPI: Interpreter enabled
[    1.280824] ACPI: (supports S0 S3 S4 S5)
[    1.280866] ACPI: Using IOAPIC for interrupt routing
[    1.282112] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    1.282503] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    1.686057] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.686346] ACPI: No dock devices found.
[    1.686354] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.686869] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    1.713014] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.713244] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    1.713304] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.713410] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.713456] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.713504] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    1.713551] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    1.713690]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.713742]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    1.713745] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.721515] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    1.721964]  pci0000:ff: Requesting ACPI _OSC control (0x1d)
[    1.721967]  pci0000:ff: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    1.721970] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.722676] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    1.722737] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.722797] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    1.722856] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.722917] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.722976] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.723034] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    1.723094] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    1.723709] PCI: Using ACPI for IRQ routing
[    1.769203] pnp: PnP ACPI init
[    1.769220] ACPI: bus type pnp registered
[    1.769768] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.968906] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.968956] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.969105] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.969168] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.969337] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.969394] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.969473] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.969536] pnp 00:08: Plug and Play ACPI device, IDs PNP0f13 (active)
[    1.969609] pnp 00:09: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active)
[    1.970143] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.970381] pnp 00:0b: Plug and Play ACPI device, IDs PNP0a03 (active)
[    1.970523] pnp 00:0c: Plug and Play ACPI device, IDs ENE0100 (active)
[    1.970529] pnp: PnP ACPI: found 13 devices
[    1.970531] ACPI: ACPI bus type pnp unregistered
[    1.970534] PnPBIOS: Disabled by ACPI PNP
[    2.244824] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.444842] ACPI: AC Adapter [AC] (on-line)
[    2.444952] ACPI: Power Button [PWRB]
[    2.445033] ACPI: Lid Switch [LID0]
[    2.445096] ACPI: Sleep Button [SLPB]
[    2.445157] ACPI: Power Button [PWRF]
[    2.646504] ACPI: Invalid active0 threshold
[    2.646811] ACPI: Thermal Zone [THRM] (41 C)
[    2.646835] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.646843] ACPI: Battery Slot [BAT0] (battery present)
[    4.249082] ACPI: Battery Slot [BAT0] (battery present)
[   30.112710] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   30.114320] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[   31.097741] pci 0000:01:00.0: power state changed by ACPI to D0
[   31.097748] pci 0000:01:00.0: power state changed by ACPI to D0


---

### Post by 2F4U on 2012-10-10
There is a log file related to suspend, which is /var/log/pm-suspend.log, which has kind of debugging data about suspend actions and steps in it. If I were you I would compare the content from the successful and unsuccessful attempts and see if there are any differences.

---

### Post by PrinceNo1 on 2012-10-10
2F4U thanks for the comment. I checked that file but there are lots of information there :) i only can say that there is "success" at the end of some attempts and "not applicable" at some. Do you want me to paste that all here?

---

### Post by Toz on 2012-10-10
If its suspending when you manually suspend but not when the lid is closed, there may be an issue with sensing the lid closure (your dmesg log file shows that the Lid is properly being recognized). 

Can you tell if it tries to suspend when you close the lid? Perhaps posting the contents of /var/log/pm-suspend.log right after a lid close event would help answer that question.

You might also want to try this command. It will report back the contents of the lid state file as you close and re-open the lid:
```
while true; do date && cat /proc/acpi/button/lid/*/state; sleep 1; done
```
...Start the command, close the lid, wait 5 seconds, re-open the lid, Ctrl+C to cancel the command, and post back the results.

---

### Post by PrinceNo1 on 2012-10-10
> **Toz said:**
> If its suspending when you manually suspend but not when the lid is closed, there may be an issue with sensing the lid closure (your dmesg log file shows that the Lid is properly being recognized). 

Can you tell if it tries to suspend when you close the lid? Perhaps posting the contents of /var/log/pm-suspend.log right after a lid close event would help answer that question.

You might also want to try this command. It will report back the contents of the lid state file as you close and re-open the lid:
```
while true; do date && cat /proc/acpi/button/lid/*/state; sleep 1; done
```...Start the command, close the lid, wait 5 seconds, re-open the lid, Ctrl+C to cancel the command, and post back the results.
 Firstly, thanks for the response. Here is the result of that command:
```
Wed Oct 10 21:13:15 EEST 2012
state:      open
Wed Oct 10 21:13:16 EEST 2012
state:      open
Wed Oct 10 21:13:17 EEST 2012
state:      open
Wed Oct 10 21:13:18 EEST 2012
state:      open
Wed Oct 10 21:13:19 EEST 2012
state:      open
Wed Oct 10 21:13:20 EEST 2012
state:      open
Wed Oct 10 21:13:21 EEST 2012
state:      open
Wed Oct 10 21:13:22 EEST 2012
state:      open
Wed Oct 10 21:13:23 EEST 2012
state:      open
Wed Oct 10 21:13:24 EEST 2012
state:      open
Wed Oct 10 21:13:25 EEST 2012
state:      open
Wed Oct 10 21:13:26 EEST 2012
state:      open
Wed Oct 10 21:13:27 EEST 2012
state:      open
Wed Oct 10 21:13:28 EEST 2012
state:      open
Wed Oct 10 21:13:29 EEST 2012
state:      open
Wed Oct 10 21:13:30 EEST 2012
state:      open
Wed Oct 10 21:13:31 EEST 2012
state:      open
Wed Oct 10 21:13:32 EEST 2012
state:      open
Wed Oct 10 21:13:33 EEST 2012
state:      open
Wed Oct 10 21:13:34 EEST 2012
state:      open
Wed Oct 10 21:13:35 EEST 2012
state:      open
Wed Oct 10 21:13:36 EEST 2012
state:      open
Wed Oct 10 21:13:37 EEST 2012
state:      open
Wed Oct 10 21:13:38 EEST 2012
state:      open
Wed Oct 10 21:13:39 EEST 2012
state:      open
Wed Oct 10 21:13:40 EEST 2012
state:      open
Wed Oct 10 21:13:41 EEST 2012
state:      open
Wed Oct 10 21:13:42 EEST 2012
state:      open
^C

``` I think it doesn't sense it :S I remember my earlier ubuntu systems sensed that though

---

### Post by Toz on 2012-10-10
A few more questions and another test:

1. Do you have an external monitor attached? If so, try without the monitor connected.

2. Is the notebook in a dock? If so, try undocked.

3. Does it go to suspend in Windows when you close the lid?

And try running this command, closing and re-opening the lid, to see if anything gets registered:
```
acpi_listen
```
...post back the results,

EDIT: You might also want to try booting previous kernel versions to see if it is a regression in this kernel version.

---

### Post by PrinceNo1 on 2012-10-11
1-No i use only laptop screen
2-Laptop is not docked
3-Yes it suspends in Windows, i tried that
4-The command you quoted did not do anything at first. I closed the lid, waited 10 seconds and opened, and nothing changed. Then i began typing here and it suddenly decided to suspend. I mean it suspended 1 or 2 minutes after i closed and re-opened the lid. The command returned : ```
button/lid LID0 00000080 00000001
button/lid LID0 00000080 00000002

``` What's the delay?

---

### Post by clay7 on 2012-10-11
For hibernating, make sure that your Ubuntu swap partition is equal in size to your RAM (I usually set mine to 1MB more than my RAM).

I know your question is about suspending, but I've had problems with suspension before and making sure the swap partition was large enough solved it for me. A swap of 2G should be more than enough for suspending unless you have a very large amount of RAM.

---

### Post by Toz on 2012-10-11
> **PrinceNo1 said:**
> 1-No i use only laptop screen
2-Laptop is not docked
3-Yes it suspends in Windows, i tried that
4-The command you quoted did not do anything at first. I closed the lid, waited 10 seconds and opened, and nothing changed. Then i began typing here and it suddenly decided to suspend. I mean it suspended 1 or 2 minutes after i closed and re-opened the lid. The command returned : ```
button/lid LID0 00000080 00000001
button/lid LID0 00000080 00000002

``` What's the delay?

That is odd. Can you confirm whether this delay happens all the time (is repeatable)?

Also, have you tried booting previous kernels to see if the problem is specific to this kernel?

---

### Post by PrinceNo1 on 2012-10-11
I just repeated that, yes it happened again. By the way there is something i forgot to mention. When i drag my mouse to the upper left corner of the screen, the gnome activities panel opens up. There i see my desktop background image corrupted. Nothing else, just the background image is corrupted. Ok now i will try another kernel

---

### Post by PrinceNo1 on 2012-10-11
> **clay7 said:**
> For hibernating, make sure that your Ubuntu swap partition is equal in size to your RAM (I usually set mine to 1MB more than my RAM).

I know your question is about suspending, but I've had problems with suspension before and making sure the swap partition was large enough solved it for me. A swap of 2G should be more than enough for suspending unless you have a very large amount of RAM.
I can't see my swap partition in nautilus, how can i see that?

edit. ok i see it now from disk utility, it is 4.3 gb

---

### Post by PrinceNo1 on 2012-10-11
I booted in previous kernel (the only one i have as previous) 3.2.029 now and there is nothing different. The problem is same. But i have classic gnome in this kernel is this normal?

---

### Post by Toz on 2012-10-11
> **PrinceNo1 said:**
> I booted in previous kernel (the only one i have as previous) 3.2.029 now and there is nothing different. The problem is same. But i have classic gnome in this kernel is this normal?

1. Does this delay happen every time you close and open the lid?

2. Can you close lid, wait 5 seconds, open lid then post back /var/log/pm-suspend.log and /var/log/syslog? Use these commands and post back the link that is generated:
```
pastebinit /var/log/pm-suspend.log
pastebinit /var/log/syslog

```

I want to see if there is anything in your log files.

---

### Post by PrinceNo1 on 2012-10-12
Toz, thank you for giving time, i appreciate your help. My ubuntu doesn't recognize it when i close the lid at all. Suspend only works with "acpi_listen" command and with a couple of minutes delay. Also works only manually. Also everything works in my windows os. Here is the generated links: 
[http://paste.ubuntu.com/1274489/](http://paste.ubuntu.com/1274489/)
[http://paste.ubuntu.com/1274490/](http://paste.ubuntu.com/1274490/)

---

### Post by PrinceNo1 on 2012-10-12
Strange things happen here. Now i just did what you asked, closed lid and waited and opened and installed pastebinit, ran the commands you told me to, wrtitten a message and it suddenly decided to suspend after so long time (around 3-4 minutes maybe much later) :)

---

### Post by Toz on 2012-10-12
I don't see anything wrong or of interest in your log files. Do you have some acpi-related settings in your bios? Perhaps something about a timer?

---

### Post by PrinceNo1 on 2012-10-12
I didn't open my bios settings for so long time, i don't remember changing anything, i go and take a look

---

### Post by PrinceNo1 on 2012-10-13
I checked my bios and there is no such setting there. In fact, there is not many settings there. So what now?

---

### Post by Toz on 2012-10-13
It might be worth booting with the live cd and seeing if the lid events are being delayed on a clean install. That would rule out a system configuration issue. Or, maybe a bios update? (Might be a shot in the dark).

If not, I think you're best bet may be to create a bug report against the acpi-support package and see if a dev can look at it. Here is the acpi-support launchpad site: [https://launchpad.net/acpi-support]("https://launchpad.net/acpi-support").

To create a bug report:
```
apport-bug acpi-support
```
...(you will need to create a launchpad account if you don't already have one).

---

### Post by PrinceNo1 on 2012-10-16
Ok Toz thanks for your time. My machine doesnt have any problems right now and in principle i don't update my bios as long as it works ok :) So the better bet is to report a bug so that if something is buggy in the software side (i guess it is, cause my windows suspends fine), they would fix it :) I mark this as solved and create a bug report for launchpad. I appreciate your time, thank you again

---

