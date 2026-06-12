---
title: "Heavy disk I/O makes my desktop unresponsive."
date: 2009-07-14
forum: General Help
---

### Post by daimaru on 2009-07-14
hi all, I have had this problem since ubuntu 7.04 and somehow none of the upgrades has fixed this (always did clean fresh installs - its not a broken upgrade issue). frankly it is starting to get on my nerves and I was hoping someone might have some suggestions as how to fix it. 

I have included a screenshot to illustrate the problem. 

Problem:
When I write to my harddisks ubuntu becomes unresponsive. this happens when copying files, or formating something etc. I have no idea how to fix this, but as I mentioned it is really annoying, because when I copy stuff I can stop using ubuntu until copying is finished. 

As shown in the screenshot Virtualbox was just creating a disk partition for a virutal machine. durring that disk writing process my desktop was totally unresponsive, as you can see from the greyed out windows in the screenshot. firefox was supposed to load a new page, in the update manager I just clicked the "check" button, and in a terminal I had just typed "clear" and hit enter. 

Nothing happend until after Virtualbox had createed the partition. Then the updatemanager responded again, firefox finally loaded that page I had clicked and the clear command in the terminal executed. 

Funny thing is that durring the unresponsive phase, I was still able to focus on all the windows, they were greyed out, but they did take focus and were not hidden behind other windows , like when WindowsXP crashes or something like that.

Well thats the best I can do in explaining  this problem. hope everyone understood what I was trying to say.

---

### Post by mikewhatever on 2009-07-14
Can you post you computer specs: CPU, RAM. Creating a file system can be rather cpu, so that other programs don't get enough cpu and hdd access.

---

### Post by schmidtbag on 2009-07-14
yes, i think knowing the amount of ram and swap space you have is important.  also, are you using a home-built computer or is the hard drive replaced?  theres an easy possibility the hard drive's jumper settings are off, or its using "cable select" on a 40 pin cable (assuming the drive is ATA)

---

### Post by daimaru on 2009-07-15
thx for your repies. heres my specs:
2gb ram 2gb swap space
3 scsi harddisks 2x500gb 1x200gb

as to the creation of a partition being cpu intensive. it also happens when i copy a movie to a different location. 

The computer is home-built, and I have added hd's over the time. It could definately have jumper setting problems. One of my harddisks fried a while back and I moved stuff around. My windows xp and linux patition are on the sdc disk. I'm not sure how linux numbers the disks, but if it has something to do with "primary master slave secondary ... " and the letters a, b, c correspond to that, then my operating systems are on the third device (sdc) weird.
I also have to map my hd2 to hd0 in grub to get windows and linux to dual boot. 
I'm not sure if this can actually affect system performance. 

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x030b030a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b1df96d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2fbe2fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       12749   102406311    7  HPFS/NTFS
/dev/sdc3           12750       21929    73738350    f  W95 Ext'd (LBA)
/dev/sdc4           21930       60801   312239340    7  HPFS/NTFS
/dev/sdc5           12750       15299    20482843+  83  Linux
/dev/sdc6           15300       21674    51207156   83  Linux
/dev/sdc7           21675       21929     2048256   82  Linux swap / Solaris


```

I will check the jumper settings. but I guess there is no way rearrange my disks without having to reinstall windows and linux right? since it will change all drive letters and stuff. 

If you need any other info please post the command I need to run . thx

---

### Post by mikewhatever on 2009-07-15
> **daimaru said:**
> thx for your repies. heres my specs:
2gb ram 2gb swap space
3 scsi harddisks 2x500gb 1x200gb

as to the creation of a partition being cpu intensive. it also happens when i copy a movie to a different location. 

...

If you need any other info please post the command I need to run . thx

I am no expert, but it seems that in both cases, file system creation and copying large files, a lot of writing to disk happens, which is cpu intensive.
Can you post the output of **cat /proc/cpuinfo** command.

---

### Post by daimaru on 2009-07-15
heres the cpu info 
```

cat cpuinfo 
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz
stepping    : 6
cpu MHz        : 1600.000
cache size    : 4096 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips    : 4266.66
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz
stepping    : 6
cpu MHz        : 1600.000
cache size    : 4096 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips    : 4266.66
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:


``````

cat meminfo 
MemTotal:        2034820 kB
MemFree:         1174496 kB
Buffers:           17408 kB
Cached:           310420 kB
SwapCached:            0 kB
Active:           590532 kB
Inactive:         190276 kB
Active(anon):     458232 kB
Inactive(anon):        0 kB
Active(file):     132300 kB
Inactive(file):   190276 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       2048248 kB
SwapFree:        2048248 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:        453104 kB
Mapped:            74804 kB
Slab:              28196 kB
SReclaimable:      15304 kB
SUnreclaim:        12892 kB
PageTables:        15504 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3065656 kB
Committed_AS:     801444 kB
VmallocTotal:   34359738367 kB
VmallocUsed:       67916 kB
VmallocChunk:   34359661051 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       34752 kB
DirectMap2M:     2062336 kB

```short version of hwinfo. attached the full version as text file. 
```

sudo hwinfo --short
cpu:                                                            
                       Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz, 1600 MHz
                       Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz, 1600 MHz
keyboard:
  /dev/input/event3    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Logitech MX518 Optical Mouse
  /dev/input/mice      Macintosh mouse button emulation
graphics card:
                       nVidia GeForce 8800 GTS
sound:
                       nVidia MCP51 High Definition Audio
storage:
                       Floppy disk controller
                       nVidia MCP51 Serial ATA Controller
                       nVidia MCP51 Serial ATA Controller
                       nVidia MCP51 IDE
network:
  eth0                 nVidia MCP51 Ethernet Controller
network interface:
  pan0                 Ethernet network interface
  eth0                 Ethernet network interface
  lo                   Loopback network interface
disk:
  /dev/sdc             ST3500630A
  /dev/sdb             ST3200822AS
  /dev/sda             SAMSUNG HD501LJ
partition:
  /dev/sdc1            Partition
  /dev/sdc3            Partition
  /dev/sdc4            Partition
  /dev/sdc5            Partition
  /dev/sdc6            Partition
  /dev/sdc7            Partition
  /dev/sdb1            Partition
  /dev/sda1            Partition
cdrom:
  /dev/sr0             _NEC DVD_RW ND-3550A
usb controller:
                       nVidia MCP51 USB Controller
                       nVidia MCP51 USB Controller
bios:
                       BIOS
bridge:
                       nVidia MCP51 PCI Bridge
                       nVidia MCP51 LPC Bridge
                       nVidia C55 PCI Express bridge
                       nVidia C55 Host Bridge
hub:
                       Linux 2.6.28-13-generic ohci_hcd OHCI Host Controller
                       Linux 2.6.28-13-generic ehci_hcd EHCI Host Controller
memory:
                       Main Memory
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       PS/2 Controller
                       nVidia MCP51 Memory Controller 0
                       nVidia MCP51 SMBus
                       nVidia MCP51 Host Bridge
                       nVidia C55 Memory Controller
                       nVidia C55 Memory Controller
                       nVidia C55 Memory Controller
                       nVidia C55 Memory Controller
                       nVidia C55 Memory Controller
                       nVidia C55 Memory Controller
                       nVidia C55 Memory Controller
                       nVidia C55 Memory Controller
                       nVidia C55 Memory Controller
                       nVidia C55 Memory Controller
                       nVidia C55 Memory Controller
                       nVidia C55 Memory Controller
                       nVidia C55 Memory Controller
                       nVidia C55 Memory Controller
                       nVidia C55 Memory Controller
                       nVidia C55 Memory Controller
                       nVidia C55 Memory Controller
                       Sennheiser USB Headset


```I might have been wrong I think I have 1 IDE disk and 2 SCSI disks. OS is on IDE i think is there a command to see if i have ide or scsi disks while showing the partitions, because i think hwinfo --short  shows that i have a ide one right ?
```

storage:
                       Floppy disk controller
                       nVidia MCP51 Serial ATA Controller
                       nVidia MCP51 Serial ATA Controller
                       nVidia MCP51 IDE

```or does this tell me my mainboard has those controlers?

why does it say IDE on all these disks weird
```

hwinfo --disk
35: IDE 400.0: 10600 Disk                                       
  [Created at block.243]
  UDI: /org/freedesktop/Hal/devices/storage_serial_SATA_ST3500630A_9QG3KB4C
  Unique ID: _kuT.mUgM6TiI1BE
  Parent ID: qnJ_.krcH2k4p6jB
  SysFS ID: /class/block/sdc
  SysFS BusID: 4:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:0d.0/host4/target4:0:0/4:0:0:0
  Hardware Class: disk
  Model: "ST3500630A"
  Device: "ST3500630A"
  Revision: "3.AA"
  Driver: "pata_amd", "sd"
  Device File: /dev/sdc
  Device Number: block 8:32-8:47
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #8 (IDE interface)

36: IDE 100.0: 10600 Disk
  [Created at block.243]
  UDI: /org/freedesktop/Hal/devices/storage_serial_SATA_ST3200822AS_5LJ1FC7X
  Unique ID: WZeP.pJDgRQBG5Z4
  Parent ID: vuMS.AKlBEx7WwV8
  SysFS ID: /class/block/sdb
  SysFS BusID: 1:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:0e.0/host1/target1:0:0/1:0:0:0
  Hardware Class: disk
  Model: "ST3200822AS"
  Device: "ST3200822AS"
  Revision: "3.01"
  Driver: "sata_nv", "sd"
  Driver Modules: "sata_nv"
  Device File: /dev/sdb
  Device Number: block 8:16-8:31
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #7 (IDE interface)

37: IDE 00.0: 10600 Disk
  [Created at block.243]
  UDI: /org/freedesktop/Hal/devices/storage_serial_SATA_SAMSUNG_HD501LJS0MUJ13P324408
  Unique ID: 3OOL.rUyjWzw3l_F
  Parent ID: vuMS.AKlBEx7WwV8
  SysFS ID: /class/block/sda
  SysFS BusID: 0:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:0e.0/host0/target0:0:0/0:0:0:0
  Hardware Class: disk
  Model: "SAMSUNG HD501LJ"
  Vendor: "SAMSUNG"
  Device: "HD501LJ"
  Revision: "CR10"
  Driver: "sata_nv", "sd"
  Driver Modules: "sata_nv"
  Device File: /dev/sda
  Device Number: block 8:0-8:15
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #7 (IDE interface)


```

---

### Post by schmidtbag on 2009-07-15
if you change the jumper settings you shouldn't have to worry about reinstalling.  i'm pretty sure the drive letters in linux work the same way as they do in windows, where they are labeled by whenever they were detected.  i would take out all drives that don't have an OS on it, see if that will improve speeds.  when that happens, you either have jumper settings wrong or theres an issue with your hard drive controller, but maybe what "mikewhatever" said is true too, i'm not sure

---

### Post by t4thfavor on 2009-07-15
The Nvidia Sata controller uses a ton of CPU to write to the disk, I have the same issue on my quad, though its hardly as noticable as it would be on a single or dual proc machine.

EVGA 790i mobo with 2xSeagate 500GB in mirror set.  FYI.

---

### Post by mikewhatever on 2009-07-15
> **schmidtbag said:**
> if you change the jumper settings you shouldn't have to worry about reinstalling.  i'm pretty sure the drive letters in linux work the same way as they do in windows, where they are labeled by whenever they were detected.  i would take out all drives that don't have an OS on it, see if that will improve speeds.  when that happens, you either have jumper settings wrong or theres an issue with your hard drive controller, but maybe what "mikewhatever" said is true too, i'm not sure

I think the OP only has SATA hard drives. Do they also have jumpers? Can you suggest specific jumper settings, it seems impractical modifying them at random.
I asked for the CPU specs thinking it might be a P4 or similar, but that core2duo should probably be more then enough for disk writing operations. I really don't know what's the problem.

---

### Post by schmidtbag on 2009-07-15
a p4 could still handle all of that, and to answer your question, sata drives do have jumper settings but like you said, its impractical.  there really is no need to use them at all, in fact i don't know why they're there.  but, daimaru says he has 3 SCSI hard drives, which do use jumper settings

---

### Post by 3rdalbum on 2009-07-16
I do actually have the same problem - I assumed it was par for the course. I've got a 3GHz Core 2 Duo and two SATA HDDs. I get the same problem on my Aspire One netbook.

---

### Post by t4thfavor on 2009-07-16
Jumpers on SATA drives are used to lock a sata 300 drive at sata 150 specs. The jumper should be off the drive in most cases to open up full speed.

I attribute this to the crappy sata drivers for the software based controller. I don't think there will be anything you can do about it. You will either get lucky, and not have a problem, or be unlucky, and have one. Best bet is to try reinstalling from scratch, and then updating immediatly, instead of upgrading from an older distro. Like I said, I have high CPU usage on my Quad when performing disk IO (mirror) but its hardly noticable, because of the power of the CPU.

---

### Post by schmidtbag on 2009-07-16
would perhaps a bios update work?

---

### Post by daimaru on 2009-07-16
ok thx for all the replies guys. Going to try reinstalling if nothing else works. but right now i am testing the 64bit version instead of 32 to see if that improves performance. too bad the download is extremely slow from virtualbox repo. 

will report back when i have it installed and try to create another partition.

---

### Post by Skyjumper Z on 2009-07-20
I think I have the same problem. Haven't researched it too much yet, but it sounds like this: [http://bugzilla.kernel.org/show_bug.cgi?id=12309](http://bugzilla.kernel.org/show_bug.cgi?id=12309)

---

### Post by schmidtbag on 2009-07-20
i actually completely forgot to mention - i have an asus motherboard that will not allow linux to be installed on ATA hard drives.  SATA works fine (i'm using this computer right now) but ATA will not do anything.  windows will install on ATA drives too.  to me, it really just seems like linux, or at least specific distros, will not cooperate with hard drives depending on what the chipsets are, and theres really nothing we can do about it

---

### Post by moster on 2009-07-20
Linux can  be installed on ATA but boot order must be different then :)

I suggest you boot from Ubuntu USB stick, then do your heavy coping. If there is no slowdown then you borked your installation. But if is slowdown even there visible, try to change your disk communication in BIOS. Turn on AHCI or similar if you have it. Ubuntu will use another driver for file transfer. 

If you have much memory you could also look into "swappiness" option. Search this forum for that.. But that swappiness is only little help, not much.

---

### Post by psypher on 2010-03-23
Hi All,

I have been experiencing the exact same issue on my laptop and desktop since I cannot even remember anymore. I thought also it's just par for the course and that is what linux does :(

The topic says this is solved, but it does not state what the solution is??

daimaru what did you do to solve?

Thanks

---

### Post by psypher on 2010-03-23
This is a kernel bug AHCI mode made no difference. More info check out this post: [http://ubuntuforums.org/showthread.php?p=9014788#post9014788]("http://ubuntuforums.org/showthread.php?p=9014788#post9014788http://ubuntuforums.org/showthread.php?p=9014788#post9014788")

---

### Post by Dr Tommo on 2012-02-23
The solution on this page seems to have worked for me:
[http://techtitbits.com/2010/04/get-rid-of-freeze-ups-during-disk-io-activity-in-ubuntu/](http://techtitbits.com/2010/04/get-rid-of-freeze-ups-during-disk-io-activity-in-ubuntu/)

---

### Post by dcstar on 2012-02-24
Setting up Control Groups works for me (I use the second option):

[http://www.serverwatch.com/tutorials/article.php/3921001/Setting-Up-Linux-Cgroups.htm](http://www.serverwatch.com/tutorials/article.php/3921001/Setting-Up-Linux-Cgroups.htm)
[http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html)

---

