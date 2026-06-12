---
title: "Audacity"
date: 2011-12-06
forum: General Help
---

### Post by cwejg on 2011-12-06
Hello,
In way over my head here, trying to open mp4 files but audacity closes soon as I select a mp4 file. mp3 files will open ok. If I start Audacity from the command line I get this message:

chuck@chuck-laptop:~$ audacity
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Expression 'stream->capture.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3653

Hope someone can help. Sorry I selected lubuntu and it should have been Ubuntu

Thanks,
Chuck

---

### Post by phidia on 2011-12-06
The error output is related to bluetooth. Are you using bluetooth on this computer?

Try > sudo apt-get remove bluez-alsa and see if the problem goes away.

---

### Post by cwejg on 2011-12-06
> **phidia said:**
> The error output is related to bluetooth. Are you using bluetooth on this computer?

Try  and see if the problem goes away.

That cleared the bt errors but still have



Expression 'stream->capture.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3653

---

### Post by phidia on 2011-12-06
Module isn't loaded methinks.

Try > modprobe -r snd-ens1371 && modprobe snd-ens1371

(you might need to use sudo?) If that works add the module(s) to /etc/module
If this doesn't solve your problem though you can try searching the multimedia forum here there are some [related threads]("http://ubuntuforums.org/showthread.php?t=1439440") there.

---

### Post by Rodney9 on 2011-12-06
See This site - [http://getch.wordpress.com/2009/08/13/playing-mp4-files-in-linux/](http://getch.wordpress.com/2009/08/13/playing-mp4-files-in-linux/)

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by SteveDee on 2011-12-07
> **cwejg said:**
> ...In way over my head here, trying to open mp4 files but audacity closes soon as I select a mp4 file...

Surely Audacity is an audio editor, and MP4 is a video container format?

If you want to play MP4 try SMplayer or VLC, and if you want to edit it try Avidemux.

---

