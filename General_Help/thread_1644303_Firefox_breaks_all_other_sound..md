---
title: "Firefox breaks all other sound."
date: 2010-12-13
forum: General Help
---

### Post by nickajeglin on 2010-12-13
Hi, I've been stuck in the windows side of my dual boot for about a month, I came back over to the ubuntu side and updated/upgraded and ran into this issue: When I log in everything sound related works fine. I can play audio and record audio off of the monitor using audacity. As soon as I start firefox though, all audio breaks. I can't play audio in any other program, recording in audacity fails, etc. Closing Firefox doesn't help, rebooting seems to be the only thing that works. I've already tried purging and reinstalling flash, but that doesn't seem to have had any effect. When starting audacity it throws this error: ```
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Expression 'stream->capture.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3653
```

I'm on Lucid if that is of any relevance. It seems to me that firefox is monopolizing the audio device both while running and after it closes. What is odd is that I've never had this problem before, and all I did was update. Any help would be wonderful, but I often run audio in firefox and record it with audacity, so a fix allowing both programs to run in parallel would be great.

Thanks,

Nick

p.s. I use pavucontrol to set up recording, and firefox no longer shows up as a playback application when playing audio.

---

### Post by Nexusx6 on 2010-12-13
Ahh, good old Connection Refused. This error and I went through quite a boxing match a few versions ago. This may or may not fix it, 

```
pulseaduio -D
```

Try typing that in terminal once you notice the problem and see if that resuscitates PA. If it doesn't, try restarting your computer and typing that first thing after reboot and go about testing from there.

Also, you might want to read through [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449") and see if you can garnish any information from there.

---

### Post by nickajeglin on 2010-12-13
Oookay. So pulseaudio -D always throws the error: E: main.c: Daemon startup failed. I'm almost sure that the audacity errors are unrelated and that this is a flash issue. It turns out that audacity always produces those errors, even when it works perfectly. In fact I can play and record audio all I want when firefox is running, as long as I don't try to use anything related to flash in the browser. That instantly causes the recording cursor in audacity to stop and stutter, with no recording happening. It also causes audio playback in other programs (totem) to stop working. This now persists until I close firefox, then everything goes back to normal. Perhaps I'll see if I can downgrade to an earlier version of flash. Ideas?

It also has to do with plugin-container. The reason I thought that I had to reboot to fix this earlier was that plugin-container hangs around in the background after I close firefox. As soon as I kill plugin-container, everything returns to normal. I was under the impression that plugin-container was a relatively new addition to firefox. I've never noticed the process before, and certainly never had any trouble with it. Does anyone know if plugin-container could be the problem, or is it just that plugin-container is related to flash?

Update, this is my problem: [http://ubuntuforums.org/showthread.php?t=772632](http://ubuntuforums.org/showthread.php?t=772632) I'm seeing all sorts of useful things. I'm currently working through psyke's pulseaudio configuration tut.

---

### Post by nickajeglin on 2010-12-13
Success!! I had previously made a configuration file called .asoundrc to get an alsa based graphic equalizer working. When I deleted this file, Everything worked. It seems that somehow, this config file was preventing flash from using pulseaudio, and instead it was connecting directly to my audio device, causing anything trying to use pulse, like good little programs, to fail.

---

