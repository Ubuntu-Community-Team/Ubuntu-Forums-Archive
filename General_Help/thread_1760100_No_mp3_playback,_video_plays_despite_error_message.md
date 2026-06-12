---
title: "No mp3 playback, video plays despite error message"
date: 2011-05-16
forum: General Help
---

### Post by Niniel on 2011-05-16
After upgrading from 10.10, Banshee simply won't play mp3s, but Totem produces an error message:
> The playback of this movie requires a GStreamer element audioconvert plugin which is not installed.
Totem offers to search for a suitable plugin, but does not find GStreamer element audioconvert.
The same happens with flash and mp4 videos, except when I cancel the search for a plugin they are played back just fine, including sound. 
The system will also play the music when I hover over the file with the mouse pointer. 

I already tried several things, including uninstalling GStreamer plugins and then re-installing them.

Is there anything I can do other than installing Ubuntu from scratch, wiping out my current installation?

---

### Post by Hedgehog1 on 2011-05-17
If you have not done so already, please do this:

```
sudo apt-get install ubuntu-restricted-extras
```

***The Hedge***

:KS

---

### Post by Niniel on 2011-05-17
Thank you, but that did not help.
The two plugins **Gstreamer element audioconvert** and **Gstreamer element videoscale** still cannot be found.

---

### Post by oaxacamatt1 on 2011-05-17
Hi N,
Have you tried install all the 'bad' gstreamer plug-ins? Goto System/Adminstration/Synaptic Package Manager.  Then in the 'Quick Search' bar enter 'gstreamer' and 'bad'. You should see at least two plugins that will be useful.  Never mind the -dbg (debugging stuff).  Check the boxes on the left and apply.  You should need to re-install the whole OS for this problem.  YOu may want to goto the Ubuntu music forum for more specific questions, too.
Cheers
M

---

### Post by Niniel on 2011-05-18
I had all that, and then some.

What finally did point me in the right direction was this:
[http://www.fedoraforum.org/forum/showthread.php?t=256543](http://www.fedoraforum.org/forum/showthread.php?t=256543)

My ~/.gstreamer-0.10/ contained 2 files registry.i486.bin and registry.i686.bin. 

First I got rid of the i486.bin file - to no avail. Then I deleted the entire directory.
Now things are working fine.
The directory has also been re-created, with only registry.i686.bin in it.

---

