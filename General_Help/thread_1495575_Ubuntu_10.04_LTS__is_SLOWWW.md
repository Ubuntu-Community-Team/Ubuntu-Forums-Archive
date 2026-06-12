---
title: "Ubuntu 10.04 LTS  is SLOWWW"
date: 2010-05-28
forum: General Help
---

### Post by winxpuser on 2010-05-28
Hello,

As my name suggest I have been a longtime windows user however I decided to try out ubuntu on my test machine that is running xp and I have to say that this thing is super slow. The bootup process is fine and once I login and such the desktop shows up ok but after that everything I do is slow. The mouse moves slowly the menus take 10 seconds or more to open after I click on them, applications take forever to load etc.. Did I mention that it's SLOOOW. 

Anyway I am not a novice to computers (just linux) and have a feeling this is a driver related issue except I have no idea where to find the driver(s) that will work for my setup which is as follows.

System Specs: 
=============
BIOS:
```
BIOS Version    P4M80P - 42302e31 Phoenix - AwardBIOS v6.00PG Phoenix - AwardBIOS v6.00PG
BIOS Date    02/22/06
```CPU:
```
Number of Logical Processors    2
Number of Physical Processors    1
CPU #1    Intel Pentium 4
CPU Name    Intel(R) Pentium(R) 4 CPU 3.00GHz
CPU Code Name    Prescott
Vendor    GenuineIntel
Number of Bits    32
Instruction Set    MMX, SSE, SSE2, SSE3
Platform Name    Socket 478 mPGA
Revision    C0
Technology    90 nm
Original Clock    3000 MHz
Original System Clock    200 MHz
Original Multiplier    15.0
CPU Clock    3000 MHz
System Clock    200.0 MHz
FSB    800.0 MHz
Number of Cores    1
Core #1
Speed    3000.1 MHz
Multiplier    15.0
Virtual Technology Supported    No
Hyper Threading Supported    Yes
Hyper Threading Enabled    Yes
Cache
L1 Data Cache    16 KBytes
L1 Trace Cache    12 Kµops
L2 Cache    1024 KBytes
```MEMORY:
```
DRAM Frequency    200.0 MHz
Memory Timings    3-3-3-8 (CL-RCD-RP-RAS)

Device Locator    Slot 1
Capacity    1024 MBytes
Memory Type    DDR (PC3200)
Speed    200 MHz
Supported Frequencies    133.3 MHz, 166.7 MHz, 200.0 MHz
Memory Timings    2-2-2-6-0 at 133.3 MHz, at 2.5 volts (CL-RCD-RP-RAS-RC)
Memory Timings    2-3-3-7-0 at 166.7 MHz, at 2.5 volts (CL-RCD-RP-RAS-RC)
Memory Timings    3-3-3-8-0 at 200.0 MHz, at 2.5 volts (CL-RCD-RP-RAS-RC)
Data Width    64 bits
EPP SPD Support    No
XMP SPD Support    No


Device Locator    Slot 2
Capacity    1024 MBytes
Memory Type    DDR (PC3200)
Speed    200 MHz
Supported Frequencies    133.3 MHz, 166.7 MHz, 200.0 MHz
Memory Timings    2-2-2-6-0 at 133.3 MHz, at 2.5 volts (CL-RCD-RP-RAS-RC)
Memory Timings    2-3-3-7-0 at 166.7 MHz, at 2.5 volts (CL-RCD-RP-RAS-RC)
Memory Timings    3-3-3-8-0 at 200.0 MHz, at 2.5 volts (CL-RCD-RP-RAS-RC)
Data Width    64 bits
EPP SPD Support    No
XMP SPD Support    No
```VIDEO:
```

Video Adapter    Radeon X1650 Series
Code Name    RV535
Video Processor    ATI Radeon Graphics Processor AGP (0x71C7)
Technology    80 nm
Adapter DAC Type    Internal DAC(400MHz)
PCI ID    0x1002 / 0x71C7 (ATI Technologies Inc / RADEON X1650 SERIES)
PCI sub ID    0x1787 / 0x3000 (Hightech Information System Ltd (Medion??))
Memory    512 MBytes
BIOS Date    10/08/08
PnP Device Id    PCI\VEN_1002&DEV_71C7&SUBSYS_30001787&REV_9E\4&8CA73A7&0&0008
Video Mode Description    1024 x 768 x 4294967296 colors
Driver Version    6.14.10.6764
Driver Date    2008-01-12 04:12:07
DirectX    DirectX 9.0
Driver Name    ati2dvag.dll
Driver Description    Radeon X1650 Series
Video Adapter    Radeon X1650 Series Secondary
Video Processor    ATI Radeon Graphics Processor AGP (0x71E7)
Adapter DAC Type    Internal DAC(400MHz)
PCI ID    0x1002 / 0x71E7 (ATI Technologies Inc / RADEON X1650 SERIES SECONDARY)
PCI sub ID    0x1787 / 0x3001 (Hightech Information System Ltd (Medion??))
Memory    512 MBytes
DirectX    DirectX 9.0
Driver Name    ati2dvag.dll
Driver Description    Radeon X1650 Series

```OS:
```
Windows XP SP2
```Anything else needed just ask I can supply an exhaustive list of my system and if it matters at all I used the wubi installer to install Ubuntu into my C:\ drive

Thanks,
Mike

---

### Post by winxpuser on 2010-05-28
Well as far as first impressions go I have to say the lack of response here is quite disappointing, I guess I will just have to uninstall ubuntu and find another distro that actually works.

---

### Post by cloyd on 2010-05-29
I hope I'm not too late, but I'd make one suggestion. 10.4 is the latest release. I'm using 9.10 on one machine, and 9.04 on another . . . they both run very well. I'll probably switch to 10.4, after several issues are worked out. In the meanwhile, the older versions are working very well. If you haven't tried them already, I'd suggest you do. Either one should work well, unless there is some hardware incompatibility. I can't compare to Windows 7, but for me, they run hands down better than XP or Vista.

---

### Post by quimkaos on 2010-05-29
well, you give us a lot of hardware specs but almost nothing about the system software...

is this going on since the 1st boot up?
have you tried to update the system?
are you using visual effects?
did you install any proprietary drivers (eg.: ati video driver)?
any info on how you did your HD partitions? (open an console window and write sudo fdisk -l)
did you try testing you memory by using memtest that is shipped with your ubuntu cd?

i have some slowdown problems in 10.04 too, but not like yours... after login my menus take about 5 secs to show up, but after that it works regularly... i have always about 10 apps open with no problems.

just one thing don't expect to change Operating System and not run in to trouble or issues that you don't know how to solve. I bet that the first time you used windows you had problems that you need to solve.

---

### Post by XubuRoxMySox on 2010-05-29
I found that [SIZE="6"][COLOR="Blue"]X[/COLOR][/SIZE][COLOR="Blue"]ubuntu[/COLOR] (Karmic and Lucid) run much faster on my old hand-me-down Dell than "vanilla" (Gnome) Ubuntu did. Alot of people talk about Xubuntu's "bloat," but I think their complaints have more to do with disk space than with performance.

Both _X_ubuntu and the new _[COLOR="Blue"]L[/COLOR]_[COLOR="Blue"]ubuntu[/COLOR] (using the ultralight LXDE environment) are definitely worth trying before you look too far for a distro unless you had unsolvable hardware issues when you tried Ubuntu.

Just a suggestion,
Robin

---

### Post by jerome1232 on 2010-05-29
Since you used wubi, if the file that contains the virtual file-system is fragmented heavily, then I could see that causing issues similar to what your describing.

I would personally use a real install (since wubi add's some performance drawbacks). You could try defraging your windows file-system and see if you see any improvement.

Another note, check if your ati card has it's video driver installed unfortunately I have no experience with ati, I only have nvidia cards so I can't help you much with that.

10.04 LTS runs fine on my system which is lower spec'd than yours.

---

### Post by winxpuser on 2010-06-07
Thanks for the replies. I have installed the 9.04 version (would have went for 9.10 but I heard there were problems with GRUB with that version so didn't want to risk it) and it seems to be working much better. I have some other issues but they are not related to this problem so I will create a new post for those. 

Thanks Again,
Mike.

---

### Post by afrodeity on 2010-06-07
I would recommend upgrading to Lucid for the speed factor alone. It is a lot faster than Karmic on the same hardware. Obviously with the speed focus, a lot of other issues come into play. I'm still not entirely happy with my bootup and plymouth, but have a reasonable working system after applying [fixes/workarounds for known issues]("http://www.ubuntugeek.com/known-ubuntu-10-04lucid-lynx-issuesbugs-with-workarounds.html"). 

Karmic should have been the LTS as far as I'm concerned, because it had less annoying bugs. I think the all the focus on the eye candy and rebranding for Lucid resulted in less time being spent on improving the undercarriage. But this is FOSS, you can always choose another distro.

---

