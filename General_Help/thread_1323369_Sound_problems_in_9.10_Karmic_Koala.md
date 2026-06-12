---
title: "Sound problems in 9.10 Karmic Koala"
date: 2009-11-11
forum: General Help
---

### Post by Tiganjero on 2009-11-11
In Ubuntu 9.04 everything worked perfectly... After I upgraded to 9.10, I've had a handful of problems, and managed to fix all of them but one. Every time I play a sound or a video file (same in all players) or an application sound plays, the output sound is distorted, crackling and quite annoying. I have tried to fix it using these tutorials [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384) [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012), but had no luck. Thanks! :D

---

### Post by VMOS on 2009-11-11
this might help, I had lots of random pops come out of my speakers

open this file /etc/modprobe.d/alsa-base.conf

find this line

options snd-hda-intel power_save=10 power_save_controller=N


change it to

#options snd-hda-intel power_save=10 power_save_controller=N

save and reboot, see how that goes

---

### Post by Tiganjero on 2009-11-12
I tried commenting out the last line of that file which didn't work. I also tried replacing power_save=10 with power_save=0, which also had no effect. Thanks for the effort anyway VMOS. :)

EDIT:
Ok, so now I'm pretty sure that I got Pulseaudio working heres the output
```
tiganjero@Dolphin:~$ pulseaudio
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
```
Using a bunch of threads I found here, I have managed to fix a lot of stuff and make 90% of this work, I think that my main problem now is (after fixing Pulseaudio) that I can't open System>Preferences>Default Sound Card. I also tried running it from the terminal
```
tiganjero@Dolphin:~$ asoundconf-gtk
sh: /usr/bin/asoundconf: not found
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!

```
Can anyone who has had this problem before help me?
Thanks, George :)

---

### Post by Tiganjero on 2009-11-12
bump

---

### Post by Tiganjero on 2009-11-12
bump
Sorry to bump again, but this is really important.

---

### Post by Tiganjero on 2009-11-13
Bump. #3 :P

---

### Post by nadian on 2009-11-13
have you tried?
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Tiganjero on 2009-11-13
> **nadian said:**
> have you tried?
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Umm, this is all about alsa, isn't my problem Pulseaudio? Anyway, thanks for replying it seems that no one knows how to fix this problem...

Cheers,
George

---

### Post by Tiganjero on 2009-11-14
bump #4

---

### Post by nerdy_kid on 2009-11-14
i had crackling issues with libsdl (compleatly unrelated i know; either this or bump #5), have you tried
```

pulseaudio --kill

```

and then try playing audio?

(you might have to restart some music players; such as amarok)
 or switch to KDE and forget pulseaudio....

---

### Post by Tiganjero on 2009-11-14
> **nerdy_kid said:**
> i had crackling issues with libsdl (compleatly unrelated i know; either this or bump #5), have you tried
```

pulseaudio --kill

```

and then try playing audio?

(you might have to restart some music players; such as amarok)
 or switch to KDE and forget pulseaudio....

Thanks a lot, it completely fixed my problem. Guess theres no need for bump #5 :P

EDIT:
Well... not completely... :) but it's good enough :P Thanks!

Cheers,
George

---

### Post by nerdy_kid on 2009-11-14
glad to help!  as a sidenote, i fixed the libsdl issue which was crashing pulse by 
```

sudo apt-get install libsdl1.2debian-pulseaudio

```i dont know if this will fix it all the way; but give it a shot :)

---

### Post by Tiganjero on 2009-11-14
I noticed that when playing a mp3 file, it's very good, almost perfect. But when I tried playing a video, the sound was the same as before... Also all the system, and application sounds are still distorted. I already have this package installed... Will removing all the Pulseaudio packages help?

---

### Post by nerdy_kid on 2009-11-14
it would fix it....but also disable more then on app playing sound at a time...try KDE?

---

### Post by Tiganjero on 2009-11-14
Umm... I tried playing a sound file with VLC, it was ok. Then I tried playing a video file, again with VLC, and it was horrible, just like before... So ```
pulseaudio --kill
``` only fixed sound file reproduction, but the video and the system and application sounds are still distorted. Will removing all of Pulseaudio packages fix my problem? And why should I try KDE? What does it have to do with sound? :)

Cheers,
George

---

### Post by nerdy_kid on 2009-11-14
pulseaudio is optional in KDE (id do a little research first, i am only 80% sure)

try to set the audio system in the apps you use to pulse.

OH with vlc MAKE SURE the video drivers arnt sdl -- there is a bug ([https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/461221](https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/461221)) that i posted about this, and i was told it is libsdl -- so avoid it whenever possible.

---

### Post by Tiganjero on 2009-11-14
> **nerdy_kid said:**
> pulseaudio is optional in KDE (id do a little research first, i am only 80% sure)

try to set the audio system in the apps you use to pulse.

OH with vlc MAKE SURE the video drivers arnt sdl -- there is a bug ([https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/461221](https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/461221)) that i posted about this, and i was told it is libsdl -- so avoid it whenever possible.

I'll first try removing all the Pulseaudio packages, and then I'll check KDE out. I have set Pulseaudio in VLC. The music is ok, but the **sound** in the videos is still the same...the video is ok but the sound in it isn't... I'll test some things and post it later...

Cheers

---

### Post by Tiganjero on 2009-11-14
I didn't manage to get Pulseaudio to work, though removing all of the Pulseaudio packages restored my clear sound. I have tried KDE, I didn't use it enough to have an opinion about it, but the sound is even worse... For the 16 other who voted yes I suggest you do the same, if you still have this problem. I don't know how this 'solution' affects games in Ubuntu, though I think that everything will work perfectly. Hope this helped someone.

Cheers,
George

---

### Post by shannon.jacobs on 2009-11-29
Basically bumping the thread for two more machines (because this is the top-rated Google result for "sound problem koala". As near as I can tell, the problem is NOT solved, and it is beyond my 'job requirements' to be fixing what seems to be a pretty basic lack of competent testing at the Ubuntu end... 

First machine is a Lenovo X61 running Ubuntu using VMware Player. I'm not sure when it was first set up, but a while ago, and it has been working without problem for several upgrades--until Koala, which has completely killed the sound.

Second machine is a Sharp notebook. It's a couple of years old, and I've already forgotten the exact model number, but it's been running Ubuntu for some years. Actually it has several partitions with various versions of Ubuntu. First I tried it with the Live CD for Koala. It boots, but no sound. Then I upgraded one of the scratch partitions to Koala, which seemed to complete, but again, no more sound.

I really hate Microsoft, I somewhat dislike Apple, and I'd really like to see Ubuntu (or some other Linux distro) succeed as a real alternative for real choice and real freedom--but this sort of basic failure with pretty basic functions makes me despair of success.

---

### Post by Tiganjero on 2009-11-30
My problem was that sound was crap, crackling, distorted and very very annoying. I actually did solve it, with going back to alsa. System sounds are back to normal too, but I don't know why because they are set to use Pulseaudio, and this cannot be changed... I would suggest that (if you don't find a solution for your problem) you go back to Ubuntu 8.10 LTS.

Cheers

---

