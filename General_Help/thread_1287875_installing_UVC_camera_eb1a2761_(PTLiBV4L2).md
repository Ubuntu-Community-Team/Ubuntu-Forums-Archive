---
title: "installing UVC camera eb1a:2761 (PTLiB/V4L2)"
date: 2009-10-10
forum: General Help
---

### Post by alexboybkk on 2009-10-10
Hello to all. I am new to Ubuntu and this forum. Can someone please help? i am trying to install my webcam on my laptop. My webcam is: UVC camera eb1a:2761 (PTLib/V4L2)

other infos are: eMPIA 2761 EmPIA technology.

EeePC 701 integrated webcam.

I am trying to use Kmess or Skype in order to chat et but these programs do not detect or activate my webcam.

I have tried Ekiga which seems to 'see' the camera but i still cannot activate it.

i would appreciate some good advices.

thanks to all in advance. 

alexboy:)

---

### Post by delcypher on 2009-10-10
First make sure your computer has detected your webcam, run
```
dmesg | grep uvc
```

You should see something like
```
[   10.170878] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a4)
[   10.194967] usbcore: registered new interface driver uvcvideo

```

If you don't see anything then you may need some extra driver to get your camera working (I don't know much about that so I can't really help you there).

If you did see something then let's carry on

A good tool for testing webcams is luvcview, you can install it by running
```
sudo aptitude install luvcview
```

once installed see what video devices you have, run
```
ls /dev/video*
```

I have /dev/video0 so now I can test my webcam using luvcview, run
```
luvcview -d /dev/video0
```
where /dev/video0 is the video device you found.

I found a webcam on my laptop didn't like this command once, you can try instead
```
luvcview -d /dev/video0 -f yuv
``` or
```
luvcview -d /dev/video0 -f uyvy
```

If none of this works have you looked at [https://help.ubuntu.com/community/Webcam]("https://help.ubuntu.com/community/Webcam") ?

---

