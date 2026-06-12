---
title: "send output to /var/www/ ?"
date: 2009-09-15
forum: General Help
---

### Post by mysoogal on 2009-09-15
somebody good with bash scripting tell me why it doesn't send the output and jpg to /var/www/ 

> #!/bin/bash



sourcelocation="/home/mysoogal/Videos/"
# Extension of source videos
sourceext="avi"


find ${sourcelocation} -iname "*${sourceext}" -exec ffmpeg -v 0 -y -i "/home/mysoogal/Videos{}" -vframes 1 -ss 90 -vcodec mjpeg -f rawvideo -s 286x160 -aspect 16:9 "/var/www{}.jpg" \;


if [ -e "${sourcelocation}*.avi" ] && [ -e "${sourcelocation}*.jpg" ]; then
	Delete videos	
	rm ${sourcelocation}*.ogm
	# Sleep for 10 seconds before shutting down
	sleep 10
	# Shutdown computer
	# sudo shutdown -h now
else
	echo "Encoding FAILED"
fi


# Convert all video clips to ITU H264 OGM video container
find ${sourcelocation} -iname "*${sourceext}" -exec mencoder "/home/mysoogal/Videos{}" -o "/var/www{}.ogm" -af volume=10 -aspect 16:9 -of avi -noodml -ovc x264 -x264encopts bitrate=300:level_idc=41:bframes=3:frameref=2: nopsnr: nossim: pass=1: threads=auto -oac mp3lame \;



exit


it gives me this error

> root@ubuntu:~/Desktop# mysoogal.sh
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
/home/mysoogal/Videos/home/mysoogal/Videos/[DB]_Bleach_236_[8FAF19E1].avi: no such file or directory
Encoding FAILED
MEncoder 2:1.0~rc2-0ubuntu19 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU          540  @ 1.86GHz (Family: 6, Model: 22, Stepping: 1)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
File not found: '/home/mysoogal/Videos/home/mysoogal/Videos/[DB]_Bleach_236_[8FAF19E1].avi'
Failed to open /home/mysoogal/Videos/home/mysoogal/Videos/[DB]_Bleach_236_[8FAF19E1].avi.
Cannot open file/device.


what is the right format to send output video to /var/www/ and send jpg output to /var/www/ :confused:

im confused with this. i think i use double paths but not sure. someone can tell me what's wrong.


thank you

---

### Post by lloyd_b on 2009-09-15
It's the double path - it's simply not finding the source avi file because of that.  Here's the problem:```
find ${sourcelocation} -iname "*${sourceext}" -exec ffmpeg -v 0 -y -i "[COLOR="Red"]/home/mysoogal/Videos[/COLOR]{}" -vframes 1 -ss 90 -vcodec mjpeg -f rawvideo -s 286x160 -aspect 16:9 "/var/www{}.jpg" \;
```What's happening is that the "find" command is returning the full path to the file ("/home/mysoogal/Videos/[DB]_Bleach_236_[8FAF19E1].avi" in this case), but your explicit "/home/mysoogal/Videos" is prepending that onto the full path.

So change the line to ```
find ${sourcelocation} -iname "*${sourceext}" -exec ffmpeg -v 0 -y -i "{}" -vframes 1 -ss 90 -vcodec mjpeg -f rawvideo -s 286x160 -aspect 16:9 "/var/www{}.jpg \;
``` and see if that helps.

Lloyd B.

---

### Post by mysoogal on 2009-10-23
thanks,

why dont i get ubuntu emails sent to me ? when new reply has been made always reply late

---

### Post by DaithiF on 2009-10-23
> **mysoogal said:**
> thanks,

why dont i get ubuntu emails sent to me ? when new reply has been made always reply late
Have you configured it to send you an email when a thread is replied to?  Go to User CP (control panel), then Edit Options, then set the "Default Thread Subscription Mode:"to "Instant email notification".  That should to the trick.

---

