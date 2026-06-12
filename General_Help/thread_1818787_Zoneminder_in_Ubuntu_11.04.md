---
title: "Zoneminder in Ubuntu 11.04"
date: 2011-08-05
forum: General Help
---

### Post by bo.vestergaard on 2011-08-05
Has anyone got Zoneminder working in Ubuntu 11.04 with a USB camera? I had it running in 10.04 but I cannot get it working in 11.04. If anyone out there got it working I would like to hear from them.

I run Ubuntu 11.04 Desktop on a Dell Dimension with a Logitech C200 webcam. I know the webcam is working because I can see use it in another applications such as XawTV but Zoneminder does not recognise it.

I have tried it both as V4L1 and V4L2.

Bo

---

### Post by HermanAB on 2011-08-05
Howdy,

Install 'cheese'.  That usually makes camera problems go away.

---

### Post by bo.vestergaard on 2011-08-05
Hello,

Thanks for the suggestion. I tried it but it ddn't make any difference. I can capture video in Cheese.

Bo

---

### Post by bo.vestergaard on 2011-08-05
Here is the output from zmu:

zmu -d /dev/video0 -q -v
Video Device: /dev/video0
General Capabilities
  Driver: uvcvideo
  Card: UVC Camera (046d:0802)
  Bus: usb-0000:02:09.2-3
  Version: 1.0.0
  Type: 0x4000001
    Supports video capture (X)
    Does not support video output
    Does not support frame buffer overlay
    Does not support VBI capture
    Does not support VBI output
    Does not support sliced VBI capture
    Does not support sliced VBI output
    Does not support video output overlay
    Does not have tuner
    Does not have audio in and/or out
    Does not have radio
    Does not support read/write i/o (X)
    Does not support async i/o
    Supports streaming i/o (X)
    Standards:
  Formats:
    YUV 4:2:2 (YUYV) (YUYV)
    MJPEG (MJPG)
Crop Capabilities
  Bounds: 640 x 480
  Default: 640 x 480
  Current: Cropping is not supported
Inputs: 1
  Input 0
    Name: Camera 1
    Type: Camera
    Audioset: 00000000
    Standards: 0x0
    Power on  (X)
    Signal detected  (X)
    Colour Signal detected 
    Horizontal Lock detected

---

### Post by bo.vestergaard on 2011-08-05
I got it partly working now. I did the following:

Changed the permissions on /dev/video0 to crw-rw-rw-+. I am not sure if this was necessary.

Changed the device from /dev/video to /dev/video0. For some reason Zoneminder by default uses /dev/video but in Ubuntu the first video device is /dev/video0. I remember in previous versions of Ubuntu there used to be a link called /dev/video which pointed at /dev/video0 but that does not appear to be there in 11.04

Changed the video format to YUYV. For some reason none of the others work.

Changed the resolution to 640x400. This is the strange one. The camera is 640x480 but when I set that resolution I get an error in the log file about shared memory and invalid argument. When I change the resolution to 640x400 it works, even though that is not the correct resolution for the camera. It cuts the top off the image but at least it works. I would like to get it working with the correct resolution because I want to monitor the top of the image. I attach the syslog for both resolutions so that you can see the difference. I am not much of a Linux expert so I would appreciate it if some of you guys can comment on this. I am not sure if the Shared Memory error is real or just some standard message because something else failed.

When it does NOT work at 640x480 the log file reads the following:

Aug  5 15:56:06 Desktop-Luton zmwatch[4051]: last message repeated 3 times
Aug  5 15:56:06 Desktop-Luton zmdc[4014]: INF [Command 'zmc -d /dev/video0' removed from pending list at 11/08/05 15:56:06]
Aug  5 15:56:06 Desktop-Luton zmdc[4014]: INF ['zmc -d /dev/video0' starting at 11/08/05 15:56:06, pid = 4081]
Aug  5 15:56:06 Desktop-Luton zmdc[4081]: INF ['zmc -d /dev/video0' started at 11/08/05 15:56:06]
Aug  5 15:56:06 Desktop-Luton zmc_dvideo0[4081]: INF [Debug Level = 0, Debug Log = <none>]
Aug  5 15:56:06 Desktop-Luton zmc_dvideo0[4081]: ERR [Can't shmget, probably not enough shared memory space free: Invalid argument]
Aug  5 15:56:06 Desktop-Luton zmdc[4014]: ERR ['zmc -d /dev/video0' exited abnormally, exit status 255]
Aug  5 15:56:06 Desktop-Luton zmdc[4014]: INF [Starting pending process, zmc -d /dev/video0]
Aug  5 15:56:06 Desktop-Luton zmdc[4014]: INF ['zmc -d /dev/video0' starting at 11/08/05 15:56:06, pid = 4084]
Aug  5 15:56:06 Desktop-Luton zmdc[4084]: INF ['zmc -d /dev/video0' started at 11/08/05 15:56:06]
Aug  5 15:56:06 Desktop-Luton zmc_dvideo0[4084]: INF [Debug Level = 0, Debug Log = <none>]
Aug  5 15:56:06 Desktop-Luton zmc_dvideo0[4084]: ERR [Can't shmget, probably not enough shared memory space free: Invalid argument]
Aug  5 15:56:06 Desktop-Luton zmdc[4014]: ERR ['zmc -d /dev/video0' exited abnormally, exit status 255]
Aug  5 15:56:06 Desktop-Luton zmdc[4014]: INF [Command 'zma -m 1' removed from pending list at 11/08/05 15:56:06]
Aug  5 15:56:07 Desktop-Luton zmdc[4014]: INF ['zma -m 1' starting at 11/08/05 15:56:07, pid = 4087]
Aug  5 15:56:07 Desktop-Luton zmdc[4087]: INF ['zma -m 1' started at 11/08/05 15:56:07]
Aug  5 15:56:07 Desktop-Luton zma_m1[4087]: INF [Debug Level = 0, Debug Log = <none>]
Aug  5 15:56:07 Desktop-Luton zma_m1[4087]: ERR [Can't shmget, probably not enough shared memory space free: Invalid argument]
Aug  5 15:56:07 Desktop-Luton zmdc[4014]: ERR ['zma -m 1' exited abnormally, exit status 255]
Aug  5 15:56:07 Desktop-Luton zmdc[4014]: INF [Starting pending process, zma -m 1]
Aug  5 15:56:07 Desktop-Luton zmdc[4014]: INF ['zma -m 1' starting at 11/08/05 15:56:07, pid = 4088]
Aug  5 15:56:07 Desktop-Luton zmdc[4088]: INF ['zma -m 1' started at 11/08/05 15:56:07]
Aug  5 15:56:07 Desktop-Luton zma_m1[4088]: INF [Debug Level = 0, Debug Log = <none>]
Aug  5 15:56:07 Desktop-Luton zma_m1[4088]: ERR [Can't shmget, probably not enough shared memory space free: Invalid argument]
Aug  5 15:56:07 Desktop-Luton zmdc[4014]: ERR ['zma -m 1' exited abnormally, exit status 255]
Aug  5 15:56:09 Desktop-Luton zmwatch[4051]: ERR [Can't get shared memory id '7a6d0001', 1: No such file or directory]
Aug  5 15:56:09 Desktop-Luton zmwatch[4051]: ERR [Can't get shared memory id '7a6d0001', 1: No such file or directory]
Aug  5 15:56:11 Desktop-Luton zmdc[4014]: INF [Starting pending process, zmc -d /dev/video0]
Aug  5 15:56:11 Desktop-Luton zmdc[4014]: INF ['zmc -d /dev/video0' starting at 11/08/05 15:56:11, pid = 4099]
Aug  5 15:56:11 Desktop-Luton zmdc[4099]: INF ['zmc -d /dev/video0' started at 11/08/05 15:56:11]
Aug  5 15:56:11 Desktop-Luton zmc_dvideo0[4099]: INF [Debug Level = 0, Debug Log = <none>]
Aug  5 15:56:11 Desktop-Luton zmc_dvideo0[4099]: ERR [Can't shmget, probably not enough shared memory space free: Invalid argument]
Aug  5 15:56:11 Desktop-Luton zmdc[4014]: ERR ['zmc -d /dev/video0' exited abnormally, exit status 255]
Aug  5 15:56:12 Desktop-Luton zmdc[4014]: INF [Starting pending process, zma -m 1]
Aug  5 15:56:12 Desktop-Luton zmdc[4014]: INF ['zma -m 1' starting at 11/08/05 15:56:12, pid = 4100]
Aug  5 15:56:12 Desktop-Luton zmdc[4100]: INF ['zma -m 1' started at 11/08/05 15:56:12]
Aug  5 15:56:12 Desktop-Luton zma_m1[4100]: INF [Debug Level = 0, Debug Log = <none>]
Aug  5 15:56:12 Desktop-Luton zma_m1[4100]: ERR [Can't shmget, probably not enough shared memory space free: Invalid argument]
Aug  5 15:56:12 Desktop-Luton zmdc[4014]: ERR ['zma -m 1' exited abnormally, exit status 255]
Aug  5 15:56:19 Desktop-Luton zmwatch[4051]: ERR [Can't get shared memory id '7a6d0001', 1: No such file or directory]
Aug  5 15:56:19 Desktop-Luton zmwatch[4051]: ERR [Can't get shared memory id '7a6d0001', 1: No such file or directory]
Aug  5 15:56:21 Desktop-Luton zmdc[4014]: INF [Starting pending process, zmc -d /dev/video0]
Aug  5 15:56:21 Desktop-Luton zmdc[4014]: INF ['zmc -d /dev/video0' starting at 11/08/05 15:56:21, pid = 4121]
Aug  5 15:56:21 Desktop-Luton zmdc[4121]: INF ['zmc -d /dev/video0' started at 11/08/05 15:56:21]
Aug  5 15:56:21 Desktop-Luton zmc_dvideo0[4121]: INF [Debug Level = 0, Debug Log = <none>]
Aug  5 15:56:21 Desktop-Luton zmc_dvideo0[4121]: ERR [Can't shmget, probably not enough shared memory space free: Invalid argument]
Aug  5 15:56:21 Desktop-Luton zmdc[4014]: ERR ['zmc -d /dev/video0' exited abnormally, exit status 255]
Aug  5 15:56:22 Desktop-Luton zmdc[4014]: INF [Starting pending process, zma -m 1]
Aug  5 15:56:22 Desktop-Luton zmdc[4014]: INF ['zma -m 1' starting at 11/08/05 15:56:22, pid = 4122]
Aug  5 15:56:22 Desktop-Luton zmdc[4122]: INF ['zma -m 1' started at 11/08/05 15:56:22]
Aug  5 15:56:22 Desktop-Luton zma_m1[4122]: INF [Debug Level = 0, Debug Log = <none>]
Aug  5 15:56:22 Desktop-Luton zma_m1[4122]: ERR [Can't shmget, probably not enough shared memory space free: Invalid argument]
Aug  5 15:56:22 Desktop-Luton zmdc[4014]: ERR ['zma -m 1' exited abnormally, exit status 255]


When it works at 640x400 the log file reads the following:
Aug  5 15:58:04 Desktop-Luton zmwatch[4051]: last message repeated 7 times
Aug  5 15:58:04 Desktop-Luton zmdc[4014]: INF [Command 'zmc -d /dev/video0' removed from pending list at 11/08/05 15:58:04]
Aug  5 15:58:05 Desktop-Luton zmdc[4014]: INF ['zmc -d /dev/video0' starting at 11/08/05 15:58:05, pid = 4143]
Aug  5 15:58:05 Desktop-Luton zmdc[4143]: INF ['zmc -d /dev/video0' started at 11/08/05 15:58:05]
Aug  5 15:58:05 Desktop-Luton zmc_dvideo0[4143]: INF [Debug Level = 0, Debug Log = <none>]
Aug  5 15:58:05 Desktop-Luton zmc_dvideo0[4143]: INF [Starting Capture]
Aug  5 15:58:05 Desktop-Luton zmdc[4014]: INF [Command 'zma -m 1' removed from pending list at 11/08/05 15:58:05]
Aug  5 15:58:05 Desktop-Luton zmc_dvideo0[4143]: WAR [Hue control is not supported]
Aug  5 15:58:05 Desktop-Luton zmdc[4014]: INF ['zma -m 1' starting at 11/08/05 15:58:05, pid = 4148]
Aug  5 15:58:05 Desktop-Luton zmdc[4148]: INF ['zma -m 1' started at 11/08/05 15:58:05]
Aug  5 15:58:05 Desktop-Luton zma_m1[4148]: INF [Debug Level = 0, Debug Log = <none>]
Aug  5 15:58:06 Desktop-Luton zma_m1[4148]: INF [In mode 3/1, warming up]
bo@Desktop-Luton:/dev$ 

Can anyone out there make any sense of these log files? Is it really running out of shared memory? If so, how do I increase it.

Thanks! Bo

---

### Post by bo.vestergaard on 2011-08-07
Yes, it was running out of shared memory. There is an explanation of that on the Zoneminer WIKI FAQ.

However, I reinstalled Ubuntu 11.04 and ZM but now I have a different problem. It does not register any alarms at all. No matter how much movement there is in front of the camera. I have tried the "Fast High Sensitivity" present but even that does not register anything. Has anyone seen that problem before?

---

