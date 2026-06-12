---
title: "Ubuntu stability"
date: 2010-06-06
forum: General Help
---

### Post by tejashs on 2010-06-06
Is ubuntu really as stable as it claims to be?
I recently tried(4/6/2010) to updated lucid lynx from update manager it installed about 100 mb of files on reboot the graphical interface was gone and a command line interface ( like dos ) came up which said something like 
ubuntu tty login
username

As i dont know even abcd's of linux commands 
i am stuck there
i have tried fail safe graphics mode and dpkg in recovery mode to no avail

The installation is in win XP using wubi

my system is 



-----------------------------------------------------------------------------------------------------

>>Center Processor      

               CPU Name      AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
               Code Name      Model 11, Stepping 2
               Manufacturer      AuthenticAMD
               Current Clock Speed      2712Mhz
               Max Clock Speed      2712Mhz
               Voltage      1.5V
               External Clock      200Mhz
               Serial Number      178BFBFF00060FB2
               CPU ID      x86 Family 15 Model 107 Stepping 2
               Socket Designation      AM2
               L1-Cache      256KB
               L2-Cache      1024KB
               L3-Cache      0KB

>>Motherboard      

               Model      M2N68-AM SE2
               Manufacturer      ASUSTeK Computer INC.
               Serial Number      MS1C92BJ1L00646
               BIOS Name      BIOS Date: 01/16/09 23:08:43 Ver: 08.00.14
               BIOS Vendor      American Megatrends Inc.
               SMBIOS Version      0212   
               BIOS Date      16-Jan-09
>>BIOS Features      

               ISA is supported      Yes
               PCI is supported      Yes
               Plug and Play is supported      Yes
               APM is supported      Yes
               BIOS is Upgradable (Flash)      Yes
               BIOS shadowing is allowed      Yes
               ESCD support is available      Yes
               Boot from CD is supported      Yes
               Selectable Boot is supported      Yes
               BIOS ROM is socketed      Yes
               EDD (Enhanced Disk Drive) Specification is supported      Yes
               Int 13h - 5.25 /1.2MB Floppy Services are supported      Yes
               Int 13h - 3.5 / 720 KB Floppy Services are supported      Yes
               Int 13h - 3.5 / 2.88 MB Floppy Services are supported      Yes
               Int 5h, Print Screen Service is supported      Yes
               Int 9h, 8042 Keyboard services are supported      Yes
               Int 14h, Serial Services are supported      Yes
               Int 17h, printer services are supported      Yes
               Int 10h, CGA/Mono Video Services are supported      Yes
               ACPI supported      Yes
               USB Legacy is supported      Yes
               LS-120 boot is supported      Yes
               ATAPI ZIP Drive boot is supported      Yes

>>Memory Resource      

               Total Memory      1919 MB
               Used Memory      637 MB
               Free Memory      1281 MB
               Memory Usage      33%

>>Physical Memory      

               Memory Bank      BANK0
               Description      Physical Memory 0
               Device Location      DIMM0
               Capacity      1024 MB
               Speed      667Mhz
               Manufacturer      NULL
               Data Width      64bit
               Memory Type      Unknown
               Form Factor      DIMM

>>Physical Memory      

               Memory Bank      BANK1
               Description      Physical Memory 1
               Device Location      DIMM1
               Capacity      1024 MB
               Speed      667Mhz
               Manufacturer      NULL
               Data Width      64bit
               Memory Type      Unknown
               Form Factor      DIMM

>>Disk drive      

               Name      ST316081 3AS SCSI Disk Device
               Media Type      Fixed    hard disk media
               Capacity      160GB
               Interface Type      IDE
               Partitions      5
               Total Cylinders      19457
               Total Heads      255
               Total Sectors      312576705
               Total Tracks      4961535
               Tracks Per Cylinder      255
               Sectors Per Track      512
               Bytes Per Sector      63
               S.M.A.R.T Support      Yes
               Current Temperature      34C (93.2F)


>>IDE Controller 
     
               Name      Standard Dual Channel PCI IDE Controller
               Manufacturer      (Standard IDE ATA/ATAPI controllers)
               Status      OK

>>IDE Controller 
     
               Name      Primary IDE Channel
               Manufacturer      (Standard IDE ATA/ATAPI controllers)
               Status      OK

>>IDE Controller 
     
               Name      Secondary IDE Channel
               Manufacturer      (Standard IDE ATA/ATAPI controllers)
               Status      OK

>>IDE Controller  
    
               Name      NVIDIA nForce Serial ATA Controller
               Manufacturer      NVIDIA Corporation
               Status      OK


>>Video Adapter  
    
               Name      NVIDIA GeForce 7025 / NVIDIA nForce 630a
               Video Processor      GeForce 7025 / NVIDIA nForce 630a
               Manufacturer      NVIDIA
               Video Architecture      VGA
               DAC Type      Integrated RAMDAC
               Memory Size      512MB
               Memory Type      Unknown
               Video Mode      1152 x 864 x 4294967296 colors
               Current Refresh Rate      60Hz
               Driver Version      6.14.11.8160
               Driver Date      21-Jan-09 04:08:00 PM

>>Monitor      

               Name      Plug and Play Monitor
               Screen Height      864
               Screen Width      1152
               Status      OK

>>Local Area Connection 2      

               Product Name      NVIDIA nForce 10/100 Mbps Ethernet 
               Driver File      NVENETFD
               Manufacturer      NVIDIA
               MAC Address      00:24:8C:39:82:70

>>Sound Device    
  
               Name      Realtek High Definition Audio
               Manufacturer      Realtek
               Status      OK

---

### Post by lavinog on 2010-06-07
Wubi installs are not as stable/reliable as a regular install.
This is because a failure with the ntfs partition would cause ubuntu to fail.

Many installation issues are hardware related.  Many times it is due to a faulty cd drive.  The drive might seem to work just fine with regular cds, but the ubuntu installation disks are so tightly packed, cd error correction is likely to fail.

---

### Post by tejashs on 2010-06-07
i first downloaded wubi.exe then installed from internet directly and not by a disk.

---

### Post by an0dos on 2010-06-07
What happens if you log in and type "startx"

---

### Post by sites on 2010-06-07
> **tejashs said:**
> Is ubuntu really as stable as it claims to be?

Yes, it is when you install it properly.  Wubi is for trying Ubuntu.  It's not the official distribution.

---

### Post by 4Orbs on 2010-06-07
I can offer a suggestion based upon my own (non-wubi) experience with Lucid. Before booting into Ubuntu again, go into Windows and change the screen resolution to 1280x1024 or 1024x768 (whichever one is the native res for your monitor). Then reboot and try Ubuntu again. My nvidia card seems to only deal well with the native resolution for my monitor. After I get Ubuntu working with the native res, I always need to manually edit the xorg.conf file before I can get 1152x864 working correctly. This may not solve your problem... just a long shot.

---

### Post by tejashs on 2010-06-10
> **an0dos said:**
> What happens if you log in and type "startx"

startx command seems to work but i have noticed that sometimes it directly comes to graphical mode without startx command.

will fragmentation in the drive where i install ubuntu matter( about 60% fragmentation) i am unable to defragment the 10 Gb file in ubuntu folder.

do i need to take any precautions while updating ubuntu from update manager?

---

### Post by tejashs on 2010-06-10
> **4Orbs said:**
> I can offer a suggestion based upon my own (non-wubi) experience with Lucid. Before booting into Ubuntu again, go into Windows and change the screen resolution to 1280x1024 or 1024x768 (whichever one is the native res for your monitor). Then reboot and try Ubuntu again. My nvidia card seems to only deal well with the native resolution for my monitor. After I get Ubuntu working with the native res, I always need to manually edit the xorg.conf file before I can get 1152x864 working correctly. This may not solve your problem... just a long shot.



resolution is not a problem although i had some problems this worked for me

[http://ubuntuforums.org/showpost.php?p=8924307&postcount=23](http://ubuntuforums.org/showpost.php?p=8924307&postcount=23)

---

### Post by lavinog on 2010-06-10
> **tejashs said:**
> startx command seems to work but i have noticed that sometimes it directly comes to graphical mode without startx command.

will fragmentation in the drive where i install ubuntu matter( about 60% fragmentation) i am unable to defragment the 10 Gb file in ubuntu folder.

do i need to take any precautions while updating ubuntu from update manager?

Fragmentation shouldn't cause any issues except speed.

---

### Post by tejashs on 2010-06-10
or something like this mght be the issue???


[http://ubuntuforums.org/showpost.php?p=8919584&postcount=2](http://ubuntuforums.org/showpost.php?p=8919584&postcount=2)

---

### Post by tejashs on 2010-06-22
Using startx i am only able to login into UBUNTU. I am unable to log in into KUBUNTU

---

