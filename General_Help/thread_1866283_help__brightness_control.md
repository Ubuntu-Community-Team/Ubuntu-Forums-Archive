---
title: "help : brightness control"
date: 2011-10-21
forum: General Help
---

### Post by dsuresh on 2011-10-21
hi,,

   i am using xubuntu 11.10  in samsung mini n148 laptop.. how to control brightness ...default key  fn + down arrow not control the brightness ...  please help...

thank  u

---

### Post by matt_symes on 2011-10-21
Hi

Please post the output of

```
ls /sys/class/backlight
```

Kind regards

---

### Post by dsuresh on 2011-10-21
desktop@ubuntu:/etc/default$ ls /sys/class/backlight

acpi_video0  intel_backlight




> **matt_symes said:**
> Hi

Please post the output of

```
ls /sys/class/backlight
```

Kind regards

---

### Post by matt_symes on 2011-10-21
Hi

> **dsuresh said:**
> desktop@ubuntu:/etc/default$ ls /sys/class/backlight

acpi_video0  intel_backlight

Interesting. You have two entries. Let's see which one works (if either).

From the terminal type

```
sudo bash -c "echo 2 > /sys/class/backlight/acpi_video0/brightness"
```Does that darken the screen ? If not try

```
sudo bash -c "echo 2 > /sys/class/backlight/intel_backlight/brightness"
```Does that darken the screen ?

If the screen is darkened then type

 ```
sudo bash -c "echo 9 > /sys/class/backlight/**ZZZZ**/brightness"


```and replace **ZZZZ** with which ever one darkened the screen.

Post back results.

**EDIT:** I have to pop out for a couple of hours. If no one else picks this up i will continue it later.

Kind regards

---

### Post by dsuresh on 2011-10-21
this command working : 

sudo bash -c "echo 2 > /sys/class/backlight/intel_backlight/brightness"

...

---

### Post by matt_symes on 2011-10-21
Hi

> **dsuresh said:**
> this command working : 

sudo bash -c "echo 2 > /sys/class/backlight/intel_backlight/brightness"

...

Can you post the output of

```
cat /proc/cmdline
```

It may help to resolve why you have two entries.

So we need to remove acpi_video0. Open a terminal and type

```
sudo modprobe -r video
```

Check your brightness buttons again. 

Post back the results.

This will not persist after a reboot so, if it works, we can look at making it permanent.

Kind regards

---

### Post by dsuresh on 2011-10-21
desktop@ubuntu:~$ cat /proc/cmdline

[COLOR="Sienna"]BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=be5daad2-0aa9-49ca-b2e3-aae1cca3bee6 ro quiet splash vt.handoff=7[/COLOR]


desktop@ubuntu:~$ sudo modprobe -r video
[sudo] password for desktop: 
[COLOR="Sienna"]FATAL: Module video is in use.
[/COLOR]

---

### Post by matt_symes on 2011-10-21
Hi
> **dsuresh said:**
> desktop@ubuntu:~$ cat /proc/cmdline

[COLOR=Sienna]BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=be5daad2-0aa9-49ca-b2e3-aae1cca3bee6 ro quiet splash vt.handoff=7[/COLOR]

Nothing wrong with this command line.

> 
desktop@ubuntu:~$ sudo modprobe -r video
[sudo] password for desktop: 
[COLOR=Sienna]FATAL: Module video is in use.
[/COLOR]

This is interesting and may be the reason why you have two entries.

Let's try to blacklist it and reboot.

From the terminal...

```
sudo bash -c "echo 'blacklist video' >> /etc/modprobe.d/blacklist.conf"
```

```
sudo reboot
```

Post back.

Kind regards

---

### Post by dsuresh on 2011-10-21
no.its not working....

---

### Post by matt_symes on 2011-10-22
Hi

The good thing is we know what the problem is. We just need to work out how to fix it.

Let's try to force it to use Intels version. Open a terminal and type

```
sudo nano /etc/default/grub
```Look for the two line that say

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```and edit them so they say

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```Press ctrl + o to save and ctrl + x to exit.

Then type

```
sudo update-grub
```Reboot your PC and try again.

Post back the results of

```
cat /proc/cmdline
```and 

```
ls /sys/class/backlight
```after making the above changes.

Kind regards

---

### Post by dsuresh on 2011-10-22
$: cat /proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=450425e4-b41a-441e-9d3e-1af04189e5a2 ro quiet splash vt.handoff=7


$; /sys/class/backlight

acpi_video0  intel_backlight

---

### Post by matt_symes on 2011-10-22
Hi

Sorry. Please repeat the commands in my last post #10 but instead of using ...
[FONT=monospace]
[/FONT]```
sudo updategrub
```please use

```
sudo update-grub
```I have a sticky keyboard that needs cleaning :(

I have edited post #10

Kind regards

---

### Post by dsuresh on 2011-10-22
hi matt_symes,  thanks... its working...great effort ....thanks again...

---

### Post by matt_symes on 2011-10-22
Hi

Your welcome :). Please could you mark this thread as solved.

Kind regards

---

### Post by donovan6000 on 2011-10-30
Sorry for reviving a week old topic, but I'm having a similar problem.

My /sys/class/backlight/ contains the folders acpi_video0 and acpi_video1

I've determined that acpi_video0 is able to change my backlight through 
sudo bash -c "echo 6 > /sys/class/backlight/acpi_video0/brightness"

But acpi_video1 doesn't do anything

Is there a way I can blacklist just one of them?

---

### Post by dsuresh on 2011-10-30
hi, donovan6000,

          try to run the 10 & 12 post....



> **donovan6000 said:**
> Sorry for reviving a week old topic, but I'm having a similar problem.

My /sys/class/backlight/ contains the folders acpi_video0 and acpi_video1

I've determined that acpi_video0 is able to change my backlight through 
sudo bash -c "echo 6 > /sys/class/backlight/acpi_video0/brightness"

But acpi_video1 doesn't do anything

Is there a way I can blacklist just one of them?

---

### Post by donovan6000 on 2011-10-30
I've already tried just about every solution I've come across, but none of them work.

When I try the fix from those post my backlight just stays at 100% no matter what. And there are no files in my /sys/class/backlight folder.

---

### Post by matt_symes on 2011-10-31
Hi

Open a terminal and type

```
sudo modprobe -r video
```

Post back results and also the results of 

```
ls /sys/class/backlight
```

Kind regards

---

### Post by donovan6000 on 2011-11-01
After I add the lines to my /etc/default/grub file and update grub, my /sys/class/backlight folder become empty.

Even after running modprobe -r video, the backlight remains unchangable. Do the ati drivers use a different directory for the backlight?

---

### Post by matt_symes on 2011-11-02
Hi

> **donovan6000 said:**
> After I add the lines to my /etc/default/grub file and update grub, my /sys/class/backlight folder become empty.

Even after running modprobe -r video, the backlight remains unchangable. Do the ati drivers use a different directory for the backlight?

If your backlight folder is empty after adding the kernel command line then this means it has not loaded the backlight kernel module for your laptop.

What is the exact make and model of your laptop ?

Also now that the default backlight folder is empty open a terminall and type

```
sudo modprobe video
```

This will reload the backlight video kernel modue. How many entries do you have in your backlight folder ?

Does this lower your backlight brightness ?

```
echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

If this works then we need to find out why two video module nodes are being created.

Kind regards

---

### Post by donovan6000 on 2011-11-02
Unfortunatley, as long as I have "acpi_backlight=vendor" in my /etc/default/grub file, then the backligth folder continues to remain empty.

Even after running "modprobe video", the folder is still empty

Without editing the grub file, acpi_video0 and acpi_video1 appear in the backlight folder

and if I run sudo bash -c "echo 6 > /sys/class/backlight/acpi_video0/brightness", then I am able to change my backlight via the teminal

my laptop is an HP Pavilion dv7t-4100
the graphics card it uses is the ATI mobility radeon 5650

Thanks for trying to help so much :D

---

### Post by matt_symes on 2011-11-02
Hi

I am intrigued by this. 

I am not sure if it's an ACPI issue caused by your BIOS or if it's higher up.

Have you looked into seeing if there is an update for your BIOS ?

Remove the acpi=vendor kernel command line for the moment and, for my curiosity, can you post the output of

```
ls -l /sys/devices/virtual/backlight/acpi_video*/device
```

I will look around to see if there is backlight module for your laptop. There is obviously not in the default distribution.

Kind regards

---

### Post by donovan6000 on 2011-11-02
Just checked, and my bios are upto date.

When I run

ls -l /sys/devices/virtual/backlight/acpi_video*/device
It doesnt disply anything. So i looked and there is no backlight folder there.

but there a backlight folder in my

/sys/devices/pci0000:00/0000:00:03.0/0000:01:00.0/backlight

and

ls -l /sys/devices/pci0000:00/0000:00:03.0/0000:01:00.0/backlight/acpi_video*/device

displays this

lrwxrwxrwx 1 root root 0 2011-11-02 19:15 /sys/devices/pci0000:00/0000:00:03.0/0000:01:00.0/backlight/acpi_video0/device -> ../../../0000:01:00.0
lrwxrwxrwx 1 root root 0 2011-11-02 19:15 /sys/devices/pci0000:00/0000:00:03.0/0000:01:00.0/backlight/acpi_video1/device -> ../../../0000:01:00.0

It this what that command was supposed to output?

---

### Post by matt_symes on 2011-11-03
Hi

> lrwxrwxrwx 1 root root 0 2011-11-02 19:15  /sys/devices/pci0000:00/0000:00:03.0/0000:01:00.0/backlight/acpi_video0/device  -> ../../../0000:01:00.0
lrwxrwxrwx 1 root root 0 2011-11-02 19:15  /sys/devices/pci0000:00/0000:00:03.0/0000:01:00.0/backlight/acpi_video1/device  -> ../../../0000:01:00.0

It this what that command was supposed to output?

Yes that is near enough. For some reason it is registering the same interface twice

Not quite sure why at the moment. I did assume it was a problem with your BIOS because,  as far as i am aware, the video.ko driver uses generic ACPI functionality to control the backlight.

It might be worth looking around to see if there is a backlight module specifically for your laptop.

Just as a sanity check can you post the output of
```

modprobe -l video
lsmod | grep video
```

Also, let's see if there is anything in dmesg

```
dmesg | grep -i acpi
```

I am not sure what is going on with your setup at the moment. :confused:

I may not be able to look again for a couple of days.

Kind regards

---

### Post by donovan6000 on 2011-11-03
When I run
```
modprobe -l video lsmod | grep video
```It outputs:

```

uvcvideo                       72711  0 
videodev                       93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
video                             19412  0

```
and
```
dmesg | grep -i acpi
```outputs this

```

[    0.000000]  BIOS-e820: 00000000bbebf000 - 00000000bbfbf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bbfbf000 - 00000000bbfff000 (ACPI data)
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 00000000bbffe120 00074 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 00000000bbffc000 000F4 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 00000000bbfe9000 0F2FB (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 00000000bbf5e000 00040
[    0.000000] ACPI: ASF! 00000000bbffd000 000A5 (v32 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: HPET 00000000bbffb000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 00000000bbffa000 0008C (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 00000000bbff9000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 00000000bbfe8000 00176 (v01 HPQOEM SLIC-MPC 00000001 SLIC 000F4240)
[    0.000000] ACPI: BOOT 00000000bbfe5000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: ASPT 00000000bbfe2000 00034 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: WDAT 00000000bbfe1000 00224 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 00000000bbfe0000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
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
[    0.006583] ACPI: Core revision 20110413
[    2.691491] PM: Registering ACPI NVS region at bbebf000 (1048576 bytes)
[    2.693470] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    2.693473] ACPI: bus type pci registered
[    2.719569] ACPI: EC: Look up EC in DSDT
[    2.742599] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.748674] ACPI: SSDT 00000000bbe91a98 0032A (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    2.749266] ACPI: Dynamic OEM Table Load:
[    2.749269] ACPI: SSDT           (null) 0032A (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    2.749500] ACPI: SSDT 00000000bbe90018 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    2.750068] ACPI: Dynamic OEM Table Load:
[    2.750071] ACPI: SSDT           (null) 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    2.822890] ACPI: SSDT 00000000bbe91718 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    2.823532] ACPI: Dynamic OEM Table Load:
[    2.823535] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    2.854681] ACPI: SSDT 00000000bbe8fd98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    2.855299] ACPI: Dynamic OEM Table Load:
[    2.855302] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    2.931790] ACPI: Interpreter enabled
[    2.931795] ACPI: (supports S0 S3 S4 S5)
[    2.931846] ACPI: Using IOAPIC for interrupt routing
[    3.351799] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    3.352011] ACPI: No dock devices found.
[    3.352016] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    3.352489] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-7e])
[    3.361321] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    3.361444] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    3.361489] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    3.361510] ACPI Warning: For \_SB_.PCI0.P0P1._PRT: Return Package has no elements (empty) (20110413/nspredef-456)
[    3.361546] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    3.361585] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    3.361688]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    3.361733]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    3.361735] ACPI _OSC control for PCIe not granted, disabling ASPM
[    3.367911] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus 7f])
[    3.368324]  pci0000:7f: Requesting ACPI _OSC control (0x1d)
[    3.368327]  pci0000:7f: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    3.368329] ACPI _OSC control for PCIe not granted, disabling ASPM
[    3.368856] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    3.368918] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    3.368980] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    3.369041] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    3.369102] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    3.369164] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    3.369227] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    3.369290] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    3.369812] PCI: Using ACPI for IRQ routing
[    3.408739] pnp: PnP ACPI init
[    3.408751] ACPI: bus type pnp registered
[    3.409259] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    3.409367] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    3.409406] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    3.409567] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    3.409618] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    3.409754] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.409803] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    3.409861] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    3.409925] pnp 00:08: Plug and Play ACPI device, IDs SYN1e1d SYN1e00 SYN0002 PNP0f13 (active)
[    3.410080] pnp 00:09: Plug and Play ACPI device, IDs HPQ0004 (active)
[    3.410433] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    3.607157] pnp 00:0b: Plug and Play ACPI device, IDs PNP0a03 (active)
[    3.607178] pnp: PnP ACPI: found 12 devices
[    3.607179] ACPI: ACPI bus type pnp unregistered
[    3.763817] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    3.815756] ACPI: AC Adapter [ACAD] (on-line)
[    3.815835] ACPI: Power Button [PWRB]
[    3.816215] ACPI: Lid Switch [LID0]
[    3.816271] ACPI: Power Button [PWRF]
[    3.816300] ACPI: acpi_idle yielding to intel_idle
[    4.017487] ACPI: Thermal Zone [TZ01] (40 C)
[    4.017511] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    4.223769] ACPI: Battery Slot [BAT0] (battery present)
[   17.816842] acpi device:0c: registered as cooling_device8
[   17.824557] acpi device:0d: registered as cooling_device9
[   17.824735] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   17.865790] pci 0000:01:00.0: power state changed by ACPI to D0
[   17.865795] pci 0000:01:00.0: power state changed by ACPI to D0

```

Im in no rush, so take all the time you need

---

### Post by matt_symes on 2011-11-04
Hi
[FONT=monospace]
[/FONT]> [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignoredThis is interesting. Your BIOS is asking your operating system if it is Linux. 

Nowadays Linux will just tell your BIOS that it is Windows OS, however it is possible to let your BIOS know it is running Linux OS.

This is from the kernel source file drivers/acpi/osl.c
> 
/*
 * The story of _OSI(Linux)
 *
 * From pre-history through Linux-2.6.22,
 * Linux responded TRUE upon a BIOS OSI(Linux) query.
 *
 * Unfortunately, reference BIOS writers got wind of this
 * and put OSI(Linux) in their example code, quickly exposing
 * this string as ill-conceived and opening the door to
 * an un-bounded number of BIOS incompatibilities.
 *
 * For example, OSI(Linux) was used on resume to re-POST a
 * video card on one system, because Linux at that time
 * could not do a speedy restore in its native driver.
 * But then upon gaining quick native restore capability,
 * Linux has no way to tell the BIOS to skip the time-consuming
 * POST -- putting Linux at a permanent performance disadvantage.
 * On another system, the BIOS writer used OSI(Linux)
 * to infer native OS support for IPMI!  On other systems,
 * OSI(Linux) simply got in the way of Linux claiming to
 * be compatible with other operating systems, exposing
 * BIOS issues such as skipped device initialization.
 *
 * So "Linux" turned out to be a really poor chose of
 * OSI string, and from Linux-2.6.23 onward we respond FALSE.
 *
 * BIOS writers should NOT query _OSI(Linux) on future systems.
 * Linux will complain on the console when it sees it, and return FALSE.
 * To get Linux to return TRUE for your system  will require
 * a kernel source update to add a DMI entry,
 * or boot with "acpi_osi=Linux"
 */
You can tell your BIOS that it is running Linux by adding the command *acpi_osi=Linux* to the kernel command line and then updating grub. This may or may not fix the issue and could introduce other issues.

I am interested in your BIOS. Open a terminal and type

```
sudo apt-get install dmidecode
```Then type 

```
sudo dmidecode -t 0
```Post the results back here.

Kind regards

---

### Post by donovan6000 on 2011-11-04
Adding *acpi_osi=Linux* to my grub file didn't change anything. I also tried it with acpi_backlight=vendor and it still didn't change anything.

sudo dmidecode -t 0 outputs```

# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Hewlett-Packard
    Version: F.23
    Release Date: 10/21/2010
    ROM Size: 1536 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
        Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        8042 keyboard services are supported (int 9h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 15.35
    Firmware Revision: 101.53

```

---

### Post by matt_symes on 2011-11-06
Hi

> Adding *acpi_osi=Linux* to my grub file didn't change anything.

Tht's a shame. More hope than anything else was that suggestion. 

I have to say that i am scratching my head here.

Kind regards

---

### Post by matt_symes on 2011-11-06
Hi

Let's try this. Again not sure if it will work as it should be set to false already.

From drivers/acpi/video.c.

> 
/*
 * By default, we don't allow duplicate ACPI video bus devices
 * under the same VGA controller
 */
static int allow_duplicates;
module_param(allow_duplicates, bool, 0644);Update the kernel command line and add *video.allow_duplicates=0* and then sudo update-grub. Reboot and try again. Look in /sys/class/backlight

Kind regards

---

### Post by donovan6000 on 2011-11-08
Still didn't change anything. Even with the new kernel command, my /sys/class/backlight still has both folders in it.

---

### Post by matt_symes on 2011-11-08
Hi

I'm at a loss at the moment. :confused: 

It does sound like buggy ACPI AML in your BIOS. I'm not sure how to fix it though. It could well be a bug as well in the ACPI code in the kernel or video driver.

I will keep looking as i am, slowly, going through the ACPI code and spec but at the moment i am not sure what the problem is.

Boot into a LiveCD/USB and try to change the brightness there. If it happens then suspect a bug in the code.

Kind regards

---

### Post by donovan6000 on 2011-11-19
Sorry it took so long to reply. Well I tried booting from a liveUSB, but the brightness still doesn't work there. It still just goes from 0% to 100% without any middle ground.

---

### Post by markbl on 2011-11-19
See my comment in another brightness thread but I solved all the brightness problems I was having with 11.10 by updating the bios in my laptop.

---

### Post by donovan6000 on 2011-11-20
So I finally managed to fix my backlight. I decided to try downgrading my bios and it worked. Now my backlight works natively in ubuntu without any additional commands on startup.

Thanks for all the help everyone :)

---

### Post by Toz on 2012-07-25
Thread closed.

---

