---
title: "Mangler crashes frequently with memory errors"
date: 2012-10-01
forum: General Help
---

### Post by HousieMousie2 on 2012-10-01
This is the exact text I submitted to LaunchPad, but I figured I would put it here as well and see if any of the smart and wonderful Ubuntu Community might be able to help sort this puppy out!  I will, of course, update the bug report if we can get it fixed.

----

Mangler "seems" to stay up longer if I do not use it to transmit my voice, but use it to only listen, though it does still crash. Crashes happen 1-5 times an hour, most often when I key to speak, but not always. Sometimes the Mangler window 'grays out' and it will state that it has crashed, ask if I want to leave it closed or relaunch it, other times Mangler will simply close on its own. Sometimes it knows it crashed and says so very quickly, other times it will say nothing until I click to close it, when I click to close it, it does not always pop up the Leave Closed/Relaunch dialog box.

Text from the console from different crashes:

:~$mangler
mmap() failed: Cannot allocate memory <---this line repeats 15 times
alsa: snd_pcm_open() failed: Input/output error
mmap() failed: Cannot allocate memory <---this line repeats 4 times
Assertion 'b' failed at pulsecore/memblock.c:454, function pa_memblock_acquire(). Aborting.
Aborted (core dumped)

----

mmap() failed: Cannot allocate memory
pulse: pa_simple_new() failed: Internal error
mmap() failed: Cannot allocate memory
Assertion 'b' failed at pulsecore/memblock.c:454, function pa_memblock_acquire(). Aborting.
Aborted (core dumped)

----

mmap() failed: Cannot allocate memory
alsa: snd_pcm_open() failed: Input/output error

(mangler:2536): glibmm-CRITICAL **:
unhandled exception (type Glib::Error) in signal handler:
domain: g_thread_error
code : 0
what : Error creating thread: Resource temporarily unavailable

The application (or it's libraries) caught a Segmentation Fault. Backtrace follows:
Backtrace: /usr/lib/libg15daemon_client.so.1(+0xa2b) [0xb6c1ca2b]
Backtrace: [0xb77ce400]
Backtrace: /lib/i386-linux-gnu/libc.so.6(+0x130364) [0xb6a69364]
Backtrace: /usr/lib/libventrilo3.so.0(_v3_create_event+0x6b) [0xb75e46fb]
Backtrace: /usr/lib/libventrilo3.so.0(_v3_process_message+0x6d1) [0xb75e5ed1]
Backtrace: mangler() [0x8089372]
Backtrace: mangler() [0x80721c9]
Backtrace: /usr/lib/i386-linux-gnu/libglibmm-2.4.so.1(+0x388c2) [0xb71dd8c2]
Backtrace: /lib/i386-linux-gnu/libglib-2.0.so.0(+0x6a6b3) [0xb6e3e6b3]
Backtrace: /lib/i386-linux-gnu/libpthread.so.0(+0x6d4c) [0xb6f25d4c]
Backtrace: /lib/i386-linux-gnu/libc.so.6(clone+0x5e) [0xb6a23ace]
End of Backtrace.

----

I have tried using both ALSA and Pulse, both crash at roughly the same rate. I ran Memtest 86+ for twelve passes, no errors.

I am not a trouleshooter, programmer, scripter, or otherwise tech-type person, but if you give me clear, step by step instructions, I will be more than happy to follow them in order to provide more information.

ProblemType: Bug
DistroRelease: Ubuntu 12.04
Package: mangler 1.2.2-2
ProcVersionSignature: Ubuntu 3.2.0-31.50-generic-pae 3.2.28
Uname: Linux 3.2.0-31-generic-pae i686
NonfreeKernelModules: nvidia wl
ApportVersion: 2.0.1-0ubuntu13
Architecture: i386
Date: Mon Oct 1 20:35:13 2012
InstallationMedia: Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
ProcEnviron:
 TERM=xterm
 PATH=(custom, no user)
 LANG=en_US.UTF-8
 SHELL=/bin/bash
SourcePackage: mangler
UpgradeStatus: Upgraded to precise on 2012-07-31 (62 days ago)

----

Thank you for your time!

---

