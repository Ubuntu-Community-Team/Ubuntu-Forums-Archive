---
title: "Problems with Webcam"
date: 2006-04-28
forum: General Help
---

### Post by tc10b on 2006-04-28
Hi,

I'm having a problem with my webcam. It is a Creative Webcam Vista, as always I turned to the wiki first, which advised me to install easycam2 which I did, I then ran it and installed the drivers for my camera, all seemed to be going ok.

I then tried to run the test feature in easycam and the computer just hung and didn't do anything again until I rebooted. The same happens when I try to use camorama.

I don't know if this is just a problem with the driver or just the particular software that I am using. :confused: ](*,) 
Any help would be much appreciated.

Thanks

Tom.

---

### Post by Robert A. Matthews on 2006-05-03
I have just had the same problem but with a [COLOR=Red]Logitech QuickCam
Express[/COLOR] - on running [COLOR=Red]camorama[/COLOR] or [COLOR=Red]gqcam[/COLOR], my system hangs.

I too would appreciate some help!

Thanks

Robert

---

### Post by Robert A. Matthews on 2006-05-04
I see I was a bit hasty in my above post - sorry
about that.

Further searching revealed this problem has been
covered elsewhere:

[http://ubuntuforums.org/showthread.php?t=75284]("http://ubuntuforums.org/showthread.php?t=75284")

I note that the fix specified there involves taking software
from a web site unknown to me, so I am extremely reluctant
to use it (I mean no offence here it is just that I am
somewhat paranoid over security)

So, I live in hope that Dapper will include the fix.

Robert

P.S.

The problem also gets a mention here:

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras")

For me the relevant entry is for the Logitech QuickCam Express, with
a usb id of 046d:0928

---

### Post by GAS on 2006-05-19
Hi,

This this [http://ubuntuforums.org/showthread.php?t=75284]("http://ubuntuforums.org/showthread.php?t=75284")

Cheers

[QUOTE=tc10b]Hi,

I'm having a problem with my webcam. It is a Creative Webcam Vista, as always I turned to the wiki first, which advised me to install easycam2 which I did, I then ran it and installed the drivers for my camera, all seemed to be going ok.

I then tried to run the test feature in easycam and the computer just hung and didn't do anything again until I rebooted. The same happens when I try to use camorama.

I don't know if this is just a problem with the driver or just the particular software that I am using. :confused: ](*,) 
Any help would be much appreciated.

Thanks

Tom.[/QUOTE]

---

### Post by eurika on 2006-06-03
I win with this way 
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-4.0
wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060402.tar.gz
tar xvfz spca5xx-20060501.tar.gz
cd spca5xx-20060402
sudo make CC=gcc-4.0

sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
```

Take the last driver : [http://mxhaard.free.fr/spca50x/Download/](http://mxhaard.free.fr/spca50x/Download/)

[source]("http://66.249.93.104/search?q=cache:yuHHQoUtaCcJ:forum.ubuntu-fr.org/viewtopic.php%3Fid%3D23086%26p%3D4+spca5xx:+no+version+for+%22struct_module%22+found:+kernel+tainted.&hl=fr&ct=clnk&cd=1&client=firefox")

---

### Post by Gaute65 on 2006-06-04
[QUOTE=eurika]I win with this way 
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-4.0
wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060402.tar.gz
tar xvfz spca5xx-20060501.tar.gz
cd spca5xx-20060402
sudo make CC=gcc-4.0

sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
```

Take the last driver : [http://mxhaard.free.fr/spca50x/Download/](http://mxhaard.free.fr/spca50x/Download/)

[source]("http://66.249.93.104/search?q=cache:yuHHQoUtaCcJ:forum.ubuntu-fr.org/viewtopic.php%3Fid%3D23086%26p%3D4+spca5xx:+no+version+for+%22struct_module%22+found:+kernel+tainted.&hl=fr&ct=clnk&cd=1&client=firefox")[/QUOTE]


Hi, new to this forum and Ubuntu

I did get my camera working last night by using the guide from eurika. when I start ubuntu today, no programs  can see the webcam. What are i doing wrong?

---

