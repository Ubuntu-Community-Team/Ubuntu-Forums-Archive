---
title: "PC Crashes using Skype with C310 Webcam"
date: 2011-06-23
forum: General Help
---

### Post by Mr_JMM on 2011-06-23
Hi,

I have found a few threads regarding this issue but none seem to be exactly what I've got or were too old to re-open the thread.

Ubuntu 11.04
Skype 2.2.0.35-1
Logitech Quickcam
Logitech C310 720HD webcam

Basic: Video call in Skype using the C310 causes the PC to crash at random times during the session. The quickcam seems to be ok, just an awful experience.
Thought it might be a pulseaudio problem so did the following:
added autospawn = no to .pulse/client.conf
killall pulseaudio
Restarted Skype
Changed audio settings in Skype to use MB chip ICH5
Restarted pulseaudio -D


No difference (if anything crashes quicker) except the CPU load is halved.

The pc freezes and is unresponsive. lights on keyboard flash.

I have no idea if this is sound or video card related.

Below is a link to a screen shot.

[Photo of screen errors]("https://picasaweb.google.com/lh/photo/FjW1GQZLm472tbkR_6UsYyKOrV62q6-jbo2nDmxb_r4?feat=directlink")

If anyone can help I'd be very grateful. Let me know if you need more info.

Cheers.

---

### Post by Mr_JMM on 2011-06-26
Can anyone help find out what's causing this?
Does the screenshot show anything relevant?

It now happens within 2 minutes of starting a video call but using an older webcam works ok (though the CPU temp climbs to nearly 70degrees.

System is old. P4 2.8, 1.5GB RAM, 128MB ATI Radeon 9200 GPU.

Camera works fine using Cheese and I can create video's ok. Only Skype has this issue and on;y with the newer web cam (though not tested GTalk Video call).

I'm really hoping the info in the screenshot will help point to the problem.

Cheers.

---

### Post by no2498 on 2011-06-26
does skype use adobe flash 
in fire fox look in tools abought plugins type in flash aid install it then run it
i could not read the screen shot

---

### Post by Mr_JMM on 2011-06-27
Flash is installed. Like I say, Skype works fine with old webcam.

What happened when you tried to open screenshot?

---

### Post by no2498 on 2011-06-27
it was a blur for me is all

---

### Post by Dragonbite on 2011-06-27
Since Skype updated my video didn't work even though it worked with the previous version.  At the same time, Cheese works fine.

I run it with ```
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```and the video works.

I am doubtful that this will solve your issue but it may be worth a try.

---

### Post by Mr_JMM on 2011-06-27
Thanks Dragonbite. I saw that posted a lot but thought it was only if you got no video at all. Have created a desktop shortcut and replaced the command with your reply.

Soon as I can will test and let you know.

Cheers.

---

### Post by no2498 on 2011-06-28
ill see if i can find the how to make that into a bin file

---

### Post by Dragonbite on 2011-06-28
> **no2498 said:**
> ill see if i can find the how to make that into a bin file

If you are referring to that the command I mentioned, I would first run it in a terminal and see if it works.

For me, I then went into the Menu Editor and changed it there.  This has been an off-and-on fight for me (depending on the distro and the version and the application).

---

### Post by no2498 on 2011-06-28
only after you tested it

3. Open the file as:
 arun@machinix:~$ sudo gedit /usr/local/bin/skype

 - Type in the following 

 #!/bin/bash
 LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype

 - Save and close the gedit.



[http://ubuntuforums.org/showthread.php?t=993262&highlight=skype&page=4](http://ubuntuforums.org/showthread.php?t=993262&highlight=skype&page=4)

its on like the sixth page

---

