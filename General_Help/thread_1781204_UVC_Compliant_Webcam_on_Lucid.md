---
title: "UVC Compliant Webcam on Lucid"
date: 2011-06-13
forum: General Help
---

### Post by sj1410 on 2011-06-13
Hi,

I have a UVC Compliant Webcam and want to use it on Lucid to take screenshots. I tried different application like vgrabbj, streamer, cheese and all of this does not work. It seems some problem with the UVC driver in lucid. 

Output of some of the commands are

# lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 160a:3184 VIA Technologies, Inc. VIA VNT-6656 [WiFi 802.11b/g USB Dongle]
Bus 001 Device 002: ID 1871:0501 Aveo Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


# lsmod | grep video
uvcvideo               55269  1 
videodev               42106  2 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev


# v4l-info

### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
driver                  : "uvcvideo"
card                    : "USB2.0 Camera"
bus_info                : "usb-0000:00:10.4-4"
version                 : 0.1.0
capabilities            : 0x4000001 [VIDEO_CAPTURE,STREAMING]

standards

inputs
    VIDIOC_ENUMINPUT(0)
index                   : 0
name                    : "Camera 1"
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
description             : "YUV 4:2:2 (YUYV)"
pixelformat             : 0x56595559 [YUYV]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
type                    : VIDEO_CAPTURE
fmt.pix.width           : 640
fmt.pix.height          : 480
fmt.pix.pixelformat     : 0x56595559 [YUYV]
fmt.pix.field           : NONE
fmt.pix.bytesperline    : 1280
fmt.pix.sizeimage       : 614400
fmt.pix.colorspace      : SRGB
fmt.pix.priv            : 0

controls
    VIDIOC_QUERYCTRL(BASE+0)
id                      : 9963776
type                    : INTEGER
name                    : "Brightness"
minimum                 : 0
maximum                 : 100
step                    : 1
default_value           : 50
flags                   : 0
    VIDIOC_QUERYCTRL(BASE+1)
id                      : 9963777
type                    : INTEGER
name                    : "Contrast"
minimum                 : 1
maximum                 : 5
step                    : 1
default_value           : 2
flags                   : 0
    VIDIOC_QUERYCTRL(BASE+2)
id                      : 9963778
type                    : INTEGER
name                    : "Saturation"
minimum                 : 0
maximum                 : 100
step                    : 1
default_value           : 50
flags                   : 0
    VIDIOC_QUERYCTRL(BASE+3)
id                      : 9963779
type                    : INTEGER
name                    : "Hue"
minimum                 : -10
maximum                 : 10
step                    : 1
default_value           : 0
flags                   : 0

### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
name                    : "USB2.0 Camera"
type                    : 0x1 [CAPTURE]
channels                : 1
audios                  : 0
maxwidth                : 0
maxheight               : 0
minwidth                : 48
minheight               : 32

channels
    VIDIOCGCHAN(0)
channel                 : 0
name                    : "Camera 1"
tuners                  : 0
flags                   : 0x0 []
type                    : CAMERA
norm                    : 0

tuner
ioctl VIDIOCGTUNER: Invalid argument

audio
ioctl VIDIOCGAUDIO: Invalid argument

picture
    VIDIOCGPICT
brightness              : 32768
hue                     : 32768
colour                  : 32768
contrast                : 16384
whiteness               : 43690
depth                   : 16
palette                 : YUYV

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


# dmesg | grep video
[    0.175174] pci 0000:00:01.0: Boot video device
[   11.351655] Linux video capture interface: v2.00
[   11.418808] via_v4l_drv: disagrees about version of symbol video_devdata
[   11.418817] via_v4l_drv: Unknown symbol video_devdata
[   11.419639] via_v4l_drv: disagrees about version of symbol video_unregister_device
[   11.419643] via_v4l_drv: Unknown symbol video_unregister_device
[   11.420101] via_v4l_drv: disagrees about version of symbol video_register_device
[   11.420106] via_v4l_drv: Unknown symbol video_register_device
[   11.421088] uvcvideo: Found UVC 1.00 device USB2.0 Camera (1871:0501)
[   11.422756] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   11.423917] usbcore: registered new interface driver uvcvideo
[   11.943994] via_v4l_drv: disagrees about version of symbol video_devdata
[   11.944042] via_v4l_drv: Unknown symbol video_devdata
[   11.944882] via_v4l_drv: disagrees about version of symbol video_unregister_device
[   11.944886] via_v4l_drv: Unknown symbol video_unregister_device
[   11.945296] via_v4l_drv: disagrees about version of symbol video_register_device
[   11.945300] via_v4l_drv: Unknown symbol video_register_device
[   89.435099] uvcvideo: Failed to query (130) UVC probe control : -32 (exp. 26).
[   89.435472] uvcvideo: Failed to query (130) UVC probe control : -32 (exp. 26).

---

### Post by no2498 on 2011-06-13
i seen this some time back hope it helps you


BicyclerBoy 
Skinny Soy Caramel Ubuntu

  
Join Date: Apr 2009
Location: Aotearoha
 Beans: 656 
 Ubuntu 10.04 Lucid Lynx 	Re: Webcam not working (Dell SP2208WFP) 
Try from terminal
rmmod uvcvideo
 modprobe uvcvideo
 dmseg

 Repeat these (<5) until the camera initialises okay..

 You could try this ppa to update some v4l components..

[https://launchpad.net/~libv4l/+archi...ilter=maverick](https://launchpad.net/~libv4l/+archi...ilter=maverick)


sudo rmmod uvcvideo
sudo modprobe uvcvideo

---

### Post by sj1410 on 2011-06-14
yes tried it, but the same, vgrabbj give me the following error


Device doesn't support width/height
There was no map allocated to be freed...

tried different width/hight

---

### Post by no2498 on 2011-06-14
set the size in cheese it is to have all the settings

or try guvcview

---

### Post by sj1410 on 2011-06-15
cheese quits with this error, either this cam or the driver is not allowing to set any format or change the size.

libv4l2: error setting pixformat: Input/output error
Segmentation fault

---

### Post by no2498 on 2011-06-15
install guvcview 

xawtv

wxcam

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)
you can get wxcam in a deb file 
just try 1 till it loads

first 1 finds the mic, guvcview

---

### Post by sj1410 on 2011-06-16
couldn't query device capabilities
make sure the device driver supports v4l2.,

cannot set device properties, blah blah blah blah .....

If anybody has a solution for it, or like to work on this, i am ready to pay.

swapnil.indore <at> gmail <dot> com

---

### Post by no2498 on 2011-06-16
in a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

---

