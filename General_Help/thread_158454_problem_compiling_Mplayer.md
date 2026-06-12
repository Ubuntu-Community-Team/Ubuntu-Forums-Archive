---
title: "problem compiling Mplayer"
date: 2006-04-11
forum: General Help
---

### Post by harys on 2006-04-11
hi, i'm compiling Mplayer. i ran the command :
sudo apt-get install gcc-3.4
ive got it install and ran the ./configure --enable-gui and that's what i got from my xterm :

harys@harys:~/Desktop/MPlayer-1.0pre7try2$ ./configure --enable-gui
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... not found
Checking for gcc version ... not found
Checking for gcc-3.4 version ... 3.4.5, ok
Checking for host cc ... gcc-3.4
Checking for CPU vendor ... GenuineIntel (15:4:3)
Checking for CPU type ...  Intel(R) Pentium(R) 4 CPU 3.00GHz
Checking for GCC & CPU optimization abilities ... Your gcc-3.4 does not even support "i386" for '-march' and '-mtune'.
error
Checking for kernel support of mmx ... failed
It seems that your kernel does not correctly support mmx.
To use mmx extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of mmx2 ... failed
It seems that your kernel does not correctly support mmx2.
To use mmx2 extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of sse ... failed
It seems that your kernel does not correctly support sse.
To use sse extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of sse2 ... failed
It seems that your kernel does not correctly support sse2.
To use sse2 extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for mtrr support ... yes
Checking for assembler support of -pipe option ... no
Checking for assembler (as 2.16.1) ... ok
Checking for Linux kernel version ... 2.6.12-10-386, ok
Checking for mplayer binary name ... mplayer
Checking for awk ... mawk
Checking for extra headers ... none
Checking for extra libs ... none
Checking for -lposix ... no
Checking for -lm ... no
Checking for i18n ... no
Checking for iconv ... no
Checking for langinfo ... no
Checking for language ... using en (man pages:  en)
Checking for enable sighandler ... yes
Checking for runtime cpudetection ... no
Checking for restrict keyword ... none
Checking for __builtin_expect ... no
Checking for kstat ... no
Checking for posix4 ... no
Checking for lrintf ... no
Checking for nanosleep ... no
Checking for socklib ... no
Checking for inet_pton() ... no (=> i'll try inet_aton next)
Checking for inet_aton() ... no (=> network support disabled)
Checking for inttypes.h (required) ... no
Checking for bitypes.h (inttypes.h predecessor) ...
Error: Cannot find header either inttypes.h or bitypes.h (see DOCS/HTML/en/faq.html).

Check "configure.log" if you do not understand why it failed.
harys@harys:~/Desktop/MPlayer-1.0pre7try2$ sudo apt-get install gcc-3.4

need a help. thanks. harys

---

### Post by Monster_user on 2006-04-11
Isn't mPlayer in the Universe repository???

I found a FAQ.
[http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/faq.html](http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/faq.html)

Do a find for inttypes.h.

find /etc/*inttypes*
find /etc/*/*inttypes*
find /etc/*/*/*inttypes*

Then copy, or link it to the mplayer compile directory.

---

### Post by krismatth3 on 2006-04-11
Try:

# CC=/usr/bin/gcc-3.4 ./configure --enable-gui

(I am not positive of the gcc-3.4 path. First try running /usr/bin/gcc-3.4 to make sure it's the right path.)

---

### Post by Sboulema on 2006-04-11
I compiled MPlayer on Kubuntu Breezy:
[http://members.lycos.nl/linkdata/deb/mplayer_1.0pre7try2-1_i386.deb](http://members.lycos.nl/linkdata/deb/mplayer_1.0pre7try2-1_i386.deb)

---

### Post by Al3xanR0 on 2006-04-11
[QUOTE=harys]hi, i'm compiling Mplayer. i ran the command :
sudo apt-get install gcc-3.4
ive got it install and ran the ./configure --enable-gui and that's what i got from my xterm :[/QUOTE]

Wouldn't it just be easier to "apt-get install mplayer" I can't see that app not being in the repository due to its popularity.

---

### Post by tsb on 2006-05-02
[QUOTE=Sboulema]I compiled MPlayer on Kubuntu Breezy:
[http://members.lycos.nl/linkdata/deb/mplayer_1.0pre7try2-1_i386.deb](http://members.lycos.nl/linkdata/deb/mplayer_1.0pre7try2-1_i386.deb)[/QUOTE]

Thanks!

---

