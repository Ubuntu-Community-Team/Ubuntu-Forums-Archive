---
title: "Sound problems"
date: 2010-10-11
forum: General Help
---

### Post by petrasflorin on 2010-10-11
I have a 5.1 sound sistem and headphones with microphone plugged in. I have the following problem: no matter what I select the subwoofer won't work once the Sound Preferences is closed. I mean, in order to make the subwoofer to work I have to leave that thing on, more on this: i can't change tracks in rhythmbox, if I change them subwoofer won't work, if they change by themselves, it works. spooky huh ?!

---

### Post by petrasflorin on 2010-10-11
bump

---

### Post by petrasflorin on 2010-10-11
Already tried with alsamixer, all at max, saved with alsactl store. Nothing.
This is my pulseaudio daemon.conf

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = 

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = no

flat-volumes = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10

After checking this I noticed in the settings of this things there is a setting for 2 channels, shouldn't that be surround ? How do I set it to surround ?
Oh and by the way this is from /etc/pulse/daemon.conf and not ~/.pulse/daemon.conf as the latter one is empty.

---

### Post by petrasflorin on 2010-10-11
Please help, it's like the sound preferences isn't saving my configuration but it is saving because after restarting the settings I've done are still there, it's like... it's not applied, but it is applied, only for the moment (for the one song).
WTH I've never seen anything stranger than this on a computer.

---

### Post by pather on 2010-10-11
Hey, I'm not sure if this work, but try to uncomment these lines by deleting the semicolon at the start of each line 

```
resample-method = speex-float-1
enable-remixing = yes
enable-lfe-remixing = no
```

and then change last line to YES, like this

```
enable-lfe-remixing = yes
```

Dont worry about that 2 channels, because that line is commented out, so pulse doesnt take care of it. Your speaker settings can be modified in sound preferences.

---

### Post by petrasflorin on 2010-10-12
It's been 2 days since I was trying to make my 5.1 sistem work. I was going crazy. But that did the trick, you Sir, are a genius. Thank you.

---

### Post by Mariusmssj on 2010-10-12
i got same problem with a creative sound blaster sound card.

the code "resample-method = speex-float-1" gave an error so i manually installed it and then 

mariusmssj@Mariusmssj:~$ resample method = speex float 1

*** resample: Must specify sampling-rate conversion factor via '-to' or '-by' option 

USAGE: One of the following:

      resample -to srate [-noFilterInterp] [-linearSignalInterp] [-f filterFile] [-terse] inputSoundFile outputSoundFile
      resample -by factor [options as above] inputSoundFile outputSoundFile
      resample -version

Options can be abbreviated.

Report bugs to <bug-resample@w3k.org>.

mariusmssj@Mariusmssj:~$ enable remixing = yes
bash: enable: remixing: not a shell builtin
bash: enable: =: not a shell builtin
bash: enable: yes: not a shell builtin
mariusmssj@Mariusmssj:~$ enable lfe remixing = yes
bash: enable: lfe: not a shell builtin
bash: enable: remixing: not a shell builtin
bash: enable: =: not a shell builtin
bash: enable: yes: not a shell builtin
mariusmssj@Mariusmssj:~$ ^C
mariusmssj@Mariusmssj:~$ 

i am really brand new to ubuntu, i would appreciate any help guys

---

### Post by pabloferz on 2010-10-13
Hi *Mariusmssj*

You don't have to enter in the terminal any of the lines posted by *pather*. Instead, you have to edit your pulse daemon.conf file by doing

```
sudo gedit /etc/pulse/daemon.conf
```

Once the file is opened, you search for the lines:

resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = no

and uncomment them by deleting the semicolon at the beginning of each line. Also you'd have to change the 'no' in the last one by a 'yes' in order to have

enable-lfe-remixing = yes

Hope it helps you.
Greetings

---

### Post by esorensen on 2010-10-17
Unfortunately these lines in daemon.conf didn't work for me! I added those and I still can't see the "5.1 Analog output" under Hardware/Sound Preferences. I just did a fresh install of 10.10 64 bits. I found some threads about the 64 being the problem... but at this moment I'm not willing to go to 32bits, and want to solve the problem!
I appreciate some help!
Regards

---

### Post by Mariusmssj on 2010-10-18
i changed everything as you said but no luck, it's weird the systems sees my sound card just fine, i got all the options i would want but there just is no sound

---

### Post by mastablasta on 2010-10-18
you don't get sound even with analog stereo output?
 
Have you already tried to upgrade ALSA? Fixed my porbelm with no sound. issue was similar as i could see the card, even change the volume with alsamixer...

---

