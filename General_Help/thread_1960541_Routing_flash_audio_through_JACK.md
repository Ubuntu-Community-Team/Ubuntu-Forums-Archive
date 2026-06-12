---
title: "Routing flash audio through JACK"
date: 2012-04-17
forum: General Help
---

### Post by sirriffsalot on 2012-04-17
Hey!

I am on a Dream Studio distribution based on Ubuntu, and as great as it is I am having trouble routing flash video audio to JACK...

I'm following this guide [http://jackaudio.org/routing_flash](http://jackaudio.org/routing_flash) but get stuck at the "make" stage where the end output is

```
 flashsupport.c:184:28: fatal error: linux/videodev.h: No such file or directory
compilation terminated.
make[1]: *** [libflashsupport_la-flashsupport.lo] Error 1
make[1]: Leaving directory `/home/sirriffsalot/libflashsupport-jack'
make: *** [all] Error 2 
```

Any ideas?:) I've tried installing headers, various lib dev packages already, so I can't imagine what the issue may be.. Cheers!

- LTB

---

### Post by sirriffsalot on 2012-04-18
bump :)

---

### Post by HiImTye on 2012-04-18
[http://jackaudio.org/routing_alsa](http://jackaudio.org/routing_alsa)

---

### Post by sirriffsalot on 2012-04-18
Pay attention, lol:) I've already tried, it's the guide I'm having trouble with

---

### Post by HiImTye on 2012-04-18
no, you are having troubles with the 'routing_flash' page, I linked the 'routing_alsa' page which is straight forward and doesnt require any compiling. just install libasound2-plugins and paste the stuff into the files it tells you to

---

### Post by sirriffsalot on 2012-04-18
Ah, yes, my apologies... But this solution I have tried and is as the guide says very unhandy for the purposes I need this. I would really appreciate getting it routed the way the first guide suggests...:)

---

### Post by HiImTye on 2012-04-18
are you not using Ubuntu? ALSA should be your default sound system so the method I linked should work perfectly

---

### Post by sirriffsalot on 2012-04-18
I am using Dream Studio like I said in the beginning, which has Ubuntu as it's basis :-P

---

### Post by HiImTye on 2012-04-18
[http://dream.dickmacinnis.com/forum/forum](http://dream.dickmacinnis.com/forum/forum)
I would give that a try as Im not sure how they have their sound system configured

---

### Post by sirriffsalot on 2012-04-18
Alright, I figured things out!

After a lot of asking and searching, I found this [http://aur.archlinux.org/packages.php?ID=26219](http://aur.archlinux.org/packages.php?ID=26219)

The solution is to edit the flashsupport.c file within your libflashsupport-jack file which you get from following the guide mentioned in the beginning [http://jackaudio.org/routing_flash](http://jackaudio.org/routing_flash). In the flashsupport.c file, press Ctrl + F and search for 

```
<linux/videodev.h>
```

once you find it, change what is within the "< >" to 

```
<libv4l1-videodev.h>
```

Save the file. Once that is done, follow the guide again and if everything seems to have installed successfully, restart your browser and go to a flash-player video (YouTube for example) and check in the "connections" tab in QJackCtl (graphical interface for the JACK server) whether the video's outputs have arrived. It should be noted that editing the file as described above will crash the flash plugin in Chromium and Firefox4 (x86_64), so keep the changes you are making in the back of your mind and save the webpage offering this solution somewhere in case you want to change it back later. 

I suspect this solution will be just as temporary relatively speaking, since the developer of the [http://jackaudio.org/routing_flash](http://jackaudio.org/routing_flash) setup does not have time to keep up with the changes that go on with Ubuntu, but hopefully someone else will pick it up. Hope this helps!

---

### Post by HiImTye on 2012-04-18
Ubuntu uses ALSA by default, and plugs into it using PulseAudio, so they don't really need to keep up with the changes for Ubuntu. it's other distros that are 'based on Ubuntu' but not Ubuntu that have problems

---

### Post by sirriffsalot on 2012-04-18
I've talked to a few, including the developer himself, who say that certain people using straight Ubuntu are also having problems. This is a temporary fix I suppose;)

---

### Post by HiImTye on 2012-04-18
people using straight Ubuntu would only have to use the first page I linked, creating an .asoundrc and installing 'libasound2-plugins'

---

### Post by sirriffsalot on 2012-04-19
Let's hope so! This is obviously for people who have modified their settings otherwise:-P Thanks for your help!

---

### Post by HuaiDan on 2012-04-23
I'm having the same exact issue. This is what I'm going to try when I get home to my Ubuntu box: Opening up flashsupport.c and deleting v4l defines. The archlinux link you posted says they're redundant anyway, and other research has led to the discovery that v4l is being phased out. I'm not sure how to comment them out, as they already appear to be commented out. As you can probably tell, I'm not a C programmer. I'll let you know how that works out.

---

### Post by HuaiDan on 2012-04-23
It works! All I did was edit the line in flashsupport.c
> #define V4L1
to read
> //#define V4L1

I also learned how to comment out a line in C.

---

