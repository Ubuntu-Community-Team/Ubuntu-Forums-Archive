---
title: "Error -5 with loading module uvesafb..."
date: 2010-06-11
forum: General Help
---

### Post by BobSands on 2010-06-11
Hi There!,
Trying to solve the problem of slow startup i apply the workaround mentioned in this post:
[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)
(section Bootup/Plymouth)

and also i do this:
[http://n00bsonubuntu.com/content/how-fix-big-blurry-and-ugly-logo-startupshutdown-ubuntu-1004-lts-lucid-lynx](http://n00bsonubuntu.com/content/how-fix-big-blurry-and-ugly-logo-startupshutdown-ubuntu-1004-lts-lucid-lynx)

Apparently everything works fine, now i can see the splash startup/shutdown Ubuntu logo, but checking the system log i found this:

uvesafb: ATI Technologies Inc., P6  , 01.00, OEM: ATI MOBILITY RADEON, VBE v2.0
uvesafb: protected mode interface info at c000:5587
uvesafb: pmi: set display start = c00c561b, set palette = c00c5667
uvesafb: pmi: ports = 3010 3016 3054 3038 303c 305c 3000 3004 30b0 30b2 30b4 
uvesafb: no monitor limits have been set, default refresh rate will be used
uvesafb: scrolling: ywrap using protected mode interface, yres_virtual=2048
**uvesafb: probe of uvesafb.0 failed with error -5**

Can anyone please point me in the right direction to solve this?...

---

### Post by BobSands on 2010-06-16
... is anybody there?...

---

### Post by dino99 on 2010-06-16
This indicates that you are NOT using uvesafb.  Could you please provide the
output of `fbset -i` as well as the contents of /proc/iomem?

if you have added this (or some piece), remove that in red :
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset [COLOR="Red"]video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywra[/COLOR]p"


sudo update-pciids && update-usbids 
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by BobSands on 2010-06-16
Hi!
Thanks for the reply!. 

I know that the message indicate that the uvesafb is not working correctly, but once i made the modification to supposedly make it work, my ubuntu starts and shutdowns flawlessly...

Here the info that you ask for:
-----
fbset -i
-----
mode "1024x768-76"
    # D: 78.653 MHz, H: 59.949 kHz, V: 75.694 Hz
    geometry 1024 768 1024 768 32
    timings 12714 128 32 16 4 128 4
    rgba 8/16,8/8,8/0,0/0
endmode

Frame buffer device information:
    Name        : EFI VGA
    Address     : 0xe0000000
    Size        : 3145728
    Type        : PACKED PIXELS
    Visual      : TRUECOLOR
    XPanStep    : 0
    YPanStep    : 0
    YWrapStep   : 0
    LineLength  : 4096
    Accelerator : No
-----
/proc/iomem
-----
00000000-00001fff : System RAM
00002000-00005fff : reserved
00006000-0009efff : System RAM
0009f000-0009ffff : reserved
000a0000-000bffff : Video RAM area
000c0000-000cffff : Video ROM
000d0000-000d0fff : Adapter ROM
000d1000-000d1fff : Adapter ROM
000d2000-000d3fff : reserved
000dc000-000fffff : reserved
  000e0000-000effff : Extension ROM
  000f0000-000fffff : System ROM
00100000-7ff5ffff : System RAM
  00100000-00590662 : Kernel code
  00590663-007a2e47 : Kernel data
  0084c000-008d9e97 : Kernel bss
7ff60000-7ff77fff : ACPI Tables
7ff78000-7ff79fff : ACPI Non-volatile Storage
7ff7a000-7ff7ffff : RAM buffer
7ff80000-7fffffff : reserved
80000000-800003ff : 0000:00:1f.1
b0000000-b0000fff : 0000:02:00.0
  b0000000-b0000fff : yenta_socket
b1000000-b1000fff : 0000:02:00.1
  b1000000-b1000fff : yenta_socket
c0000000-c00003ff : 0000:00:1d.7
  c0000000-c00003ff : ehci_hcd
c0000800-c00008ff : 0000:00:1f.5
  c0000800-c00008ff : Intel 82801DB-ICH4
c0000c00-c0000dff : 0000:00:1f.5
  c0000c00-c0000dff : Intel 82801DB-ICH4
c0100000-c01fffff : PCI Bus 0000:01
  c0100000-c010ffff : 0000:01:00.0
  c0120000-c013ffff : 0000:01:00.0
c0200000-cfffffff : PCI Bus 0000:02
  c0200000-c0200fff : 0000:02:02.0
    c0200000-c0200fff : ipw2100
  c0201000-c0201fff : 0000:02:08.0
    c0201000-c0201fff : e100
  c0202000-c02027ff : 0000:02:00.2
    c0202000-c02027ff : ohci1394
  c4000000-c7ffffff : PCI CardBus 0000:03
  c8000000-cbffffff : PCI CardBus 0000:07
d0000000-dfffffff : 0000:00:00.0
e0000000-e7ffffff : PCI Bus 0000:01
  e0000000-e7ffffff : 0000:01:00.0
    e0000000-e02fffff : efifb
e8000000-efffffff : PCI Bus 0000:02
  e8000000-ebffffff : PCI CardBus 0000:03
  ec000000-efffffff : PCI CardBus 0000:07
ff800000-ffffffff : reserved
-----

For the commands that you suggest, i ran the update-usbids and the update-pciids, and i get this error:
-----
sudo update-pciids && update-usbids 
-----
Downloaded daily snapshot dated     2010-06-12 03:15:02
touch: cannot touch `/var/lib/usbutils/usb.ids': Permission denied
/var/lib/usbutils/usb.ids is read-only, exiting.
-----

But i ran the commands separated and not in one line and works fine.

By the way, maybe this could be helpful or not, but i didn't mention that i'm using a Thinkpad X31, with a ATI Radeon Mobile M6 LY,

Again, thanks for the answer, i hope we can solve this issue!.

---

### Post by BobSands on 2010-06-21
Hello...

---

### Post by BobSands on 2010-06-25
Heeeelloooo...

---

