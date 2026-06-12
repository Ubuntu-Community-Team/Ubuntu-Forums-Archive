---
title: "Sound problems!"
date: 2010-12-04
forum: General Help
---

### Post by t0ncas on 2010-12-04
-hey, hi. This is my first post, and my very first stupid problem with ubuntu!  Get ready for the story...:popcorn:

i've used ubuntu several times as a normal average user, but a week ago i removed windows completely and kept just ubuntu 10.10 so that i can learn whatever i have to in order to work fine.
I'm not the kind of guy that gets scared for mess the whole s.o., so i moved a loooooot of things with ubuntu this week xD.
 
Now, the thing is that over the week i installed several applications to try (packages, dependences, all the ubuntu center said i needed, and compiled programs too, like cinelerra), but today i tried to play a xvid movie and it didn't work. The image looked slow, and the sound didnt play, and after a few seconds of playing, the movie player stopped with an error (right now, it doesn't matter wich one is it)

Thing is that.. with this error, i started an oddysey of mess over mess. I uninstalled every application i've installed over the week, and when it didn't worked as a solution, i went to synaptics and did a couple more of stupid things.
After all the things i played with, nothing substantial has changed on ubuntu; movies plays the same (with the same error), mp3 sounds fine, and everything's working.. except for the sound manager (when you clic on the sound button, it has an option that sais "Sound preferences". When i click it, nothing shows).
On the menu System - preferences, there's nothing for sound either.

As i said, sound plays just fine (if it's only sound)... but i'm interested on know wich package i have to put back on to be able to change the sound preferences. I was gonna reinstall ubuntu to start over again, but i decided to ask in order to learn something. First of all, i'm interested on knowing if someone knows how to get back the manager, and... later, if the advices are not "don't you ever play with the system again" and stuffs like that, i'll give the details of the video error so that you guys can help me to fix it.

Thanks for everything!!!

---

### Post by Spyderkid on 2010-12-04
You could go to System > Administration > Additional Drivers and install all the recommended drivers.

Also you could boot Ubuntu in Safe Mode and see if it repairs.

You can go to  System > Administration > System testing and skip the test till you get to the sound related ones and try them.

Also if you got the programs you were compiling from the internet they could of had malicious commands in them.

Go to System > Administration > Update manager and install any updates

Hope this is some help :)

---

### Post by t0ncas on 2010-12-05
it didn't work =( but thnx anyway! ;)

---

### Post by steelkitsune on 2010-12-05
Yeah, I've accidentally removed control features too. 

The terminal command to reach the main menu volume control is ```
gnome-volume-control
```

if that's the thing you're missing, i mean. If you key that into terminal and it still doesn't come up, you might be able to copy it back out of a live instance, since it's part of the gnome interface. it should be living in
```
/usr/bin/gnome-volume-control
```

If you punch it into terminal and it DOES work, you can always re-add it to the main menu through system>preferences>main menu and then fix it under that sound icon.

---

### Post by t0ncas on 2010-12-05
Wiiii!!!! it was that what i needed!! =D
I wrote the first command on a terminal window, and it showed me that the program wasn't installed. I used sudo apt-get to get it back, and now it's back there again!!
Huge Thanks!!

...as for the other problem, a couple of minutes ago i discovered that if i open the file with movie player and forward it before it plays the beginning, sound and movie play just fine, but if i let the movie player to start the movie from the beggining, it pops out four errors:

"disconnected
pa_stream_writable_size() failed...
disconnected
pa_stream_cork() failed.."

At least, i can watch my movie now! lol but if you (or someone) knows something about this behavior, it'll be great to fix it!

---

### Post by t0ncas on 2010-12-05
Hey!, my problem is solved now! =)
It seems that my problem was the configuration of the subwoofer. I have a home theater 4.1 from creative. In the sound preferences, when i put the output to 4.1 i cant play anything without hearing gapless and weird sounds. Then, i putted the output to 4.0 and sound plays very good.
About the problems i was having with video, it was related to the same. I changed the output to a simple Stereo Surround, and all the movies started and played perfectly good.

Thanx (in the first place) to [Spyderkid]("http://ubuntuforums.org/member.php?u=1191200") and to [steelkitsune]("http://ubuntuforums.org/member.php?u=745590") for the suggestion and solutions of the first part. That's why i could fix it :D

¡Open source rules! ;)

---

### Post by LinuxCharms on 2010-12-05
For sound you should check on Pulseaudio, that will let you change your sound settings.


As for the videos being slow, I have that problem too.
Check here: [http://www.ubuntugamer.com/2010/10/how-to-install-the-latest-proprietary-graphics-driver-in-ubuntu/](http://www.ubuntugamer.com/2010/10/how-to-install-the-latest-proprietary-graphics-driver-in-ubuntu/)

Also try to go into your Software Center and make sure you have all the needed flash stuff.

---

