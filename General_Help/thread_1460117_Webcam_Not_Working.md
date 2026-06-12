---
title: "Webcam Not Working"
date: 2010-04-22
forum: General Help
---

### Post by ambdeep on 2010-04-22
I just got the HP Mobile Conference 1.3 MP Webcam(Targus AVC04PA). I cant get it to work on ubuntu with the help of any software and there seems to be no help regarding the same online....when i run cheese via the terminal i get the following output....please help....
```
libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: fill_nbits error: need 2 more bits

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: fill_nbits error: need 2 more bits

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: fill_nbits error: need 3 more bits

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

```

---

### Post by ambdeep on 2010-04-22
*bump*

---

### Post by ambdeep on 2010-04-22
i have been surfing the net reading about this topic.....i guess i need a new codec although ive installed all gstreamer plugins....any ideas?

---

### Post by no2498 on 2010-04-22
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

try the cam in cheese
if cheese brakes it come back do it over
try it in ekiga softphone
find a program that you can use the cam with like wxcam

---

### Post by ambdeep on 2010-04-23
u tried all the different combinations of settings....still no result....but i am getting a very dull b/w output on ekiga(which i was getting before doing the settings any ways)....i tried to run it on vlc but i get a black screen.....but it runs fine on windows vlc......so im stuck now.....

---

### Post by gradinaruvasile on 2010-04-23
First: when you have issues, please provide kernel ubuntu + kernel version. This is probably related to the webcam drivers.

Try this (in terminal):

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

And see here:

[https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/502866](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/502866)

---

### Post by ambdeep on 2010-04-23
> **gradinaruvasile said:**
> First: when you have issues, please provide kernel ubuntu + kernel version. This is probably related to the webcam drivers.
srry abt that....im using ubuntu 9.10 and kernel 2.6.31-21-generic
ive already tried the command u gave me.....it gives the same error....thanks for the link on the bug though.....it looks a lot similar to my problem.....
if you are aware of any solution please help.....
ive also tried a lot of different programs and i dont get an output on any of them exept for ekiga where i get a very dull b/w output.....

---

### Post by ambdeep on 2010-04-23
Here is the output i get with ekiga.....all other software give an error or a black screen...

---

### Post by ambdeep on 2010-04-23
ive found a software which helps me fix the ekiga output but im not able to run the webcam on any other program.....the name of the software package is luvcview....can some one please help me work the webcam on other software....also im getting a weird border around the output.....is there a way of removing that?
Here is a snapshot of the new output after using luvcview...

---

### Post by ambdeep on 2010-04-23
ok....i think i got the problem....the video output is set to BA81...all the other programs need a jepg output....when i change it in guvcview(which changes the VIDIOCGPICT settings) it crashes....after that when i open any other program....the first frame is captured and the i get an error....so now the question is how can i change the output to jepg and keep it that way for other programs to work.....

---

### Post by no2498 on 2010-04-23
hope you can get this installed wxcam
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

read and install all that page tells you to

also try, guvcview  should be in your add & remove
hope this helps

---

