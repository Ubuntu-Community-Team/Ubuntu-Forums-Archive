---
title: "Undefined resource with make"
date: 2012-04-28
forum: General Help
---

### Post by enabulator on 2012-04-28
REPOSTED IN: Packaging and Compiling. THIS CAN BE DELETED. I DON'T KNOW HOW TO, OR IF I CAN. THANK YOU FOR LOOKING.

Hi - I was trying to install software (dfu-programmer) from source to fix my arduino:[http://arduino.cc/forum/index.php/topic,92148.msg692355.html#msg692355]("http://arduino.cc/forum/index.php/topic,92148.msg692355.html#msg692355"). It is from source so that I can change it for my 16u2 instead of 8u2.

THE PROBLEM: I think I modified the source OK, but after I ```
./boostrap.sh
``` and ```
./configure
```, and then try to ```
make
``` I get errors:

```

...
...
...
dfu.o: In function `dfu_device_init':
/home/paul/Desktop/dfu-programmer-0.5.4/src/dfu.c:419: undefined reference to `libusb_claim_interface'
/home/paul/Desktop/dfu-programmer-0.5.4/src/dfu.c:436: undefined reference to `libusb_release_interface'
/home/paul/Desktop/dfu-programmer-0.5.4/src/dfu.c:426: undefined reference to `libusb_free_device_list'
dfu.o: In function `dfu_make_idle':
/home/paul/Desktop/dfu-programmer-0.5.4/src/dfu.c:814: undefined reference to `libusb_reset_device'
dfu.o: In function `dfu_device_init':
/home/paul/Desktop/dfu-programmer-0.5.4/src/dfu.c:431: undefined reference to `libusb_free_device_list'
collect2: ld returned 1 exit status
make[2]: *** [dfu-programmer] Error 1
make[2]: Leaving directory `/home/paul/Desktop/dfu-programmer-0.5.4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/paul/Desktop/dfu-programmer-0.5.4'
make: *** [all] Error 2

```

When searching online for an answer I think it might have something to do with headers or linking or pkg-config. I don't have much experience with C (if it's even the issue- the file extensions in the folder have .c and .h). In case this helps you help me:
```
paul@paul-laptop:~/Desktop/dfu-programmer-0.5.4$ pkg-config --cflags libusb-1.0
-I/usr/include/libusb-1.0  
paul@paul-laptop:~/Desktop/dfu-programmer-0.5.4$ pkg-config --libs libusb-1.0

-lusb-1.0
```


I spent hours try to get my board working yesterday. I even tried using Windows. :) Does anyone know what's going on with the ```
make
```?

Thank you. :|

---

