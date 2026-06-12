---
title: "Can't quit Motion in the terminal"
date: 2011-07-26
forum: General Help
---

### Post by rapattack1 on 2011-07-26
I have installed this but it is command line and i don't know how to quit the thing. Motion is command line. It keeps capturing unless i shutdown the computer. Very frustrating. I also would like help to understand how to configure Motion if someone can fill in the information gaps on this website
[http://www.chriswpage.com/2009/05/setup-an-advanced-webcam-security-system-with-ubuntu-8-04-and-motion/](http://www.chriswpage.com/2009/05/setup-an-advanced-webcam-security-system-with-ubuntu-8-04-and-motion/)
I have also tried zoneminder but it does not want to run for some reason. I have gone to the zoneminder forum and asked but i don't seem to get very far. They got me to download a zoneminder/ubuntu live cd. I used that but it wasn't seeing the camera. Whereas on the distro i have right now cheese, kamoso so see it.
I can live stream with Motion within firefox but i need the motion capturing part configured and without something that will quit Motion the app it's a bit useless. Would appreciate some advice as i have been struggling a long time trying to get this security thing happening

---

### Post by blind2314 on 2011-07-26
> **rapattack1 said:**
> I have installed this but it is command line and i don't know how to quit the thing. Motion is command line. It keeps capturing unless i shutdown the computer. Very frustrating. I also would like help to understand how to configure Motion if someone can fill in the information gaps on this website
[http://www.chriswpage.com/2009/05/setup-an-advanced-webcam-security-system-with-ubuntu-8-04-and-motion/](http://www.chriswpage.com/2009/05/setup-an-advanced-webcam-security-system-with-ubuntu-8-04-and-motion/)
I have also tried zoneminder but it does not want to run for some reason. I have gone to the zoneminder forum and asked but i don't seem to get very far. They got me to download a zoneminder/ubuntu live cd. I used that but it wasn't seeing the camera. Whereas on the distro i have right now cheese, kamoso so see it.
I can live stream with Motion within firefox but i need the motion capturing part configured and without something that will quit Motion the app it's a bit useless. Would appreciate some advice as i have been struggling a long time trying to get this security thing happening
 
 
Post the output of ```
 ps -ef | grep -i mot
```. Assuming the process has something with *mot* in the name, that should find it.

---

### Post by rapattack1 on 2011-07-26
Is this it
> root      6409     1  3 01:29 ?        00:01:38 motion
root      6535     1  1 01:33 ?        00:00:56 motion
carla    10031 10009  0 02:21 pts/2    00:00:00 grep --color=auto -i mot


---

### Post by blind2314 on 2011-07-26
> **rapattack1 said:**
> Is this it
 
 
Possible. Try ```
sudo kill 6409
sudo kill 6535
``` and wait a few seconds. Run the ps command again, and see if they're gone.
 
If not, do this (DISCLAIMER: This can cause data corruption for the file that is actively being written to, if there is one).
 
```
sudo kill -9 6409
sudo kill -9 6535
```

---

### Post by rapattack1 on 2011-07-26
Actually i found this video on youtube yesterday [http://www.youtube.com/watch?v=rzrXJLdNHwM&feature=related](http://www.youtube.com/watch?v=rzrXJLdNHwM&feature=related) and got as far as finding the 'scripts' folder....problem is it is not where they say it is. Can anyone tell me as i was making good progress. I wanted to log into youtube to ask the person that made the video but can't remember my damn password :0)

Finally reset my password so was about to post about where the scripts directory is....in the meantime can anyone tell me here on?

---

### Post by rapattack1 on 2011-08-10
Well it seems that all i have to do is close the terminal and that quits Motion. Pity it took a lot of observation to come to that conclusion lol....wish i could work out the other stuff. Seems to be no forum anywhere that anyone knows how to use Motion...such a pity because it has so much potential

---

### Post by realzippy on 2011-08-10
[I]"...that anyone knows how to use Motion"
[/I]
*Kenneth Lavrsen* has an extremely helpful motion documentation;
used it years ago setting up motion:

[http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome)

---

### Post by rapattack1 on 2011-08-10
Thanks that is the first thing i found but it is not basic enough for a beginner. There is too much terminology. I got motion going by using a youtube video [http://www.youtube.com/watch?v=rzrXJLdNHwM](http://www.youtube.com/watch?v=rzrXJLdNHwM)
but i got stuck at when i had to do something with the scripts folder near the end of part one. There is no scripts folder. I created it but it does not contain what i need to continue with part two of the tutorial video

---

### Post by realzippy on 2011-08-10
Will have a look at this video.
What exactly do you want motion to do?Maybe I can assist a little...

---

### Post by rapattack1 on 2011-08-10
Well near the end of that video(part 1) there is a mention of the scripts folder. I want to keep following the video. But i can't when i can't. I have been using motion anyway but gee there are a thousand questions. This video has motion synced with dropbox but i had to change the target directory as dropbox has a maximum of 2gb that it can hold and that got full quick. Plus i want to record video as well not just video/snapshots. Anyway if i can progress further it would be most helpful. I am using this as a security camera as i have junkie neighbours that get up too all sorts of theiving and damage to everyones properties

---

### Post by realzippy on 2011-08-10
Yep,forget about dropbox.
Create a folder and send the pictures/movies there.
The script folder is not there by default,the lovely lady with that lovely 
sweater created it...you can also create that folder by
```
mkdir scripts
```

Don 't understand exactly:
*Plus i want to record video as well not just video/snapshots.*

You want a separate folder for snapshots and videos?


Btw,there is also part 2 of that video on youtube...

---

### Post by rapattack1 on 2011-08-10
No i created the scripts folder. I didn't see her create the folder. She has contents in that folder that i do not have.

Sorry i made a typo. I want to capture audio as well as the video. I don't know how to do that.

---

### Post by realzippy on 2011-08-10
Don 't think motion is made for audio also,cannot find anything about audio
in the motion.conf file.
Will search for it..

---

### Post by rapattack1 on 2011-08-10
Ah ok yeah i can't find anything either but i am too inexperienced to know what to look for he he.
I did try to get zoneminder and mythtv working as well but i am not getting very far with that. I can open mythtv but there is a lot i don't understand. I tried to get zoneminder working on its own but can't get anything in the browser at all :0(

---

### Post by realzippy on 2011-08-11
Indeed no sound:

Motion - Feature Request
[http://www.lavrsen.dk/foswiki/bin/view/Motion/FeatureRequest2005x05x07x154113](http://www.lavrsen.dk/foswiki/bin/view/Motion/FeatureRequest2005x05x07x154113)

---

### Post by rapattack1 on 2011-08-11
Thanks for that info. Its a pity but maybe i can get zoneminder and mythtv working one day

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

### Post by rapattack1 on 2011-08-23
OK was hoping that someone would jump on the comment about mythtv or zoneminder. Its frustrating that no one seems to know :0(

---

### Post by netherstar on 2012-11-01
Cannot comment on mythtv or others, but I have found the "official" way to end motion.  Unfortunately, it is much as what has already been mentioned.  
First run the ps and grep commands to find the process id.  Then run:

kill -s SIGTERM <pid>

Doing it this way will allow motion to politely end any movie it is currently making before terminating.  You can also do this with SIGHUP to reload the config file.

---

### Post by rapattack1 on 2012-11-02
Hi thanks i can't remember but i think i had different cameras when i used motion. Now i have ethernet cameras and they are being used with my windows machine. I wish i had a linux solution

---

