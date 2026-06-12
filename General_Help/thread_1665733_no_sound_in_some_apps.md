---
title: "no sound in some apps"
date: 2011-01-12
forum: General Help
---

### Post by klirka on 2011-01-12
hello,

firefox plays sound in videos, system bell works at startup and shutdown, and i can play a test sound in "system settings --> multimedia --> phonon". but in several other apps, sound doesn't work, e.g. thunderbirds makes no sound when new mail arrives, although beeping is enabled, it only shows an alert; the same in my chess program. do you have any idea? it all worked fine in kubuntu 10.04, now i have kubuntu 10.10. thank you!

---

### Post by klirka on 2011-01-13
please help, thank you!

---

### Post by cptrohn on 2011-01-13
Did you try opening up the sound control panel?  On my KDE computer I sometimes have to go there and also turn up the sound in the PCI part of it.

---

### Post by klirka on 2011-01-13
> **cptrohn said:**
> Did you try opening up the sound control panel?  On my KDE computer I sometimes have to go there and also turn up the sound in the PCI part of it.

thanks for your help! sorry, but what "sound control panel" (apart from the one i mentioned in my initial post) do you have in mind? what is PCI, and where should I do what with it?

in case it helps, i can attach a screenshot of my current alsamixer settings.

---

### Post by cptrohn on 2011-01-13
Sorry, if you go to your speaker icon and then right click on it it will open a tab for the master volume, click on the mixer button and it should bring up another window that will have a Master volume, a front volume and a PCM volume as well as a headphone volume.... I would check to make sure the PCM volume is turned up.  I have had this happpen to me installing or upgrading in kubuntu a few times.

---

### Post by klirka on 2011-01-13
indeed, i remember those were settings to play with when right-clicking the speaker icon under kubuntu 10.04, but now on 10.10 i am not given these windows any more. now there is just "playback devices: internal audio analog stereo", but no individual pcm/speaker/master/... slots.

the alsamixer screenshot in my previous post shows PCM at 100, though it is not clear whether muted or not. but again: sound works fine in most apps, just not in all.

any other ideas? thank you!

---

### Post by Zorael on 2011-01-13
Did you upgrade to 10.10 or did you do a clean install? PulseAudio is included in Kubuntu by default in 10.10, but not in 10.04. If you upgrade I'm not sure it gets tagged for installation, but I may be wrong there. You should see a **pulseaudio** process running in the System Activity window (Ctrl+Esc) or in the full-blown System Monitor.

Anyway, I get the same behavior on my two laptops, using PulseAudio. Sound works fine in most programs, but in (for instance) VLC there's no sound at all, ever. The solution was to bump the sample rate to 48kHz.

Near the end of **/etc/pulse/daemon.conf**;
```
**[COLOR="Red"]_;_[/COLOR]** default-sample-rate = **_[COLOR="Red"]44100[/COLOR]_**
```
...becomes...
```
default-sample-rate = **_[COLOR="Green"]48000[/COLOR]_**
```
Note the absence of a commenting semicolon infront of the line. You'll need a text editor with superuser permissions to edit that, such as by running '**kdesudo kate**' from a run box (Alt+F2).

Alternatively, enter this in the terminal;
```
$ sudo sed -i 's/\; default-sample-rate = 44100/default-sample-rate = 48000/g' /etc/pulse/daemon.conf
```

The changes should apply after a reboot - or you could force a close of PulseAudio, but that might mess up sound in programs currently running. (At least Skype and maybe Wine.)
```
$ pulseaudio -k
```
It will restart itself immediately. Try closing and reopening the program you had sound problems in and see if it helped. Again, all and any running programs *may* need to be restarted to get their sound back. It depends on how well they interface with PulseAudio, I think.

---

### Post by Zorael on 2011-01-13
(double post)

---

### Post by Zorael on 2011-01-13
(another double post. it took ages to submit the reply, so upon retrying it apparently ended up this way. apologies.)

---

### Post by klirka on 2011-01-13
near the end of my /etc/pulse/daemon.conf file it reads 44100, not 44000:

```
; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2
; default-channel-map = front-left,front-right
```

i put the line you gave me [sudo sed -i ...] in konsole and received this error message:

```
kate(2270)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/[...]/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon
```

glad you try to help me, thank you very much!

---

### Post by Zorael on 2011-01-13
Erp, sorry, yes; 44100. I updated the post.

That terminal output is just Kate being silly. You can run **kdebugdialog** and tick Diable all debug output to lessen KDE programs' verbosity.

The terminal command was wrong too, so run the updated one, please.

Does your **/etc/pulse/daemon.conf** now have the line uncommented and with 48000 instead of 44100?

```
default-sample-rate = 48000
```

---

### Post by klirka on 2011-01-13
yes, thank you. file now reads:

```
; default-sample-format = s16le
default-sample-rate = 48000
; default-sample-channels = 2
; default-channel-map = front-left,front-right
```

i rebooted, but, still no sound... :(
and yes, it was a fresh install of kubuntu 10.10, no upgrade from 10.04.

---

### Post by Zorael on 2011-01-13
I don't see how it should matter if you're running PulseAudio, but try unmuting those Speaker channels in alsamixer. Hit M when you have one selected. It should say 00 and not MM.

---

### Post by klirka on 2011-01-13
> **Zorael said:**
> I don't see how it should matter if you're running PulseAudio, but try unmuting those Speaker channels in alsamixer. Hit M when you have one selected. It should say 00 and not MM.

i did this, still not working.

btw, i can attach another screenshot, this time of the sound settings in my chess program. it should make a beep when opponent moves (and worked well in kubuntu 10.04). now it doesn't, and when i click "test", it also doesn't work.

---

### Post by Zorael on 2011-01-13
That looks like an OSS application. Try starting it via **padsp**.

```
$ padsp *<nameofchessgamebinary>*
```

---

### Post by klirka on 2011-01-13
> **Zorael said:**
> That looks like an OSS application. Try starting it via **padsp**.

```
$ padsp *<nameofchessgamebinary>*
```

yeahh!! this works! magic! :)
thank you so much. i don't care much about thunderbird not beeping when mail arrives, but you gave me back my chess sound and this is what matters most to me, because my endgame sucks, i really need the sound in time trouble.
i will mark this thread as solved then.
thanks for all your efforts, Zorael!

---

