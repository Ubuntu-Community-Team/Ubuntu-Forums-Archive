---
title: "Cannot get Skype working properly"
date: 2009-10-11
forum: General Help
---

### Post by Rick Abraham on 2009-10-11
Hi guys I have downloaded Skype and installed it.
When I connect to my mates I can see and hear them fine.
But my webcam isnt working or my microphone ??????????????
And I dont know why can anyone help me ?

I am using a Logitech QuickCam V11.1
and just a basic mic that plugs into the microphone port

---

### Post by Rick Abraham on 2009-10-12
When I go to the terminal and type the command $ lsusb 
I get the following

Bus 001 Device 007: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 006: ID 0461:4d15 Primax Electronics, Ltd 
Bus 001 Device 004: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 050d:805c Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:08af Logitech, Inc. QuickCam Easy/Cool
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:5112 Dell Computer Corp. Photo AIO Printer 924
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

As you can see the Logitech QuickCam is there but not sure why Skype wont pick it up.
Do I need to install drivers and if so where can I get them ??

---

### Post by rb0171610 on 2009-10-12
> **Rick Abraham said:**
> When I go to the terminal and type the command $ lsusb 
I get the following

Bus 001 Device 007: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 006: ID 0461:4d15 Primax Electronics, Ltd 
Bus 001 Device 004: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 050d:805c Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:08af Logitech, Inc. QuickCam Easy/Cool
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:5112 Dell Computer Corp. Photo AIO Printer 924
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

As you can see the Logitech QuickCam is there but not sure why Skype wont pick it up.
Do I need to install drivers and if so where can I get them ??

which version  of Ubuntu are you using? also lsmod command can give you a list of the currently running modules. Example with output:
[I]$ lsmod | grep video
video                  25872  0
output                 11008  1 video
uvcvideo               63368  0
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev[/I]
Also, are you able to record sound with other applications? Sound recorder, etc?  
Try installing cheese, a webcam utility and making sure that your webcam is recognized and the drivers are installed.

---

### Post by rb0171610 on 2009-10-12
> **Rick Abraham said:**
> Hi guys I have downloaded Skype and installed it.
When I connect to my mates I can see and hear them fine.
But my webcam isnt working or my microphone ??????????????
And I dont know why can anyone help me ?

I am using a Logitech QuickCam V11.1
and just a basic mic that plugs into the microphone port
You can also use the command line to quickly search for packages related to webcams.  I know that camorama in the list will also work if you cannot see your cam when you open cheese.
[I]$ sudo apt-cache search webcam                                                                                                                        
[sudo] password for rob:                                                                                                                                       
came - Rewrite of the xawtv webcam app using imlib2                                                                                                            
cameramonitor - Webcam monitoring in system tray                                                                                                               
camgrab - A command line tool to download a single image from a webcam
camorama - gnome utility to view and save images from a webcam
camstream - collection of tools for webcams and other video-devices
camstream-doc - documentation for CamStream
cheese - A tool to take pictures and videos from your webcam
feh - imlib2 based image viewer
geekast - GNOME interface to peercast
geekast-binary - GNOME interface to peercast - binaries
gkrellkam - GKrellM plugin that displays a periodically updating image
gmotionlive - A simple multipart/x-mixed-replace viewer
gqcam - GTK Webcam control
gspca-source - source for the gspca v4l kernel module
libdecodeqr-dev - A C/C++ library for decoding QR code
libdecodeqr-examples - Sample program in C/C++ library for decoding QR code
libdecodeqr0 - A C/C++ library for decoding QR code
luvcview - USB Video Class grabber
lynkeos.app - Tool to process planetary astronomical images for GNUstep
motion - V4L capture program supporting motion detection
ov51x-jpeg-source - Source for the ov51x-jpeg driver
peercast-geekast - GNOME interface to peercast - peercast-servent data files
pymissile - Control Marks and Spencer USB Missile Launcher
pyrocket - control Striker II and Dream Cheeky USB Missile Launchers
qc-usb-source - source for the QuickCam Express driver
qc-usb-utils - utility programs for the QuickCam Express driver
setpwc - program to set and query settings of (mainly) Philips WebCams
telak - display remote or local pictures on your desktop
uvccapture - USB UVC Video Class snapshot software
vgrabbj - grabs a image from a camera and puts it in jpg/png format
webcam - image grabber and uploader
webcam-server - a tool to share webcam streaming in www-browser
webcamd - Capture images from video devices
zebra-tools - scanning and decoding bar codes (utilities)
[/I]

---

### Post by Rick Abraham on 2009-10-12
thanks rob, i am using ubuntu 9.04. 
I sorta follow what your telling me.

What apps exactly did you say i need to install to try and get my webcam working ?

---

