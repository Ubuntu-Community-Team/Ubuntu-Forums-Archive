---
title: "Karmic (amd64) - Memory usage never exceeds 1gb"
date: 2010-03-10
forum: General Help
---

### Post by quequotion on 2010-03-10
Hello!

This may not be a problem... it just strikes me as odd.
Currently I have one instance of Avidemux indexing a 16GB mpeg2 file, another instance of Avidemux transcoding a 4.7GB mpeg2 file into an 860MB mpeg4 (by two pass encoding with fully exhaustive motion detection, extra quality filters, and a wide VBR range), vlc playing a DVD-quality avi, totem playing a DVD-quality ogm, and I'm capturing video from a pvr card.. With compiz managing the desktop (with all the most disgusting eyecandy on: wobbly windows, Atlantis, desktop sphere, experimental plugins from git, etc).

My processor (3GHz Athlon x2) is completely maxed out of course... but I can't seem to raise the memory usage over "1.2GiB (16%) of 7.8 GiB"

Is that normal? Is there something else I could do to test my memory capacity? (as in really useful applications, not just benchmarks)?

Alternatively, if karmic is never going to use the rest of that memory, I might opt to run some parts of the desktop environment and/or kernel from a ramdisk... Any ideas for implementation?

Also, three cheers for Karmic simply refusing to lock up. Today is day three of this contious test (actually it only doubles as a test; I'm converting my friend's complete TOHO Monster Movie collection from VHS to digital & DVD with as much quality retention/improvement as possible)

---

### Post by iponeverything on 2010-03-10
I think it sounds right. There appears to be a bottleneck in the system somewhere, probably the CPU considering what you are doing at the moment. My guess is that the applications are designed to grab a big chunk of data and load it into memory for encoding.

---

### Post by rnerwein on 2010-03-10
hi 
i guess for your aplikation Avidemux exists a config file where you can configure the maximum
usage of memory ( a couple of applications works in that way ). if it so then it's are good aplikation.
i'm sure that karmic can address high memory - my own experience.
ciao

---

### Post by quequotion on 2010-03-10
[QUOTE=iponeverything]There appears to be a bottleneck in the system somewhere, probably the CPU [/QUOTE]

Could it be that the program is blocking itself this way? Everything appears to be running smoothly. Even dragging the avidemux window around each side of the desktop makes very little impact on performance of either it or compiz. I can use my computer normally as well, even though my cpu is at 100% (***great*** scheduling in kernel 2.6.32-14?).
 
> My guess is that the applications are designed to grab a big chunk of data and load it into memory for encoding.

I agree. I wonder how big a chunk avidemux uses and if it can be increased... I feel like that would speed up the transcoding process, but I could be wrong.

[QUOTE=rnerwein]a config file where you can configure the maximum
usage of memory ( a couple of applications works in that way )[/QUOTE]

There's nothing in the GUI or the text config file for Avidemux, but it's pretty much a front end for either ffmpeg or mencoder which I believe *do* have such an option. I am not using either cli because the features are almost entirely undocumented and I'm not an expert on transcoding.

> i'm sure that karmic can address high memory - my own experience.

May I ask what you were doing and how much memory did Karmic successfully address?

---

### Post by iponeverything on 2010-03-10
I have had karmic use every last bit of memory on 1TB squid server with 8 gigs of ram. (300 clients at any one time).

---

### Post by quequotion on 2010-03-10
> **iponeverything said:**
> I have had karmic use every last bit of memory on 1TB squid server with 8 gigs of ram. (300 clients at any one time).

Wow!

---

### Post by 3rdalbum on 2010-03-10
Your system can grab data from the hard disk and put it into memory quicker than it can be processed and transcoded, so I wouldn't worry about the memory use.

I'm guessing the 1.2 GiB is active memory use. Linux also caches data into RAM; this is data that might not need to be used again, but if it is needed it'll be there. If something else "actively" needs that RAM, the data will be purged. I'm pretty sure you'll have more than 1.2 GiB being used in some capacity.

---

### Post by egalvan on 2010-03-10
This post is similar to another I read, so the answer will be similar...

Linux Is Not Windows

Linux utilizes RAM more efficiently.. one reason it´s RAM requerements are usually lower than Windows.

If your processes are only utilizing 1.2GB, then that is all that is needed...

Checking swap usuage will tell the tale... I bet that swap is never touched on your machine.

> I might opt to run some parts of the desktop environment and/or kernel from a ramdisk... Any ideas for implementation?

Sure... let the kernel take care of it... :p

Seriously, the kernel (all or parts), the DE, or any other program and/or data is never swapped out untill RAM is low... so what advantage will this bring? Linux Is Not Winows.

Now, certain temp directories or log files may benefit being in a ramdisk.
Just make sure any needed data (especially logs) is flushed correctly.

Also, as others have stated, checking the apps you are using for options to use a larger buffer *may* yield better results..
but many apps size their buffers as a percentage of RAM, so this probably *not *yield performance gains (or gains so small as to be insignificant).

The app needs to be I/O bounded to show good benefits from a larger buffers/work space, and yours may be process bounded...


But in the end, it´s your RAM, your time, and your call.
Certainly it will be a learning experience and/or fun, and that can be a good thing ;)
I always enjoy learning new things. :p

---

### Post by no2498 on 2010-03-10
i may be off but to = things out
go to system preferences multimedia system selector click video
set the plugin to,x window system (no xv)

this comes from the cheese help faq's

gstreamer-properties in a terminal same window pops up

---

### Post by no2498 on 2010-03-10
sorry you may need to restart the computer be for you see it work

---

### Post by quequotion on 2010-04-12
> **egalvan said:**
> Linux Is Not Windows


I know this :) I just wondered if I could encourage the app to be a little less responsible with the memory.

I also enjoy learning new things, even if I do get a lot of headaches -_-

---

