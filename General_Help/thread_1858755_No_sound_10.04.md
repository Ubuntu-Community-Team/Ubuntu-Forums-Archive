---
title: "No sound 10.04"
date: 2011-10-13
forum: General Help
---

### Post by raceon4 on 2011-10-13
I have looked all over for the solution and can't seem to figure this out.  Nothing is muted at all and I have uninstalled and reinstalled pulse audio to no avail.

The weird thing is that sound was working fine up until a couple of days ago.  Any ideas on what might be wrong?


Here are a few readouts.


aplay -l
**** List of PLAYBACK Hardware Devices ****
=card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

pkill pulseaudio; sleep 2; pulseaudio -vv
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 6b9786a8a26e96c703fb66d94c5dda50.
I: main.c: Session ID is 6b9786a8a26e96c703fb66d94c5dda50-1318191856.839144-1156764303.
I: main.c: Using runtime directory /home/andrew/.pulse/6b9786a8a26e96c703fb66d94c5dda50-runtime.
I: main.c: Using state directory /home/andrew/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.


Any help would be greatly appreciated.

---

### Post by raceon4 on 2011-10-13
installed the libasound2 packages and everything seems to be working again.

---

