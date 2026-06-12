---
title: "no webcam: /dev/video0 not found"
date: 2010-09-17
forum: General Help
---

### Post by JohnnyC35 on 2010-09-17
Hey, I have been tryin to get my webcam working  for about half the day, It's a Logitech Messenger. I have looked thru  the ubuntuforums, and Google and I am still stumped.
When I try to  view the webcam in Cheese I am told that the device isn't found. wxcam  gives me '/dev/video0: No such device or address' .
I have tried  running 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so ' with cheese and with  wxcam at the end. I have checked to make sure I am part of the video  group. I have tried changing the permissions so that others have full  access to video0 . 
ummm... what else...
I have gstreamer  good/bad/ugly/10 installed. in gstreamer-properties I have access to  Video for Linux and Video for Linux 2, as well as test and custom.  custom doesn't do anything useful. Test is just that. and V4L(2) tells  me it can't read/write /dev/video0 . I have checked that any and all  libv4l* is installed via synaptic. 
xawtv gives me:
> 
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.32-24-generic)
xinerama 0: 1920x1080+0+0
WARNING: No DGA direct video mode for this display.
can't open /dev/video0: No such device or address
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such device or address
v4l2: open /dev/video0: No such device or address
v4l: open /dev/video0: No such device or address
no video grabber device available
sudo  modprobe gspca is giving me "FATAL: Module gspca not found." but I  haven't found a package to install it. or be able to work around it.
and I will post 'sudo modprobe -l | grep gsp' at the end as it is a long list.
Does  anyone else have any idea what else I can do?  It use to work under Ubuntu before, I have  Peppermint One installed. I posted this issue there also but their forum has a smaller community than this forum and as Peppermint is based on Ubuntu...  Thanks everyone.
and here is the grep gsp:
> 
kernel/drivers/media/video/gspca/gspca_main.ko
kernel/drivers/media/video/gspca/gspca_conex.ko
kernel/drivers/media/video/gspca/gspca_etoms.ko
kernel/drivers/media/video/gspca/gspca_finepix.ko
kernel/drivers/media/video/gspca/gspca_jeilinj.ko
kernel/drivers/media/video/gspca/gspca_mars.ko
kernel/drivers/media/video/gspca/gspca_mr97310a.ko
kernel/drivers/media/video/gspca/gspca_ov519.ko
kernel/drivers/media/video/gspca/gspca_ov534.ko
kernel/drivers/media/video/gspca/gspca_pac207.ko
kernel/drivers/media/video/gspca/gspca_pac7311.ko
kernel/drivers/media/video/gspca/gspca_sn9c20x.ko
kernel/drivers/media/video/gspca/gspca_sonixb.ko
kernel/drivers/media/video/gspca/gspca_sonixj.ko
kernel/drivers/media/video/gspca/gspca_spca500.ko
kernel/drivers/media/video/gspca/gspca_spca501.ko
kernel/drivers/media/video/gspca/gspca_spca505.ko
kernel/drivers/media/video/gspca/gspca_spca506.ko
kernel/drivers/media/video/gspca/gspca_spca508.ko
kernel/drivers/media/video/gspca/gspca_spca561.ko
kernel/drivers/media/video/gspca/gspca_sq905.ko
kernel/drivers/media/video/gspca/gspca_sq905c.ko
kernel/drivers/media/video/gspca/gspca_sunplus.ko
kernel/drivers/media/video/gspca/gspca_stk014.ko
kernel/drivers/media/video/gspca/gspca_t613.ko
kernel/drivers/media/video/gspca/gspca_tv8532.ko
kernel/drivers/media/video/gspca/gspca_vc032x.ko
kernel/drivers/media/video/gspca/gspca_zc3xx.ko
kernel/drivers/media/video/gspca/m5602/gspca_m5602.ko
kernel/drivers/media/video/gspca/stv06xx/gspca_stv06xx.ko
kernel/drivers/media/video/gspca/gl860/gspca_gl860.ko
Also, I tried compiling gspca but it errored out

> 
 REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
    .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
    *.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

 LOAD gspca in memory 
FATAL: Module gspca not found.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/john/Desktop/gspca CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/john/Desktop/gspca/gspca_core.o
/home/john/Desktop/gspca/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
In file included from /home/john/Desktop/gspca/gspca_core.c:845:
/home/john/Desktop/gspca/utils/spcausb.h: In function 'spca5xxRegRead':
/home/john/Desktop/gspca/utils/spcausb.h:95: error: implicit declaration of function 'info'
/home/john/Desktop/gspca/utils/spcausb.h: In function 'spca_set_interface':
/home/john/Desktop/gspca/utils/spcausb.h:278: error: implicit declaration of function 'warn'
In file included from /home/john/Desktop/gspca/gspca_core.c:853:
/home/john/Desktop/gspca/Sunplus-jpeg/sp5xxfw2.h: In function 'sp5xxfw2_init':
/home/john/Desktop/gspca/Sunplus-jpeg/sp5xxfw2.h:122: error: called object 'info' is not a function
/home/john/Desktop/gspca/Sunplus-jpeg/sp5xxfw2.h:136: error: called object 'info' is not a function
/home/john/Desktop/gspca/Sunplus-jpeg/sp5xxfw2.h:141: error: called object 'info' is not a function
/home/john/Desktop/gspca/Sunplus-jpeg/sp5xxfw2.h:148: error: called object 'info' is not a function
/home/john/Desktop/gspca/Sunplus-jpeg/sp5xxfw2.h:176: error: called object 'info' is not a function
/home/john/Desktop/gspca/Sunplus-jpeg/sp5xxfw2.h: In function 'sp5xxfw2_start':
/home/john/Desktop/gspca/Sunplus-jpeg/sp5xxfw2.h:214: error: called object 'info' is not a function
/home/john/Desktop/gspca/Sunplus-jpeg/sp5xxfw2.h:230: error: called object 'info' is not a function
/home/john/Desktop/gspca/gspca_core.c: In function 'spca5xx_ioctl':
/home/john/Desktop/gspca/gspca_core.c:2463: error: implicit declaration of function 'video_usercopy'
/home/john/Desktop/gspca/gspca_core.c: At top level:
/home/john/Desktop/gspca/gspca_core.c:2609: error: unknown field 'owner' specified in initializer
/home/john/Desktop/gspca/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/john/Desktop/gspca/gspca_core.c:2611: error: unknown field 'type' specified in initializer
/home/john/Desktop/gspca/gspca_core.c:2615: warning: initialization from incompatible pointer type
/home/john/Desktop/gspca/gspca_core.c: In function 'spca50x_create_sysfs':
/home/john/Desktop/gspca/gspca_core.c:2769: error: implicit declaration of function 'video_device_create_file'
/home/john/Desktop/gspca/gspca_core.c:2780: error: implicit declaration of function 'video_device_remove_file'
/home/john/Desktop/gspca/gspca_core.c: In function 'spca5xx_probe':
/home/john/Desktop/gspca/gspca_core.c:4301:  error: incompatible types when assigning to type 'struct device' from  type 'struct device *'
make[2]: *** [/home/john/Desktop/gspca/gspca_core.o] Error 1
make[1]: *** [_module_/home/john/Desktop/gspca] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [default] Error 2


---

### Post by llamabr on 2010-09-17
I don't know anything about that webcam.  But here's good advice.  if it's not listed as a webcam that's well supported by ubuntu, don't waste your time trying to set it up.  Find one that you know is supported, spend the 15 dollars, plug it in, and you're done.  You'll spend the next week trying to make some random webcam work, and you will fail.

Please let me save you a future wasted week.  Spend the 15 dollars.

---

### Post by JohnnyC35 on 2010-09-17
I would but I'm stuck in 'it use to work' world atm. so I'm going to fight the darn thing atm :P heh

---

### Post by no2498 on 2010-09-18
if it works in gstreamer-properties

it should work in cheese

did you try this in a terminal
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 


is a how to make it come on  but it was for skype and i do not use skype

---

### Post by DarthScape on 2010-09-18
Have you tried the camera with any other computer or os? you said it used to work, it could still be the hardware...

---

### Post by JohnnyC35 on 2010-09-18
ya it use to work. I had Ubuntu 9.10 or 10.04 on here a couple months ago and it worked. It could be the hardware though you are right. The webcam was bought ... in the early 90's. heh.
doing "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese" doesn't help, it still doesn't see it. neither does going into gstreamer-properties and trying the 2 available gives "Device "/dev/video0" does not exist." and it does exist. Here's the terminal info
```

john@mediabuntu ~ $ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc1]

```I am hoping I will have time tomorrow, I am going to install Ubuntu on a usb stick and if the webcam works, see what files are in play to make it work and see if I can get them into Peppermint.

---

### Post by JohnnyC35 on 2010-09-20
well after trying a few distributions and a few different usb ports I  think I can say that my poor 15 year old webcam has now bit the big one.  Thanks for the help :)

---

### Post by Quackers on 2010-09-20
My laptop webcam used to work in both 32 bit and 64 bit in Ubuntu. After several updates it works in neither version now and it isn't even recognised at all now (a couple of lines appear at boot saying that the uvc device is not initialised). 
Go figure :-)

---

### Post by no2498 on 2010-09-20
did you try v4l2
and click the bottom test ?

---

### Post by JohnnyC35 on 2010-09-20
yep. tried all 3, and custom. no joy :(

---

### Post by defishguy on 2010-09-20
I have a Dell M1330 with a camera that worked perfectly until Lucid.  After the install I had to install linux-firmware from the repos to make the camera work.

> sudo apt-get install linux-firmware

---

### Post by JohnnyC35 on 2010-09-20
> **defishguy said:**
> I have a Dell M1330 with a camera that worked perfectly until Lucid.  After the install I had to install linux-firmware from the repos to make the camera work.

thanks for the idea but that's installed already. :S

---

### Post by no2498 on 2010-09-21
try the cam with/in xawtv

---

### Post by tango_ninja on 2010-11-13
I'm having the save sort of problem [here]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=10112144") with no video0.  I'll be monitoring this thread for any possible solutions so please don't be shy with ideas!  If I get anywhere on my problem I will be sure to post a message here.

---

### Post by no2498 on 2010-11-15
this is a linux/ubuntu problem
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'

i get all the rest of them
your not getting the dev's set
no video or audio 

send a note to CHEESE
they have all the webcam settings now days

---

### Post by no2498 on 2010-11-15
as a matter of fact my 2 cams just went to heck a few weeks ago
all brown and cant change any settings in any program
ill get off the soap box
this is on 2 computers 1 804 1 10.04

---

