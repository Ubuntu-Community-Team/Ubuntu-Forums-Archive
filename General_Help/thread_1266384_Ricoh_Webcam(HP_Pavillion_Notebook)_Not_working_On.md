---
title: "Ricoh Webcam(HP Pavillion Notebook) Not working On Ubuntu Jaunty (9.04)"
date: 2009-09-14
forum: General Help
---

### Post by sacsha30 on 2009-09-14
Hi All

I am trying to install webcam on ubuntu jaunty but not able to do so.

I have already tried following methods:

[LIST=1]
[*]Tried installing luvcview ([http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops#webcam](http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops#webcam))
[*]Tried installing webcam2
[*]Tried installing luvcview ([http://ubuntuguide.org/wiki/Ubuntu:Jaunty#WebCams)]](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#WebCams)])

Its shows following error:
$luvcview -f yuv
luvcview 0.2.4

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
ERROR opening V4L interface: No such file or directory 
[/LIST]

Tested it on:
[LIST=1]
[*]Test it on cheese
[*]Tested it on skype
[*]Tested it on xawtv
[/LIST]

My configuration is:
HP Pavillion dv6000
Ricoh Webcam

Please help!!

Thanks
Sac

---

### Post by AlanR8 on 2009-09-14
I have a Sony Vaio VGN-FZ21S with a similar Ricoh Webcam. There's a thread elsewhere on this forum about issues surrounding this device,

> [http://ubuntuforums.org/showthread.php?t=968381](http://ubuntuforums.org/showthread.php?t=968381)

I've just got my webcam working again under Karmic by following the instructions below. When I installed the firmware .deb I got error messages but I continued to install the driver as below and all works well now.


> Go to:

[http://linux.softpedia.com/progDownload/ricoh-webcam-r5u870-Download-30296.html](http://linux.softpedia.com/progDownload/ricoh-webcam-r5u870-Download-30296.html)

and download the latest firmware as a .deb file

Double click to install.

Go to:

 [http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html)

to pick up the latest driver. At the time of writing it was r5u870_k2.6.30_i386.tar.bz2

Extract the to your home directory.

Then open a terminal and navigate to the folder

sudo make

sudo make install

sudo modprobe r5u870

IMPORTANT: the module r5u870 goes in conflict with the uvcvideo module, therefore it is necessary to uninstall or to unload the uvcvideo module!

sudo modprobe -r uvcvideo  

---

### Post by sacsha30 on 2009-09-14
Hi Alan

Thanks for reply.

I have tried the steps you have mention in the later quote. I am having this error while issuing make command now:

CC [M]  /home/sac/Desktop/r5u870/usbcam/usbcam_dev.o
In file included from /home/sac/Desktop/r5u870/usbcam/usbcam_dev.c:21:
/home/sac/Desktop/r5u870/usbcam/usbcam_priv.h:123: error: field &#8216;um_v4l_fops&#8217; has incomplete type
/home/sac/Desktop/r5u870/usbcam/usbcam_dev.c: In function &#8216;usbcam_work_ref&#8217;:
/home/sac/Desktop/r5u870/usbcam/usbcam_dev.c:779: warning: format not a string literal and no format arguments
make[3]: *** [/home/sac/Desktop/r5u870/usbcam/usbcam_dev.o] Error 1
make[2]: *** [/home/sac/Desktop/r5u870/usbcam] Error 2
make[1]: *** [_module_/home/sac/Desktop/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [all] Error 2

Please suggest.

Sac

---

### Post by sacsha30 on 2009-09-14
Hi All

I have tried installing ricoh-webcam-r5u870 but it says failed dependency ricoh-webcam-r5u870-driver and broken link.

I have tried all the possible ways. Never come across this kind of problem with Ubuntu.

Any help will be a blessing for me... :-(

Regards
Sac

---

### Post by AlanR8 on 2009-09-15
Sorry to hear of your troubles. Did you look through the other post I gave the link too? There's lots of information there and it's mostly about a year to three months old so is probably more relevant to Jaunty.

I'm running Karmic Alpha 5, fully patched and it worked for me.

---

### Post by sacsha30 on 2009-09-15
Hi Alan

I have tried almost everything. The problem is that my webcam works fine in windows 7 that I have as a second OS on my laptop. But I dont like windows as I do my all work but webcam on ubuntu. So you can say just for webcam I have my lot of space occupied...

Is there any logs anywhere which can provide my any hint of what the problem is?

Another output which may help.

$lsusb
Bus 001 Device 002: ID 05ca:1870 Ricoh Co., Ltd Webcam 1000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

moreover when I an installing r5u87 driver from source code it installed properly. but when I do:

$sudo r5u87x-loader --reload r5u87x firmware loader v0.2
r5u87x firmware loader v0.2

Searching for device...

Error: Failed to find any supported webcams.

Regards
Sac

---

### Post by sacsha30 on 2009-09-15
Hi Alan

Just to update.. I have found a long list of people complaining about the issue I have...I think it is still some kinda bug for hp laptops with Ricoh webcams...

[http://bitbucket.org/ahixon/r5u87x/issue/26/hp-pavillion-dv9000s-webcam-not-supported](http://bitbucket.org/ahixon/r5u87x/issue/26/hp-pavillion-dv9000s-webcam-not-supported)

hope to find a solution shortly...

---

### Post by AlanR8 on 2009-09-18
A further update.

Remember I'm running Karmic, NOT Jaunty. An update I applied earlier this week, Tuesday, was an update too far! 

A fully borked system and a full reinstall required.

This evening I've just reinstalled the web cam and it worked fist time.

However, in my original post I referenced applying the firmware update. That install did not take but I continued with the driver install as per the original post, 

What I also did, and I can't remember if I did it the first time, is make sure my user was in the Video user group.

If you haven't tried that, give it a go.

---

### Post by sacsha30 on 2009-09-21
Hi Alan

Great thanks for reply.

I did not have enabled the video priviledges to the user. I have enabled now. But now it started giving this error:

$sudo ./loader r5u87x firmware loader v0.2
r5u87x firmware loader v0.2

Searching for device...
Found camera: 05ca:1870
Warning: Failed to get microcode status.

Error: Failed to upload firmware to device: Connection timed out (code -110).

Regards
Sac

---

### Post by wilfon on 2009-09-26
Hi,
You could try the solution given by alarcon in: [http://ubuntuforum-pt.org/index.php?topic=49371.0](http://ubuntuforum-pt.org/index.php?topic=49371.0)
it's in portuguese but not hard to understand.
I am using a Vaio SZ770n (Ricoh webcam 05ca:183a) running Ubuntu Jaunty 9.04 and it worked for me :)!! Thanks alarcon.

---

### Post by bcurry on 2009-10-04
> **AlanR8 said:**
> I have a Sony Vaio VGN-FZ21S with a similar Ricoh Webcam. There's a thread elsewhere on this forum about issues surrounding this device,



I've just got my webcam working again under Karmic by following the instructions below. When I installed the firmware .deb I got error messages but I continued to install the driver as below and all works well now.

Are you running 32-bit or 64-bit?  I'd hesitant to try this on my 64-bit system without first understanding that.

Thanks!

bc

---

### Post by AlanR8 on 2009-10-04
Hi

As I said in the other thread about the web cam, I just did a clean install of Karmic Beta and the camera just worked first time with NO tweaks or work rounds.

Good things come to those who wait!!!!

---

### Post by wolf2588 on 2009-10-13
First post, i got a dv6000 with Jaunty

Download from here

[http://avilella.googlepages.com/r5u870_patched.tar.bz2](http://avilella.googlepages.com/r5u870_patched.tar.bz2)

Extract it on your Desktop and ask the terminal to go there

cd Desktop

cd r5u870_patched

now we start playing around

sudo make

sudo make install

sudo chmod a+rw /dev/video0



Try it with this

gst-launch-0.10 v4l2src ! ffmpegcolorspace ! ximagesink .


greetings from Costa Rica

---

