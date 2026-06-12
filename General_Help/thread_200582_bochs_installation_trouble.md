---
title: "bochs installation trouble"
date: 2006-06-20
forum: General Help
---

### Post by killzoneman0 on 2006-06-20
after going through the site's how-to forums, i can't figure out how to install bochs. i cant get it to work.  i have installed the files from here, [http://bochs.sourceforge.net/](http://bochs.sourceforge.net/)

then ran      sh .conf.win32-vcpp
the site said that that would configure it to emulate windows.

when running  ./configure   there were the following errors

checking for wx-config... not_found
checking for wxWidgets configuration script... not_found
checking for wxWidgets library version...
configure: WARNING: Bochs for wxWidgets cannot be compiled here, disabling it
checking for default gui on this platform... x11
ERROR: X windows gui was selected, but X windows libraries were not found.




after the    sh .conf.win32-vcpp   command compiled, i am stuck on what to do.
(i checked the makefile  and there is nothing in it.)

 
what next?

---

### Post by newrhyme on 2006-10-29
Hey!
I wondered if you have tried installing and running the PRE-compiled BOCHS that came with version 6.06 <Dapper>???

What version are you using?

I had the same trouble, ...could not configure with --with-win32 
  , or, with

   --with--wx

BUT< still was able to get a BASIC gui, with SDL ---

   --with-sdl.

But, of course, you must have SDL already installed.

Hope this helps...
       :-D 




> **killzoneman0 said:**
> after going through the site's how-to forums, i can't figure out how to install bochs. i cant get it to work.  i have installed the files from here, [http://bochs.sourceforge.net/](http://bochs.sourceforge.net/)

then ran      sh .conf.win32-vcpp
the site said that that would configure it to emulate windows.

when running  ./configure   there were the following errors

checking for wx-config... not_found
checking for wxWidgets configuration script... not_found
checking for wxWidgets library version...
configure: WARNING: Bochs for wxWidgets cannot be compiled here, disabling it
checking for default gui on this platform... x11
ERROR: X windows gui was selected, but X windows libraries were not found.




after the    sh .conf.win32-vcpp   command compiled, i am stuck on what to do.
(i checked the makefile  and there is nothing in it.)

 
what next?

---

### Post by marcio.f on 2007-08-04
Hi, 
 
Can someone help with installing Bochs on Ubuntu (actually is Kubuntu, but I think this doesn't really matters that much)? 
 
This is what I've tried, but without success: 
- Since I didn't have the "rpm" command line utility I downloaded its source code ("rpm-4.4.2.1.tar.gz") and tried to install it: 
$ ./configure 
$ make 
make all-recursive 
make[1]: Entering directory `/home/marcio/rpm-4.4.2.1/rpm-4.4.2.1' 
Making all in po 
make[2]: Entering directory `/home/marcio/rpm-4.4.2.1/rpm-4.4.2.1/po' 
make[2]: Nothing to be done for `all'. 
make[2]: Leaving directory `/home/marcio/rpm-4.4.2.1/rpm-4.4.2.1/po' 
Making all in misc 
make[2]: Entering directory `/home/marcio/rpm-4.4.2.1/rpm-4.4.2.1/misc' 
gcc -DHAVE_CONFIG_H -I. -I.. -I. -I.. -g -O2 -fPIC -DPIC -D_GNU_SOURCE -D_REENTRANT -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wno-char-subscripts -fno-strict-aliasing -MT glob.o -MD -MP -MF .deps/glob.Tpo -c -o glob.o glob.c 
In file included from glob.c:47: 
../system.h:295:29: error: selinux/selinux.h: No such file or directory 
make[2]: *** [glob.o] Error 1 
make[2]: Leaving directory `/home/marcio/rpm-4.4.2.1/rpm-4.4.2.1/misc' 
make[1]: *** [all-recursive] Error 1 
make[1]: Leaving directory `/home/marcio/rpm-4.4.2.1/rpm-4.4.2.1' 
make: *** [all] Error 2 
 
- As that didn't work out I tried to unarchive the Bochs rpm file with 7-Zip: 
$ 7z x bochs-2.3-1.i586.rpm 
$ 7z x bochs-2.3-1.i586.cpio.gz 
$ 7z x \[Content\] 
Then I moved the folder "usr" to the filesystem root and: 
$ chmod +x /usr/bin/bochs* /usr/bin/bx* 
$ bochs 
5 <ENTER> 
00000000000i[ ] installing sdl module as the Bochs GUI 
00000000000i[ ] Bochs x86 Emulator 2.3 
00000000000i[ ] Build from CVS snapshot on August 27, 2006 
00000000000i[ ] System configuration 
00000000000i[ ] processors: 1 (cores=1, HT threads=1) 
00000000000i[ ] A20 line support: yes 
00000000000i[ ] APIC support: no 
00000000000i[ ] CPU configuration 
00000000000i[ ] level: 5 
00000000000i[ ] paging support: yes, tlb enabled: yes 
00000000000i[ ] SMP support: no 
00000000000i[ ] FPU support: yes 
00000000000i[ ] MMX support: yes 
00000000000i[ ] SSE support: no 
00000000000i[ ] v8086 mode support: yes 
00000000000i[ ] VME support: yes 
00000000000i[ ] 3dnow! support: no 
00000000000i[ ] PAE support: no 
00000000000i[ ] PGE support: no 
00000000000i[ ] PSE support: yes 
00000000000i[ ] x86-64 support: no 
00000000000i[ ] SEP support: no 
00000000000i[ ] Optimization configuration 
00000000000i[ ] Guest2HostTLB support: no 
00000000000i[ ] RepeatSpeedups support: no 
00000000000i[ ] Icache support: no 
00000000000i[ ] Host Asm support: yes 
00000000000i[ ] Fast function calls: no 
00000000000i[ ] Devices configuration 
00000000000i[ ] NE2000 support: no 
00000000000i[ ] PCI support: no 
00000000000i[ ] SB16 support: no 
00000000000i[ ] USB support: no 
00000000000i[ ] VGA extension support: 
00000000000i[MEM0 ] allocated memory at 0xb5a7c008. after alignment, vector=0xb5a7d000 
00000000000i[MEM0 ] 32.00MB 
00000000000i[MEM0 ] rom at 0xffff0000/65536 ('/usr/local/share/bochs/BIOS-bochs-latest') 
00000000000i[MEM0 ] rom at 0xc0000/38400 ('/usr/local/share/bochs/VGABIOS-lgpl-latest') 
00000000000i[CMOS ] Using local time for initial clock 
00000000000i[CMOS ] Setting initial clock to: Sat Aug 4 14:42:27 2007 (time0=1186234947) 
00000000000i[DMA ] channel 4 used by cascade 
00000000000i[DMA ] channel 2 used by Floppy Drive 
00000000000i[MEM0 ] Register memory access handlers: 000a0000-000bffff 
00000000000p[SDL ] >>PANIC<< Unable to initialize SDL libraries 
00000000000i[SYS ] Last time is 1186234947 
00000000000i[ ] restoring default signal behavior 
======================================================================== 
Bochs is exiting with the following message: 
[SDL ] Unable to initialize SDL libraries 
======================================================================== 
00000000000i[CTRL ] quit_sim called with exit code 1 
 
- After this I tried to compile Bochs ("bochs-2.3.tar.gz"): 
$ ./configure 
configure: WARNING: Bochs for wxWidgets cannot be compiled here, disabling it 
checking for default gui on this platform... x11 
ERROR: X windows gui was selected, but X windows libraries were not found. 
 
- Then I saw it could use SDL, so I downloaded SDL ("SDL-1.2.12.zip") and compiled it: 
$ ./configure 
$ make 
$ sudo make install 
 
- Proceeded to Bochs: 
$ ./configure --with-sdl 
$ make 
$ sudo make install 
 
- No problems here so I tried to run Bochs once again: 
$ bochs 
5 <ENTER> 
00000000000i[ ] installing sdl module as the Bochs GUI 
00000000000i[ ] using log file bochsout.txt 
======================================================================== 
Bochs is exiting with the following message: 
[SDL ] Unable to initialize SDL libraries 
======================================================================== 
 
- After that I tried to use the SDL rpm file ("SDL-1.2.12-1.i386.rpm"): 
$ 7z x SDL-1.2.12-1.i386.rpm 
$ 7z x SDL-1.2.12-1.i386.cpio.gz 
$ 7z x SDL-1.2.12-1.i386.cpio 
 
- Moved the folder "usr" to the filesystem root and: 
$ bochs 
5 <ENTER> 
00000000000i[ ] installing sdl module as the Bochs GUI 
00000000000i[ ] Bochs x86 Emulator 2.3 
00000000000i[ ] Build from CVS snapshot on August 27, 2006 
00000000000i[ ] System configuration 
00000000000i[ ] processors: 1 (cores=1, HT threads=1) 
00000000000i[ ] A20 line support: yes 
00000000000i[ ] APIC support: no 
00000000000i[ ] CPU configuration 
00000000000i[ ] level: 5 
00000000000i[ ] paging support: yes, tlb enabled: yes 
00000000000i[ ] SMP support: no 
00000000000i[ ] FPU support: yes 
00000000000i[ ] MMX support: yes 
00000000000i[ ] SSE support: no 
00000000000i[ ] v8086 mode support: yes 
00000000000i[ ] VME support: yes 
00000000000i[ ] 3dnow! support: no 
00000000000i[ ] PAE support: no 
00000000000i[ ] PGE support: no 
00000000000i[ ] PSE support: yes 
00000000000i[ ] x86-64 support: no 
00000000000i[ ] SEP support: no 
00000000000i[ ] Optimization configuration 
00000000000i[ ] Guest2HostTLB support: no 
00000000000i[ ] RepeatSpeedups support: no 
00000000000i[ ] Icache support: no 
00000000000i[ ] Host Asm support: yes 
00000000000i[ ] Fast function calls: no 
00000000000i[ ] Devices configuration 
00000000000i[ ] NE2000 support: no 
00000000000i[ ] PCI support: no 
00000000000i[ ] SB16 support: no 
00000000000i[ ] USB support: no 
00000000000i[ ] VGA extension support: 
00000000000i[MEM0 ] allocated memory at 0xb5ac0008. after alignment, vector=0xb5ac1000 
00000000000i[MEM0 ] 32.00MB 
00000000000i[MEM0 ] rom at 0xffff0000/65536 ('/usr/local/share/bochs/BIOS-bochs-latest') 
00000000000i[MEM0 ] rom at 0xc0000/38400 ('/usr/local/share/bochs/VGABIOS-lgpl-latest') 
00000000000i[CMOS ] Using local time for initial clock 
00000000000i[CMOS ] Setting initial clock to: Sat Aug 4 14:52:16 2007 (time0=1186235536) 
00000000000i[DMA ] channel 4 used by cascade 
00000000000i[DMA ] channel 2 used by Floppy Drive 
00000000000i[MEM0 ] Register memory access handlers: 000a0000-000bffff 
00000000000p[SDL ] >>PANIC<< Unable to initialize SDL libraries 
00000000000i[SYS ] Last time is 1186235536 
00000000000i[ ] restoring default signal behavior 
======================================================================== 
Bochs is exiting with the following message: 
[SDL ] Unable to initialize SDL libraries 
======================================================================== 
00000000000i[CTRL ] quit_sim called with exit code 1 
 
- Finally I tried with WxWidgets ("wxWidgets-2.8.4.tar.gz"): 
$ ./configure --with-x11 --disable-shared --enable-log --enable-debug -without-odbc --enable-debug_cntxt 
configure: error: X11 not found, please use --x-includes and/or --x-libraries options (see config.log for details) 
 
$ ./configure --with-sdl --disable-shared --enable-log --enable-debug -without-odbc --enable-debug_cntxt 
configure: error: X11 not found, please use --x-includes and/or --x-libraries options (see config.log for details) 

Thanks!

---

### Post by marcio.f on 2007-08-06
Never mind guys, I have successfully installed it. Thanks anyway. :)

---

### Post by pramodp on 2008-02-06
Hi 

Can you share the exact steps that you followed to install bochs... I also getting the same error as u.

configure: WARNING: Bochs for wxWidgets cannot be compiled here, disabling it
checking for default gui on this platform... x11
ERROR: X windows gui was selected, but X windows libraries were not found.


Thanks in advance 


-Pramod

---

### Post by marcio.f on 2008-02-06
I'm sorry but I can't remember anymore... :(

---

### Post by pramodp on 2008-02-07
I was able to resolve the above error.... !!
These are the steps

apt-get install build-essential
apt-get install libwxgtk2.6-0
apt-get install libwxgtk2.6-dev wx2.6-headers wx-common

apt-get install libx11-dev
apt-get install libxmu-dev
apt-get install libxmuu-dev
apt-get install xlibs-dev

-Pramod

---

