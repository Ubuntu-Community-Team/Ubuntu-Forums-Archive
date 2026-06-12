---
title: "rip/copy internet radio"
date: 2011-02-09
forum: General Help
---

### Post by jerrrys on 2011-02-09
I have a need to rip/record some internet radio.  Im running Banshee and loaded the stream rip plugin, but haven&#8217;t got it working yet.  Also though it would be better if I just found a FireFox plugin, and I did; a ton of them.
   
  


[http://www.giveawayoftheday.com/record+streaming+audio+firefox+plugin/](http://www.giveawayoftheday.com/record+streaming+audio+firefox+plugin/)


    
    Anyone got a suggestion

---

### Post by Habitual on 2011-02-09
I have a terminal script that I use to record Grooveshark when I choose to.

Want to give it a spin?

---

### Post by jerrrys on 2011-02-09
love to

---

### Post by Habitual on 2011-02-09
[http://ubuntuforums.org/showpost.php?p=10191836&postcount=8](http://ubuntuforums.org/showpost.php?p=10191836&postcount=8)

Create it.
chmod it.
run it in terminal (leave it open in terminal)
Surf it.
Record it.

Lemme know!

---

### Post by ajgreeny on 2011-02-09
I use **streamtuner** and streamripper, to listen to and record most radio streams, but also used to use mplayer as well for some that streamed in realplayer file types, from the BBC.  Those are no longer available, so it is no longer needed, and streamripper has taken over mainly.

It is a command line application, but can easily be used in cron jobs to time recordings, for which I have written several shell scripts, depending on the length of the recording needed, eg
```
#!/bin/bash
/usr/bin/streamripper http://webaddress -t -r -d /home/username/Radio -l 7320
```where -t gives separate tracks for each use to save overwriting the previous one if you have not moved it, -r allows a localhost:8000 relay of the stream so you can listen without doubling the download size, -d is the destination, ie /home/username/Radio and finally, -l is the length in seconds (7320 being 2hours + 1 minute for safety).

---

### Post by jerrrys on 2011-02-09
that works great and nice touch converting it to wav; im going to us it.  thanks habitual

---

### Post by jerrrys on 2011-02-09
**streamtuner** and streamripper and mplayer; thanks for the tip

---

### Post by Habitual on 2011-02-09
jerrrys:

You're Very Welcome.

Glad it worked out.

Here's a tip:
sound_cap.sh "Stairway to heaven.wav"
else
sound_cap recording_DATE_TIME_STAMP.wav

to "name" them.

Have fun.

---

### Post by perezomail on 2011-02-10
> **ajgreeny said:**
> I use **streamtuner** and streamripper, to listen to and record most radio streams, but also used to use mplayer as well for some that streamed in realplayer file types, from the BBC.  Those are no longer available, so it is no longer needed, and streamripper has taken over mainly.

It is a command line application, but can easily be used in cron jobs to time recordings, for which I have written several shell scripts, depending on the length of the recording needed, eg
```
#!/bin/bash
/usr/bin/streamripper http://webaddress -t -r -d /home/username/Radio -l 7320
```where -t gives separate tracks for each use to save overwriting the previous one if you have not moved it, -r allows a localhost:8000 relay of the stream so you can listen without doubling the download size, -d is the destination, ie /home/username/Radio and finally, -l is the length in seconds (7320 being 2hours + 1 minute for safety).

streamripper link -r -l 400
now gives a command not found for -r 
before i used to be able to pick up the relay under 
vlc [http://localhost:8000](http://localhost:8000)

under help it now specifies 
-r [[ip:]port] - Create relay server on base ip:port, default port 8000
im having a little trouble understanding the syntax order of 
 [[ip:]port]

especially as to how it would now apply to vlc [http://localhost:8000](http://localhost:8000)
particularly as to which ip it would be asking for shoutcast or mine

these changes have not been added to yelp which gave me a good example to use before the change

any ideas?

---

### Post by ajgreeny on 2011-02-10
/usr/bin/gnome-mplayer [http://localhost:8000](http://localhost:8000) works for me , no problem, as does vlc, so I am baffled why it does not for you.

---

