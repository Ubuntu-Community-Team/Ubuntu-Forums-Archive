---
title: "Amarok Launch Problem"
date: 2010-06-06
forum: General Help
---

### Post by yankeesrock1423 on 2010-06-06
When I attempt to launch Amarok from the Application Launcher, nothing happens.  When I try and run it from the terminal, I get the following:

Version mismatch detected between the NVIDIA libGL.so
and libGLcore.so shared libraries (libGL.so version:
195.36.24; libGLcore.so version: 195.36.15).
Please try reinstalling the NVIDIA driver

I have tried using NVIDIA drivers both from NVIDIAs website as well as the ones included with Lucid.  Any ideas?

---

### Post by yankeesrock1423 on 2010-06-11
bump

---

### Post by NightwishFan on 2010-06-11
Try reverting back to the nouveau driver, and then running Amarok. If this works, then perhaps file a bug. Reinstall Nvidia drivers and see if it has the same behavior.

---

### Post by DThurman on 2010-06-11
This is on Ubuntu v10.4:

# amarok
<unknown program name>(14405)/: KUniqueApplication: Cannot find the D-Bus session server:  "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." 

<unknown program name>(14404)/: KUniqueApplication: Pipe closed unexpectedly.

Also, Amarok does not appear in Applications->Sound & Video list.

---

### Post by NightwishFan on 2010-06-11
Copy and paste this in a terminal:
```
sudo aptitude update && sudo apt-get -f install && sudo aptitude install amarok
```

---

### Post by yankeesrock1423 on 2010-06-11
Good call.. disabling all proprietary drivers (both the newest NVIDIA and the ones included with Lucid) allows Amarok to function, but of course really hampers video performance in other areas.  Reinstalling the drivers causes the problem to re-emerge.  

To be sure it's a bug and not something that I messed up by flipping between 30 different drivers, I'm going to try a fresh install inside a virtual machine and see if it does the same thing.  Thank You!

---

### Post by NightwishFan on 2010-06-11
Try purging the Nvidia drivers.
```
sudo aptitude purge nvidia-current
```

---

### Post by DThurman on 2010-06-12
> **NightwishFan said:**
> Copy and paste this in a terminal:
```
sudo aptitude update && sudo apt-get -f install && sudo aptitude install amarok
```

Hmm, this is what I get:

# sudo aptitude update && sudo apt-get -f install && sudo aptitude install amarok
sudo: /etc/sudoers.d/aegir is mode 0600, should be 0440
>>> /etc/sudoers.d/README: /etc/sudoers.d/aegir near line 18 <<<
sudo: parse error in /etc/sudoers.d/README near line 18
sudo: no valid sudoers sources found, quitting
*** glibc detected *** sudo: double free or corruption (!prev): 0x09732ca0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0xd2c591]
/lib/tls/i686/cmov/libc.so.6(+0x6cde8)[0xd2dde8]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0xd30ecd]
/lib/tls/i686/cmov/libc.so.6(fclose+0x14a)[0xd1caaa]
sudo[0x805785d]
sudo[0x80587f6]
sudo[0x80563ce]
sudo[0x805a134]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0xcd7bd6]
sudo[0x804a7c1]
======= Memory map: ========
00110000-00111000 r-xp 00000000 00:00 0          [vdso]
00256000-00273000 r-xp 00000000 08:2c 3932243    /lib/libgcc_s.so.1
00273000-00274000 r--p 0001c000 08:2c 3932243    /lib/libgcc_s.so.1
00274000-00275000 rw-p 0001d000 08:2c 3932243    /lib/libgcc_s.so.1
0027f000-00288000 r-xp 00000000 08:2c 3932217    /lib/tls/i686/cmov/libcrypt-2.11.1.so
00288000-00289000 r--p 00008000 08:2c 3932217    /lib/tls/i686/cmov/libcrypt-2.11.1.so
00289000-0028a000 rw-p 00009000 08:2c 3932217    /lib/tls/i686/cmov/libcrypt-2.11.1.so
0028a000-002b1000 rw-p 00000000 00:00 0 
00509000-0051c000 r-xp 00000000 08:2c 3932269    /lib/tls/i686/cmov/libnsl-2.11.1.so
0051c000-0051d000 r--p 00012000 08:2c 3932269    /lib/tls/i686/cmov/libnsl-2.11.1.so
0051d000-0051e000 rw-p 00013000 08:2c 3932269    /lib/tls/i686/cmov/libnsl-2.11.1.so
0051e000-00520000 rw-p 00000000 00:00 0 
006ce000-006d6000 r-xp 00000000 08:2c 3932285    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
006d6000-006d7000 r--p 00007000 08:2c 3932285    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
006d7000-006d8000 rw-p 00008000 08:2c 3932285    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
00938000-0093a000 r-xp 00000000 08:2c 3932223    /lib/tls/i686/cmov/libdl-2.11.1.so
0093a000-0093b000 r--p 00001000 08:2c 3932223    /lib/tls/i686/cmov/libdl-2.11.1.so
0093b000-0093c000 rw-p 00002000 08:2c 3932223    /lib/tls/i686/cmov/libdl-2.11.1.so
00aa5000-00ab0000 r-xp 00000000 08:2c 3932292    /lib/libpam.so.0.82.2
00ab0000-00ab1000 r--p 0000a000 08:2c 3932292    /lib/libpam.so.0.82.2
00ab1000-00ab2000 rw-p 0000b000 08:2c 3932292    /lib/libpam.so.0.82.2
00ae1000-00afc000 r-xp 00000000 08:2c 3932163    /lib/ld-2.11.1.so
00afc000-00afd000 r--p 0001a000 08:2c 3932163    /lib/ld-2.11.1.so
00afd000-00afe000 rw-p 0001b000 08:2c 3932163    /lib/ld-2.11.1.so
00cc1000-00e14000 r-xp 00000000 08:2c 3932209    /lib/tls/i686/cmov/libc-2.11.1.so
00e14000-00e15000 ---p 00153000 08:2c 3932209    /lib/tls/i686/cmov/libc-2.11.1.so
00e15000-00e17000 r--p 00153000 08:2c 3932209    /lib/tls/i686/cmov/libc-2.11.1.so
00e17000-00e18000 rw-p 00155000 08:2c 3932209    /lib/tls/i686/cmov/libc-2.11.1.so
00e18000-00e1b000 rw-p 00000000 00:00 0 
00f08000-00f0e000 r-xp 00000000 08:2c 3932271    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00f0e000-00f0f000 r--p 00006000 08:2c 3932271    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00f0f000-00f10000 rw-p 00007000 08:2c 3932271    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00f44000-00f4e000 r-xp 00000000 08:2c 3932275    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00f4e000-00f4f000 r--p 00009000 08:2c 3932275    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00f4f000-00f50000 rw-p 0000a000 08:2c 3932275    /lib/tls/i686/cmov/libnss_files-2.11.1.so
08048000-08066000 r-xp 00000000 08:2c 11011220   /usr/bin/sudo
08066000-08067000 r--p 0001d000 08:2c 11011220   /usr/bin/sudo
08067000-08068000 rw-p 0001e000 08:2c 11011220   /usr/bin/sudo
08068000-0806b000 rw-p 00000000 00:00 0 
09729000-0974a000 rw-p 00000000 00:00 0          [heap]
b7600000-b7621000 rw-p 00000000 00:00 0 
b7621000-b7700000 ---p 00000000 00:00 0 
b775d000-b779c000 r--p 00000000 08:2c 11017998   /usr/lib/locale/en_US.utf8/LC_CTYPE
b779c000-b78ba000 r--p 00000000 08:2c 11017737   /usr/lib/locale/en_US.utf8/LC_COLLATE
b78ba000-b78bc000 rw-p 00000000 00:00 0 
b78c6000-b78c7000 r--p 00000000 08:2c 11018003   /usr/lib/locale/en_US.utf8/LC_NUMERIC
b78c7000-b78c8000 r--p 00000000 08:2c 11020563   /usr/lib/locale/en_US.utf8/LC_TIME
b78c8000-b78c9000 r--p 00000000 08:2c 11020564   /usr/lib/locale/en_US.utf8/LC_MONETARY
b78c9000-b78ca000 r--p 00000000 08:2c 11020565   /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b78ca000-b78cb000 r--p 00000000 08:2c 11018264   /usr/lib/locale/en_US.utf8/LC_PAPER
b78cb000-b78cc000 r--p 00000000 08:2c 11017807   /usr/lib/locale/en_US.utf8/LC_NAME
b78cc000-b78cd000 r--p 00000000 08:2c 11020566   /usr/lib/locale/en_US.utf8/LC_ADDRESS
b78cd000-b78ce000 r--p 00000000 08:2c 11020567   /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b78ce000-b78cf000 r--p 00000000 08:2c 11017805   /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b78cf000-b78d6000 r--s 00000000 08:2c 11011554   /usr/lib/gconv/gconv-modules.cache
b78d6000-b78d7000 r--p 00000000 08:2c 11020568   /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b78d7000-b78d9000 rw-p 00000000 00:00 0 
bff47000-bff5c000 rw-p 00000000 00:00 0          [stack]
Aborted


ok, I chmodded /etc/sudoers.d/aegir to mode 0400, ran it again
and it worked.  However, amarok did not install properly.

I removed amarok* once again and retried your suggestion and
it worked!!!

Thanks!

---

### Post by NightwishFan on 2010-06-12
Ok, I am glad it worked. Still I wonder what caused that issue to begin with.

---

### Post by DThurman on 2010-06-12
> **NightwishFan said:**
> Ok, I am glad it worked. Still I wonder what caused that issue to begin with.

It says in the crash log:

```

sudo: /etc/sudoers.d/aegir is mode 0600, should be 0440
>>> /etc/sudoers.d/README: /etc/sudoers.d/aegir near line 18 <<<
sudo: parse error in /etc/sudoers.d/README near line 18
sudo: no valid sudoers sources found, quitting

```

So, it has something to do with the aegir-provision package....

---

### Post by robertinams on 2010-07-19
Amarok was not staring due to the libGL.so and libGLcore.so version mismatch. After deinstalling - reinstalling my nvidia drivers a couple of times, I decided to follow the suggestion of removing: /usr/lib/libGL* I reinstalled the nvidia driver and problem was solved.

1) Now not a single ligGL* file has been recreated
2) Amarok is working
3) Advanced desktop effects are working, fan of video card is slowed down to almost no sound, so that's working
4) What are those libGL* files for anyway and why don't I miss them?
5) Where to report a bug?

It is always with the proprietary software (flash, acroread, nvidia) where we go wrong.

Gr,
Robert

---

### Post by robertinams on 2010-07-19
Sorry, made a mistake and posted twice

---

