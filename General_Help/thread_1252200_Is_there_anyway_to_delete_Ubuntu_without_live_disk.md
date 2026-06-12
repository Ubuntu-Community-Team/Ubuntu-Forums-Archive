---
title: "Is there anyway to delete Ubuntu without live disk."
date: 2009-08-28
forum: General Help
---

### Post by curtis0432 on 2009-08-28
Hello I have not been experiencing not very good things with Linux. I am using Ubuntu 9.04 right now and it is not working and good as I thought it would. So I would like to delete it and try a different Linux.

First of all. I installed ubuntu(desktop version 9.04 64bit) perfectly. My dvd drive worked great. but after the installation i noticed that i could not load any type of media in my drive. And i also noticed that I could not transfer songs from ubuntu to my sansa fuze and sansa e250(which works with windows). So i was thinking of trying another linux beacause ubuntu realy doesnt seem to be working for me.

If i could fix those 2 major problems i would be happy using ubuntu.
And say if my email works on outlook express and it is from my ISP telus. how can i get it to work on ubuntu.

Im also woundering what i should try. If i can delete ubuntu desktop. I might try ubuntu 8.04 the bisnuss one and see if that works or Kubuntu. I have both of those live disk burnt. so i just need to know how to delete the partition and start over again.

Thanks

---

### Post by rajeev1204 on 2009-08-28
> **curtis0432 said:**
> Hello I have not been experiencing not very good things with Linux. I am using Ubuntu 9.04 right now and it is not working and good as I thought it would. So I would like to delete it and try a different Linux.

First of all. I installed ubuntu(desktop version 9.04 64bit) perfectly. My dvd drive worked great. but after the installation i noticed that i could not load any type of media in my drive. And i also noticed that I could not transfer songs from ubuntu to my sansa fuze and sansa e250(which works with windows). So i was thinking of trying another linux beacause ubuntu realy doesnt seem to be working for me.

If i could fix those 2 major problems i would be happy using ubuntu.
And say if my email works on outlook express and it is from my ISP telus. how can i get it to work on ubuntu.

Im also woundering what i should try. If i can delete ubuntu desktop. I might try ubuntu 8.04 the bisnuss one and see if that works or Kubuntu. I have both of those live disk burnt. so i just need to know how to delete the partition and start over again.

Thanks

Hello.

You can use the live cd to format the partition and install the version from the live cd.
Or you could use another partition editor to wipe your hard drive clean.

But it will delete all data on that hard drive.You cant just 'delete' ubuntu ,you format a partition which prepares the partition clean for a fresh install.

Also,when you say you cant load any media in your drive ,do you mean you cant play any media?Do you get any missing codecs messages.?

Also, 8.04 is the LTS(long term support) release and it will be generally more stable than newer releases,you could try it if you are having problems with your drive.

thanks

rajeev

---

### Post by MTGap on 2009-08-28
Changing distros most likely won't help solve those problems, you should first try giving more details of those problems so that you could have them fixed.

How did you configure outlook express with your email? Just do the same with ubuntu's email client (Is gnome's empathy?, I use kmail)

---

### Post by curtis0432 on 2009-08-28
Yes when i put in a disc(dvd,cd,live disc) nothing happens and when i go to load it manualy it says unable to mount location Cant mount file.

So how do i wipe my hard disk and try Ubuntu 8.04?

thanks for your help so-far

---

### Post by crownedzero on 2009-08-28
> **MTGap said:**
> Changing distros most likely won't help solve those problems.

Agreed.

Swapping to Ubuntu or any Linux distro has a learning curve. You've got to do your homework and try and resolve issues.

Try googling some of your problems and odds are you will find the solutions.


Sansa Fuze and Linux
[http://forums.sandisk.com/sansa/](http://forums.sandisk.com/sansa/)

As far as the dvdrom is concerned, you won't get much help without a description of what it is that is taking place.

Email and Ubuntu (I'm sure there's info on this site, but this is the first link that popped up on Google.)
[http://www.easy-ubuntu-linux.com/email-configure-1.html](http://www.easy-ubuntu-linux.com/email-configure-1.html)

Hope that helps.

Remember, try Google first, if you can't make heads or tails of that ask, it beats having to swap your OS everytime something doesn't work as intended.

---

### Post by rajeev1204 on 2009-08-28
> **curtis0432 said:**
> Yes when i put in a disc(dvd,cd,live disc) nothing happens and when i go to load it manualy it says unable to mount location Cant mount file.

So how do i wipe my hard disk and try Ubuntu 8.04?

thanks for your help so-far

I have this exact problem with 9.04,so i use 8.04 where dvd drive works nice.
PLease try it and report back .


To install ubuntu 8.04,use a live cd of 8.04 and set bios option to boot from cd.
Once it boots,follow instructions to install.

Just make sure you have back up of all important files,because installation will destroy all data on drive(or partition to which you install)

But before you install,lets try to see what the actual problem with dvd drive is.

Could you try command 'mount' in terminal and paste the output here.

Also,i would like to see the output of dmesg.

---

### Post by curtis0432 on 2009-08-28
Ya but the problem is, is that i cant get the disc to read/be reconized ubuntu. so do you know if when i go into the bios it will beable to read the disc. and if that method doesn't work is there a way to manually delete everything off my hard disk.

by the way i have tried researching about my problems and i haven't been able to find the solution.

---

### Post by curtis0432 on 2009-08-29
OK here is the output of the commands that you wanted to see.

command 'mount'

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/family/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nod

dmesg

[    0.340224] node 0 link 0: mmio [fe900000, feafffff]
[    0.340224] node 0 link 0: mmio [feb00000, ffefffff]
[    0.340224] TOM2: 0000000130000000 aka 4864M
[    0.340224] bus: [00,07] on node 0 link 0
[    0.340224] bus: 00 index 0 io port: [0, ffff]
[    0.340224] bus: 00 index 1 mmio: [a0000, bffff]
[    0.340224] bus: 00 index 2 mmio: [d0000000, dfffffff]
[    0.340224] bus: 00 index 3 mmio: [f0000000, ffffffff]
[    0.340224] bus: 00 index 4 mmio: [130000000, fcffffffff]
[    0.340224] ACPI: bus type pci registered
[    0.340224] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.340224] PCI: Not using MMCONFIG.
[    0.340224] PCI: Using configuration type 1 for base access
[    0.340224] PCI: Using configuration type 1 for extended access
[    0.340589] ACPI: EC: Look up EC in DSDT
[    0.351488] ACPI: Interpreter enabled
[    0.351490] ACPI: (supports S0 S1 S3 S4 S5)
[    0.351505] ACPI: Using IOAPIC for interrupt routing
[    0.351556] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.355740] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.364506] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.372186] ACPI: No dock devices found.
[    0.372247] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.372341] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.372343] pci 0000:00:0a.0: PME# disabled
[    0.372388] pci 0000:00:11.0: reg 10 io port: [0xc000-0xc007]
[    0.372395] pci 0000:00:11.0: reg 14 io port: [0xb000-0xb003]
[    0.372400] pci 0000:00:11.0: reg 18 io port: [0xa000-0xa007]
[    0.372406] pci 0000:00:11.0: reg 1c io port: [0x9000-0x9003]
[    0.372412] pci 0000:00:11.0: reg 20 io port: [0x8000-0x800f]
[    0.372418] pci 0000:00:11.0: reg 24 32bit mmio: [0xfe8ffc00-0xfe8fffff]
[    0.372435] pci 0000:00:11.0: set SATA to AHCI mode
[    0.372462] pci 0000:00:12.0: reg 10 32bit mmio: [0xfe8fe000-0xfe8fefff]
[    0.372509] pci 0000:00:12.1: reg 10 32bit mmio: [0xfe8fd000-0xfe8fdfff]
[    0.372573] pci 0000:00:12.2: reg 10 32bit mmio: [0xfe8ff800-0xfe8ff8ff]
[    0.372608] pci 0000:00:12.2: supports D1 D2
[    0.372609] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.372613] pci 0000:00:12.2: PME# disabled
[    0.372641] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe8fc000-0xfe8fcfff]
[    0.372688] pci 0000:00:13.1: reg 10 32bit mmio: [0xfe8fb000-0xfe8fbfff]
[    0.372751] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe8ff400-0xfe8ff4ff]
[    0.372786] pci 0000:00:13.2: supports D1 D2
[    0.372787] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.372791] pci 0000:00:13.2: PME# disabled
[    0.372888] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.372894] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.372899] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.372905] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.372911] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]
[    0.372962] pci 0000:00:14.2: reg 10 64bit mmio: [0xfe8f4000-0xfe8f7fff]
[    0.372993] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.372996] pci 0000:00:14.2: PME# disabled
[    0.373086] pci 0000:00:14.5: reg 10 32bit mmio: [0xfe8fa000-0xfe8fafff]
[    0.373197] pci 0000:01:05.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
[    0.373200] pci 0000:01:05.0: reg 14 io port: [0xd000-0xd0ff]
[    0.373203] pci 0000:01:05.0: reg 18 32bit mmio: [0xfeaf0000-0xfeafffff]
[    0.373208] pci 0000:01:05.0: reg 24 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.373214] pci 0000:01:05.0: supports D1 D2
[    0.373250] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.373252] pci 0000:00:01.0: bridge 32bit mmio: [0xfe900000-0xfeafffff]
[    0.373256] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.373286] pci 0000:02:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.373300] pci 0000:02:00.0: reg 18 64bit mmio: [0xfdfff000-0xfdffffff]
[    0.373309] pci 0000:02:00.0: reg 20 64bit mmio: [0xfdff8000-0xfdffbfff]
[    0.373315] pci 0000:02:00.0: reg 30 32bit mmio: [0xfebe0000-0xfebfffff]
[    0.373323] pci 0000:02:00.0: supports D1 D2
[    0.373324] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.373327] pci 0000:02:00.0: PME# disabled
[    0.373379] pci 0000:00:0a.0: bridge io port: [0xe000-0xefff]
[    0.373381] pci 0000:00:0a.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.373384] pci 0000:00:0a.0: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.373436] pci 0000:00:14.4: transparent bridge
[    0.373453] bus 00 -> node 0
[    0.373458] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.373756] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.373854] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.373948] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.376217] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *7 10 11 12 14 15)
[    0.376325] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.376430] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.376534] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
[    0.376638] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.376743] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.376848] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 10 *11 12 14 15)
[    0.376953] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.377050] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 39, should be 2E [20080926]
[    0.377097] ACPI: WMI: Mapper loaded
[    0.377134] SCSI subsystem initialized
[    0.377134] libata version 3.00 loaded.
[    0.377134] usbcore: registered new interface driver usbfs
[    0.377134] usbcore: registered new interface driver hub
[    0.377134] usbcore: registered new device driver usb
[    0.377134] PCI: Using ACPI for IRQ routing
[    0.392008] Bluetooth: Core ver 2.13
[    0.392018] NET: Registered protocol family 31
[    0.392018] Bluetooth: HCI device and connection manager initialized
[    0.392018] Bluetooth: HCI socket layer initialized
[    0.392018] NET: Registered protocol family 8
[    0.392018] NET: Registered protocol family 20
[    0.392023] NetLabel: Initializing
[    0.392024] NetLabel:  domain hash size = 128
[    0.392025] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.392035] NetLabel:  unlabeled traffic allowed by default
[    0.392142] PCI-DMA: Disabling AGP.
[    0.392202] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.392203] PCI-DMA: using GART IOMMU.
[    0.392206] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.393732] AppArmor: AppArmor Filesystem Enabled
[    0.404010] pnp: PnP ACPI init
[    0.404025] ACPI: bus type pnp registered
[    0.408026] pnp: PnP ACPI: found 19 devices
[    0.408028] ACPI: ACPI bus type pnp unregistered
[    0.408039] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.408041] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.408045] system 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[    0.408047] system 00:0c: ioport range 0x40b-0x40b has been reserved
[    0.408048] system 00:0c: ioport range 0x4d6-0x4d6 has been reserved
[    0.408050] system 00:0c: ioport range 0xc00-0xc01 has been reserved
[    0.408051] system 00:0c: ioport range 0xc14-0xc14 has been reserved
[    0.408053] system 00:0c: ioport range 0xc50-0xc51 has been reserved
[    0.408054] system 00:0c: ioport range 0xc52-0xc52 has been reserved
[    0.408056] system 00:0c: ioport range 0xc6c-0xc6c has been reserved
[    0.408057] system 00:0c: ioport range 0xc6f-0xc6f has been reserved
[    0.408059] system 00:0c: ioport range 0xcd0-0xcd1 has been reserved
[    0.408060] system 00:0c: ioport range 0xcd2-0xcd3 has been reserved
[    0.408062] system 00:0c: ioport range 0xcd4-0xcd5 has been reserved
[    0.408063] system 00:0c: ioport range 0xcd6-0xcd7 has been reserved
[    0.408065] system 00:0c: ioport range 0xcd8-0xcdf has been reserved
[    0.408066] system 00:0c: ioport range 0x800-0x89f has been reserved
[    0.408068] system 00:0c: ioport range 0xb00-0xb0f has been reserved
[    0.408070] system 00:0c: ioport range 0xb20-0xb3f has been reserved
[    0.408071] system 00:0c: ioport range 0x900-0x90f has been reserved
[    0.408073] system 00:0c: ioport range 0x910-0x91f has been reserved
[    0.408074] system 00:0c: ioport range 0xfe00-0xfefe has been reserved
[    0.408076] system 00:0c: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.408078] system 00:0c: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.408084] system 00:10: ioport range 0x290-0x29f has been reserved
[    0.408087] system 00:11: iomem range 0xe0000000-0xefffffff has been reserved
[    0.408090] system 00:12: iomem range 0x0-0x9ffff could not be reserved
[    0.408092] system 00:12: iomem range 0xc0000-0xcffff has been reserved
[    0.408094] system 00:12: iomem range 0xe0000-0xfffff could not be reserved
[    0.408095] system 00:12: iomem range 0x100000-0xcfffffff could not be reserved
[    0.408097] system 00:12: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.412725] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.412727] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.412729] pci 0000:00:01.0:   MEM window: 0xfe900000-0xfeafffff
[    0.412731] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.412734] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
[    0.412736] pci 0000:00:0a.0:   IO window: 0xe000-0xefff
[    0.412738] pci 0000:00:0a.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.412740] pci 0000:00:0a.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.412743] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.412744] pci 0000:00:14.4:   IO window: disabled
[    0.412748] pci 0000:00:14.4:   MEM window: disabled
[    0.412751] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.412766] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.412768] pci 0000:00:0a.0: setting latency timer to 64
[    0.412774] bus: 00 index 0 io port: [0x00-0xffff]
[    0.412776] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.412777] bus: 01 index 0 io port: [0xd000-0xdfff]
[    0.412779] bus: 01 index 1 mmio: [0xfe900000-0xfeafffff]
[    0.412780] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.412781] bus: 01 index 3 mmio: [0x0-0x0]
[    0.412783] bus: 02 index 0 io port: [0xe000-0xefff]
[    0.412784] bus: 02 index 1 mmio: [0xfeb00000-0xfebfffff]
[    0.412785] bus: 02 index 2 mmio: [0xfdf00000-0xfdffffff]
[    0.412786] bus: 02 index 3 mmio: [0x0-0x0]
[    0.412787] bus: 03 index 0 mmio: [0x0-0x0]
[    0.412788] bus: 03 index 1 mmio: [0x0-0x0]
[    0.412789] bus: 03 index 2 mmio: [0x0-0x0]
[    0.412790] bus: 03 index 3 io port: [0x00-0xffff]
[    0.412792] bus: 03 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.412800] NET: Registered protocol family 2
[    0.452048] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.452389] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.453582] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.453906] TCP: Hash tables configured (established 262144 bind 65536)
[    0.453908] TCP reno registered
[    0.464088] NET: Registered protocol family 1
[    0.464179] checking if image is initramfs... it is
[    0.860711] Freeing initrd memory: 7773k freed
[    0.863578] audit: initializing netlink socket (disabled)
[    0.863595] type=2000 audit(1251589367.860:1): initialized
[    0.868958] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.869728] VFS: Disk quotas dquot_6.5.1
[    0.869763] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.870133] fuse init (API version 7.10)
[    0.870180] msgmni has been set to 7300
[    0.870311] alg: No test for stdrng (krng)
[    0.870322] io scheduler noop registered
[    0.870324] io scheduler anticipatory registered
[    0.870325] io scheduler deadline registered
[    0.870347] io scheduler cfq registered (default)
[    0.952104] Switched to high resolution mode on CPU 0
[    0.952480] Switched to high resolution mode on CPU 1
[    0.988520] pci 0000:01:05.0: Boot video device
[    0.992219] pcieport-driver 0000:00:0a.0: setting latency timer to 64
[    0.992238] pcieport-driver 0000:00:0a.0: found MSI capability
[    0.992256] pcieport-driver 0000:00:0a.0: irq 2303 for MSI/MSI-X
[    0.992262] pci_express 0000:00:0a.0:pcie00: allocate port service
[    0.992272] pci_express 0000:00:0a.0:pcie03: allocate port service
[    0.992307] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.992312] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.992405] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.992407] ACPI: Power Button (FF) [PWRF]
[    0.992438] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.992440] ACPI: Power Button (CM) [PWRB]
[    0.992692] processor ACPI_CPU:00: registered as cooling_device0
[    0.992696] ACPI: Processor [P001] (supports 8 throttling states)
[    0.992734] processor ACPI_CPU:01: registered as cooling_device1
[    1.024148] hpet_acpi_add: no address or irqs in _CRS
[    1.024159] Linux agpgart interface v0.103
[    1.024167] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.024267] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.024362] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.024609] 00:0f: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.025049] brd: module loaded
[    1.025243] loop: module loaded
[    1.025285] Fixed MDIO Bus: probed
[    1.025290] PPP generic driver version 2.4.2
[    1.025328] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.025347] Driver 'sd' needs updating - please use bus_type methods
[    1.025353] Driver 'sr' needs updating - please use bus_type methods
[    1.025376] ahci 0000:00:11.0: version 3.0
[    1.025392] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.025486] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.025489] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.025783] scsi0 : ahci
[    1.025856] scsi1 : ahci
[    1.025895] scsi2 : ahci
[    1.025938] scsi3 : ahci
[    1.025995] ata1: SATA max UDMA/133 irq_stat 0x00400000 irq 22, PHY RDY changed
[    1.025998] ata2: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd80 irq 22
[    1.026001] ata3: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe00 irq 22
[    1.026004] ata4: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe80 irq 22
[    1.912035] ata1: softreset failed (device not ready)
[    1.912072] ata1: failed due to HW bug, retry pmp=0
[    2.076039] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.076834] ata1.00: ATA-8: WDC WD5001AALS-00L3B2, 01.03B01, max UDMA/133
[    2.076835] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.077742] ata1.00: configured for UDMA/133
[    2.576030] ata2: softreset failed (device not ready)
[    2.576061] ata2: failed due to HW bug, retry pmp=0
[    2.740032] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.740615] ata2.00: ATA-7: ST3250410AS, 4.AAA, max UDMA/133
[    2.740617] ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.741343] ata2.00: configured for UDMA/133
[    3.076021] ata3: SATA link down (SStatus 0 SControl 300)
[    3.412029] ata4: SATA link down (SStatus 0 SControl 300)
[    3.428083] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5001AALS-0 01.0 PQ: 0 ANSI: 5
[    3.428139] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    3.428148] sd 0:0:0:0: [sda] Write Protect is off
[    3.428150] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.428163] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.428201] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    3.428208] sd 0:0:0:0: [sda] Write Protect is off
[    3.428209] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.428221] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.428225]  sda: sda1 sda2 < sda5 >
[    3.452827] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.452856] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.452911] scsi 1:0:0:0: Direct-Access     ATA      ST3250410AS      4.AA PQ: 0 ANSI: 5
[    3.452968] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    3.452977] sd 1:0:0:0: [sdb] Write Protect is off
[    3.452979] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.452995] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.453035] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    3.453042] sd 1:0:0:0: [sdb] Write Protect is off
[    3.453043] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.453056] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.453059]  sdb: unknown partition table
[    3.461561] sd 1:0:0:0: [sdb] Attached SCSI disk
[    3.461585] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    3.461743] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.461765] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    3.461829] scsi4 : pata_atiixp
[    3.461872] scsi5 : pata_atiixp
[    3.462904] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    3.462906] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    3.791883] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.791896] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.791908] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    3.791944] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    3.791964] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    3.791980] ehci_hcd 0000:00:12.2: debug port 1
[    3.791994] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe8ff800
[    3.800015] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    3.800067] usb usb1: configuration #1 chosen from 1 choice
[    3.800084] hub 1-0:1.0: USB hub found
[    3.800089] hub 1-0:1.0: 6 ports detected
[    3.800159] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.800167] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    3.800191] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    3.800207] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    3.800222] ehci_hcd 0000:00:13.2: debug port 1
[    3.800233] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe8ff400
[    3.812008] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    3.812040] usb usb2: configuration #1 chosen from 1 choice
[    3.812057] hub 2-0:1.0: USB hub found
[    3.812060] hub 2-0:1.0: 6 ports detected
[    3.812120] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.812130] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.812137] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    3.812162] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    3.812179] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe8fe000
[    3.872034] usb usb3: configuration #1 chosen from 1 choice
[    3.872047] hub 3-0:1.0: USB hub found
[    3.872054] hub 3-0:1.0: 3 ports detected
[    3.872108] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.872114] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    3.872142] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    3.872153] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe8fd000
[    3.928029] usb usb4: configuration #1 chosen from 1 choice
[    3.928043] hub 4-0:1.0: USB hub found
[    3.928049] hub 4-0:1.0: 3 ports detected
[    3.928108] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.928116] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.928137] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    3.928153] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe8fc000
[    3.984028] usb usb5: configuration #1 chosen from 1 choice
[    3.984040] hub 5-0:1.0: USB hub found
[    3.984046] hub 5-0:1.0: 3 ports detected
[    3.984102] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.984109] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.984132] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    3.984143] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe8fb000
[    4.040021] usb usb6: configuration #1 chosen from 1 choice
[    4.040035] hub 6-0:1.0: USB hub found
[    4.040041] hub 6-0:1.0: 3 ports detected
[    4.040099] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.040107] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    4.040133] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    4.040144] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe8fa000
[    4.096024] usb usb7: configuration #1 chosen from 1 choice
[    4.096037] hub 7-0:1.0: USB hub found
[    4.096043] hub 7-0:1.0: 2 ports detected
[    4.096095] uhci_hcd: USB Universal Host Controller Interface driver
[    4.096150] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    4.098736] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.098739] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.108530] mice: PS/2 mouse device common for all mice
[    4.144546] rtc_cmos 00:05: RTC can wake from S4
[    4.144568] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    4.144588] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    4.144625] device-mapper: uevent: version 1.0.3
[    4.144680] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    4.144755] device-mapper: multipath: version 1.0.5 loaded
[    4.144758] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.144844] cpuidle: using governor ladder
[    4.144845] cpuidle: using governor menu
[    4.145112] TCP cubic registered
[    4.145154] NET: Registered protocol family 10
[    4.145417] lo: Disabled Privacy Extensions
[    4.145603] NET: Registered protocol family 17
[    4.145616] Bluetooth: L2CAP ver 2.11
[    4.145617] Bluetooth: L2CAP socket layer initialized
[    4.145618] Bluetooth: SCO (Voice Link) ver 0.6
[    4.145619] Bluetooth: SCO socket layer initialized
[    4.145644] Bluetooth: RFCOMM socket layer initialized
[    4.145649] Bluetooth: RFCOMM TTY layer initialized
[    4.145650] Bluetooth: RFCOMM ver 1.10
[    4.145682] powernow-k8: Found 1 AMD Athlon(tm) 7850 Dual-Core Processor processors (2 cpu cores) (version 2.20.00)
[    4.145714] powernow-k8:    0 : pstate 0 (2800 MHz)
[    4.145716] powernow-k8:    1 : pstate 1 (1400 MHz)
[    4.145840] registered taskstats version 1
[    4.145939]   Magic number: 5:318:758
[    4.146001] rtc_cmos 00:05: setting system clock to 2009-08-29 23:42:51 UTC (1251589371)
[    4.146003] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.146004] EDD information not available.
[    4.146030] Freeing unused kernel memory: 532k freed
[    4.146190] Write protecting the kernel read-only data: 6688k
[    4.167580] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.264536] Floppy drive(s): fd0 is 1.44M
[    4.279913] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.279930] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.279943] r8169 0000:02:00.0: setting latency timer to 64
[    4.280024] r8169 0000:02:00.0: irq 2302 for MSI/MSI-X
[    4.280464] eth0: RTL8168d/8111d at 0xffffc2000007e000, 00:19:66:c2:d7:64, XID 283000c0 IRQ 2302
[    4.285004] FDC 0 is a post-1991 82077
[    4.392516] usb 3-2: new full speed USB device using ohci_hcd and address 2
[    4.580206] usb 3-2: configuration #1 chosen from 1 choice
[    4.584902] PM: Starting manual resume from disk
[    4.584905] PM: Resume from partition 8:5
[    4.584906] PM: Checking hibernation image.
[    4.585045] PM: Resume from disk failed.
[    4.628321] kjournald starting.  Commit interval 5 seconds
[    4.628330] EXT3-fs: mounted filesystem with ordered data mode.
[    8.281138] udev: starting version 141
[    8.619823] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x043D pid 0x0057
[    8.619854] usbcore: registered new interface driver usblp
[    8.682345] input: PC Speaker as /devices/platform/pcspkr/input/input4
[    8.754528] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.819144] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[    8.819147] ACPI: Device needs an ACPI driver
[    8.819154] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    8.950923] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    9.178927] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    9.194523] [fglrx] Maximum main memory to use for locked dma buffers: 3493 MBytes.
[    9.194543] [fglrx]   vendor: 1002 device: 9614 count: 1
[    9.194693] [fglrx] ioport: bar 1, base 0xd000, size: 0x100
[    9.194705] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.194709] pci 0000:01:05.0: setting latency timer to 64
[    9.195887] [fglrx] Driver built-in PAT support is enabled successfully
[    9.195968] [fglrx] module loaded - fglrx 8.60.40 [Mar 14 2009] with 1 minors
[    9.197683] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[    9.253819] ip_tables: (C) 2000-2006 Netfilter Core Team
[    9.322252] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.337539] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[    9.337690] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[    9.337691] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[    9.337693] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[    9.505147] lp: driver loaded but no devices found
[    9.555990] Adding 10948256k swap on /dev/sda5.  Priority:-1 extents:1 across:10948256k
[   59.683878] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   59.684174] EXT3 FS on sda1, internal journal
[   60.532236] type=1505 audit(1251589427.886:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2746
[   60.562091] type=1505 audit(1251589427.914:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2750
[   60.562176] type=1505 audit(1251589427.914:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2750
[   60.562203] type=1505 audit(1251589427.914:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2750
[   60.562227] type=1505 audit(1251589427.914:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2750
[   60.586314] type=1505 audit(1251589427.938:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=2755
[   60.680052] type=1505 audit(1251589428.034:8): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2759
[   60.680174] type=1505 audit(1251589428.034:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2759
[   60.698493] type=1505 audit(1251589428.050:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2763
[   64.568472] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   64.568474] Bluetooth: BNEP filters: protocol multicast
[   64.689232] Bridge firewalling registered
[   66.100127] ppdev: user-space parallel port driver
[   67.465521] [fglrx] GART Table is not in FRAME_BUFFER range 
[   67.467446] fglrx_pci 0000:01:05.0: irq 2301 for MSI/MSI-X
[   67.476224] [fglrx] Firegl kernel thread PID: 3921
[   67.478590] APIC error on CPU1: 00(08)
[   67.478594] APIC error on CPU0: 00(08)
[   67.493896] [fglrx] Gart USWC size:1761 M.
[   67.493899] [fglrx] Gart cacheable size:60 M.
[   67.493903] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   67.493905] [fglrx] Reserved FB block: Unshared offset:17ffb000, size:5000 
[   69.647705] r8169: eth0: link up
[   69.647714] r8169: eth0: link up
[   80.568005] eth0: no IPv6 routers present
[  207.810102] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[  208.314934] psmouse.c: resync failed, issuing reconnect request
[  208.388727] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume



Thanks

---

