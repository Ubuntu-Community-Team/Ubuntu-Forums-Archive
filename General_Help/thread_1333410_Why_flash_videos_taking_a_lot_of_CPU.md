---
title: "Why flash videos taking a lot of CPU?"
date: 2009-11-21
forum: General Help
---

### Post by mirchichamu on 2009-11-21
I have noted that when I plash any flash videos OR facebook application, my CPU usage hikes to 50 to 60 %, why? And laptop become hot.
Any suggestion. Thanks.

---

### Post by eriqjaffe on 2009-11-21
Flash is a CPU hog, basically.

The new 10.1 beta is supposed to be able to offload some of the processing to the GPU, but I haven't tried it out yet.  You can install it by following the steps [here](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-1-beta-in-ubuntu.html), if you're interested.

---

### Post by mirchichamu on 2009-11-21
> **eriqjaffe said:**
> Flash is a CPU hog, basically.

The new 10.1 beta is supposed to be able to offload some of the processing to the GPU, but I haven't tried it out yet.  You can install it by following the steps [here](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-1-beta-in-ubuntu.html), if you're interested.

Thanks eriqjaffe for your support.
I will wait for the final release. I am having x64 version of utbuntu.

---

### Post by NoaHall on 2009-11-21
> **mirchichamu said:**
> Thanks eriqjaffe for your support.
I will wait for the final release. I am having x64 version of utbuntu.

Do you use the proper 64 bit version of Flash then?

---

### Post by mirchichamu on 2009-11-21
> **NoaHall said:**
> Do you use the proper 64 bit version of Flash then?

Thanks NoaHall once again for coming to my help.
How do I know that I am having 64bit flash?

Thanks again.

---

### Post by pfcosta on 2009-11-21
> **mirchichamu said:**
> I have noted that when I plash any flash videos OR facebook application, my CPU usage hikes to 50 to 60 %, why? And laptop become hot.
Any suggestion. Thanks.
Are you using Adobe's flash or the open source one? This made a huge difference in my case. Note that by default you're probably using the open source one.
(altough I'm all for open source, I had to open an exception on this one...)

---

### Post by mirchichamu on 2009-11-21
> **pfcosta said:**
> Are you using Adobe's flash or the open source one? This made a huge difference in my case. Note that by default you're probably using the open source one.
(altough I'm all for open source, I had to open an exception on this one...)

Thanks pfcosta for reply.
I don't know actually. How do I know that?
Need further help.

---

### Post by Bobhuber on 2009-11-21
[http://ubuntuforums.org/showthread.php?p=8342697#post8342697](http://ubuntuforums.org/showthread.php?p=8342697#post8342697)

Go to this link if you are using the 64 bit    version of Ubuntu.
It solved my problem completely (same one).

---

### Post by Treeh on 2009-11-21
> **mirchichamu said:**
> Thanks pfcosta for reply.
I don't know actually. How do I know that?
Need further help.

How did you install it?

Did you download the .so Firefox plug-in file from Adobe Labs?

Also, could you give any indication of what your Laptop's specs are?

---

### Post by lisati on 2009-11-21
Processing video data in general can be a resource hog, not just when using Flash. Example: I have several hours of video I recorded at a series of meetings the other week.. Yesterday I was working on a 40-minute section where back-lighting was a problem for me, and some portions ended up with the people looking very dark. Selecting which portions to fix up digitally was fairly easy and didn't take too long, but rendering (applying) the "fix up" effects I'd selected took something like 12 hours. (Since doing the initial recording I've partially figured out setting the camera manually rather than relying on the camera's automatic exposure)

---

### Post by Bobhuber on 2009-11-21
[http://ubuntuforums.org/showthread.php?t=1259102]("http://ubuntuforums.org/showthread.php?t=125910")


Sorry I posted the wrong link. This is the one you want. Thread 1259102

---

### Post by mirchichamu on 2009-11-21
Thanks bobhuber and Treeh!
What a community? I appreciate your help.
Actually I forgot. I downloaded one 64 bit version from adobe but I don't know whether I installed it or not. Is there any way to know what version I have?

---

### Post by Treeh on 2009-11-21
> **mirchichamu said:**
> Thanks bobhuber and Treeh!
What a community? I appreciate your help.
Actually I forgot. I downloaded one 64 bit version from adobe but I don't know whether I installed it or not. Is there any way to know what version I have?

I suppose the simplest way is to simply check if you have the .so file or not...

```
locate libflashplayer.so 
```

Edit note: sorry for the previously incorrect .so file

---

### Post by mirchichamu on 2009-11-21
> **Treeh said:**
> I suppose the simplest way is to simply check if you have the .so file or not...

```
locate libflashplayer.so 
```

Edit note: sorry for the previously incorrect .so file

Thanks treeh once again.
I got the following response. See attachment.
I am using Toshiba satellite A205-S5880 Intel coe duo T2390
Ram 3Gb, HDD 200 GB.

---

### Post by Bobhuber on 2009-11-21
That thread I gave you will show you how to uninstall the wrong .so file and install the correct version.

---

### Post by Treeh on 2009-11-21
> **mirchichamu said:**
> Thanks treeh once again.
I got the following response. See attachment.
I am using Toshiba satellite A205-S5880 Intel coe duo T2390
Ram 3Gb, HDD 200 GB.

```

sudo rm /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so 
cd ~/Downloads/
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar xvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz 
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo rm libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz 

```

Restart Firefox, and you're set.

If you still have CPU issues, consider 10.1...although I didn't see an x64 release of it...is there one?

---

### Post by mirchichamu on 2009-11-21
> **Bobhuber said:**
> That thread I gave you will show you how to uninstall the wrong .so file and install the correct version.

Thanks bobhuber for help. I will give a try.

---

### Post by mirchichamu on 2009-11-21
> **Treeh said:**
> ```

sudo rm /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so 
cd ~/Downloads/
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar xvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz 
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo rm libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz 

```

Restart Firefox, and you're set.

If you still have CPU issues, consider 10.1...although I didn't see an x64 release of it...is there one?

Thanks Treeh! You are No 1.
It worked. Now CPU usage is less than before. One million thanks.

---

### Post by ajgreeny on 2009-11-21
I have also installed the new beta version of flash 10.1, and can also confirm that it is not such a cpu hog as the 10.0 version.  I have only just done this a half hour ago, but so far all looks good; cpu is down from an average of around 55% to 20 - 40%.  It varies quite a lot from moment to moment, just as 10.0 did, but seems that bit lower overall.

I simply downloaded the new tar.gz and extracted it to my disk, then manually copied the libflashplayer.so file it contained to /usr/lib/adobe-flashplugin, having first renamed the present 10.0 file to a backup, just in case the new one does not work properly.

EDIT
I have just noticed that a lot of youtube flash videos that work well in flash 10 produce a colour rendering problem with flash 10.1, making the picture worse than useless and totally unwatchable, so have gone back to flash 10.

Ah well, one step forward, two steps back, again.

---

