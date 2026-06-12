---
title: "(Ubuntu/XP dual-boot) XP removal how-to?"
date: 2010-05-04
forum: General Help
---

### Post by Happehwalrus on 2010-05-04
**Ubuntu NBR 10.04**
I wish to somehow backup my XP files and settings, delete XP, resize Ubuntu to use my whole hard drive, and then make an XP VirtualBox so I won't have to switch from Ubuntu to Windows all the time. I have my XP .iso needed to make a VirtualBox, and I use VirtualBox OSE. Could someone give me a step-by step tutorial on how to do this?

---

### Post by colorlessprism on 2010-05-04
[Disk2vhd]("http://technet.microsoft.com/en-us/sysinternals/ee656415.aspx") It will  show you various hard disks and partitions on your computer. Select the  one you would like turned into virtual hard disks, hit create and the  applications goes about doing its thing. The process could take really long so you might as well go out grab  something to eat/drink and come back &#8212; and if you are lucky, it would  have created the virtual hard disk. The time it requires would depend on  the size of the disk you are trying to turn into a virtual hard disk.  Generally be prepared to wait for quite a while. The tool works from within the operating system so you dont to boot from a CD. One thing  you will require is free hard disk space.
VirtualBox's standard is the Virtual Disk Image (VDI) format, VirtualBox  is also able to support []("http://www.virtuatopia.com/index.php/Understanding_and_Configuring_VirtualBox_Virtual_Hard_Disks#")VMDK (VMWARE) and Microsoft's VHD virtual hard disk formats. Virtual disk image  files in either of these third party formats may be added to the  VirtualBox media library using the: [I]
Virtual Media Manager[/I]  (accessed via the *File->Virtual Media Manager* menu option)

---

