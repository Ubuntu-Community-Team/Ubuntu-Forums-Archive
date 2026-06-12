---
title: "mjpg_streamer ubuntu 11.10 64bit"
date: 2011-11-28
forum: General Help
---

### Post by Plasma_NZ on 2011-11-28
Solved - here's howto for Ubuntu 11.10 64bit mjpg_streamer

```
sudo apt-get install libjpeg62-dev
```
```
svn co https://mjpg-streamer.svn.sourceforge.net/svnroot/mjpg-streamer mjpg-streamer
```
```
cd /mjpg-streamer/mjpg-streamer/
```
```
make
```
```
sudo make install
```

Should compile, install and work as it should...

Big thanks to sevenmachines for the solution to this problem....


basically, trying to compile from source...


mjpg_streamer-r93/94 

Followed supplied install instructions...

Do a ```
make all clean
```

receive the following error

```
mjpg_streamer.c:27:28: fatal error: linux/videodev.h: No such file or directory
compilation terminated.
make: *** [mjpg_streamer.o] Error 1

```

Went looking for the file and found it, albeit a slightly different...

so im am assuming they mean this file which is located

```
/usr/include/linux/videodev2.h
```

so i edited the source file with the line containing the linux/videodev.h and changed it to linux/videodev2.h

then ran ```
make all clean
```

which made a difference... but now i have a different error 

```
mjpg_streamer.o: In function `signal_handler':
mjpg_streamer.c:(.text+0x107): undefined reference to `dlclose'
mjpg_streamer.c:(.text+0x12c): undefined reference to `dlclose'
mjpg_streamer.o: In function `main':
mjpg_streamer.c:(.text.startup+0x27c): undefined reference to `dlopen'
mjpg_streamer.c:(.text.startup+0x29c): undefined reference to `dlsym'
mjpg_streamer.c:(.text.startup+0x2bd): undefined reference to `dlsym'
mjpg_streamer.c:(.text.startup+0x2de): undefined reference to `dlsym'
mjpg_streamer.c:(.text.startup+0x2ff): undefined reference to `dlsym'
mjpg_streamer.c:(.text.startup+0x378): undefined reference to `dlopen'
mjpg_streamer.c:(.text.startup+0x395): undefined reference to `dlsym'
mjpg_streamer.c:(.text.startup+0x3b0): undefined reference to `dlsym'
mjpg_streamer.c:(.text.startup+0x3cb): undefined reference to `dlsym'
mjpg_streamer.c:(.text.startup+0x3e6): undefined reference to `dlsym'
mjpg_streamer.c:(.text.startup+0x532): undefined reference to `dlerror'
mjpg_streamer.c:(.text.startup+0x6f1): undefined reference to `dlerror'
mjpg_streamer.c:(.text.startup+0x839): undefined reference to `dlerror'
collect2: ld returned 1 exit status
make: *** [mjpg_streamer] Error 1

```

Not entirely sure what to do now...

---

### Post by Plasma_NZ on 2011-11-29
Went to the sourceforge page, found someone else with the same problem... but has been no help there...

---

### Post by SevenMachines on 2011-11-29
Ubuntu now passes --as-needed to the compiler, this means libraries in the Makefile of mjpg-streamer need to be moved. See
[http://ubuntuforums.org/showpost.php?p=11418489&postcount=2](http://ubuntuforums.org/showpost.php?p=11418489&postcount=2)

Look for the section defined there in the Makefile and make the changes, or possibly, in the source directory, this should work

```
$ sed -i 's/$(CC) $(CFLAGS) $(LFLAGS) $(OBJECTS) -o $(APP_BINARY)/$(CC) $(CFLAGS) $(OBJECTS) $(LFLAGS) -o $(APP_BINARY)/g' Makefile 

$ make
```

---

### Post by SevenMachines on 2011-11-29
Note, 
```
 $ make all
```to build everything
```
 $ make clean
```to clean up the source tree and remove built files, not both at the same time

Also, renaming include files to fix missing headers is generally likely to end in tears at some point, changing the names doesnt change the contents of the file after all :) I would recommend not making changes inside the system directories at all unless you know what you're doing

---

### Post by Plasma_NZ on 2011-11-29
> **SevenMachines said:**
> Ubuntu now passes --as-needed to the compiler, this means libraries in the Makefile of mjpg-streamer need to be moved. See
[http://ubuntuforums.org/showpost.php?p=11418489&postcount=2](http://ubuntuforums.org/showpost.php?p=11418489&postcount=2)

Look for the section defined there in the Makefile and make the changes, or possibly, in the source directory, this should work

```
$ sed -i 's/$(CC) $(CFLAGS) $(LFLAGS) $(OBJECTS) -o $(APP_BINARY)/$(CC) $(CFLAGS) $(OBJECTS) $(LFLAGS) -o $(APP_BINARY)/g' Makefile 

$ make
```

still have this pesky problem 

```

physics@physics:~/Downloads/mjpg-streamer-r63$ make
gcc -O2 -DLINUX -D_GNU_SOURCE -Wall   -c -o mjpg_streamer.o mjpg_streamer.c
mjpg_streamer.c:27:28: fatal error: linux/videodev.h: No such file or directory
compilation terminated.
make: *** [mjpg_streamer.o] Error 1
physics@physics:~/Downloads/mjpg-streamer-r63$ 

```

- Have fixed that error by editing the makefile... now it spitting something else..

```

physics@physics:~/Downloads/mjpg-streamer-r63$ make
gcc -O2 -DLINUX -D_GNU_SOURCE -Wall   -c -o mjpg_streamer.o mjpg_streamer.c
gcc -O2 -DLINUX -D_GNU_SOURCE -Wall mjpg_streamer.o utils.o -olpthread -ldl -o mjpg_streamer
chmod 755 mjpg_streamer
make -C plugins/input_uvc all
make[1]: Entering directory `/home/physics/Downloads/mjpg-streamer-r63/plugins/input_uvc'
gcc -c -O2 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -o jpeg_utils.lo jpeg_utils.c
jpeg_utils.c:27:21: fatal error: jpeglib.h: No such file or directory
compilation terminated.
make[1]: *** [jpeg_utils.lo] Error 1
make[1]: Leaving directory `/home/physics/Downloads/mjpg-streamer-r63/plugins/input_uvc'
make: *** [input_uvc.so] Error 2

```

Ok, fixed that issue by install "libjpeg62-dev" - and now theres a different problem lol... never ending... once i've finished and its work i'll write a howto

```

make -C plugins/input_uvc all
make[1]: Entering directory `/home/physics/Downloads/mjpg-streamer-r63/plugins/input_uvc'
gcc -c -O2 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -o jpeg_utils.lo jpeg_utils.c
In file included from v4l2uvc.h:36:0,
                 from jpeg_utils.c:30:
uvcvideo.h:38:0: warning: "V4L2_CID_BACKLIGHT_COMPENSATION" redefined [enabled by default]
/usr/include/linux/videodev.h:1114:0: note: this is the location of the previous definition
uvcvideo.h:39:0: warning: "V4L2_CID_POWER_LINE_FREQUENCY" redefined [enabled by default]
/usr/include/linux/videodev.h:1105:0: note: this is the location of the previous definition
uvcvideo.h:40:0: warning: "V4L2_CID_SHARPNESS" redefined [enabled by default]
/usr/include/linux/videodev.h:1113:0: note: this is the location of the previous definition
uvcvideo.h:41:0: warning: "V4L2_CID_HUE_AUTO" redefined [enabled by default]
/usr/include/linux/videodev.h:1111:0: note: this is the location of the previous definition
uvcvideo.h:43:0: warning: "V4L2_CID_FOCUS_AUTO" redefined [enabled by default]
/usr/include/linux/videodev.h:1380:0: note: this is the location of the previous definition
uvcvideo.h:44:0: warning: "V4L2_CID_FOCUS_ABSOLUTE" redefined [enabled by default]
/usr/include/linux/videodev.h:1378:0: note: this is the location of the previous definition
uvcvideo.h:45:0: warning: "V4L2_CID_FOCUS_RELATIVE" redefined [enabled by default]
/usr/include/linux/videodev.h:1379:0: note: this is the location of the previous definition
uvcvideo.h:47:0: warning: "V4L2_CID_PAN_RELATIVE" redefined [enabled by default]
/usr/include/linux/videodev.h:1370:0: note: this is the location of the previous definition
uvcvideo.h:48:0: warning: "V4L2_CID_TILT_RELATIVE" redefined [enabled by default]
/usr/include/linux/videodev.h:1371:0: note: this is the location of the previous definition
uvcvideo.h:51:0: warning: "V4L2_CID_EXPOSURE_AUTO" redefined [enabled by default]
/usr/include/linux/videodev.h:1360:0: note: this is the location of the previous definition
uvcvideo.h:52:0: warning: "V4L2_CID_EXPOSURE_ABSOLUTE" redefined [enabled by default]
/usr/include/linux/videodev.h:1367:0: note: this is the location of the previous definition
uvcvideo.h:53:0: warning: "V4L2_CID_EXPOSURE_AUTO_PRIORITY" redefined [enabled by default]
/usr/include/linux/videodev.h:1368:0: note: this is the location of the previous definition
uvcvideo.h:56:0: warning: "V4L2_CID_WHITE_BALANCE_TEMPERATURE" redefined [enabled by default]
/usr/include/linux/videodev.h:1112:0: note: this is the location of the previous definition
gcc -c -O2 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -o dynctrl.lo dynctrl.c
In file included from dynctrl.c:35:0:
uvcvideo.h:38:0: warning: "V4L2_CID_BACKLIGHT_COMPENSATION" redefined [enabled by default]
/usr/include/linux/videodev2.h:1114:0: note: this is the location of the previous definition
uvcvideo.h:39:0: warning: "V4L2_CID_POWER_LINE_FREQUENCY" redefined [enabled by default]
/usr/include/linux/videodev2.h:1105:0: note: this is the location of the previous definition
uvcvideo.h:40:0: warning: "V4L2_CID_SHARPNESS" redefined [enabled by default]
/usr/include/linux/videodev2.h:1113:0: note: this is the location of the previous definition
uvcvideo.h:41:0: warning: "V4L2_CID_HUE_AUTO" redefined [enabled by default]
/usr/include/linux/videodev2.h:1111:0: note: this is the location of the previous definition
uvcvideo.h:43:0: warning: "V4L2_CID_FOCUS_AUTO" redefined [enabled by default]
/usr/include/linux/videodev2.h:1380:0: note: this is the location of the previous definition
uvcvideo.h:44:0: warning: "V4L2_CID_FOCUS_ABSOLUTE" redefined [enabled by default]
/usr/include/linux/videodev2.h:1378:0: note: this is the location of the previous definition
uvcvideo.h:45:0: warning: "V4L2_CID_FOCUS_RELATIVE" redefined [enabled by default]
/usr/include/linux/videodev2.h:1379:0: note: this is the location of the previous definition
uvcvideo.h:47:0: warning: "V4L2_CID_PAN_RELATIVE" redefined [enabled by default]
/usr/include/linux/videodev2.h:1370:0: note: this is the location of the previous definition
uvcvideo.h:48:0: warning: "V4L2_CID_TILT_RELATIVE" redefined [enabled by default]
/usr/include/linux/videodev2.h:1371:0: note: this is the location of the previous definition
uvcvideo.h:51:0: warning: "V4L2_CID_EXPOSURE_AUTO" redefined [enabled by default]
/usr/include/linux/videodev2.h:1360:0: note: this is the location of the previous definition
uvcvideo.h:52:0: warning: "V4L2_CID_EXPOSURE_ABSOLUTE" redefined [enabled by default]
/usr/include/linux/videodev2.h:1367:0: note: this is the location of the previous definition
uvcvideo.h:53:0: warning: "V4L2_CID_EXPOSURE_AUTO_PRIORITY" redefined [enabled by default]
/usr/include/linux/videodev2.h:1368:0: note: this is the location of the previous definition
uvcvideo.h:56:0: warning: "V4L2_CID_WHITE_BALANCE_TEMPERATURE" redefined [enabled by default]
/usr/include/linux/videodev2.h:1112:0: note: this is the location of the previous definition
gcc -O2 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -ljpeg -o input_uvc.so input_uvc.c v4l2uvc.lo jpeg_utils.lo dynctrl.lo
In file included from v4l2uvc.h:36:0,
                 from input_uvc.c:44:
uvcvideo.h:38:0: warning: "V4L2_CID_BACKLIGHT_COMPENSATION" redefined [enabled by default]
/usr/include/linux/videodev.h:1114:0: note: this is the location of the previous definition
uvcvideo.h:39:0: warning: "V4L2_CID_POWER_LINE_FREQUENCY" redefined [enabled by default]
/usr/include/linux/videodev.h:1105:0: note: this is the location of the previous definition
uvcvideo.h:40:0: warning: "V4L2_CID_SHARPNESS" redefined [enabled by default]
/usr/include/linux/videodev.h:1113:0: note: this is the location of the previous definition
uvcvideo.h:41:0: warning: "V4L2_CID_HUE_AUTO" redefined [enabled by default]
/usr/include/linux/videodev.h:1111:0: note: this is the location of the previous definition
uvcvideo.h:43:0: warning: "V4L2_CID_FOCUS_AUTO" redefined [enabled by default]
/usr/include/linux/videodev.h:1380:0: note: this is the location of the previous definition
uvcvideo.h:44:0: warning: "V4L2_CID_FOCUS_ABSOLUTE" redefined [enabled by default]
/usr/include/linux/videodev.h:1378:0: note: this is the location of the previous definition
uvcvideo.h:45:0: warning: "V4L2_CID_FOCUS_RELATIVE" redefined [enabled by default]
/usr/include/linux/videodev.h:1379:0: note: this is the location of the previous definition
uvcvideo.h:47:0: warning: "V4L2_CID_PAN_RELATIVE" redefined [enabled by default]
/usr/include/linux/videodev.h:1370:0: note: this is the location of the previous definition
uvcvideo.h:48:0: warning: "V4L2_CID_TILT_RELATIVE" redefined [enabled by default]
/usr/include/linux/videodev.h:1371:0: note: this is the location of the previous definition
uvcvideo.h:51:0: warning: "V4L2_CID_EXPOSURE_AUTO" redefined [enabled by default]
/usr/include/linux/videodev.h:1360:0: note: this is the location of the previous definition
uvcvideo.h:52:0: warning: "V4L2_CID_EXPOSURE_ABSOLUTE" redefined [enabled by default]
/usr/include/linux/videodev.h:1367:0: note: this is the location of the previous definition
uvcvideo.h:53:0: warning: "V4L2_CID_EXPOSURE_AUTO_PRIORITY" redefined [enabled by default]
/usr/include/linux/videodev.h:1368:0: note: this is the location of the previous definition
uvcvideo.h:56:0: warning: "V4L2_CID_WHITE_BALANCE_TEMPERATURE" redefined [enabled by default]
/usr/include/linux/videodev.h:1112:0: note: this is the location of the previous definition
input_uvc.c: In function &#8216;input_init&#8217;:
input_uvc.c:307:3: warning: implicit declaration of function &#8216;input_cmd&#8217; [-Wimplicit-function-declaration]
make[1]: Leaving directory `/home/physics/Downloads/mjpg-streamer-r63/plugins/input_uvc'
cp plugins/input_uvc/input_uvc.so .
make -C plugins/output_file all
make[1]: Entering directory `/home/physics/Downloads/mjpg-streamer-r63/plugins/output_file'
gcc -O2 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -o output_file.so output_file.c
output_file.c: In function &#8216;worker_thread&#8217;:
output_file.c:173:13: warning: ignoring return value of &#8216;system&#8217;, declared with attribute warn_unused_result [-Wunused-result]
make[1]: Leaving directory `/home/physics/Downloads/mjpg-streamer-r63/plugins/output_file'
cp plugins/output_file/output_file.so .
make -C plugins/output_http all
make[1]: Entering directory `/home/physics/Downloads/mjpg-streamer-r63/plugins/output_http'
gcc -c -O2 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -o httpd.lo httpd.c
httpd.c: In function &#8216;command&#8217;:
httpd.c:552:8: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result [-Wunused-result]
httpd.c: In function &#8216;send_error&#8217;:
httpd.c:388:8: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result [-Wunused-result]
httpd.c: In function &#8216;send_snapshot&#8217;:
httpd.c:260:8: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result [-Wunused-result]
gcc -O2 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -o output_http.so output_http.c httpd.lo
make[1]: Leaving directory `/home/physics/Downloads/mjpg-streamer-r63/plugins/output_http'
cp plugins/output_http/output_http.so .
make -C plugins/input_testpicture all
make[1]: Entering directory `/home/physics/Downloads/mjpg-streamer-r63/plugins/input_testpicture'
gcc -O2 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -o input_testpicture.so input_testpicture.c
make[1]: Leaving directory `/home/physics/Downloads/mjpg-streamer-r63/plugins/input_testpicture'
cp plugins/input_testpicture/input_testpicture.so .
make -C plugins/output_autofocus all
make[1]: Entering directory `/home/physics/Downloads/mjpg-streamer-r63/plugins/output_autofocus'
gcc -c -DDEBUG -O2 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -o processJPEG_onlyCenter.lo processJPEG_onlyCenter.c
processJPEG_onlyCenter.c: In function &#8216;getFrameSharpnessValue&#8217;:
processJPEG_onlyCenter.c:45:7: warning: variable &#8216;quant_Y&#8217; set but not used [-Wunused-but-set-variable]
gcc -DDEBUG -O2 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -lm -o output_autofocus.so output_autofocus.c processJPEG_onlyCenter.lo
make[1]: Leaving directory `/home/physics/Downloads/mjpg-streamer-r63/plugins/output_autofocus'
cp plugins/output_autofocus/output_autofocus.so .
make -C plugins/input_gspcav1 all
make[1]: Entering directory `/home/physics/Downloads/mjpg-streamer-r63/plugins/input_gspcav1'
gcc -c -O2 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -o spcav4l.lo spcav4l.c
In file included from spcav4l.c:25:0:
spcav4l.h:134:20: error: field &#8216;vmmap&#8217; has incomplete type
spcav4l.h:135:26: error: field &#8216;videocap&#8217; has incomplete type
spcav4l.h:137:20: error: field &#8216;videombuf&#8217; has incomplete type
spcav4l.h:138:23: error: field &#8216;videopict&#8217; has incomplete type
spcav4l.h:139:22: error: field &#8216;videowin&#8217; has incomplete type
spcav4l.h:140:23: error: field &#8216;videochan&#8217; has incomplete type
spcav4l.c: In function &#8216;convertframe&#8217;:
spcav4l.c:162:7: error: &#8216;VIDEO_PALETTE_YUV420P&#8217; undeclared (first use in this function)
spcav4l.c:162:7: note: each undeclared identifier is reported only once for each function it appears in
spcav4l.c:165:7: error: &#8216;VIDEO_PALETTE_RGB24&#8217; undeclared (first use in this function)
spcav4l.c:168:7: error: &#8216;VIDEO_PALETTE_RGB565&#8217; undeclared (first use in this function)
spcav4l.c:171:7: error: &#8216;VIDEO_PALETTE_RGB32&#8217; undeclared (first use in this function)
spcav4l.c: In function &#8216;v4lGrab&#8217;:
spcav4l.c:200:26: error: &#8216;VIDIOCSYNC&#8217; undeclared (first use in this function)
spcav4l.c:236:27: error: &#8216;VIDIOCMCAPTURE&#8217; undeclared (first use in this function)
spcav4l.c:192:10: warning: variable &#8216;temps&#8217; set but not used [-Wunused-but-set-variable]
spcav4l.c: In function &#8216;GetVideoPict&#8217;:
spcav4l.c:294:22: error: &#8216;VIDIOCGPICT&#8217; undeclared (first use in this function)
spcav4l.c: In function &#8216;SetVideoPict&#8217;:
spcav4l.c:310:22: error: &#8216;VIDIOCSPICT&#8217; undeclared (first use in this function)
spcav4l.c: In function &#8216;init_v4l&#8217;:
spcav4l.c:335:22: error: &#8216;VIDIOCGCAP&#8217; undeclared (first use in this function)
spcav4l.c:342:23: error: &#8216;VIDIOCGCHAN&#8217; undeclared (first use in this function)
spcav4l.c:393:26: error: &#8216;VIDIOCGMBUF&#8217; undeclared (first use in this function)
spcav4l.c:410:23: error: &#8216;VIDIOCMCAPTURE&#8217; undeclared (first use in this function)
spcav4l.c:424:26: error: &#8216;VIDIOCGWIN&#8217; undeclared (first use in this function)
spcav4l.c:428:26: error: &#8216;VIDIOCSWIN&#8217; undeclared (first use in this function)
spcav4l.c: In function &#8216;probePalette&#8217;:
spcav4l.c:439:33: error: &#8216;VIDEO_PALETTE_YUV420P&#8217; undeclared (first use in this function)
spcav4l.c:439:55: error: &#8216;VIDEO_PALETTE_RGB24&#8217; undeclared (first use in this function)
spcav4l.c:439:75: error: &#8216;VIDEO_PALETTE_RGB565&#8217; undeclared (first use in this function)
spcav4l.c:439:96: error: &#8216;VIDEO_PALETTE_RGB32&#8217; undeclared (first use in this function)
spcav4l.c:440:23: error: storage size of &#8216;pict&#8217; isn&#8217;t known
spcav4l.c:446:21: error: &#8216;VIDIOCGPICT&#8217; undeclared (first use in this function)
spcav4l.c:446:2: warning: passing argument 2 of &#8216;ioctl&#8217; makes integer from pointer without a cast [enabled by default]
/usr/include/x86_64-linux-gnu/sys/ioctl.h:42:12: note: expected &#8216;long unsigned int&#8217; but argument is of type &#8216;int *&#8217;
spcav4l.c:453:6: error: request for member &#8216;palette&#8217; in something not a structure or union
spcav4l.c:453:2: warning: statement with no effect [-Wunused-value]
spcav4l.c:455:6: error: request for member &#8216;depth&#8217; in something not a structure or union
spcav4l.c:455:2: warning: statement with no effect [-Wunused-value]
spcav4l.c:456:41: error: request for member &#8216;palette&#8217; in something not a structure or union
spcav4l.c:456:54: error: request for member &#8216;depth&#8217; in something not a structure or union
spcav4l.c:456:2: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;int *&#8217; [-Wformat]
spcav4l.c:456:2: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;int *&#8217; [-Wformat]
spcav4l.c:457:21: error: &#8216;VIDIOCSPICT&#8217; undeclared (first use in this function)
spcav4l.c:457:2: warning: passing argument 2 of &#8216;ioctl&#8217; makes integer from pointer without a cast [enabled by default]
/usr/include/x86_64-linux-gnu/sys/ioctl.h:42:12: note: expected &#8216;long unsigned int&#8217; but argument is of type &#8216;int *&#8217;
spcav4l.c:462:2: warning: passing argument 2 of &#8216;ioctl&#8217; makes integer from pointer without a cast [enabled by default]
/usr/include/x86_64-linux-gnu/sys/ioctl.h:42:12: note: expected &#8216;long unsigned int&#8217; but argument is of type &#8216;int *&#8217;
spcav4l.c:467:10: error: request for member &#8216;palette&#8217; in something not a structure or union
spcav4l.c:467:19: warning: comparison between pointer and integer [enabled by default]
spcav4l.c:440:23: warning: unused variable &#8216;pict&#8217; [-Wunused-variable]
spcav4l.c: In function &#8216;probeSize&#8217;:
spcav4l.c:489:22: error: storage size of &#8216;win&#8217; isn&#8217;t known
spcav4l.c:495:21: error: request for member &#8216;maxwidth&#8217; in something not a structure or union
spcav4l.c:495:7: warning: assignment makes integer from pointer without a cast [enabled by default]
spcav4l.c:496:21: error: request for member &#8216;minwidth&#8217; in something not a structure or union
spcav4l.c:496:7: warning: assignment makes integer from pointer without a cast [enabled by default]
spcav4l.c:497:21: error: request for member &#8216;maxheight&#8217; in something not a structure or union
spcav4l.c:497:7: warning: assignment makes integer from pointer without a cast [enabled by default]
spcav4l.c:498:21: error: request for member &#8216;minheight&#8217; in something not a structure or union
spcav4l.c:498:7: warning: assignment makes integer from pointer without a cast [enabled by default]
spcav4l.c:507:22: error: &#8216;VIDIOCGWIN&#8217; undeclared (first use in this function)
spcav4l.c:507:3: warning: passing argument 2 of &#8216;ioctl&#8217; makes integer from pointer without a cast [enabled by default]
/usr/include/x86_64-linux-gnu/sys/ioctl.h:42:12: note: expected &#8216;long unsigned int&#8217; but argument is of type &#8216;int *&#8217;
spcav4l.c:513:5: error: request for member &#8216;width&#8217; in something not a structure or union
spcav4l.c:513:2: warning: statement with no effect [-Wunused-value]
spcav4l.c:514:5: error: request for member &#8216;height&#8217; in something not a structure or union
spcav4l.c:514:2: warning: statement with no effect [-Wunused-value]
spcav4l.c:515:21: error: &#8216;VIDIOCSWIN&#8217; undeclared (first use in this function)
spcav4l.c:515:2: warning: passing argument 2 of &#8216;ioctl&#8217; makes integer from pointer without a cast [enabled by default]
/usr/include/x86_64-linux-gnu/sys/ioctl.h:42:12: note: expected &#8216;long unsigned int&#8217; but argument is of type &#8216;int *&#8217;
spcav4l.c:517:13: error: request for member &#8216;width&#8217; in something not a structure or union
spcav4l.c:517:24: error: request for member &#8216;height&#8217; in something not a structure or union
spcav4l.c:517:10: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;int *&#8217; [-Wformat]
spcav4l.c:517:10: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;int *&#8217; [-Wformat]
spcav4l.c:521:8: error: request for member &#8216;width&#8217; in something not a structure or union
spcav4l.c:521:19: error: request for member &#8216;height&#8217; in something not a structure or union
spcav4l.c:521:5: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;int *&#8217; [-Wformat]
spcav4l.c:521:5: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;int *&#8217; [-Wformat]
spcav4l.c:490:21: warning: variable &#8216;minh&#8217; set but not used [-Wunused-but-set-variable]
spcav4l.c:490:16: warning: variable &#8216;maxh&#8217; set but not used [-Wunused-but-set-variable]
spcav4l.c:489:22: warning: unused variable &#8216;win&#8217; [-Wunused-variable]
spcav4l.c: In function &#8216;changeSize&#8217;:
spcav4l.c:542:31: error: request for member &#8216;palette&#8217; in something not a structure or union
spcav4l.c:542:16: warning: assignment makes integer from pointer without a cast [enabled by default]
spcav4l.c:543:28: error: request for member &#8216;depth&#8217; in something not a structure or union
spcav4l.c:543:13: warning: assignment makes integer from pointer without a cast [enabled by default]
spcav4l.c:552:16: error: request for member &#8216;height&#8217; in something not a structure or union
spcav4l.c:552:7: warning: statement with no effect [-Wunused-value]
spcav4l.c:553:16: error: request for member &#8216;width&#8217; in something not a structure or union
spcav4l.c:553:7: warning: statement with no effect [-Wunused-value]
spcav4l.c:554:16: error: request for member &#8216;format&#8217; in something not a structure or union
spcav4l.c:554:7: warning: statement with no effect [-Wunused-value]
spcav4l.c:560:26: error: &#8216;VIDIOCGWIN&#8217; undeclared (first use in this function)
spcav4l.c:560:7: warning: passing argument 2 of &#8216;ioctl&#8217; makes integer from pointer without a cast [enabled by default]
/usr/include/x86_64-linux-gnu/sys/ioctl.h:42:12: note: expected &#8216;long unsigned int&#8217; but argument is of type &#8216;int *&#8217;
spcav4l.c:562:19: error: request for member &#8216;height&#8217; in something not a structure or union
spcav4l.c:562:7: warning: statement with no effect [-Wunused-value]
spcav4l.c:563:19: error: request for member &#8216;width&#8217; in something not a structure or union
spcav4l.c:563:7: warning: statement with no effect [-Wunused-value]
spcav4l.c:564:26: error: &#8216;VIDIOCSWIN&#8217; undeclared (first use in this function)
spcav4l.c:564:7: warning: passing argument 2 of &#8216;ioctl&#8217; makes integer from pointer without a cast [enabled by default]
/usr/include/x86_64-linux-gnu/sys/ioctl.h:42:12: note: expected &#8216;long unsigned int&#8217; but argument is of type &#8216;int *&#8217;
spcav4l.c:567:20: error: request for member &#8216;height&#8217; in something not a structure or union
spcav4l.c:567:41: error: request for member &#8216;width&#8217; in something not a structure or union
spcav4l.c:567:8: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;int *&#8217; [-Wformat]
spcav4l.c:567:8: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;int *&#8217; [-Wformat]
spcav4l.c:540:7: warning: variable &#8216;erreur&#8217; set but not used [-Wunused-but-set-variable]
spcav4l.c: In function &#8216;convertpalette&#8217;:
spcav4l.c:654:7: error: &#8216;VIDEO_PALETTE_YUV420P&#8217; undeclared (first use in this function)
spcav4l.c:657:7: error: &#8216;VIDEO_PALETTE_RGB24&#8217; undeclared (first use in this function)
spcav4l.c:660:7: error: &#8216;VIDEO_PALETTE_RGB565&#8217; undeclared (first use in this function)
spcav4l.c:663:7: error: &#8216;VIDEO_PALETTE_RGB32&#8217; undeclared (first use in this function)
spcav4l.c: In function &#8216;paletteconvert&#8217;:
spcav4l.c:678:10: error: &#8216;VIDEO_PALETTE_YUV420P&#8217; undeclared (first use in this function)
spcav4l.c:678:3: warning: return makes integer from pointer without a cast [enabled by default]
spcav4l.c:681:10: error: &#8216;VIDEO_PALETTE_RGB24&#8217; undeclared (first use in this function)
spcav4l.c:681:3: warning: return makes integer from pointer without a cast [enabled by default]
spcav4l.c:684:10: error: &#8216;VIDEO_PALETTE_RGB565&#8217; undeclared (first use in this function)
spcav4l.c:684:3: warning: return makes integer from pointer without a cast [enabled by default]
spcav4l.c:687:10: error: &#8216;VIDEO_PALETTE_RGB32&#8217; undeclared (first use in this function)
spcav4l.c:687:3: warning: return makes integer from pointer without a cast [enabled by default]
spcav4l.c: In function &#8216;checkpalette&#8217;:
spcav4l.c:731:16: error: request for member &#8216;height&#8217; in something not a structure or union
spcav4l.c:731:7: warning: statement with no effect [-Wunused-value]
spcav4l.c:732:16: error: request for member &#8216;width&#8217; in something not a structure or union
spcav4l.c:732:7: warning: statement with no effect [-Wunused-value]
spcav4l.c:733:16: error: request for member &#8216;format&#8217; in something not a structure or union
spcav4l.c:733:7: warning: statement with no effect [-Wunused-value]
spcav4l.c:735:13: error: request for member &#8216;frame&#8217; in something not a structure or union
spcav4l.c:735:4: warning: statement with no effect [-Wunused-value]
spcav4l.c:736:23: error: &#8216;VIDIOCMCAPTURE&#8217; undeclared (first use in this function)
spcav4l.c:736:4: warning: passing argument 2 of &#8216;ioctl&#8217; makes integer from pointer without a cast [enabled by default]
/usr/include/x86_64-linux-gnu/sys/ioctl.h:42:12: note: expected &#8216;long unsigned int&#8217; but argument is of type &#8216;int *&#8217;
spcav4l.c: In function &#8216;GetDepth&#8217;:
spcav4l.c:888:10: error: &#8216;VIDEO_PALETTE_RAW&#8217; undeclared (first use in this function)
spcav4l.c:893:10: error: &#8216;VIDEO_PALETTE_YUV420P&#8217; undeclared (first use in this function)
spcav4l.c:898:10: error: &#8216;VIDEO_PALETTE_RGB565&#8217; undeclared (first use in this function)
spcav4l.c:901:10: error: &#8216;VIDEO_PALETTE_RGB24&#8217; undeclared (first use in this function)
spcav4l.c:904:10: error: &#8216;VIDEO_PALETTE_RGB32&#8217; undeclared (first use in this function)
spcav4l.c: In function &#8216;SpcaGetBrightness&#8217;:
spcav4l.c:924:27: error: request for member &#8216;brightness&#8217; in something not a structure or union
spcav4l.c:924:40: error: invalid operands to binary >> (have &#8216;int *&#8217; and &#8216;int&#8217;)
spcav4l.c:924:3: warning: return makes integer from pointer without a cast [enabled by default]
spcav4l.c: In function &#8216;SpcaSetBrightness&#8217;:
spcav4l.c:930:18: error: request for member &#8216;brightness&#8217; in something not a structure or union
spcav4l.c:930:3: warning: statement with no effect [-Wunused-value]
spcav4l.c: In function &#8216;SpcaGetContrast&#8217;:
spcav4l.c:945:27: error: request for member &#8216;contrast&#8217; in something not a structure or union
spcav4l.c:945:38: error: invalid operands to binary >> (have &#8216;int *&#8217; and &#8216;int&#8217;)
spcav4l.c:945:3: warning: return makes integer from pointer without a cast [enabled by default]
spcav4l.c: In function &#8216;SpcaSetContrast&#8217;:
spcav4l.c:951:18: error: request for member &#8216;contrast&#8217; in something not a structure or union
spcav4l.c:951:3: warning: statement with no effect [-Wunused-value]
spcav4l.c: In function &#8216;SpcaGetColors&#8217;:
spcav4l.c:965:27: error: request for member &#8216;colour&#8217; in something not a structure or union
spcav4l.c:965:36: error: invalid operands to binary >> (have &#8216;int *&#8217; and &#8216;int&#8217;)
spcav4l.c:965:3: warning: return makes integer from pointer without a cast [enabled by default]
spcav4l.c: In function &#8216;SpcaSetColors&#8217;:
spcav4l.c:971:18: error: request for member &#8216;colour&#8217; in something not a structure or union
spcav4l.c:971:3: warning: statement with no effect [-Wunused-value]
spcav4l.c: In function &#8216;upbright&#8217;:
spcav4l.c:982:26: error: request for member &#8216;brightness&#8217; in something not a structure or union
spcav4l.c:982:9: warning: assignment makes integer from pointer without a cast [enabled by default]
spcav4l.c:985:17: error: request for member &#8216;brightness&#8217; in something not a structure or union
spcav4l.c:985:2: warning: statement with no effect [-Wunused-value]
spcav4l.c: In function &#8216;downbright&#8217;:
spcav4l.c:998:26: error: request for member &#8216;brightness&#8217; in something not a structure or union
spcav4l.c:998:9: warning: assignment makes integer from pointer without a cast [enabled by default]
spcav4l.c:1001:17: error: request for member &#8216;brightness&#8217; in something not a structure or union
spcav4l.c:1001:2: warning: statement with no effect [-Wunused-value]
spcav4l.c: In function &#8216;upcontrast&#8217;:
spcav4l.c:1014:28: error: request for member &#8216;contrast&#8217; in something not a structure or union
spcav4l.c:1014:11: warning: assignment makes integer from pointer without a cast [enabled by default]
spcav4l.c:1017:17: error: request for member &#8216;contrast&#8217; in something not a structure or union
spcav4l.c:1017:2: warning: statement with no effect [-Wunused-value]
spcav4l.c: In function &#8216;downcontrast&#8217;:
spcav4l.c:1030:28: error: request for member &#8216;contrast&#8217; in something not a structure or union
spcav4l.c:1030:11: warning: assignment makes integer from pointer without a cast [enabled by default]
spcav4l.c:1033:17: error: request for member &#8216;contrast&#8217; in something not a structure or union
spcav4l.c:1033:2: warning: statement with no effect [-Wunused-value]
spcav4l.c: In function &#8216;spcaSetAutoExpo&#8217;:
spcav4l.c:1085:14: error: &#8216;BASE_VIDIOCPRIVATE&#8217; undeclared (first use in this function)
spcav4l.c:1085:14: error: invalid operands to binary << (have &#8216;int *&#8217; and &#8216;int&#8217;)
spcav4l.c:1085:14: error: invalid operands to binary | (have &#8216;unsigned int&#8217; and &#8216;int *&#8217;)
spcav4l.c:1085:14: error: invalid operands to binary | (have &#8216;int *&#8217; and &#8216;long unsigned int&#8217;)
spcav4l.c:1085:14: warning: passing argument 2 of &#8216;ioctl&#8217; makes integer from pointer without a cast [enabled by default]
/usr/include/x86_64-linux-gnu/sys/ioctl.h:42:12: note: expected &#8216;long unsigned int&#8217; but argument is of type &#8216;int *&#8217;
spcav4l.c: In function &#8216;spcaPrintParam&#8217;:
spcav4l.c:1093:14: error: &#8216;BASE_VIDIOCPRIVATE&#8217; undeclared (first use in this function)
spcav4l.c:1093:14: error: invalid operands to binary << (have &#8216;int *&#8217; and &#8216;int&#8217;)
spcav4l.c:1093:14: error: invalid operands to binary | (have &#8216;unsigned int&#8217; and &#8216;int *&#8217;)
spcav4l.c:1093:14: error: invalid operands to binary | (have &#8216;int *&#8217; and &#8216;long unsigned int&#8217;)
spcav4l.c:1093:14: warning: passing argument 2 of &#8216;ioctl&#8217; makes integer from pointer without a cast [enabled by default]
/usr/include/x86_64-linux-gnu/sys/ioctl.h:42:12: note: expected &#8216;long unsigned int&#8217; but argument is of type &#8216;int *&#8217;
spcav4l.c: In function &#8216;spcaSetTimeInterval&#8217;:
spcav4l.c:1105:14: error: &#8216;BASE_VIDIOCPRIVATE&#8217; undeclared (first use in this function)
spcav4l.c:1105:14: error: invalid operands to binary << (have &#8216;int *&#8217; and &#8216;int&#8217;)
spcav4l.c:1105:14: error: invalid operands to binary | (have &#8216;unsigned int&#8217; and &#8216;int *&#8217;)
spcav4l.c:1105:14: error: invalid operands to binary | (have &#8216;int *&#8217; and &#8216;long unsigned int&#8217;)
spcav4l.c:1105:14: warning: passing argument 2 of &#8216;ioctl&#8217; makes integer from pointer without a cast [enabled by default]
/usr/include/x86_64-linux-gnu/sys/ioctl.h:42:12: note: expected &#8216;long unsigned int&#8217; but argument is of type &#8216;int *&#8217;
spcav4l.c: In function &#8216;spcaSetQuality&#8217;:
spcav4l.c:1117:14: error: &#8216;BASE_VIDIOCPRIVATE&#8217; undeclared (first use in this function)
spcav4l.c:1117:14: error: invalid operands to binary << (have &#8216;int *&#8217; and &#8216;int&#8217;)
spcav4l.c:1117:14: error: invalid operands to binary | (have &#8216;unsigned int&#8217; and &#8216;int *&#8217;)
spcav4l.c:1117:14: error: invalid operands to binary | (have &#8216;int *&#8217; and &#8216;long unsigned int&#8217;)
spcav4l.c:1117:14: warning: passing argument 2 of &#8216;ioctl&#8217; makes integer from pointer without a cast [enabled by default]
/usr/include/x86_64-linux-gnu/sys/ioctl.h:42:12: note: expected &#8216;long unsigned int&#8217; but argument is of type &#8216;int *&#8217;
make[1]: *** [spcav4l.lo] Error 1
make[1]: Leaving directory `/home/physics/Downloads/mjpg-streamer-r63/plugins/input_gspcav1'
make: *** [input_gspcav1.so] Error 2

```

---

### Post by Plasma_NZ on 2011-11-29
if anyone out there can perhaps make a working .deb for mjpg_streamer for ubuntu 11.10 64bit - i'm sure there'd be alot of people who'd be very appreciative..

---

### Post by ShamenKing on 2011-11-29
I have the same query,what should I do I've been receiving errors.. :( [IMG]http://www.imagicon.info/cat/5-40/1.gif[/IMG]

---

### Post by Plasma_NZ on 2011-11-30
> **ShamenKing said:**
> I have the same query,what should I do I've been receiving errors.. :( [IMG]http://www.imagicon.info/cat/5-40/1.gif[/IMG]

paste the error's your getting.... see if we can get you to the same point as me...

---

### Post by SevenMachines on 2011-11-30
-r63 is too old for oneiric. svn works here though, and includes the videodev.h changes. Still need to alter the lib order in the Makefile but compiles fine otherwise.

```
$ svn co https://mjpg-streamer.svn.sourceforge.net/svnroot/mjpg-streamer mjpg-streamer
$ cd mjpg-streamer/mjpg-streamer
$ sed -i 's/$(CC) $(CFLAGS) $(LFLAGS) $(OBJECTS) -o $(APP_BINARY)/$(CC) $(CFLAGS) $(OBJECTS) $(LFLAGS) -o $(APP_BINARY)/g' Makefile 
$ make
```

---

### Post by Plasma_NZ on 2011-11-30
> **SevenMachines said:**
> -r63 is too old for oneiric. svn works here though, and includes the videodev.h changes. Still need to alter the lib order in the Makefile but compiles fine otherwise.

```
$ svn co https://mjpg-streamer.svn.sourceforge.net/svnroot/mjpg-streamer mjpg-streamer
$ cd mjpg-streamer/mjpg-streamer
$ sed -i 's/$(CC) $(CFLAGS) $(LFLAGS) $(OBJECTS) -o $(APP_BINARY)/$(CC) $(CFLAGS) $(OBJECTS) $(LFLAGS) -o $(APP_BINARY)/g' Makefile 
$ make
```

Your a legend.... kudos to you...

will edit my first post with instructions for anyone else whos keen

---

### Post by Plasma_NZ on 2011-11-30
Thanks SevenMachines - keep up your good work...

---

### Post by pdanilchik on 2012-08-05
I think that MANY people are pulling down 4 year old source code because the main Sourceforge page for mjpg-streamer isn't updated with the latest source files (unless I am mistaken somehow).

You can find a V4L2 updated source from here:

[http://mjpg-streamer.svn.sourceforge.net/viewvc/mjpg-streamer/mjpg-streamer/](http://mjpg-streamer.svn.sourceforge.net/viewvc/mjpg-streamer/mjpg-streamer/)

Just click on "Download GNU Tarball", near the bottom of the page.  This version has some files last updated in April of 2012. !  The Makefile seems fixed and the references to the header file too... although I haven't tried building it... yet.

---

### Post by commander_data on 2012-11-25
That's the best answer. No point messing about fixing old broken builds!!!

---

### Post by lprofil on 2013-02-24
Your tutorial helped me a lot with my Logitek c210 webcam.
Thanks for that.

Though you might want to add **subversion** and **make** to the necessary packages:

```
sudo apt-get install libjpeg62-dev subversion make
```

Also one slash is unnecessary.
The right line is:

```
cd mjpg-streamer/mjpg-streamer/
```

;)

/lprofil

---

