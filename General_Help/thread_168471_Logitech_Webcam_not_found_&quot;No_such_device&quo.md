---
title: "Logitech Webcam not found: &quot;No such device&quot;"
date: 2006-04-30
forum: General Help
---

### Post by robert_impey on 2006-04-30
Hi,

I'm using Breezy and I want to use a Logitech webcam with GnomeMeeting. 

The kernel is able to "see" the webcam:

$ lsusb
...
Bus 003 Device 004: ID 046d:08f0 Logitech, Inc.
Bus 003 Device 001: ID 0000:0000
...
$ cat /proc/bus/usb/devices
...
T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=08f0 Rev= 1.00
S:  Product=Camera
C:* #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   1 Ivl=16ms
I:  If#= 0 Alt= 1 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=01(Isoc) MxPS=1023 Ivl=1ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   1 Ivl=16ms
I:  If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 2 Alt= 0 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=83(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 2 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=83(I) Atr=01(Isoc) MxPS=  52 Ivl=1ms
...

However, no applications seem to be able to use the camera:

$ scantv
v4l2: open /dev/video0: No such device
v4l2: open /dev/video0: No such device
v4l: open /dev/video0: No such device
no grabber device available
$ xawtv --hwscan
This is xawtv-3.94, running on Linux/i686 (2.6.12-10-386)
can't open /dev/video0: No such device
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such device
v4l2: open /dev/video0: No such device
v4l: open /dev/video0: No such device
no video grabber device available

But 
$ ls -l /dev/video*
lrwxrwxrwx  1 root root       6 2006-04-30 09:42 /dev/video -> video0
crw-rw----  1 root video 81,  0 2006-04-30 09:42 /dev/video0
...
crw-rw----  1 root video 81, 63 2006-04-30 09:42 /dev/video63

It looks like the camera is there and is being detected.

Do I need to find a driver for the camera? If so, is the driver in the repositories?

Thanks in advance.

---

### Post by lothar_m on 2006-04-30
Did you install the drivers for it??

check out this excelent post by arnieboy [right here]("http://www.ubuntuforums.org/showthread.php?t=75284&highlight=logitech+webcam")

i follow this one and got my logitech webcam working great.

---

### Post by robert_impey on 2006-04-30
Thanks for the suggestion.

I've now tried that but the camera still doesn't show up when I try:

$ scantv

$ xawtv --hwscan

or run gnomemeeting. :(

Note:

The line

$ wget [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060301.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060301.tar.gz)

is now

$wget [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz)

And the lines that follow should be changed accordingly. It must be a really fresh update as I'm still in April here in Mexico.

---

### Post by Andrew MacDonald on 2006-05-07
Hey,

I have the same camera as you (046d:08f0). It's actually not supported by the spca5xx driver, if you check [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

I found a driver that worked for me here:
[http://home.mag.cx/messenger/](http://home.mag.cx/messenger/)

the link came from this thread:
[http://www.linuxquestions.org/questions//showthread.php?t=419827](http://www.linuxquestions.org/questions//showthread.php?t=419827)

---

