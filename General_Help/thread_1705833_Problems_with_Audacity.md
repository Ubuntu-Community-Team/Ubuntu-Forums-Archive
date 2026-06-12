---
title: "Problems with Audacity"
date: 2011-03-12
forum: General Help
---

### Post by Joseph Schwenker on 2011-03-12
When using the latest version of Audacity in Ubuntu 10.10's repositories, I am experiencing some weird behaviors. Firstly, I can no longer drag and drop audio files into the player. Nothing happens. Secondly, Audacity refuses to let me interact with it except via its menu bar. I cannot click the play button or select a part in an audio track. Thirdly, when I quit it from the menu, I get a segmentation fault in the terminal. I have tried to solve this by using the daily build alpha PPA, but I experience the same behavior. I tried uninstalling plugins, but to no effect. Currently, I am forced to work with a version provided by Portable Linux Apps, though there is a delay of a few seconds before audio starts playing when I click the play button. Here's the output from the current alpha build's PPA:

```
ALSA lib pcm.c:2208:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2208:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2208:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
Expression 'stream->capture.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3857
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3875
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3875
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3875
Expression 'ret' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1035
Expression 'AlsaOpen( &alsaApi->baseHostApiRep, params, streamDir, &self->pcm )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1192
Expression 'PaAlsaStreamComponent_Initialize( &self->capture, alsaApi, inParams, StreamDirection_In, NULL != callback )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1433
Expression 'PaAlsaStream_Initialize( stream, alsaHostApi, inputParameters, outputParameters, sampleRate, framesPerBuffer, callback, streamFlags, userData )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2105
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3875
Segmentation fault

```

Here's the output of the beta version in Ubuntu 10.10's repositories:

```
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Expression 'stream->capture.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3653
Segmentation fault

```

Running the version from Portable Linux Apps produces no output, though there is sometimes no sound, and there is often delay after pressing the play button.

---

### Post by orrinjelo on 2011-03-13
I've noticed I get the same thing with the latest update.  I've traced it all back to something with Alsa--you can get rid of the bt_audio stuff by purging bluez-alsa.  

So....uh....still searching for the answer, but narrowed down results.

---

### Post by Joseph Schwenker on 2011-03-13
> **orrinjelo said:**
> I've noticed I get the same thing with the latest update.  I've traced it all back to something with Alsa--you can get rid of the bt_audio stuff by purging bluez-alsa.  

So....uh....still searching for the answer, but narrowed down results.

Thanks for the response. I'm glad to know that I'm not the only one experiencing this. I purged bluez-alsa, and now all of the bt_audio errors are gone, leaving me with:

```
Expression 'stream->capture.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3653
Segmentation fault
```

And no sound.

---

### Post by ridetheteapot on 2011-03-19
I had the same problem, its not related to those bt_audio messages - you can ignore them. The problem for me was the globalmenu applet i was using, also if you use unity or the indicator-appmenu you will have the same trouble.

ref:  [https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/731451]("https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/731451")

---

### Post by Joseph Schwenker on 2011-03-19
> **ridetheteapot said:**
> I had the same problem, its not related to those bt_audio messages - you can ignore them. The problem for me was the globalmenu applet i was using, also if you use unity or the indicator-appmenu you will have the same trouble.

ref:  [https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/731451]("https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/731451")

Whoa! You're right! It's GlobalMenu that's screwing it up. If you remove GlobalMenu, the problem is solved. Unfortunately, GlobalMenu is a huge part of my workflow, so removing it isn't a solution, only a workaround. For the time being, I'm using the portable version of Audacity after I kill Pulseaudio.
Thanks for the answer.

By the way, I just tried using Audacity with indicator-appmenu, and had the same problem. However, having not tried indicator-appmenu for months, I'm finding it WAY better than GlobalMenu, though this is completely unrelated to this thread's topic.

---

### Post by drshukla14 on 2011-04-08
Audacity had following problems with Ubuntu 10.10 - would not play, would not let me export multiple, would not let me edit labels and would not save project.

This solution by Doug works: 
                 "Because this has been hanging about for a bit -
if you want to return the menus to audacity as a user then open the audacity.desktop
gksudo gedit /usr/share/applications/audacity.desktop
 Then adjust the Exec=audacity line to this
Exec=env UBUNTU_MENUPROXY=0 audacity
 (note there is a space between env and UBUNTU_MENUPROXY=0 and a space between UBUNTU_MENUPROXY=0 and audacity
 This will return menus when opening audacity from app menu and from r. click context menu


Refer: [https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/731451](https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/731451)

---

### Post by Joseph Schwenker on 2011-04-08
> **drshukla14 said:**
> Audacity had following problems with Ubuntu 10.10 - would not play, would not let me export multiple, would not let me edit labels and would not save project.

This solution by Doug works: 
                 "Because this has been hanging about for a bit -
if you want to return the menus to audacity as a user then open the audacity.desktop
gksudo gedit /usr/share/applications/audacity.desktop
 Then adjust the Exec=audacity line to this
Exec=env UBUNTU_MENUPROXY=0 audacity
 (note there is a space between env and UBUNTU_MENUPROXY=0 and a space between UBUNTU_MENUPROXY=0 and audacity
 This will return menus when opening audacity from app menu and from r. click context menu


Refer: [https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/731451](https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/731451)

Thank you so much! You get +1 internets. This solution is working perfectly for me with AppMenu.

---

