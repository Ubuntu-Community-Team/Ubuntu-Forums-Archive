---
title: "Touchscreen usb - drivers"
date: 2010-02-28
forum: General Help
---

### Post by caslor on 2010-02-28
Hi to all friends here...

i setup xbuntu 9.10  for my car-pc

In this system i have a touchscreen monitor with usb connection...


------------------------------------------------------------------------------------------------------------------------------------------------------

the touchkit company  gives these drivers for ubuntu  

[http://www.touchkit.com/drivers.htm](http://www.touchkit.com/drivers.htm)
the instructions are here  but the only the do to me is to confuse me  : [http://www.touchkit.com/proi/drive/Installation%20Note.pdf](http://www.touchkit.com/proi/drive/Installation%20Note.pdf)

here is a page with newer drivers  : [http://touchkit.com/LinuxDriver.htm](http://touchkit.com/LinuxDriver.htm)


i follow the instructions in the begging of this page and i found out that i have  :

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux xbeetle-caslor 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=87c019e1-3dd7-4edd-8c9f-cb5436f295fb ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.


```

&#922;&#945;&#953; 

```
2.6.31-19-generic
```


so i download the         Kernel 2.6.x with xorg 1.4.0.90    edition ...  

1) should i choose to download an other one ??




i follow the instructions inside the tar file for  drivers installation and i get this message

> (I) found a non-HID  compliant touch controller
(E) No x configuration file found


in the file with instructions says : 
> 
(I) For details, see the document “How to build module.pdf”.
Note that the user needs to build the TouchKit kernel module “tkusb” for touch controller if
the inbuilt kernel module “usbtouchscreen” or “touchkitusb” does NOT exist.

and in the file for making a  module  says :
> 
1.Please make sure some packages are installed before you want to build the
kernel module “tkusb.ko”, such as development library and kernel-source.
Note: The kernel-source version must be the same as your running kernel.
2. Rebuild the kernel module. It is needed for USB TocuhScreen controller.
Please follow steps below to build the kernel module “tkusb.ko”.
Note: This kernel module of ko format is used for kernel 2.6.x only.


With the help of a friend from greek community i found out tha should i download the   ''build-essential'' 

so i did that..  everything ok with that



so i went to the file where is the  ''make file''  and when i use the command  ''Make''  i get this message :

```
ake -C /lib/modules/2.6.31-19-generic/build SUBDIRS=/home/xbeetle/Downloads/TouchKit_x14/TouchKit_x14/USBSrc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
  CC [M]  /home/xbeetle/Downloads/TouchKit_x14/TouchKit_x14/USBSrc/tkusb.o
In file included from /home/xbeetle/Downloads/TouchKit_x14/TouchKit_x14/USBSrc/tkusb.c:15:
/home/xbeetle/Downloads/TouchKit_x14/TouchKit_x14/USBSrc/tkusb.h:25:27: error: asm/semaphore.h: No such file or directory
/home/xbeetle/Downloads/TouchKit_x14/TouchKit_x14/USBSrc/tkusb.c: In function ‘DoSendData’:
/home/xbeetle/Downloads/TouchKit_x14/TouchKit_x14/USBSrc/tkusb.c:47: warning: passing argument 7 of ‘usb_fill_control_urb’ from incompatible pointer type
include/linux/usb.h:1239: note: expected ‘usb_complete_t’ but argument is of type ‘void (*)(struct urb *, struct pt_regs *)’
/home/xbeetle/Downloads/TouchKit_x14/TouchKit_x14/USBSrc/tkusb.c: In function ‘irq_tscreen’:
/home/xbeetle/Downloads/TouchKit_x14/TouchKit_x14/USBSrc/tkusb.c:146: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
include/linux/usb.h:1304: note: expected ‘usb_complete_t’ but argument is of type ‘void (*)(struct urb *, struct pt_regs *)’
/home/xbeetle/Downloads/TouchKit_x14/TouchKit_x14/USBSrc/tkusb.c: In function ‘lauch_int_read’:
/home/xbeetle/Downloads/TouchKit_x14/TouchKit_x14/USBSrc/tkusb.c:180: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
include/linux/usb.h:1304: note: expected ‘usb_complete_t’ but argument is of type ‘void (*)(struct urb *, struct pt_regs *)’
make[2]: *** [/home/xbeetle/Downloads/TouchKit_x14/TouchKit_x14/USBSrc/tkusb.o] Error 1
make[1]: *** [_module_/home/xbeetle/Downloads/TouchKit_x14/TouchKit_x14/USBSrc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'
make: *** [all] Error 2
```

The same and with   ''make install''  command




when we download the tar file for the drivers and untar it we get a folder with the name  touchkit_x14 :


[img]http://i30.photobucket.com/albums/c316/caslor_1978/cabrio/t1.jpg[/img]




 inside has these :

[img]http://i30.photobucket.com/albums/c316/caslor_1978/cabrio/t2.jpg[/img]



if we untar the other tar file we will get these :

[img]http://i30.photobucket.com/albums/c316/caslor_1978/cabrio/t3.jpg[/img]




in the new folder inside has :

[img]http://i30.photobucket.com/albums/c316/caslor_1978/cabrio/t4.jpg[/img]


in  ''guide''   folder has the  3  pdf  files





in folder ''TKcal''  has :

[img]http://i30.photobucket.com/albums/c316/caslor_1978/cabrio/t5.jpg[/img] 





folder  ''USBSrc'' has :

[img]http://i30.photobucket.com/albums/c316/caslor_1978/cabrio/t6.jpg[/img]




and last in folder  ''include''  has  :

[img]http://i30.photobucket.com/albums/c316/caslor_1978/cabrio/t7.jpg[/img]


any suggestions of what steps should i make in order to setup the drivers right ??

thanks

---

### Post by caslor on 2010-03-01
anyone??   (i dont want to install windows only because is simply to install monitor drivers :( :( )

---

### Post by naugtur on 2010-03-11
Same problem here. But I don't build a car system, but prepare a set of touch screens for public services in shops for a company. 
They already had it running on windows, and we persuaded them to try linux. It'd be nice if it could run.

In my case the main "make now" throws XFree86-devel required. And i couldn't find that in repos

---

