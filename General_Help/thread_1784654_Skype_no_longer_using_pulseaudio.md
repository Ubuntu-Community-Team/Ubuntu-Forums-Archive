---
title: "Skype no longer using pulseaudio"
date: 2011-06-17
forum: General Help
---

### Post by timgood on 2011-06-17
Using Skype 2.2.0.25 on Maverick 64bit, I noticed today that my USB microphone on my webcam was no longer working. When I went to Skype/Options/Sound Devices I noticed that all my audio devices were now listed, rather than just pulseaudio. 

```
pulseaudio -vvv
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: x86_64-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux x86_64 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011
D: main.c: Found 4 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimised build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 87f478839a2f80782112c21300000009.
I: main.c: Session ID is 87f478839a2f80782112c21300000009-1308310815.111590-1899636712.
I: main.c: Using runtime directory /home/tim/.pulse/87f478839a2f80782112c21300000009-runtime.
I: main.c: Using state directory /home/tim/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

```

This is what I get from running pulseaudio in a terminal. I can play music and it shows up in the pulseaudio volume control, but with pavucontrol running, Skype will not play or record audio. I can set Skype to use the USB microphone on my webcam successfully, but why is pulseaudio no longer the default? Any answers would be gratefully recieved.

---

### Post by timgood on 2011-06-17
Image attached:

---

### Post by timgood on 2011-06-18
bump...

---

### Post by timgood on 2011-06-20
Interesting: I have looked at various Skype forums and is has been stated that Skype will (apparently) only use pulseaudio if it is running. However, it *is* running in my case and yet Skype insists on using Alsa. Any clues as to what could be amiss would be gratefully received.

---

### Post by sunasia on 2011-06-27
I just installed skype and it has pulse audio and i cant use Mic I installed alsa but thats not allowing me to open in the sound devices option , what can I do to get alsa to work or is there another sound audio device to use skype with Ubuntu?

---

### Post by Marcelo Ruiz on 2011-07-03
Same problem with Maverick x64. Skype 2.2.0.35 just works if no program is playing sounds. Also pulseaudio is not an option anymore...
It does work with Lucid x86, so I guess it's just a problem in Maverick x64.
Any ideas on how to "fool" skype and make it use pulseaudio again? :o

---

### Post by timgood on 2011-07-04
> **Marcelo Ruiz said:**
> Same problem with Maverick x64. Skype 2.2.0.35 just works if no program is playing sounds. Also pulseaudio is not an option anymore...
It does work with Lucid x86, so I guess it's just a problem in Maverick x64.
Any ideas on how to "fool" skype and make it use pulseaudio again? :o

Interesting. Could be something that happened as a result of an update? Wish I knew the answer to this. Any pulse/skype/alsa gurus out there? Anyone running Maverick x64 who also has/has not got this problem?

---

### Post by Marcelo Ruiz on 2011-07-04
@Timgood

You can try this and see what happens:

```
cd /usr/lib32
sudo chmod ugo+r libpulse.so.0.12.2
sudo chmod ugo+r libpulse-simple.so.0.0.3
mv ~/.Skype/shared.xml ~/.Skype/shared~.xml

```

That seemed to solve my problem... I took them from another post in the forum that I can't find right now to quote :(
I actually did a full pulseaudio reinstallation, but it didn't get it working, so I guess the commands posted there solved the problem.
Good luck!

---

### Post by timgood on 2011-07-04
Genius! Thanks for this mate. Virtual beers all round. My shout.

---

