---
title: "Performance on new Ubuntu Install"
date: 2012-08-03
forum: General Help
---

### Post by stuartwood89 on 2012-08-03
Hey Guys.

I have just installed the latest Ubuntu release (12.04 LTS) onto my new (well, secondhand) netbook.  The machine was originally running Windows 7 Starter, though it is designed to run Windows XP.  As soon as I got the netbook home, I installed this release from a USB stick.

After installation I noticed that the system was a bit... well... laggy.  It was no different in Windows 7, so I don't believe that this is an Ubuntu issue so much.  What I would like to know is whether there is anything I can do to speed this thing up.  Upon installation I was presented with Unity, which I'm not totally sold on, so I installed GNOME 3 using the software centre (the link from the GNOME site opens this up).  I actually like GNOME 3 a lot so far.  Any chance that both GNOME 3 and Unity being on the machine could be slowing things down?

The netbook in question is a Dell Inspiron Mini 9.  It has a dual core Intel Atom CPU running at 1.6GHz, 1GB DDR2 memory and a 16GB mini PCIe SSD.  I have included more detailed info below.

Having checked the resource usage, I find that it's not running too bad.  It using around 20% CPU and 30% memory when browsing the web.  My only conclusion is that it might be disk performance.  The netbook does take a little while to boot, rebooting is actually pretty fast however.

My understanding is that SSDs need TRIM to prevent performance degradation, and as the machine is second hand, lack of TRIM may have caused the slowness.  What I need to know is the following:

- Can I activate TRIM for this SSD?
- Is it likely to reverse any degradation that has already occurred?
- Can anyone recommend a reliable way of benchmarking the drive at all? 

The SSD is a 16GB Super Talent FEM16GHDL if that helps.  I can't seem to find any confirmation as to whether or not this will support TRIM.  I hope someone can help.

I would really appreciate any replies you can offer.

Many thanks :D


**KERNEL INFO**
```
stuart@thenetbook:~$ uname -r
3.2.0-27-generic-pae

```

**CPU INFO**
```
stuart@thenetbook:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
stepping	: 2
microcode	: 0x208
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm dts
bogomips	: 3191.88
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
stepping	: 2
microcode	: 0x208
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm dts
bogomips	: 3191.93
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:


```

**MEMORY INFO**
```
stuart@thenetbook:~$ sudo dmidecode --type memory
# dmidecode 2.11
SMBIOS 2.5 present.

Handle 0x0010, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 1 GB
	Error Information Handle: Not Provided
	Number Of Devices: 1

Handle 0x0011, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0010
	Error Information Handle: No Error
	Total Width: 32 bits
	Data Width: 32 bits
	Size: 1024 MB
	Form Factor: SODIMM
	Set: 1
	Locator: M1
	Bank Locator: Bank 0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 533 MHz
	Manufacturer:                 
	Serial Number:         
	Asset Tag:       
	Part Number:                   


```

**DISK INFO**
```
stuart@thenetbook:~$ sudo hdparm -I /dev/sda

/dev/sda:

CompactFlash ATA device
	Model Number:       STT_FEM16GHDL                           
	Serial Number:      P649047-AQX3-909A008
	Firmware Revision:  Ver2.M1A
Standards:
	Supported: 5 4 
	Likely used: 6
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   30146256
	LBA    user addressable sectors:   30146256
	Logical/Physical Sector size:           512 bytes
	device size with M = 1024*1024:       14719 MBytes
	device size with M = 1000*1000:       15434 MBytes (15 GB)
	cache/buffer size  = 1 KBytes (type=DualPort)
Capabilities:
	LBA, IORDY(cannot be disabled)
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 1	Current = 1
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	   *	Power Management feature set
	    	Write cache
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	CFA feature set
	   *	Mandatory FLUSH_CACHE
	   *	CFA advanced modes: pio5 pio6 mdma3 mdma4 
Integrity word not set (found 0x0000, expected 0xd2a5)

```

**OTHER INFO**
```
stuart@thenetbook:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
02:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
02:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

---

### Post by GreatDanton on 2012-08-03
1. I think this will help you: [http://ubuntuforums.org/showthread.php?t=1974320](http://ubuntuforums.org/showthread.php?t=1974320)

2. If I were you I would install either Lubuntu or Xubuntu. Ubuntu will run on 1Gb of ram but I think you would like to have responsive system &#8594; Lubuntu or Xubuntu is your choice.

Hope this helps.

---

### Post by ajgreeny on 2012-08-03
> **GreatDanton said:**
> If I were you I would install either Lubuntu or Xubuntu. Ubuntu will run on 1Gb of ram but I think you would like to have responsive system &#8594; Lubuntu or Xubuntu is your choice.

Hope this helps.
I would personally recommend Lubuntu.

It has got better and better over the past couple of years and now stands tall amongst the ubuntu family.  In comparison with Ubuntu using unity it is blindingly fast.  Its only slight downside is the need to manage some configuration by editing text configuration files, and the fact that the recent 12.04 version is not an LTS like all the others of the family.

Xubuntu is also a great choice but in my experience not as fast as Lubuntu.  It does, however, have a lot more configuration ability using GUI dialogs than Lubuntu.

Try them both and see what you prefer.  If you installed **lubuntu-desktop** and/or **xubuntu-desktop** to your current ubuntu you could use whichever you prefer after trying them out properly, and then remove whichever DE you don't want with the info at [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) in the "Playing around" section.

---

### Post by stuartwood89 on 2012-08-04
Hey, thanks for the replies :)

I have followed the info in the link, and all seemed to go well.  I also tried running the trim command, but I got the following:

```
stuart@thenetbook:~$ sudo fstrim -v / 
fstrim: /: FITRIM ioctl failed: Operation not supported
stuart@thenetbook:~$ 

```

Does this mean I cannot use trim on my SSD?

EDIT::

I've included my fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=82f094d2-d28a-4759-8127-644494bfe0b9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8aa6fda6-3b0b-46b6-93a3-c889c7644149 none            swap    sw              0       0
UUID=82f094d2-d28a-4759-8127-644494bfe0b9 /               ext4 noatime,discard,errors=remount-ro 0       1

```

---

### Post by Statia on 2012-08-04
Yes, adding discard to the options in fstab should do the trick.
Also make sure in the BIOS AHCI mode is enabled for your harddisk, not IDE.
I found this a valuable resource when setting up my SSD:

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

FWIW: I have a netbook with comparable specs, 1.6Ghz CPU, 1 GB RAM, no SSD but regular HDD and Unity is indeed slow, Gnome sort of acceptable. However, a lighter desktop environment might make working on it nicer. Xfce4 could be nice, or an old favourite: Windowmaker. 

Good luck!

---

### Post by Statia on 2012-08-04
And to test whether TRIM is working:

[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2]("http://http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2")

---

### Post by stuartwood89 on 2012-08-04
Thanks for the link.  It looks like the TRIM isn't working as it should be.  Deleted the test file and checked the sectors again, no change.  I have emailed Super Talent, asking them directly whether or not the drive supports TRIM.  I've yet to hear back from them.

Sadly due to the size of the netbook, I am restricted to what SSD I can replace it with which might have that support.

---

### Post by stuartwood89 on 2012-08-05
Still haven't heard anything from Super Talent, but also found out that even if the SSD does support TRIM, the limitation of the netbook itself would prevent me from utilising it.  I cannot enable AHCI mode in the BIOS as it's not there.  Looks like it's stuck on IDE mode.  

I've been trying to find a method of manually trimming the SSD, and so far I've found that there is a bash script included with hdparm, which should help.  The script is called 'wiper.sh', and is located in /usr/share/doc/hdparm/contrib/wiper.sh.gz.  The script is zipped up, so tried unzipping it with gunzip wiper.sh.gz, and the seems to have worked.  When I try to load the script, I get the following:

```

stuart@thenetbook:~$ cd /usr/share/doc/hdparm/contrib/
stuart@thenetbook:/usr/share/doc/hdparm/contrib$ sudo bash wiper.sh /dev/sda
wiper.sh: Linux SATA SSD TRIM utility, version 3.3, by Mark Lord.
/usr/bin/gawk: needed but not found, aborting.

```

Again, not entirely sure if this is a hardware limitation (what with it not being a SATA drive).

---

### Post by black veils on 2012-08-05
i would install Xubuntu and do this:


open the Terminal and copy-paste:
```
gksudo gedit /etc/sysctl.conf
```
press Enter key

Scroll to the bottom of the text file and add your swappiness parameter to override the default, so copy/paste the following lines:
```
#
# Decrease swap usage to a workable level
vm.swappiness=10
```
Close the text file and reboot your computer.

After the reboot, check the new swappiness value.
open the Terminal and copy-paste:
```
cat /proc/sys/vm/swappiness
```
press Enter key

Now it should be the chosen new value.

---

### Post by HermanAB on 2012-08-05
+2 for Xubuntu or Lubuntu and +1 for Kubuntu.

Unity and Gnome3 are both really crummy by comparison and worse than useless on a netbook.

---

