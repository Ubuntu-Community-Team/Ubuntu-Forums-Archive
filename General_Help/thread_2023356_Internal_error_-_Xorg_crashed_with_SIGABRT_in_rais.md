---
title: "Internal error - Xorg crashed with SIGABRT in raise()"
date: 2012-07-12
forum: General Help
---

### Post by vittau on 2012-07-12
Hi everyone,

I've recently updated to 12.04, and since day-1 I keep getting these errors. They usually happen when I check updates on the Update Manager, and also sometimes when I come back after the computer's been suspended for a while.

I've seen some similar reports on Launchpad.net, but can't seem to find a solution, or at least understand the cause of this problem.

Can someone help me understand/fix this?

Thanks! :)

*Dell Inspiron N5110 - i5 2410M - Intel HD 3000*

---

### Post by dino99 on 2012-07-12
is it really xorg that is crashing ? never seen it.
what you get inside /var/crash/ ?
have you reported this issue ?

are you using third party packages (ppa) ?

---

### Post by vittau on 2012-07-12
> **dino99 said:**
> is it really xorg that is crashing ? never seen it.
what you get inside /var/crash/ ?
have you reported this issue ?

are you using third party packages (ppa) ?
ProblemType: Crash
Architecture: i386
CrashCounter: 1
Date: Wed Jul  4 16:22:13 2012
DistroRelease: Ubuntu 12.04
ExecutablePath: /usr/bin/Xorg
ExecutableTimestamp: 1336434518
ProcCmdline: /usr/bin/X :2 -auth /var/run/lightdm/root/:2 -nolisten tcp vt9 -novtswitch
ProcCwd: /etc/X11
ProcEnviron: 
ProcMaps:
 b635f000-b6361000 rw-p 00000000 00:00 0 
 b638a000-b638b000 rw-s 3be91000 00:05 1725       /dev/dri/card0
 b638f000-b6390000 rw-s 3be8c000 00:05 1725       /dev/dri/card0
 b6390000-b6391000 rw-s 3bfa1000 00:05 1725       /dev/dri/card0
 b6391000-b6392000 rw-s 3be6f000 00:05 1725       /dev/dri/card0
 b6392000-b6393000 rw-s 3bf9f000 00:05 1725       /dev/dri/card0
 b6394000-b639e000 rw-s 3bf94000 00:05 1725       /dev/dri/card0
 b639e000-b63a1000 rw-s 3be89000 00:05 1725       /dev/dri/card0
[COLOR=Red]... (and it goes on and on)[/COLOR]

[COLOR=Black]I have sent the report multiple times...

Like I said, it happens since when I first installed 12.04, I didn't even have 3rd party ppas back then (now I do have the grub-customizer ppa).

Thanks.
[/COLOR]

---

### Post by bogan on 2012-07-12
Hi!, **Vittau,,**

Have you updated 12.04 today- Thursday -??

Update manager is currently updating both 'xserver-common' and 'xserver-xorg-core', which may possibly influence your setup.

I also frequently get similar error and crash reports, though not nearly so many as a month ago. They are also frequent on running 'Check' in Update manager, but show 'dbus' or 'Nautilus' as the source, and segfaults as the cause.

Chao!, **bogan.**

---

### Post by vittau on 2012-07-12
> **bogan said:**
> Hi!, **Vittau,,**

Have you updated 12.04 today- Thursday -??

Update manager is currently updating both 'xserver-common' and 'xserver-xorg-core', which may possibly influence your setup.

I also frequently get similar error and crash reports, though not nearly so many as a month ago. They are also frequent on running 'Check' in Update manager, but show 'dbus' or 'Nautilus' as the source, and segfaults as the cause.

Chao!, **bogan.**Yes I've noticed this, but like I said, it's not a new problem.

---

### Post by pdjohnso on 2012-09-09
Vittau,

I get the same error frequently.  Did you find any resolution?

Thanks,

Phil

---

### Post by vittau on 2012-09-09
> **pdjohnso said:**
> Vittau,

I get the same error frequently.  Did you find any resolution?

Thanks,

Phil
Not really. It has reduced recently, but still happens from time to time...

Sometimes I also get errors while Rhythmbox is scanning the music folders, and also the weather indicator crashes once in a while...

---

### Post by bonobo on 2012-10-24
I'm seeing this as well.

This bug is also documented at [https://bugs.launchpad.net/bugs/933504](https://bugs.launchpad.net/bugs/933504)

---

