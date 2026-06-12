---
title: "Webcam not working in 10.04 LTS - strange behaviour"
date: 2010-07-29
forum: General Help
---

### Post by titomax82 on 2010-07-29
Hi guys, I'm completely new to linux environment.

I installed Ubuntu 10.04 LTS one week ago without any problems on my Packard Bell EasyNote MX67-P-023 notebook.

Everything works fine except my webcam "USB 2.0 Camera"

lsusb: Bus 001 Device 004: ID 0402:5602 ALi Corp. Video Camera Controller

In programs like aMsn, Emesene, or Cheese it's recognized as "USB 2.0 Camera"

For example(I'm translating menus from italian) in aMSN->preferences->Other->Audio Video:
- select device box: "v4l2: USB 2.0 Camera"
- select channel box:" ALi m5602"
- and in the video box where image should appear: "unable capture from device"
In the other programs it shows a completely blank screen, or sometimes a blank screen with some strange uncomprensible white-grey stripes

What's the matter? What do I need to make it work? Please help me step-by-step...but very deeply step by step :) ... I'm so noob :(

---

### Post by dino99 on 2010-07-29
some links: 

[http://www.google.com/search?as_q=webcam%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.com/search?as_q=webcam%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by titomax82 on 2010-07-29
I've searched so many guides in internet....but no one is specific for 10.04... or if it deals with it... has some broken packages or link....that's why i asked a step by step assistance here

---

### Post by titomax82 on 2010-07-29
i'm trying lots of guides sine 8 hours.....nothing works...please help

---

### Post by no2498 on 2010-07-29
look in add remove, program
see if gstreamer good,bad,ugly,and 10 is installed


gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

---

### Post by titomax82 on 2010-07-30
I can't find "add remove program" to see if gstreamer good,bad,ugly,and 10 is installed... however in gstreamer-properties:

1) Plugin: Video for Linux 2 (v4l2)
    Device: USB 2.0 Camera
    Test Result: blank screen with artifacts

2) Plugin: Video for Linux (v4l)
    Device: """i can't select nothing, tab button it's grey""    Maybe the problem is here?

---

### Post by no2498 on 2010-07-30
click applications very bottom of the list is add/remove

also look in sound & video for cheese webcam booth
try the cam in cheese after we get the cam up in gstreamer-properties

---

### Post by titomax82 on 2010-07-30
gstreamer packages are all ok... I tried all your suggestions...but nothing changed and if i try to use cheese after having get up the webcam in gstreamer-properties, cheese close itself....maybe because webcam can't be accessed by 2 apps at the same time.

Talking about gstreamer-properties only:
When I select v4l2 (video for linux 2), I can select the webcam to test it (even if it gives me that corrupted screen); instead when I select the "old first version" v4l (video for linux) I cannot select the device in the box (greyd).... makes me think I'm unable to test the old v4l mode...
I think this could be the right solution because, searching in internet i found that some  ubuntu older versions users, like 8 and 9, are able to use this kind of webcam, maybe just because that old ubuntu version have v4l and not vfl2 like 10.04

Can this thinking be right? If yes...how to I enable the old vfl?

---

### Post by titomax82 on 2010-07-31
Hi guys, I'm completely new to linux environment.

I installed Ubuntu 10.04 LTS one week ago without any problems on my Packard Bell EasyNote MX67-P-023 notebook.

Everything works fine except my webcam "USB 2.0 Camera"

lsusb: Bus 001 Device 004: ID 0402:5602 ALi Corp. Video Camera Controller

In programs like aMsn, Emesene, or Cheese it's recognized as "USB 2.0 Camera"

For example(I'm translating menus from italian) in aMSN->preferences->Other->Audio Video:
- select device box: "v4l2: USB 2.0 Camera"
- select channel box:" ALi m5602"
- and in the video box where image should appear: "unable capture from device"
In the other programs it shows a completely blank screen, or sometimes a  blank screen with some strange uncomprensible white-grey stripes

What's the matter? What do I need to make it work? Please help me step-by-step...but very deeply step by step :smile: ... I'm so noob :sad:

---

### Post by no2498 on 2010-07-31
this come from a skype post i did not save it sory
you may need to do a make file before it works

open a terminal type/copy paste


LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 

try the cam in cheese

hope that helps

---

### Post by no2498 on 2010-07-31
try these

open a terminal put this in it


LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese


sounds like this is not loaded/installed LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so

---

### Post by titomax82 on 2010-08-01
already tried...nothing change

---

### Post by titomax82 on 2010-08-01
already tried...nothing change

---

### Post by Iowan on 2010-08-01
Threads merged.
If you decide you'd rather have it in Multimedia & Video, use the "Report abuse" button to have it moved.

---

### Post by titomax82 on 2010-08-01
you're right... i will remove the other

---

### Post by titomax82 on 2010-08-04
i tried all the guides in the web....still no result :(

---

### Post by titomax82 on 2010-08-05
tries go on.... latest versions of: Slax, Slax Remix, Knoppix, DSL, Puppy, Mint, Mandriva, openSUSE..... always the same result....

old ubuntu users (8.x and 9.x) managed to make this webcam work...but no notice on 10.04... so I think it's a kernel problem.... a problem of the newest version...am I right?

another thought: I installed ubuntu 10.04 lts form windows...so I don't have a dedicated partition for ubuntu....but it's installed in a folder of the vista's partition with few files in it that ubuntu, when boots, sees as a normal linux partition.... can these problems be referred to this kind of installation or is a completely silly thought?

---

### Post by utilitytrack on 2010-08-07
to **titomax82**

Hello again :) Troubles with camera it's not my specialisation :) , but I'm try to help you anyway.

> Slax, Slax Remix, Knoppix, DSL, Puppy, Mint, Mandriva, openSUSE..... always the same result....


Do you wish say that you tried install all of these systems, and no one can't get working camera? Yes?

>  a problem of the newest version...am I right? ...so I think it's a kernel problem

I will watch.

> can these problems be referred to this kind of installation or is a completely silly thought?

Generally no, but still you understand that when Linux have dedicated partition it's more good.

---

### Post by titomax82 on 2010-08-07
yes...I tried them all (2 entire days...i'm mad :) )

---

### Post by utilitytrack on 2010-08-07
give here this info

```
$ uname -r
$ lspci -nn
$ dmesg | egrep -i 'cam|video'
# modprobe --list | grep -i cam
# lsmod | egrep 'cam|video'
$ ls -l /dev/video*
$ grep -e video /etc/group

```

and wich program you tried use for make a videorecord.

---

### Post by utilitytrack on 2010-08-07
Also likely do you use one display (i.e. built-in laptop display) and never use auxilary display (connected to VGA port), yes? I'm right?

PS
Please answer on **all** my questions exactly.

---

### Post by titomax82 on 2010-08-07
uname -r:
2.6.32-24-generic

lspci -nn:
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G72M [GeForce Go 7400] [10de:01d8] (rev a1)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
06:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
06:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
06:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)
06:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
06:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
06:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

dmesg | egrep -i 'cam|video':
[    0.000000]   AMD AuthenticAMD
[    0.269757] pci 0000:01:00.0: Boot video device
[   22.776626] asus_laptop: Brightness ignored, must be controlled by ACPI video driver
[   23.741381] Linux video capture interface: v2.00
[   23.764116] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:15/LNXVIDEO:00/input/input9
[   23.764178] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)

dmesg | egrep -i 'cam|video':
[    0.000000]   AMD AuthenticAMD
[    0.269757] pci 0000:01:00.0: Boot video device
[   22.776626] asus_laptop: Brightness ignored, must be controlled by ACPI video driver
[   23.741381] Linux video capture interface: v2.00
[   23.764116] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:15/LNXVIDEO:00/input/input9
[   23.764178] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
gtm@ubuntu:~$ modprobe --list | grep -i cam
kernel/crypto/camellia.ko
kernel/drivers/media/video/c-qcam.ko
kernel/drivers/media/video/bw-qcam.ko
kernel/drivers/media/video/ovcamchip/ovcamchip.ko
kernel/drivers/media/video/stkwebcam.ko
kernel/drivers/media/video/usbvideo/ibmcam.ko
kernel/drivers/media/video/usbvideo/ultracam.ko
kernel/drivers/media/video/usbvideo/vicam.ko
kernel/drivers/media/video/usbvideo/quickcam_messenger.ko
kernel/drivers/media/video/soc_camera.ko
kernel/drivers/media/video/soc_camera_platform.ko

modprobe --list | grep -i cam:
kernel/crypto/camellia.ko
kernel/drivers/media/video/c-qcam.ko
kernel/drivers/media/video/bw-qcam.ko
kernel/drivers/media/video/ovcamchip/ovcamchip.ko
kernel/drivers/media/video/stkwebcam.ko
kernel/drivers/media/video/usbvideo/ibmcam.ko
kernel/drivers/media/video/usbvideo/ultracam.ko
kernel/drivers/media/video/usbvideo/vicam.ko
kernel/drivers/media/video/usbvideo/quickcam_messenger.ko
kernel/drivers/media/video/soc_camera.ko
kernel/drivers/media/video/soc_camera_platform.ko
gtm@ubuntu:~$ lsmod | egrep 'cam|video'
video                  17375  0 
output                  1871  1 video
videodev               34361  1 gspca_main
v4l1_compat            13251  1 videodev

ls -l /dev/video*:
crw-rw----+ 1 root video 81, 0 2010-08-07 11:48 /dev/video0

grep -e video /etc/group
video:x:44:

and I add this extract from dmesg:
[   23.764454] gspca: probing 0402:5602
[   23.764457] ALi m5602: Probing for a po1030 sensor
[   24.113334] ALi m5602: Probing for a mt9m111 sensor
[   24.130960] ALi m5602: Probing for a s5k4aa sensor
[   24.162718] ALi m5602: Probing for an ov9650 sensor
[   24.205665] ALi m5602: Sensor reported 0xffff
[   24.205669] ALi m5602: Probing for a s5k83a sensor
[   24.226466] ALi m5602: Detected a s5k83a sensor
[   24.283962] gspca: probe ok
[   24.284024] usbcore: registered new interface driver ALi m5602
[   24.284031] ALi m5602: registered

Program used: skype, cheese, aMsn, Emesene, Ekiga, gstreamer-properties

Never used auxiliary port...

Continuing from the other post: I have two kernels: 2.6.32-24 (in use) and the one the came with the installation cd, 2.6.32-21, both of them can't make cam work... maybe some older kernel can make it work...but i have no idea...

---

### Post by Quackers on 2010-08-07
I installed Lucid on my laptop and could not get the webcam detected at all. As it's not a major problem to me I just accepted that it wasn't going to work.
However, I later re-installed Lucid on the second hard drive and voila! the webcam is detected and worked right away! Same system, same laptop. Strange inconsistencies.

---

### Post by titomax82 on 2010-08-07
very strange quackers....maybe you installed the first lucid within windows and the second through cd-booting with a dedicated partition?

---

### Post by Quackers on 2010-08-07
No, that's not the case titomax82. The first time Lucid was installed to the 3rd partition of my first hard drive. The second time it was installed to the 1st partition of my second hard drive. Same laptop, same system from the same cd. The webcam was picked up the second time but not the first.

---

### Post by utilitytrack on 2010-08-07
to **Quackers**

This proves that Ubuntu 10.04 it's very beta and people should not do upgrade immediately...

to **titomax82**

As I see your problem apparently is more deep than I supposed. It's look like some incompatibility between V4L and V4L2 versions of this API. Ok, give here:

```
$ dmesg | egrep -i 'cam|video|gspca'
# lsmod | egrep 'cam|video|gspca|v4l'
$ ls -l /usr/lib/libv4l* && ls -l /usr/lib/libv4l/*
$ ls -l /dev/v4l/by-id/* && ls -l /dev/v4l/by-path/*
```

Also, again post here [FONT="Courier New"]grep -e video /etc/group[/FONT] (*before that disable smilies in text*)

I wiil wait your results.

---

### Post by titomax82 on 2010-08-07
dmesg | egrep -i 'cam|video|gspca'
[    0.000000]   AMD AuthenticAMD
[    0.269753] pci 0000:01:00.0: Boot video device
[   24.161335] asus_laptop: Brightness ignored, must be controlled by ACPI video driver
[   24.277669] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:15/LNXVIDEO:00/input/input8
[   24.277725] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   24.285878] Linux video capture interface: v2.00
[   24.289452] gspca: main v2.7.0 registered
[   24.291349] gspca: probing 0402:5602
[   24.505795] gspca: probe ok

lsmod | egrep 'cam|video|gspca|v4l'
gspca_m5602            51833  0 
gspca_main             21199  1 gspca_m5602
videodev               34361  1 gspca_main
video                  17375  0 
output                  1871  1 video
v4l1_compat            13251  1 videodev

ls -l /usr/lib/libv4l* && ls -l /usr/lib/libv4l/*
-rw-r--r-- 1 root root  19112 2010-02-23 20:41 /usr/lib/libv4l1.so.0
-rw-r--r-- 1 root root  38216 2010-02-23 20:41 /usr/lib/libv4l2.so.0
-rw-r--r-- 1 root root 116204 2010-02-23 20:41 /usr/lib/libv4lconvert.so.0

/usr/lib/libv4l:
totale 56
-rwxr-xr-x 1 root root 13700 2010-02-23 20:41 ov511-decomp
-rwxr-xr-x 1 root root 21892 2010-02-23 20:41 ov518-decomp
-rw-r--r-- 1 root root  5356 2010-02-23 20:41 v4l1compat.so
-rw-r--r-- 1 root root  5412 2010-02-23 20:41 v4l2convert.so
-rwxr-xr-x 1 root root 13700 2010-02-23 20:41 /usr/lib/libv4l/ov511-decomp
-rwxr-xr-x 1 root root 21892 2010-02-23 20:41 /usr/lib/libv4l/ov518-decomp
-rw-r--r-- 1 root root  5356 2010-02-23 20:41 /usr/lib/libv4l/v4l1compat.so
-rw-r--r-- 1 root root  5412 2010-02-23 20:41 /usr/lib/libv4l/v4l2convert.so

ls -l /dev/v4l/by-id/* && ls -l /dev/v4l/by-path/*
lrwxrwxrwx 1 root root 12 2010-08-07 14:39 /dev/v4l/by-id/usb-0402_USB2.0_Camera-video-index0 -> ../../video0
lrwxrwxrwx 1 root root 12 2010-08-07 14:39 /dev/v4l/by-path/pci-0000:00:1d.7-usb-0:8:1.0-video-index0 -> ../../video0

grep -e video /etc/group
video:x:44:gtm

Here are the results. What did you mean with "[I]before that disable smilies in text"???
Little thought, but can be confusing: I'm thinking that the driver loaded is incorrect...ov511 or ov518 are two kind of sensors? because if they are referred to the sensore, mine should be [/I]s5k83a

---

### Post by utilitytrack on 2010-08-07
I'm not understand this:

[FONT="Courier New"]grep -e video /etc/group
video:44:gtm[/FONT]

while your previos post it was
[FONT="Courier New"]grep -e video /etc/group
video:44:[/FONT]

How it may be? Did you change something now?

PS
Look in "Additional Options" in bottom for **disable smilies in text**. It's no joke.

PPS
Not hurry me

---

### Post by titomax82 on 2010-08-07
yes...that was I try a made some hours ago, no other changes...should i remove the username in the video group? if yes tell me how please
ps: i found disable smiles

---

### Post by utilitytrack on 2010-08-07
to **titomax82**

Sorry for long time I no reply but I had to listen some important things that broadcast Echo of Moscow radio station... We have here in Russia some natural disaster...

Ok, as I spoke this line confuse me:
[FONT="Courier New"]video:44:gtm[/FONT]
Try manually (and careful) replace it on 
[FONT="Courier New"]video:x:44:[/FONT]

I suppose that all of your troubles due to the fact that your camera are non-compatible with UVC cpecification.
To see this, try make a test record use [FONT="Courier New"]luvcview -l[/FONT] program. If unsuccessful, then probable I'm right. 

Next run [FONT="Courier New"]$ gstreamer-properties[/FONT], go to Video tab, set Plugin to v4l (or v4l2) and press Test. I will wait your impressions.

PS 
please give here [FONT="Courier New"]lsusb | grep Camera[/FONT]
and also [FONT="Courier New"]$ dmesg | egrep -i 'cam|video|gspca|5602'[/FONT]

---

### Post by utilitytrack on 2010-08-07
Also I see that this driver (gspca_m5602) has active development some time ago: [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git&a=search&h=HEAD&st=commit&s=m5602]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git&a=search&h=HEAD&st=commit&s=m5602")

---

### Post by titomax82 on 2010-08-07
ok...grep back like before

luvcview -l:
luvcview 0.2.6

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
ERROR: Requested frame format MJPG is not available and no fallback format was found.
 Init v4L2 failed !! exit fatal

gstreamer-properties: if i put "v4l" the device selection box becomes grey and webcamera cannot be selected anymore ("no device available") and if I press "test" gstreamer freezes

lsusb | grep Camera:
Bus 001 Device 004: ID 0402:5602 ALi Corp. Video Camera Controller

dmesg | egrep -i 'cam|video|gspca|5602':
[    0.000000]   AMD AuthenticAMD
[    0.269753] pci 0000:01:00.0: Boot video device
[   24.161335] asus_laptop: Brightness ignored, must be controlled by ACPI video driver
[   24.277669] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:15/LNXVIDEO:00/input/input8
[   24.277725] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   24.285878] Linux video capture interface: v2.00
[   24.289452] gspca: main v2.7.0 registered
[   24.291349] gspca: probing 0402:5602
[   24.291352] ALi m5602: Probing for a po1030 sensor
[   24.336358] ALi m5602: Probing for a mt9m111 sensor
[   24.357230] ALi m5602: Probing for a s5k4aa sensor
[   24.391106] ALi m5602: Probing for an ov9650 sensor
[   24.428606] ALi m5602: Sensor reported 0xffff
[   24.428608] ALi m5602: Probing for a s5k83a sensor
[   24.448980] ALi m5602: Detected a s5k83a sensor
[   24.505795] gspca: probe ok
[   24.505823] usbcore: registered new interface driver ALi m5602
[   24.505826] ALi m5602: registered

for the link you suggested...i'm completely stupid...don't know what to do with it :(

---

### Post by utilitytrack on 2010-08-07
> **titomax82 said:**
> gstreamer-properties: if i put "v4l" the device selection box becomes grey and webcamera cannot be selected anymore ("no device available") and if I press "test" gstreamer freezes

Ok, but did you guess select v4l2 plugin and test it? Or it's not available?
Also, did you change [FONT="Courier New"]/etc/group[/FONT] file as I said? Make it and test the capture over [FONT="Courier New"]gstreamer-properties[/FONT]
Why are you so inconsiderate?

---

### Post by titomax82 on 2010-08-07
(like originally)
grep -e video /etc/group:
video:x:44:

to obtain some result with the v4l2 test, webcam has to not be never accessed since boot. Infact if gstreamer is the first to access webcam, test starts with the test bar moving, even if with a blank screen with some grey stripes (a kind of static image, like described at the beginning of this post). If some application has accessed webcam before than gstreamer, or even a previous gstremer test itself, only the test bar appears, but not the box where the image should be tested

---

### Post by utilitytrack on 2010-08-07
And I must remind to the audience that all of his difficulties occur with the [FONT="Courier New"]Packard Bell EasyNote MX67[/FONT] laptop. Fear him! It's not a friend of Linux. Be careful on the future.

---

### Post by utilitytrack on 2010-08-07
> **titomax82 said:**
> 
to obtain some result with the v4l2 test, webcam has to not be never accessed since boot. Infact if gstreamer is the first to access webcam, test starts with the test bar moving, even if with a blank screen with some grey stripes (a kind of static image, like described at the beginning of this post). If some application has accessed webcam before than gstreamer, or even a previous gstremer test itself, only the test bar appears, but not the box where the image should be tested

From what source this?

---

### Post by titomax82 on 2010-08-07
my source, my personal testing

---

### Post by utilitytrack on 2010-08-07
> **titomax82 said:**
> my source, my personal testing

I thought that you get it from some encyclopaedia :)) Sorry, I didn't understand immediately.

> only the test bar appears
It's interesting. Make a screenshot.

Ok, please reinstall [FONT="Courier New"]libv4l-0[/FONT] and install [FONT="Courier New"]libv4l-dev[/FONT] packages. And we start all over again. This time more decisively.

Also give here some part of your [FONT="Courier New"]/etc/group[/FONT] file (or give it entirely in the attachment).

---

### Post by titomax82 on 2010-08-07
[FONT=Verdana]libv4l-0 and [/FONT][FONT=Courier New][FONT=Verdana]libv4l-dev installed

/etc/group: [http://pastebin.com/ed0bspCy](http://pastebin.com/ed0bspCy)

remember i'm stupid with linux, i don't know how to make the screenshot :(, however there's only the test bar moving ahead and behind.... EDIT: i found how to :)
[/FONT][/FONT]

---

### Post by titomax82 on 2010-08-07
what's next? i don't want to hurry you, absolutely...but sometimes notifies arrive lately...

---

### Post by utilitytrack on 2010-08-07
> **titomax82 said:**
> remember i'm stupid with linux

No, I'm sure that this is not so from the moment when you start talking to me :))

> **titomax82 said:**
> what's next? ... sometimes notifies arrive lately
Forget it, **disconnect from the outside world,** otherwise there is no success.

***
I see that you finally brought [FONT="Courier New"]/etc/group[/FONT] file to the normal form. It's good. Incidentally, on screenshot I see that all your system on Italian... It's good, but this now creates unnecessary complexity for you because we communicate in English. Hint: for change interface language to english for any program run it from shell:

```
env LC_MESSAGES=C some_command
```

Ok, next you will have to work. Please see on this:

```
[FONT="Courier New"]# modinfo gspca_m5602 
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/media/video/gspca/m5602/gspca_m5602.ko
license:        GPL
description:    ALi m5602 webcam driver
author:         ALi m5602 Linux Driver Project
srcversion:     E34BF4058A55CDF5A1B5FA9
alias:          usb:v0402p5602d*dc*dsc*dp*ic*isc*ip*
depends:        gspca_main
vermagic:       2.6.32-22-generic SMP mod_unload modversions 586 
parm:           force_sensor:forces detection of a sensor, 1 = OV9650, 2 = S5K83A, 3 = S5K4AA, 4 = MT9M111, 5 = PO1030, 6 = OV7660 (int)
parm:           dump_bridge:Dumps all usb bridge registers at startup (bool)
parm:           dump_sensor:Dumps all usb sensor registers at startup providing a sensor is found (bool)
[/FONT]

```
Do you see three parameters of this module (dump_bridge, dump_sensor and force_sensor)? Pay attention to the last parameter. You will have to consistently go through all values (from 1 to 6) of this parameter until you find suitable.
I not see other solution in this case. To do it:

First remove the current module from kernel
```
# modprobe -v -r gspca_m5602

```
Next insert the module with necessary parameter
```
# modprobe -v gspca_m5602 force_sensor=1

```

Next try make test record through [FONT="Courier New"]gstreamer-properties[/FONT]. If no success, choose other value. And so on. Be advertency.

I will wait (only good!) your results.

PS
If all of these explanations don't will give good results, I think you need try/install other drivers ([FONT="Courier New"]spca5xx[/FONT] for example) or compile a fresh kernel (2.6.35), or recompile [FONT="Courier New"]gspca_m5602[/FONT] module at least. Good luck!

---

### Post by titomax82 on 2010-08-07
ok utility.... now i have to go to work....tomorrow morning i will do these tries....
i don't know why...but i think that these 6 last tries will give some result.... goodnight friend

---

### Post by titomax82 on 2010-08-07
since i have some time...i started trying....but...is this message normal?

gtm@ubuntu:~$ # modprobe -v -r gspca_m5602
gtm@ubuntu:~$ modprobe -v gspca_m5602 force_sensor=1
WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.

how do I check if change has been registered?

---

### Post by utilitytrack on 2010-08-07
I don't know why you need this file [FONT="Courier New"]/etc/modprobe.d/sound[/FONT]. Anyway you shouldn't pay attention to similar messages.

> how do I check if change has been registered?
Simply look in logs; but will better if you open second terminal and run this command: [FONT="Courier New"]# tail -f /var/log/kern.log[/FONT]. You all will see. 

Good advice: do as I suggested, with a fresh mind. It is easier to achieve success. I'm going to sleep. Good night.

---

### Post by titomax82 on 2010-08-08
Tried all 6 possibilities....still no result;
1,2,4,5,6 give a blank static image with some stripes and dots
3, insted, give a blank screen, but not static, less stripes and dots, but moving

---

### Post by utilitytrack on 2010-08-08
Hello again! I had to do some research of your situation.

> Tried all 6 possibilities....still no result.

Well, a negative result is also a result. I'm right?

I looked in kernel source tree and this is what I found:

from [FONT="Courier New"]Documentation/video4linux/m5602.txt[/FONT] ([_http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=Documentation/video4linux/m5602.txt_]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=Documentation/video4linux/m5602.txt"))
> [I]This document describes the ALi m5602 bridge connected
to the following supported sensors:
OmniVision OV9650,
Samsung s5k83a,
Samsung s5k4aa,
Micron mt9m111,
Pixel plus PO1030

This driver mimics the windows drivers, which have a braindead implementation sending bayer-encoded frames at VGA resolution.
In a perfect world we should be able to reprogram the m5602 and the connected sensor in hardware instead, supporting a range of resolutions and pixelformats

Anyway, have fun and please report any bugs to [email]m560x-driver-devel@lists.sourceforge.net[/email][/I]



I'm sorry, but of course you understand that I can't add nothing because it's developers' conclusion.

I can advice you participate in the development of **ALi Corp. M5602 driver** and recompile [FONT="Courier New"]gspca_m5602[/FONT] and [FONT="Courier New"]gspca_main[/FONT] modules for turn on debugging, then contact with developers ([_http://sourceforge.net/projects/m560x-driver/_]("http://sourceforge.net/projects/m560x-driver/")) and test it as them will say.

Also still might be some possibilities to use drivers not from mainline kernel. If these drivers exist, though. I not find them.

***
PS
Please give here this for clarity
$ cat /proc/bus/input/devices
$ v4l-info

And read careful [_https://help.ubuntu.com/community/Webcam_]("https://help.ubuntu.com/community/Webcam") for learning the situation. Also you can see status "REPORTEDUPSTREAM" in exactly the same situation on [_https://qa.mandriva.com/show_bug.cgi?id=56466_]("https://qa.mandriva.com/show_bug.cgi?id=56466")

***
PPS
There is some probability that this camera will work on more old kernels (2.6.29 particularly). See information and comments on [_http://hardware4linux.info/component/26591/_]("http://hardware4linux.info/component/26591/")

---

### Post by titomax82 on 2010-08-08
cat /proc/bus/input/devices:
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:15/LNXVIDEO:00/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0011 Vendor=0002 Product=0007 Version=3ab4
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Asus Laptop extra buttons"
P: Phys=asus_laptop/input0
S: Sysfs=/devices/virtual/input/input8
U: Uniq=
H: Handlers=rfkill kbd event8 
B: EV=3
B: KEY=100000 400 0 0 506c 900000 278 1501000 e0000 0 0 0

I: Bus=0001 Vendor=11d4 Product=1986 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/input/input9
U: Uniq=
H: Handlers=kbd event9 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c03e Version=0110
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input11
U: Uniq=
H: Handlers=mouse2 event10 
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

v4l-info:

### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
    driver                  : "ALi m5602"
    card                    : "USB2.0 Camera"
    bus_info                : "usb-0000:00:1d.7-8"
    version                 : 2.7.0
    capabilities            : 0x5000001 [VIDEO_CAPTURE,READWRITE,STREAMING]

standards

inputs
    VIDIOC_ENUMINPUT(0)
    index                   : 0
    name                    : "ALi m5602"
    type                    : CAMERA
    audioset                : 0
    tuner                   : 0
    std                     : 0x0 []
    status                  : 0x0 []

video capture
    VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)
    index                   : 0
    type                    : VIDEO_CAPTURE
    flags                   : 0
    description             : "BA81"
    pixelformat             : 0x31384142 [BA81]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
    type                    : VIDEO_CAPTURE
    fmt.pix.width           : 640
    fmt.pix.height          : 480
    fmt.pix.pixelformat     : 0x31384142 [BA81]
    fmt.pix.field           : NONE
    fmt.pix.bytesperline    : 640
    fmt.pix.sizeimage       : 307200
    fmt.pix.colorspace      : SRGB
    fmt.pix.priv            : 0

controls

### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
    name                    : "USB2.0 Camera"
    type                    : 0x1 [CAPTURE]
    channels                : 1
    audios                  : 0
    maxwidth                : 640
    maxheight               : 480
    minwidth                : 48
    minheight               : 32

channels
    VIDIOCGCHAN(0)
    channel                 : 0
    name                    : "ALi m5602"
    tuners                  : 0
    flags                   : 0x0 []
    type                    : CAMERA
    norm                    : 0

tuner
ioctl VIDIOCGTUNER: Invalid argument

audio
    VIDIOCGAUDIO
    audio                   : 0
    volume                  : 0
    bass                    : 0
    treble                  : 0

picture
    VIDIOCGPICT
    brightness              : 0
    hue                     : 0
    colour                  : 0
    contrast                : 0
    whiteness               : 0
    depth                   : 8
    palette                 : unknown

buffer
ioctl VIDIOCGFBUF: Invalid argument

window
    VIDIOCGWIN
    x                       : 0
    y                       : 0
    width                   : 640
    height                  : 480
    chromakey               : 0
    flags                   : 0


for studing/working reason i can't partecipate in develpment;
so...the only solution is to use an older kernel? I have no idea how to do this.... and it seems to me a very risky operation...

---

### Post by utilitytrack on 2010-08-08
> ...for studing/working reason i can't participate in development

Well, it's your choice. 

> ...so...the only solution is to use an older kernel? I have no idea how to do this...

I can not tell you the solution or not. I already did everything he could, my friend.

---

### Post by titomax82 on 2010-08-08
you did more than everything! i thank you very much for your patience :)

---

### Post by utilitytrack on 2010-08-08
After some time I decided to reflect on the existing situation.
> **utilitytrack said:**
> 
PS
If all of these explanations don't will give good results, I think you need ...  recompile [FONT="Courier New"]gspca_m5602[/FONT] module at least.

It's my thoughts: if you will wish follow my advice, then can try compile the driver from SVN ([http://m560x-driver.svn.sourceforge.net/viewvc/m560x-driver/]("http://m560x-driver.svn.sourceforge.net/viewvc/m560x-driver/")). But you must understand that this version of the driver, as I see, is not compatible in fresh kernels (2.6.32 particularly). This means that you will have to install the old kernel. It's not so difficult in itself, but you know to how many hardware problems this may cause. But it is a chance that we get a working camera. So that it's probably easier to have the old Ubuntu Jaunty system with 2.6.28 kernel, and check the camera work. 

On the other hand can try recompile the driver from mainline kernel Git repository. This version is adapted to fresh kernels. Maybe this will not work but there is a second chance.

---

### Post by titomax82 on 2010-08-08
i do think i'll have the skills to do this....and for sure i will not have the time for this....
i don't want to be a parassite ahahahah....but i hope someone else will fix this problem...or maybe a future kernel release...who knows...

---

### Post by inameiname on 2010-08-08
As I mentioned in your other posting, from what the others have said, it seems it's primarily a kernel issue that is keeping your webcam from working. My advice is again, to update the kernel and see if that fixes it. If not, try an older kernel.

This is all you have to do:

sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo aptitude install linux-headers-2.6.35-14-generic linux-image-2.6.35-14-generic

Then if it works, sweet. If not, you can revert back to your older kernel. Just look into how, usually by restarting and hitting 'Shift' button so it shows the boot menu, which will show which kernel you want the computer to boot with. And when you boot with your current one, 2.6.32-24-generic, you can remove the 2.6.35 one:

sudo apt-get remove --purge 2.6.35-14-*

And if you are willing to try an older kernel as suggested on here, you can always download them from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

Perhaps the 2.6.29 one? 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.29/")

All you need to download are the following three files:

[linux-headers-2.6.29-020629-generic_2.6.29-020629_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.29/linux-headers-2.6.29-020629-generic_2.6.29-020629_i386.deb")
[linux-headers-2.6.29-020629_2.6.29-020629_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.29/linux-headers-2.6.29-020629_2.6.29-020629_all.deb")
[linux-image-2.6.29-020629-generic_2.6.29-020629_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.29/linux-image-2.6.29-020629-generic_2.6.29-020629_i386.deb")

or if you have AMD64 computer:

[linux-headers-2.6.29-020629-generic_2.6.29-020629_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.29/linux-headers-2.6.29-020629-generic_2.6.29-020629_amd64.deb")
[linux-headers-2.6.29-020629_2.6.29-020629_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.29/linux-headers-2.6.29-020629_2.6.29-020629_all.deb")
[linux-image-2.6.29-020629-generic_2.6.29-020629_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.29/linux-image-2.6.29-020629-generic_2.6.29-020629_amd64.deb")

But as stated, an older kernel could suck with your computer and your Lucid operating system, so my suggestion is the latest. Nevertheless, if it works it will show it is indeed the kernel and a bad updated driver.

I never got why newer kernels work poorer than older ones. :P


FYI, I've been using 2.6.35-14-generic kernel and it's repository for a week and have found no bugs as of yet. Of course, that's just me, and with my three computers that I use, all varying ages.

---

### Post by utilitytrack on 2010-08-08
to **inameiname**

Thanks for you explain these things for **titomax82**. I just wanted to do the same. But I would first tried the old kernel because with him there are some positive results.

---

### Post by inameiname on 2010-08-08
Yeah sure. I don't know, my theory is just weird in that if it's an older kernel, designed for an older operating system, how can it truly handle and understand something that didn't exist when it was made? :P But who knows...maybe it'll work well for him.

---

### Post by titomax82 on 2010-08-08
thanks guys (inameiname and utilitytrack)... i think that the newer kernel won't help me...because one of my friend suggested me to try the "maverick" version of ubuntu and it come with a kernel 2.6.35-xx (last 2 digits i don't rember, however i downloaded yesterday)...and nothing changed... even if trying a new kernel in a new OS from a live cd could be different from trying a new kernel in the current OS "installed"...

however...one day, maybe in xmas holydays ehehe, i'll try both solutution (updated and downgraded kernel) and i'll let you know...
for the moment, if no other suggestion, my struggle with ALi webcam finishes here, maybe on xmas holydays i'll give myself a gift with an external and working webcam ahahah

thank you guys...it's been a pleasure dealing with you

---

### Post by utilitytrack on 2010-08-08
> **inameiname said:**
> Yeah sure. I don't know, my theory is just weird in that if it's an older kernel, designed for an older operating system, how can it truly handle and understand something that didn't exist when it was made? :P But who knows...maybe it'll work well for him.

Of course you unterstand that it's not in the kernel in itself, but in the driver version. Everything suggests that older versions work with the ALi m5602 camera (this is evident from the messages on [http://hardware4linux.info/component/26591/]("http://hardware4linux.info/component/26591/")), and the new does not work. However, soon we will see, I am right or not.

---

### Post by utilitytrack on 2010-08-08
> **titomax82 said:**
> ...for the moment, if no other suggestion, my struggle with ALi webcam finishes here.

Ok, I still hope that you don't will forget about it because your struggle became more and more interesting. Now I'm even sorry that I don't have access to appropriate laptops with this buggy camera where I could make my own conclusions as to whether it works or not.

> *thank you guys...it's been a pleasure dealing with you*


No, you are wrong, it's been a pleasure dealing with Linux :))

---

### Post by utilitytrack on 2010-08-08
**to the audience**

As I suppose this is driver problem (regression) on newest kernels (probably since 2.6.31 but maybe earlier). This explains a lot. All of those who experience the same troubles with **ALi Corp. m5602** camera (device ID 0402:5602) in Ubuntu 10.04 and Ubuntu 9.10 systems should see this on [https://bugzilla.kernel.org/show_bug.cgi?id=15651]("https://bugzilla.kernel.org/show_bug.cgi?id=15651")

And for to make the attention of developers on the problem, I advise all of you to send reports there and not sit in silence.

[B]to titomax82
[/B]
Please make following for me. I hope this should confirm or disprove my assumptions. First, run this for testing
```
$ mplayer tv:// -tv driver=v4l2:device=/dev/video0
```
Next run this
```
$ LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so mplayer tv:// -tv driver=v4l2:device=/dev/video0
```
Next, run the most important command
```
$ dmesg | egrep -i 'cam|video|gspca|5602|ISOC'
```
and provide the output here. Thanks.

---

### Post by titomax82 on 2010-08-09
mplayer tv:// -tv driver=v4l2:device=/dev/video0:
Creating config file: /home/gtm/.mplayer/config
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: USB2.0 Camera
 Capabilites:  video capture  read/write  streaming
 supported norms:
 inputs: 0 = ALi m5602;
 Current input: 0
 Current format: unknown (0x31384142)
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: Cannot get fps
v4l2: ioctl set mute failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Cannot find codec matching selected -vo and video format 0x31384142.
Read DOCS/HTML/en/codecs.html!
==========================================================================

v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.

Exiting... (End of file)




LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so mplayer tv:// -tv driver=v4l2:device=/dev/video0:
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: USB2.0 Camera
 Capabilites:  video capture  read/write  streaming
 supported norms:
 inputs: 0 = ALi m5602;
 Current input: 0
 Current format: RGB24
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: Cannot get fps
v4l2: ioctl set mute failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Planar YV12 
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
Audio: no sound
Starting playback...
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 
v4l2: select timeout ??% ??,?% 0 0 
libv4l2: error dequeuing buf: Invalid argument
v4l2: ioctl set mute failed: Invalid argument
v4l2: 1 frames successfully processed, 0 frames dropped.

This gave me the usual corrupted blank screen and then a green image



dmesg | egrep -i 'cam|video|gspca|5602|ISOC':
[    0.000000]   AMD AuthenticAMD
[    0.269745] pci 0000:01:00.0: Boot video device
[   22.520585] Linux video capture interface: v2.00
[   22.524817] gspca: main v2.7.0 registered
[   22.655789] asus_laptop: Brightness ignored, must be controlled by ACPI video driver
[   23.683263] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:15/LNXVIDEO:00/input/input9
[   23.683346] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   23.704845] gspca: probing 0402:5602
[   23.704849] ALi m5602: Probing for a po1030 sensor
[   23.817098] ALi m5602: Probing for a mt9m111 sensor
[   23.896100] ALi m5602: Probing for a s5k4aa sensor
[   23.944224] ALi m5602: Probing for an ov9650 sensor
[   23.985780] ALi m5602: Sensor reported 0xffff
[   23.985784] ALi m5602: Probing for a s5k83a sensor
[   24.005983] ALi m5602: Detected a s5k83a sensor
[   24.063473] gspca: probe ok
[   24.063516] usbcore: registered new interface driver ALi m5602
[   24.063522] ALi m5602: registered

---

### Post by titomax82 on 2010-08-10
utilitytrack...do this confirm your assumptions?

---

### Post by utilitytrack on 2010-08-10
Hello again, titomax82.

Information what you gave in last post is not confirm that your troubles is related with 15651 kernel bug. Well, on this moment it's difficult to say with what exactly it related, until you not try to use other (old) version of gspca_m5602 driver (i.e. older kernels as noted above).

And I would to remind that you hope for "one day, maybe in xmas ... i'll try both solutution and i'll let you know...". So I with others simply waiting the results of your experiments.

---

### Post by titomax82 on 2010-08-10
maybe after my university test....on the half of semptember (but i cannot promise:)

---

### Post by utilitytrack on 2010-08-10
Ok, I'm not rushing you. Also please add some tags to this thread for other users. The tags can be "webcam", "MX67" and "gspca".

---

### Post by no2498 on 2010-08-10
if i seen right the ( MJPEG ) does not load any more so we can not use it

he can change the settings in the program, wxcam
read and install all the page tell you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

i had to set my cam to rgb32 v4l2 to get it to work

go between, gstreamer-properties and wxcam you need to play with both programs

hope this helps

---

### Post by utilitytrack on 2010-08-10
to **no2498**

You not understood. This problem is not related with any user space programs. This problem related with video camera driver and, respectively, with the kernel.

---

### Post by titomax82 on 2010-08-10
sorry for my ignorance regarding linux environments...but i thought that installing a kernel was something long like installing a new OS.... so, when I understood it was very simple (install the 3 packages and update grub), I did it, but when i restarted with the 2.6.29...in the booting sequence i had some messages like these:

cpufreq: no nForce2 chipset
mounting none on dev/: failed .... etc.....

it contined running to desktop...and the webcam light was already on...but nothing worked: audio, keyboard, touchpad, usb mouse.... nothing...so I had to turn off the notebook by keeping pressed the power button
it didn't work even in recovery mode

fortunately...and that was my greatest fear....rebooting and choosing kernel 2.6.32-24 worked like before...and so i removed 2.6.29 kernel and re-updated grub.... all ok now (except webcam of course)

I think that ubuntu 10.04 needs an updated kernel to run well...like it's original (2.6.32-21) kernel...or howver something more than 2.6.29

So, at the end, i tried a newer kernel with the maverick version of ubuntu and webcam didn't work and i tried an older kernel and it didn't work the same, but this latest try is not complete because, with a freezed os i couldn't test webcam....so i was thinking i should try a live cd, with a ubuntu version like 2.6.29 to have the correct test....right? where can i find it?

---

### Post by no2498 on 2010-08-10
i do understand that dev/: failed 
if we can NOT use mjpeg things will fail
did not read every thing but did not see could not set pipeline


btw is the cam non uvc spca 5xx or is it a uvc

---

### Post by utilitytrack on 2010-08-10
to **titomax82**

No, I believe that your camera will work with old kernel, but you are too hurry and not properly installed the kernel. See this [https://wiki.ubuntu.com/Kernel/FAQ]("https://wiki.ubuntu.com/Kernel/FAQ")

PS
Anyway for solve this **new** problems you will need open a new thread on this forum :))  OMG

(that's joke)

---

### Post by titomax82 on 2010-08-10
i installed the 3 packages trough package manager and then updated grub, was this procedure not correct? if not...i was right thinking that installing a kernel is not for noobs linux users :)

however...i'm downloading karmic koala, jaunty and hardy, they should have older kernels,  and i'll try them with live-cd... these tries "should" clear the doubts and see if a complete os with a previous kernel version works for my webcam... if one of the tries works...i should install (in the right way if my previous was wrong) and try the old kernel...is this kind of trying right? (in the case i will install an older kernel I will need your help)

why should i open a new thread?

---

### Post by titomax82 on 2010-08-10
new update! it's certainly a kernel problem...because new kernels can't handel m5602 drivers

i tried ubuntu 8.04 hardy, but there was no /dev/video0, maybe this distro does not have the drivers needed at all

then i tried ubuntu 9.10 karmic... it came with a kernel 2.6.31... which is too high for this case...infact nothing worked

as last chance i tried ubuntu 9.04 jaunty which comes with 2.6.28-11 (less then 2.6.29) and infact it works! the webcam light is always on, even not using programs, but for the moment i've tried gstreamer-properties and ekiga and finally my face appears... i was almost crying!!!

i'm seriousely thinking about removing lucid lynx and installing jaunty....what jaunty has less than lucid? is it possible to install the ubuntu software center in jaunty? or jaunty is a bad idea?

---

### Post by utilitytrack on 2010-08-10
**Oh my God!** I'm not believe! **titomax82**, I'm very happy for you! Yeesss!!! I also would cry with you... because your dream is accomplished! And my assumptions were correct:

> **utilitytrack said:**
> ...But it is a chance that we get a working camera. So that it's probably easier to have the old Ubuntu Jaunty system with 2.6.28 kernel, and check the camera work.

I was right!

[SIZE="1"]PS
&#1059;&#1088;&#1072;!! &#1073;&#1083;&#1080;&#1085;, &#1085;&#1072;&#1082;&#1086;&#1085;&#1077;&#1094;-&#1090;&#1086; &#1086;&#1085;&#1072; &#1079;&#1072;&#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1083;&#1072;!! &#1054; &#1075;&#1086;&#1089;&#1087;&#1086;&#1076;&#1080;, &#1090;&#1099; &#1086;&#1073;&#1088;&#1072;&#1090;&#1080;&#1083; &#1074;&#1079;&#1086;&#1088; &#1085;&#1072; &#1101;&#1090;&#1086;&#1075;&#1086; &#1084;&#1091;&#1095;&#1077;&#1085;&#1080;&#1082;&#1072;.[/SIZE]

---

### Post by titomax82 on 2010-08-11
Latest (good) news and updates:
I removed lucid and installed jaunty...all work....now I'm happy :)

One last question: I want to report this bug...but since it's a kernel bug, not depending on a particular distro (such as mandriva, mint, ubuntu and so on) I think I should not contact a distro's releaser...but i should contact who realizes kernels.... where have i to do the bug report?

---

### Post by utilitytrack on 2010-08-11
I think that you should send bug report to mainline kernel bugzilla ([https://bugzilla.kernel.org/]("https://bugzilla.kernel.org/")) because development of gspca_* drivers is taking place right there. You will need open the account there. And in bug report you write in detail all of your troubles with camera when you used a stock Ubuntu 10.04 kernels (2.6.32-24-generic, 2.6.32-21 and others that you tried). Also give there a link to this thread.

PS
Accept my congratulations once again!

---

### Post by titomax82 on 2010-08-11
there's already a bug report...hoping they will fix it....but i do not trust in this....too much time passed since first 2.6.3x kernels... i'm jaunty's prisoner :)

---

### Post by utilitytrack on 2010-08-11
Please give a link. Also please post here some screeshots with working camera :)

---

### Post by titomax82 on 2010-08-11
This is the link (you had already found it in a page reguarding drivers, but it's even in the kernel bug tracker): [https://bugzilla.kernel.org/show_bug.cgi?id=15651](https://bugzilla.kernel.org/show_bug.cgi?id=15651)

And this is the screenshot: there some colors regolation to do....and don't take care of my black eyes because i'm watching monitors 18h/day since 2 weeks :)

[[IMG]http://img804.imageshack.us/img804/4866/schermatau.png[/IMG]](http://img804.imageshack.us/i/schermatau.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by utilitytrack on 2010-08-11
URA! Cool! My happiness!...  :)) 

PS
I ready to help you to make a bug report, if you want it.

---

### Post by titomax82 on 2010-08-11
do you think we must make another bug report?

---

### Post by utilitytrack on 2010-08-11
Definitely yes. Because only you experienced such problems with camera. As you can see, kernel bug 15651 is not relevant in your situation. So I think it will be good if we open new. 

[SIZE="1"]PS
As I see, you will soon become a kernel hacker :))[/SIZE]

---

### Post by titomax82 on 2010-08-11
i think it's the same thing....but if you'ready to prepare the bur report...i'm you with for all informations you need :)

---

### Post by utilitytrack on 2010-08-11
**to titomax82**

Yes, of cource. Please begin from reading [The Bugzilla Guide]("https://bugzilla.kernel.org/docs/en/html/using.html"). Next, create a account. After this, we will should know **exactly** on wich versions of kernels is appear this bug. It's will be good if we collect set of information for several kernels that you tried. Also it's important that we already collect in this thread almost all needed info (with respect to 2.6.32-24, if I'm not mistaken). Also you should describe in detail the artefacts on images from not working camera. I absolutely sure that you must make a screenshots of this. And so on. 

**to the audience** 
I would like all of you to specify to this thread [[M560x-driver-devel] Contact with Ali Corp.]("http://sourceforge.net/mailarchive/forum.php?thread_name=234fa2210811120010n17997f2cgeb23badd59d46c26@mail.gmail.com&forum_name=m560x-driver-devel"). Read it and you will know why Linux has such problems with hardware as have titomax82.

---

### Post by titomax82 on 2010-08-12
utilitytrack...i sent you a pm few minutes ago

just one thing a noticed...but i don't know if it's important or not:

when trying the unlucky kernels (2.6.3x and higher) webcam light was off and it went on only when a program requested it

with the lucky kernels (from 2.6.29-x to 2.6.28-x) webcam light is always on since startup

i have to underline for the audience that my webcam has no button activation (like some FN+x or hardware button) nor it request a particular software activation...

---

### Post by utilitytrack on 2010-08-12
I received your PM. Please add some tags to this thread (see post [http://ubuntuforums.org/showpost.php?p=9702845&postcount=61]("http://ubuntuforums.org/showpost.php?p=9702845&postcount=61"))

---

### Post by Dr Zin on 2010-08-13
I have went through most of this thread. It did not help that much. Other than the fact I am use a two different GUI. KDE, Gnome. On hard drive one see the cam just fine. One does not.

So this Upgrade them both to the latest Kernel. They both match on the kernel mods. What i am trying to figure out. Where can I any Can find conflicts.

So, Like I load Kubuntu. Log-in  play for a minute. then I go launch like skype i go test it. It works, I go to cheese it works.. etc every thing works only when you are running one app at a time. I ran through in this post in Kubuntu, and every thing check. So I am thinking is that the is app or some software accessing camera resource so its not running. WHeni am running ubuntu. Ok so I have VMware running and the I go and select it and it works. So when i go disconnect ok what just happen stop the conflict. Nope. So all day getting nothing done bang my head over this issue. i am clueless

---

### Post by titomax82 on 2010-08-14
Dr Zin...which camera you have?

I don't think it's a particular app or software problem

If I boot from Jaunty usb (2.6.28) it works, if I boot form Karmic usb (2.6.31) I it doesn't work but if I install kernel 2.6.29 it works, if I boot from lucid usb (2.6.32) it does'nt work.
The same thing if I install this distro's in the same partition one per time...

---

### Post by Dr Zin on 2010-09-06
```
n:~$ dmesg | egrep -i 'cam|video'
[    0.000000]   AMD AuthenticAMD
[    0.297469] pci 0000:00:02.0: Boot video device
[    7.039273] Linux video capture interface: v2.00
[    7.057767] uvcvideo: Found UVC 1.00 device CNF7051 (04f2:b070)
[    7.074463] usbcore: registered new interface driver uvcvideo
[    7.074509] USB Video Class driver (v0.1.0)
[    8.884881] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9
[    8.884977] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)

``````
uvcvideo               56990  1 
videodev               34361  2 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
video                  17375  1 i915
output                  1871  1 video

```

They are the in same in the Kernel Builds. the only Difference is that hard that has KDE on it has about 50 bad sectors and is only 250GB Toshiba. The hard that I have been working on is a Seagate 500GB HHD. Really. If you any specs on my system please, understand that I ran very deeply in look for the answer I do my research. So I am just need a new and fresh angle.

---

### Post by titomax82 on 2010-09-06
can you post your lsusb and dmesg?

---

### Post by Dr Zin on 2010-09-27
I had to a reinstall of Ubuntu. Not related to this issue. When I re-installed it worked. I think it had to something with VMware that was  installed, or something...Thank you.

---

### Post by utilitytrack on 2010-10-26
So, I still forgot to write a link on opened bug ticket.

Here is the report on Linux Kernel Bugzilla: 
**"ALi Corp. 5602 (m5602) webcam not working on newest kernels (2.6.31, 2.6.32, 2.6.35)" **[https://bugzilla.kernel.org/show_bug.cgi?id=16575]("https://bugzilla.kernel.org/show_bug.cgi?id=16575")

All people who see similar problems are welcome to share your skills, logs, questions and comments. Your experience is important. Thanks.

---

### Post by JakcV on 2010-11-27
I have been following this tread from begining.

I have another partition with Lucid Alpha 1, and I can use the webcam in cheese (just install cheese without do anything) but I am now using Lucid LTS, i can't use the webcam. 

Can I patch some part from the old kernal to the new one and solve the problem?

---

### Post by JakcV on 2010-11-30
I found that my webcam is using the uvcvideo as the logitech webcame from [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/533907](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/533907)

then i use the lsmod and found out, my uvcvideo module does not load automatically after the cheese is run.
Then I have to load the module manually before run the cheese, then my webcam can be used.

ps: although it is not related to your webcam but need to update the info.

---

### Post by alamocg on 2010-12-15
Quick note:

I was having the symptom "libv4l2: error dequeuing buf: Invalid argument" from the cheese program.  

My USB cam was hooked up first to a USB extension, THEN to one of the "ways" of a USB "4-way splitter".  I choose a different plug on the splitter (leaving everything else the same) and the cam seems to have worked fine after that in the cheese program!

---

### Post by titomax82 on 2010-12-16
@alamocg:
how do you run the uvcvideo? i want to do this try....
 
@JakcV:
i can't change the usb plug, because my webcam is a part of the notebook, it's on the usb bus, but not with a physical connector....

---

### Post by JakcV on 2010-12-20
my webcam also is built in at the laptop however, it can be checked using the command lsusb. 

I use this command 
```

sudo modprobe uvcvideo

```
after that i open the "cheese", then my webcam is function.

---

