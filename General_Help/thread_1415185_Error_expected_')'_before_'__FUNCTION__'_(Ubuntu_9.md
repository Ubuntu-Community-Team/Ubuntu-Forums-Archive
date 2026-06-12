---
title: "Error: expected ')' before '__FUNCTION__' (Ubuntu 9.04/9.10)"
date: 2010-02-24
forum: General Help
---

### Post by UBCEngineer on 2010-02-24
Hello friendly Ubuntu users!

I am trying to compile some C files to control a FLI CCD camera in Ubuntu. I am using FLI [Software Development Kit]("http://www.flicamera.com/fli/software.asp") to do this. 

I managed to get the driver compiled and I inserted it into the kernel using the 'insmod.' command.

To operate the camera, I have to compile a library before I can actually send commands to the camera. When I 'make' the files, I get the following error:

> gcc -Wall -O2 -g  -I/home/nick/Desktop/FLI/libfli  -I/home/nick/Desktop/FLI/libfli/unix   -c -o libfli.o libfli.c
libfli.c: In function &#8216;FLIClose&#8217;:
libfli.c:243: error: expected &#8216;)&#8217; before &#8216;__FUNCTION__&#8217;
libfli.c:249: error: expected &#8216;)&#8217; before &#8216;__FUNCTION__&#8217;
libfli.c: In function &#8216;FLIOpen&#8217;:
libfli.c:529: error: expected &#8216;)&#8217; before &#8216;__FUNCTION__&#8217;
libfli.c:535: error: expected &#8216;)&#8217; before &#8216;__FUNCTION__&#8217;
libfli.c: In function &#8216;FLIGetStepsRemaining&#8217;:
libfli.c:1221: error: expected &#8216;)&#8217; before &#8216;__FUNCTION__&#8217;
libfli.c:1227: error: expected &#8216;)&#8217; before &#8216;__FUNCTION__&#8217;
libfli.c: In function &#8216;FLIStepMotorAsync&#8217;:
libfli.c:1273: error: expected &#8216;)&#8217; before &#8216;__FUNCTION__&#8217;
libfli.c:1279: error: expected &#8216;)&#8217; before &#8216;__FUNCTION__&#8217;
libfli.c: In function &#8216;FLIStepMotor&#8217;:
libfli.c:1307: error: expected &#8216;)&#8217; before &#8216;__FUNCTION__&#8217;
libfli.c:1313: error: expected &#8216;)&#8217; before &#8216;__FUNCTION__&#8217;
libfli.c: In function &#8216;FLIGetStepperPosition&#8217;:
libfli.c:1341: error: expected &#8216;)&#8217; before &#8216;__FUNCTION__&#8217;
libfli.c:1347: error: expected &#8216;)&#8217; before &#8216;__FUNCTION__&#8217;
libfli.c: In function &#8216;FLIHomeFocuser&#8217;:
libfli.c:1368: error: expected &#8216;)&#8217; before &#8216;__FUNCTION__&#8217;
libfli.c:1374: error: expected &#8216;)&#8217; before &#8216;__FUNCTION__&#8217;
libfli.c: In function &#8216;FLIGetFocuserExtent&#8217;:
libfli.c:1396: error: expected &#8216;)&#8217; before &#8216;__FUNCTION__&#8217;
libfli.c:1402: error: expected &#8216;)&#8217; before &#8216;__FUNCTION__&#8217;
libfli.c: In function &#8216;FLIReadTemperature&#8217;:
libfli.c:1426: error: expected &#8216;)&#8217; before &#8216;__FUNCTION__&#8217;
libfli.c:1432: error: expected &#8216;)&#8217; before &#8216;__FUNCTION__&#8217;I have tried doing this on two different computers, one runnings Ubuntu 9.04 x64, and one running Ubuntu 9.10 x86. 

I am certain that there are not any errors within the code, as it has worked for other people. From what I've read online, this might be a compiler problem, but I'm not sure how to fix it.

I do have the GCC and G++ compilers installed, as well as the general C/C++ packages.

Any suggestions or help would be greatly appreciated! :D

---

### Post by Javio on 2010-06-14
Hi,

the problem you are experiencing can be solved by commenting the line 60:

#define SHOWFUNCTIONS

this line is used only in debug mode and is useless to compile correctly.

But I suppose you will have a lot of other problems compiling so I give you the code patched for Ubuntu 10.04 LTS. You can see all the changes I have done by editing fli-dist-1.71-Javio.patch wich is in the unzipped root directory. Don't forget to install cfitsio libs to manage fits images. I have used cfitsio3250.tar.gz to compile my patched fli-dist. I hope this will help you.

Saludos

Javio

---

### Post by Himbeertoni on 2011-12-20
Hi Ubuntu group,

we would like to use FLI Grab on Ubuntu as well. However, this is a measurement PC in our lab and no one in our group is familiar with compiling of drivers. It would be great, if someone can give us help here:

We are running Ubuntu 8.04 (Hardy Heron).
The distributor of our camera gave us the fli-dist-1.71.tgz

When I type the "make" command in the extracted folder, I get the following error:
> jpkroot@A0040:~/Desktop/fli-dist-1.71/fliusb$ make
make -C /lib/modules/2.6.24-30-generic/build SUBDIRS=/home/jpkroot/Desktop/fli-dist-1.71/fliusb modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-30-generic'
  CC [M]  /home/jpkroot/Desktop/fli-dist-1.71/fliusb/fliusb.o
/home/jpkroot/Desktop/fli-dist-1.71/fliusb/fliusb.c: In function ‘fliusb_sg_bulk_read’:
/home/jpkroot/Desktop/fli-dist-1.71/fliusb/fliusb.c:322: error: ‘struct scatterlist’ has no member named ‘page’
/home/jpkroot/Desktop/fli-dist-1.71/fliusb/fliusb.c:330: error: ‘struct scatterlist’ has no member named ‘page’
/home/jpkroot/Desktop/fli-dist-1.71/fliusb/fliusb.c:335: error: ‘struct scatterlist’ has no member named ‘page’
/home/jpkroot/Desktop/fli-dist-1.71/fliusb/fliusb.c:343: error: ‘SLAB_KERNEL’ undeclared (first use in this function)
/home/jpkroot/Desktop/fli-dist-1.71/fliusb/fliusb.c:343: error: (Each undeclared identifier is reported only once
/home/jpkroot/Desktop/fli-dist-1.71/fliusb/fliusb.c:343: error: for each function it appears in.)
make[2]: *** [/home/jpkroot/Desktop/fli-dist-1.71/fliusb/fliusb.o] Error 1
make[1]: *** [_module_/home/jpkroot/Desktop/fli-dist-1.71/fliusb] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-30-generic'
make: *** [module] Error 2


Regards,

Manuel

---

