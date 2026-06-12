---
title: "Lucid Sound not working"
date: 2010-08-15
forum: General Help
---

### Post by Yumi on 2010-08-15
I have no sound on speaker or headphone. The soundcard used to work until 3 days ago. Volume Meter shows moving bars, same for microphone. Can not find anything muted nor is the volumne turned down.

The only lead is that Pulse Audio Volume Meter says "Showing signal levels of **Dummy output**

~$ pulseaudio -vvv
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: i686-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.35-15-generic #21-Ubuntu SMP Wed Aug 11 16:41:40 UTC 2010
D: main.c: Found 1 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimised build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 3621f62ba43dc13d9811cf974ae11a5f.
I: main.c: Session ID is 3621f62ba43dc13d9811cf974ae11a5f-1281841296.72349-924184985.
I: main.c: Using runtime directory /home/michael/.pulse/3621f62ba43dc13d9811cf974ae11a5f-runtime.
I: main.c: Using state directory /home/michael/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
[B][COLOR="Red"]E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.[/COLOR][/B]


Had a similar problems before but always managed to solve them. Last time I shock my head as it was just a checkbox somewhere, but I forgot where.

Michael

---

### Post by dino99 on 2010-08-15
check all the settings into gnome-alsamixer , install it if not

---

### Post by bprins on 2010-08-15
restarted X using control alt backspace maybe? if so, reboot.

i found this after googling the error you got:

[https://bugzilla.redhat.com/show_bug.cgi?id=425763](https://bugzilla.redhat.com/show_bug.cgi?id=425763)

---

### Post by Yumi on 2010-08-15
I played with gnome-alsamixer and now I can hear myself. Microphone is recording and playing back through speaker and headphone.

In Sound preferences the microphone now muted itsself somehow, but is still recording!

However no sound through firefox or skype.

Also found that I cannot End the process "pulseaudio" it disappears but restarts immediatly again.
So many settings. Alsamixer, Gnome-Alsamixer, Alsamixer-Gui, Indicator applet, Sound Preferences and what else.
 
Getting a little bored listening  to myself all the time. A little interaction would be nice.

Michael

---

