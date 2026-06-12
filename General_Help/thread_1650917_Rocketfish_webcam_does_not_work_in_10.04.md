---
title: "Rocketfish webcam does not work in 10.04"
date: 2010-12-22
forum: General Help
---

### Post by Pollyanna1 on 2010-12-22
Any one has the driver for rocketfish webcam and microphone?

here is the result of lsusb

```
Bus 001 Device 025: ID 0c45:6288 Microdia PC Camera with Microphone (SN9C202 + OV9655)

```

---

### Post by Kirboosy on 2010-12-22
Hi there! :)

Try running the following command in Terminal (Applications --> Accessories--> Terminal) and see if the webcam appears there.

**gstreamer-properties**         '(you might have to sudo it. I don't remember)

I have an older logitech USB cam and it wouldn't work until I entered gstreamer-properties

---

### Post by no2498 on 2010-12-22
just a bit more info for you

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

---

### Post by Pollyanna1 on 2010-12-22
I tried both v4l1 and v4l2 ,  I can see the device on v4I2 but when I press test button I got this message on the terminal and I could not see any result from the test ....

```
libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: fill_nbits error: need 2 more bits

```

---

### Post by Pollyanna1 on 2010-12-22
Is what I am looking for in this page??

[http://cateee.net/lkddb/web-lkddb/USB_GSPCA_SN9C20X.html](http://cateee.net/lkddb/web-lkddb/USB_GSPCA_SN9C20X.html) and the driver is on this link

[http://lxr.linux.no/#linux+v2.6.36/drivers/media/video/gspca/sn9c20x.c](http://lxr.linux.no/#linux+v2.6.36/drivers/media/video/gspca/sn9c20x.c)

if yes how can I use it???

---

### Post by Kirboosy on 2010-12-23
> **Pollyanna1 said:**
> I tried both v4l1 and v4l2 ,  I can see the device on v4I2 but when I press test button I got this message on the terminal and I could not see any result from the test ....

```
libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: fill_nbits error: need 2 more bits

```

I'm not really sure why its giving this error. Could it be that you don't have the ubuntu-restricted extras installed?

---

### Post by Pollyanna1 on 2010-12-23
I just did install  ubuntu-restricted extras and it gave me the same result... Is their any driver I need to install???

---

### Post by Kirboosy on 2010-12-23
I don't remember having to install any drivers like that...I also used a logitech so I really can't compare the results. 'Cheese' might have some documentationthat will be useful.

It doesn't prompt you to install any Restricted Device drivers right? (You can manually check under System-->Administration-->Hardware Drivers) 

If it doesn't pop up in there no big deal. I'm just throwing out any ideas that come to my head.

---

### Post by Pollyanna1 on 2010-12-24
thanks Caboose885 for your help... 
 
> It doesn't prompt you to install any Restricted Device drivers right?
 
No, I was just asking...

---

### Post by no2498 on 2010-12-24
type webcam
in a terminal click enter
did it load xawtv ? as a webcam grabber
if yes try the cam in cheese
in  gstreamer-properties
try changing the plugin 
and click the bottom test

---

### Post by Pollyanna1 on 2010-12-24
this is what I got when I typed webcam after installing it by sudo apt-get install webcam

```

reading config file: /home/{user-name}/.webcamrc
video4linux webcam v1.5 - (c) 1998-2002 Gerd Knorr
grabber config:
  size 320x240 [none]
  input (null), norm (null), jpeg quality 75
  rotate=0, top=0, left=0, bottom=240, right=320

```

---

### Post by Pollyanna1 on 2010-12-24
Also when i ran cheese I got this error in the terminal...

```
libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: error: more then 63 AC components (66) in huffman unit

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: fill_nbits error: need 3 more bits

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: error: more then 63 AC components (68) in huffman unit

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: error: more then 63 AC components (68) in huffman unit

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: error: more then 63 AC components (66) in huffman unit

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

libv4l2: error got 10 consecutive frame decode errors, last error: v4l-convert: error decompressing JPEG: unknown huffman code: 0000ffff

```

---

### Post by no2498 on 2010-12-25
this may help

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

put in a terminal

or this 1

LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so cheese

---

### Post by Pollyanna1 on 2010-12-26
> **no2498 said:**
> this may help

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

put in a terminal

or this 1

LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so cheese

I open cheese program but nothing comes from the camera... 

BTW, when I ran gstreamer-properties I got this message and the properties windows opened 

```

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

```

---

### Post by no2498 on 2010-12-27
this is all common

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

you can do it this way and not see all that


click system, preferences
go down the list to multimedia systems selector, start it click video
try v4l and v4l2 click the bottom test button for each 1


btw did your cam come on in gstreamer-properties

---

### Post by Pollyanna1 on 2010-12-27
> **no2498 said:**
> 

btw did your cam come on in gstreamer-properties

yes I can see USB20 Camera when I select V4l2, also when I ran Sound Preferences I can see  PC Camera with Microphone (SN9C202 + OV9655) and I can see the sound level moves, which means ubuntu recognize the microphone and the camera!!!

---

### Post by no2498 on 2010-12-27
no did you see yourself on cam if not

take the # and name google it to see what driver you need

---

### Post by Pollyanna1 on 2010-12-27
> **no2498 said:**
> no did you see yourself on cam if not

take the # and name google it to see what driver you need

no I don't .. 
What # and name?

---

### Post by no2498 on 2010-12-29
in a terminal type lsusb click enter

you should see a number and a name for your cam

---

### Post by Pollyanna1 on 2010-12-29
Thanks no2498 for your help... 

I found this site [http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7](http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7)  with the driver for my camera but I think it works only under ubuntu 7.10 because when I ran this driver I got an error message when I install the .deb file

```
Error: Dependency is not satisfiable: linux-image-generic (= 2.6.20.16.28.1)
```

*BTW ...  linux-image-generic is installed*

---

### Post by no2498 on 2010-12-30
try this program wxcam if your not using 64 bit only

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

it comes in a deb file also

i have better luck with it myself

---

### Post by Pollyanna1 on 2010-12-31
I did install it but also gives me this error

```
Error: Dependency is not satisfiable: libwxbase2.8-0 (>= 2.8.11.0)
```

and I have libwxbase 2.8-0 installed

---

### Post by no2498 on 2010-12-31
try 1 till it loads 
i have 1.0.6
using ubuntu 10.04

i just liuke to see your cam run/come up

---

### Post by no2498 on 2011-01-02
try get deb


[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)

---

### Post by Pollyanna1 on 2011-01-02
Hey Happy new Year ..............


I do not know how it works but the last software I installed it was DeVeDe and I tried the camera in chees after that and it works ..... YEHOOOOOO (I know it does not make any sense but it wokrs..)..  Thank you every body for all your help...

---

### Post by Kirboosy on 2011-01-03
Good. Now you can make the thread as solved. ;)

---

