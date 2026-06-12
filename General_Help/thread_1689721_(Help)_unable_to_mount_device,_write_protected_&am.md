---
title: "(Help) unable to mount device, write protected &amp; read only"
date: 2011-02-17
forum: General Help
---

### Post by candrairawan on 2011-02-17
Dear all,
I used dual booting with Windows Xp and Ubuntu 10.04. 
Because errors, I reinstall Windows and then I could not enter GRUB, and Ubuntu partition disappear.
I tried to reinstall ubuntu using live CD but I could not detect last ubuntu partitions.  After I installed fresh Ubuntu on new partition, I got error message like this:

Unable to mount floppy0
Mount: block device /dev/fd0 is write protected, mounting read-only
Mount: could not determine the file system type, and none was specified

Could you help me to solve this, please?

Regards,

Candra

---

### Post by jerrrys on 2011-02-17
i have a floppy; don't use it, but i got it. if you need your floppy you can try here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Mount%3A+block+device+%2Fdev%2Ffd0+is+write+protected%2C+mounting+read-only&as_qdr=all&sa=Google+Search&lang=en#987](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Mount%3A+block+device+%2Fdev%2Ffd0+is+write+protected%2C+mounting+read-only&as_qdr=all&sa=Google+Search&lang=en#987)

---

### Post by candrairawan on 2011-02-18
Hello Jerrrys,

I do not have any floppy here. it is weird. And Gparted can not detect it.
I use Disk Management. It says:
Device     : /dev/fd0
Directory  : /media/floppy0
Filesystem: auto
It can not be mount and unmount either.

my harddisk lose about 5 Gb. It just gone.
Could anybody help me hoe to restore my harddisk, please?

Regards,

Candra

---

### Post by jerrrys on 2011-02-18
a floppy thats not there and 5G gone, your computer is possessed.

open a terminal and enter **lspci** and see what is plugged in  also

go to 'computer' and open properties and see if 5G is still missing.  different app will give different file space readings

what kind of computer is this ?

---

### Post by candrairawan on 2011-02-19
Hello Jerrrys,
Here is the response from lspci

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

I also attach some picture of the floppy partition.
It cann`t be mount and format either. 
I hope you can understand 
[IMG]file:///tmp/moz-screenshot.png[/IMG]
Regards,

Candra

---

### Post by jerrrys on 2011-02-19
you did not create or mount sda5 ?

---

### Post by candrairawan on 2011-02-20
Dear Jerrrys,

I create sda5 for /(root), as seen on gparted
regards,

Candra

---

### Post by Rhizoid on 2011-02-20
Disable floppy drive support in the bios setup.

---

### Post by candrairawan on 2011-02-20
@Rhizoid,
I have disabled floppy drive support in the bios setup but nothing happen
Regards,
Candra

---

