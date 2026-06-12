---
title: "sound mixers"
date: 2006-05-28
forum: General Help
---

### Post by iamsobored0056 on 2006-05-28
is there a way to get everything to use the sound card at once?  if i have the music player running, there wont be sound on my mplayer plugin for firefox or stuff in youtube.  its getting really annoying to have to close everything to get sound to work.

---

### Post by Sutekh on 2006-05-28
Try these HOWTOs/Threads

[Ubuntu Forums - howto multiple sounds at once]("http://www.ubuntuforums.org/showthread.php?t=101125")

[Ubuntu Forums - Have an audigy? Want multiple sounds without ESD? Do this!]("http://www.ubuntuforums.org/showthread.php?t=104388")

[Ubuntu Forums - Happy ALSA, OSS, ESD, with Duplex - Sound Settings]("http://ubuntuforums.org/showthread.php?t=44753") - (check last pages for relevance to Ubuntu 5.10)

---

### Post by iamsobored0056 on 2006-05-28
oooo thanks a lot! im going to try it out.

---

### Post by iamsobored0056 on 2006-05-28
ok i got everything but the mplayer firefox plugin to work properly.  i still need to close everything that uses the sound for videos online to work.  besides that everything works fine.  how do i make the plugin use esd?

---

### Post by Sutekh on 2006-05-28
[quote=iamsobored0056]ok i got everything but the mplayer firefox plugin to work properly.  i still need to close everything that uses the sound for videos online to work.  besides that everything works fine.  how do i make the plugin use esd?[/quote]
I'm not all that sure.  I am stuck there too.  If you work it out let everyone know?

---

### Post by iamsobored0056 on 2006-05-28
stupid me, to change the mplayer firefox plugin settings just right click on a video and select configure.  then select audio output and change it to esd.  i don't know how to change the flash plugin though.

---

### Post by Sutekh on 2006-05-28
[quote=iamsobored0056]stupid me, to change the mplayer firefox plugin settings just right click on a video and select configure.  then select audio output and change it to esd.[/quote]Ha.  Too easy #-o 

[quote=iamsobored0056]i don't know how to change the flash plugin though.[/quote]I have no sound period with my flash plugin atm, sorry.

---

### Post by iamsobored0056 on 2006-05-28
so, does anyone know how to make flash plugin use esd?

---

### Post by iamsobored0056 on 2006-05-28
soooo, i was trying to figure it out and i stumbled on this 
[http://www.ubuntuforums.org/showthread.php?t=44753&highlight=mixer](http://www.ubuntuforums.org/showthread.php?t=44753&highlight=mixer)
unfortunately, that didn't do anything different so i found this:
[http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix](http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix)
and i found this a cool solution.  you just have to add aoss to the last line of /usr/bin/firefox!  ahh so simple!  anyway, here it is:
if you are using firefox 1.5 edit last line of /usr/bin/firefox
```
sudo gedit /usr/bin/firefox
```
then do this to the last line (add aoss after exec):
```
exec_verbose aoss ${MOZ_PROGRAM} "$@"
```
tada!!! it works!  hope this will help you guys

---

