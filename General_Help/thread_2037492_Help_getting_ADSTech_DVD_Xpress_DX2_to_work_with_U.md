---
title: "Help getting ADSTech DVD Xpress DX2 to work with Ubuntu"
date: 2012-08-03
forum: General Help
---

### Post by 1976MrEMan on 2012-08-03
Hi, I'm a new linux user and I have an old ADSTech DVD Xpress DX2 that I am hoping to get working on Ubuntu 12.04. I have downloaded a Linux driver for it in tar.bz2 format, but i don't know what to do next. The Additional Drivers program just says that there are no proprietary drivers in use on my system. Any tips for me?

---

### Post by CharlesA on 2012-08-04
> **1976MrEMan said:**
> Hi, I'm a new linux user and I have an old ADSTech DVD Xpress DX2 that I am hoping to get working on Ubuntu 12.04. I have downloaded a Linux driver for it in tar.bz2 format, but i don't know what to do next. The Additional Drivers program just says that there are no proprietary drivers in use on my system. Any tips for me?
Why do you think you need the driver in the first place?

---

### Post by yuvraj23 on 2012-08-04
Try this.. say your downloaded file is diver.1.x.tar.bz2, open it using Archive manager and extract it to a new folder on root directory i.e /home/new/. Now open terminal and put these commands one by one.  ```


cd /new/
./configure > configure.txt
make > make.txt
sudo make install


```

Thats It.. Now your drive will get installed if all dependencies are satisfied. If you get some errors (like dependencies error) then upload newly created configure.txt and make.txt file here :)


Thankx 
Yuvraj

---

### Post by 1976MrEMan on 2012-08-04
> **CharlesA said:**
> Why do you think you need the driver in the first place?

I googled for info on getting the DVD Xpress to work with Ubuntu and the instructions I found provided me a link to download the drivers for it, but didn't provide any help for setting it up.

---

### Post by 1976MrEMan on 2012-08-04
> **yuvraj23 said:**
> Try this.. say your downloaded file is diver.1.x.tar.bz2, open it using Archive manager and extract it to a new folder on root directory i.e /home/new/. Now open terminal and put these commands one by one.  ```


cd /new/
./configure > configure.txt
make > make.txt
sudo make install


```

Thats It.. Now your drive will get installed if all dependencies are satisfied. If you get some errors (like dependencies error) then upload newly created configure.txt and make.txt file here :)


Thankx 
Yuvraj

Terminal will not allow me to navigate to that folder. I get a 'no such file or directory' error message even though I am typing the appropriate folder names, etc.

---

### Post by CharlesA on 2012-08-04
Just type cd ~/path/to/folder

Also, moved to own thread.

---

### Post by David Andersson on 2012-08-04
> **1976MrEMan said:**
> I googled for info on getting the DVD Xpress to work with Ubuntu and the instructions I found provided me a link to download the drivers for it, but didn't provide any help for setting it up.

When I google that card the hits indicates the linux driver is "go7007" and it appears it is available to the 2.6 kernel. (I don't have that card so I don't know what is needed to install or activate the driver.)

Some pages suggests one have to compile go7007 oneself for newer kernels, but there seems to be a package in 12.04 relating to go7007.

Is it the go7007 you were going to compile?

Have you tried if the driver is installed automatically, or via System Settings>Additional Drivers?

Just to check, in a terminal, type

```
lsmod | grep go7007
```

If it returns anything, the driver should be installed already.

---

### Post by 1976MrEMan on 2012-08-05
It is the go7007 driver. After hours of trying to type the commands in different ways I've managed to navigate to the appropriate directory. Now I am trying to install the driver, but none of the commands i've been told to use work. So far every command turns back a 'command not found' result.

---

### Post by 1976MrEMan on 2012-08-05
lsmod | grep go7007 just skips to the next line, no results

---

### Post by David Andersson on 2012-08-05
> **1976MrEMan said:**
> lsmod | grep go7007 just skips to the next line, no results

What if you install the driver with this command
```
sudo modprobe go7007
```
and then test again with
```
lsmod | grep go7007
```

---

### Post by 1976MrEMan on 2012-08-06
That actually spurns a result...

go7007                 59318  0 
v4l2_common            15793  1 go7007
videodev               86588  2 go7007,v4l2_common
snd_pcm                80845  3 go7007,snd_hda_intel,snd_hda_codec
snd                    62064  16 go7007,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

I'm a total noob, does this mean the device driver is installed? Also, I have no clue where to go from here...

UPDATE: I ran lsusb and in the results i see my video capture device listed, so it is definitely installed. Now to configure it (oh boy) to record video input. My guess is to use vlc player for the handy 'Open Capture Device' option. I guess just play with settings?

---

### Post by 1976MrEMan on 2012-08-06
Ah, I'm meant to install a patch first, located here: [http://jeff.ourexchange.net/wp-content/uploads/2010/03/wis-go7007-linux-098-5-20100325.diff](http://jeff.ourexchange.net/wp-content/uploads/2010/03/wis-go7007-linux-098-5-20100325.diff)
Any advice on how to set this up would be appreciated. In the meantime, I'll continue googling and exprimenting...
I'm not sure if i applied the patch, basically i just typed sudo apt-get patch, but i don't know that that did what i intended.

---

### Post by David Andersson on 2012-08-06
> **1976MrEMan said:**
> 
UPDATE: I ran lsusb and in the results i see my video capture device listed, so it is definitely installed. Now to configure it (oh boy) to record video input. My guess is to use vlc player for the handy 'Open Capture Device' option. 

There are many programs that captures from a video input device. You can try VLC as you said. Or try Cheese, or Kino, or XawTV. I really don't know who is easier to use, but Cheese or Kino looks easier. There are probably many more.

> **1976MrEMan said:**
> Ah, I'm meant to install a patch first, /.../

I'm not sure if i applied the patch, basically i just typed sudo apt-get patch, but i don't know that that did what i intended.

I think you have not. The modprobe command installed the go7007 driver that comes with the kernel in ubuntu. Jeffs blog claims a patch was needed (for your card) in 2007 and in 2010. I don't know if it is still needed in 2012.

Someone could research what version the current go7007 is and what version of go7007 the patch is for. If it's the same the patch is very probably needed. If the current is newer, someone could look into the ChangeLog of go7007 for clues, or someone could just try the current go7007 and see if it works.

What you installed (patch) is a program to apply a patch (a *.diff or *.patch file) to some source code (extracted from a .tar or .tgz or downloaded with git or svn).

IF the current go7007 does not work with your card, and we know it for sure, then you could try to apply the patch from Jeffs blog and apply it to the source code linked from the same page in that blog. Then we know the patch is for that version of go7007, and the result claims to work with your card. (But we don't know if the result works with your current kernel. Then, in 2010, kernel 2.x was normal and now 3.x.)

---

### Post by 1976MrEMan on 2012-08-06
> **David Andersson said:**
> There are many programs that captures from a video input device. You can try VLC as you said. Or try Cheese, or Kino, or XawTV. I really don't know who is easier to use, but Cheese or Kino looks easier. There are probably many more.



I think you have not. The modprobe command installed the go7007 driver that comes with the kernel in ubuntu. Jeffs blog claims a patch was needed (for your card) in 2007 and in 2010. I don't know if it is still needed in 2012.

Someone could research what version the current go7007 is and what version of go7007 the patch is for. If it's the same the patch is very probably needed. If the current is newer, someone could look into the ChangeLog of go7007 for clues, or someone could just try the current go7007 and see if it works.

What you installed (patch) is a program to apply a patch (a *.diff or *.patch file) to some source code (extracted from a .tar or .tgz or downloaded with git or svn).

IF the current go7007 does not work with your card, and we know it for sure, then you could try to apply the patch from Jeffs blog and apply it to the source code linked from the same page in that blog. Then we know the patch is for that version of go7007, and the result claims to work with your card. (But we don't know if the result works with your current kernel. Then, in 2010, kernel 2.x was normal and now 3.x.)


This has gone so far beyond my understanding. I think the appropriate response is to dual-boot with windows, which is unfortunate because this was the only thing left to do to get away from microsoft entirely. Thanks for your help, and i'll perhaps look into this again in the future.

---

### Post by gordintoronto on 2012-08-06
In Linux, upper and lower case matter. So, "Documents" and "documents" are completely different places. From your earlier posts, I suspect this has been an issue for you.

Good luck in your search.

---

