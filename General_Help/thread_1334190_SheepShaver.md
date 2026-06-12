---
title: "SheepShaver"
date: 2009-11-22
forum: General Help
---

### Post by acidtuch10 on 2009-11-22
Has anyone been able to successfully get sheepshaver installed and working on Ubuntu 9.10? (Opens and when you hit run it just disappears) 

I have installed on two systems (Both running 9.10) following these directions ([http://www.olpcnews.com/forum/index.php?topic=4215](http://www.olpcnews.com/forum/index.php?topic=4215))

Just to check I installed Ubuntu 9.04 and well everything worked correctly. Tried again using Ubuntu 9.10 and it failed.

---

### Post by acidtuch10 on 2009-11-25
Anyone ?

---

### Post by nyvaerld on 2009-11-29
Same problem.

I even tried compiling SheepShaver myself, which required a bit of tinkering with the source code that wouldn't compile right away.

But the emulator crashes on launch with a segmentation fault.  It used to work just fine in Ubuntu 9.04.

I can't figure out how to solve this...

---

### Post by ibuclaw on 2009-11-29
New software/libraries tend not to be backwards compatible with old software.

Having a look, the last release was SheepShaver 2.3-Pre (14.May.2006)

Try downloading the sources and compiling.
[http://gwenole.beauchesne.info/en/projects/sheepshaver#downloads](http://gwenole.beauchesne.info/en/projects/sheepshaver#downloads)

UPDATE:
I've managed to compile and start the app with no issues.
Whether or not it can load a ROM is something else that I won't test. (unless someone has something I can use/test against).
If you require the patches I made to get it started - just say.

Regards
Iain

---

### Post by loloemr2 on 2009-11-30
@tinivole : 
you succeeded under 9.10 or 9.04 ?

@others : same problems for me ... I have tried to contact the program creator, with no hope for an answer since he hasn't updated it's code for 3 years ...

---

### Post by zlef on 2009-11-30
Anybody seems to have the same problems with it. I've not yet tried on [www.emaculation.com](www.emaculation.com). They mainly seem to work for Win and OS X. Maybe I will try later, because at least, they keep the code up to date there. 
To me it appears, that autogen creates an invalid configure. Did anything change in the standard build tools from 9.04 to 9.10? 

At tinivole: can you post the patch you mention? If one of us can compile it, we can check for the segfault as well. 

Thanks, 

zlef

---

### Post by lubod on 2009-11-30
> **tinivole said:**
> New software/libraries tend not to be backwards compatible with old software.

Having a look, the last release was SheepShaver 2.3-Pre (14.May.2006)

Try downloading the sources and compiling.
[http://gwenole.beauchesne.info/en/projects/sheepshaver#downloads](http://gwenole.beauchesne.info/en/projects/sheepshaver#downloads)

UPDATE:
I've managed to compile and start the app with no issues.
Whether or not it can load a ROM is something else that I won't test. (unless someone has something I can use/test against).
If you require the patches I made to get it started - just say.

Regards
Iain

I'd be really grateful for patches/assistance in getting it to compile/run here. Karmic 9.10 amd64 system if that makes any difference.

I'd very generally/superficially familiar with the process of compiling things from source, but the specifics required for certain operations escape me, because I'm rusty, having done it rarely. I use the repositories whenever possible, including extras/commercial/multiverse/medibuntu.

Ideally I'd like to compile it, but probably better yet to make a .deb with checkinstall, maybe submit it for inclusion in the repositories.

---

### Post by afrodeity on 2009-12-12
> **tinivole said:**
> New software/libraries tend not to be backwards compatible with old software.

Having a look, the last release was SheepShaver 2.3-Pre (14.May.2006)

Try downloading the sources and compiling.
[http://gwenole.beauchesne.info/en/projects/sheepshaver#downloads](http://gwenole.beauchesne.info/en/projects/sheepshaver#downloads)

UPDATE:
I've managed to compile and start the app with no issues.
Whether or not it can load a ROM is something else that I won't test. (unless someone has something I can use/test against).
If you require the patches I made to get it started - just say.

Regards
Iain

Haven't been able to compile on Karmic. There is a jaunty build but it seg faults. If there's a patch I might be able to assist you with what you seek.;)

---

### Post by ibuclaw on 2009-12-12
Build Requires:
```
sudo apt-get install build-essential xorg-dev
```

As stated before - can get it to build + application loads OK, but have not tested any images (unless you want to point me in the right direction of that for testing).

To apply the patch:
- Extract SheepShaver tarball
- Run:
```
zcat ss.patch.gz | patch -p0
```
Then
```
cd SheepShaver-2.3/src/Unix
./configure && make
```
Regards

---

### Post by afrodeity on 2009-12-12
```

File to patch: Makefile
patching file Makefile
Hunk #1 FAILED at 41.
1 out of 1 hunk FAILED -- saving rejects to file Makefile.rej
can't find file to patch at input line 13
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- SheepShaver-2.3-orig/cxmon-3.0/src/mon_ppc.cpp	2002-03-02 15:47:52.000000000 +0000
|+++ SheepShaver-2.3/cxmon-3.0/src/mon_ppc.cpp	2009-12-12 12:44:36.000000000 +0000
---------
```

Am I patching the wrong file?

---

### Post by ibuclaw on 2009-12-12
> **afrodeity said:**
> ```

File to patch: Makefile
patching file Makefile
Hunk #1 FAILED at 41.
1 out of 1 hunk FAILED -- saving rejects to file Makefile.rej
can't find file to patch at input line 13
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- SheepShaver-2.3-orig/cxmon-3.0/src/mon_ppc.cpp	2002-03-02 15:47:52.000000000 +0000
|+++ SheepShaver-2.3/cxmon-3.0/src/mon_ppc.cpp	2009-12-12 12:44:36.000000000 +0000
---------
```

Am I patching the wrong file?

yes, lol.

it shouldn't ask you to type in the file name to patch.

If it is, try patch with the option **-p1** instead.

---

### Post by afrodeity on 2009-12-13
```

zcat ss.patch.gz | patch -p1
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- SheepShaver-2.3-orig/cxmon-3.0/src/disass/i386-dis.c	2003-02-06 10:14:47.000000000 +0000
|+++ SheepShaver-2.3/cxmon-3.0/src/disass/i386-dis.c	2009-12-12 13:42:15.000000000 +0000
--------------------------
File to patch: 

```

Maybe the problem is the path to the file  /src/XXXX

---

### Post by mitmap on 2009-12-13
I viewed source code of a patch and noticed that it tryes to patch files in "SheepShaver-2.3-orig" folder, so I changed the folder name and now the patch works correctly.

---

### Post by mitmap on 2009-12-13
BUT: after compiling it even could not open a sheepshaver window!

---

### Post by afrodeity on 2009-12-13
The patch patches. I compiled & installed. It starts but it fails miserably if I try to launch. Still seg faulting I guess, but no info in terminal. :(

My guess is something to do with SDL. The configure option lists it currently as SDL none.

---

### Post by ibuclaw on 2009-12-13
> **afrodeity said:**
> The patch patches. I compiled & installed. It starts but it fails miserably if I try to launch. Still seg faulting I guess, but no info in terminal. :(

My guess is something to do with SDL. The configure option lists it currently as SDL none.

What are you testing it with?

FYI - I do the following:
```

wget http://gwenole.beauchesne.info/projects/sheepshaver/files/SheepShaver-2.3-0.20060514.1.tar.bz2
tar -xf SheepShaver-2.3-0.20060514.1.tar.bz2 
zcat ss.patch.gz | patch -p0
cd SheepShaver-2.3/src/Unix/
./configure && make

```

I doubt it is because SDL is turned off. Just looking at the build - you can either use SDL or Xorg. Not both.

To build with SDL though:
```
./configure --enable-sdl-video
```

Since it is an old piece of software - perhaps installing gcc-3.4 and setting CC flags correct will remedy all issues it has?

---

### Post by ibuclaw on 2009-12-13
> **tinivole said:**
> 
Since it is an old piece of software - perhaps installing gcc-3.4 and setting CC flags correct will remedy all issues it has?
The lack of libstdc++5 would likely contribute to the problem also...

Statically compiling the application, in say Hardy might be the better option.

---

### Post by afrodeity on 2009-12-13
Will see where this leads me. In the meantime, searching for newworld86 rom will probably bless your machine with some apple-ability. It certainly helped me the last time.:)

BTW can one have two versions of gcc installed? i'm on karmic, so its the latest version with libstdc++6-4.4-dev.

---

### Post by afrodeity on 2009-12-13
This is interesting:

```

The program 'SheepShaver' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 9 error_code 2 request_code 105 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by afrodeity on 2009-12-13
Getting warmer. The last time I did this, there was a hack.

[http://ubuntuforums.org/archive/index.php/t-802457.html](http://ubuntuforums.org/archive/index.php/t-802457.html)

but one has to build it a bit differently.

[http://www.emaculation.com/forum/viewtopic.php?t=5886&highlight=ubuntu+karmic](http://www.emaculation.com/forum/viewtopic.php?t=5886&highlight=ubuntu+karmic)

Haven't figured it all out just yet, need to get some sleep.

---

### Post by afrodeity on 2009-12-14
It appears Karmic is configure a little different;

Changes need to be made in the /etc/sysctl.d$ directory

```
this directory contains settings similar to those found in /etc/sysctl.conf.
In general, files in the 10-*.conf range come from the procps package and
serve as system defaults.  Other packages install their files in the
30-*.conf range, to override system defaults.  End-users can use 60-*.conf
and above, or use /etc/sysctl.conf directly, which overrides anything in
this directory.

After making any changes, please run "invoke-rc.d procps start".
```

For instance, WINE which has exactly the same problem, has this file:

30-wine.conf

```

# Wine needs to access the bottom 64k of memory in order to launch
# 16 bit programs.
vm.mmap_min_addr = 0

```

I've tried adding the vm.mmap_min_addr = 0 to sysctl.conf directly, but this is obviously what we don't want to do,besides, the fix no longer works there.
So question is, what should the SheepShaver.conf file be called and how will SheepShaver see it?

---

### Post by afrodeity on 2009-12-14
I tried putting the line in 70-sheepshaver.conf

and starting it with

sudo sysctl -p /etc/sysctl.d/70-sheepshaver.conf

But still not. About to tear my hair out.Probably a bug with sysctl


[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/447197](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/447197)

---

### Post by ibuclaw on 2009-12-14
I can tell you this is where it seems to bomb out (for me).
```

#if REAL_ADDRESSING && HAVE_LINKER_SCRIPT
    /* Put in by me */
    D(bug("Running vm_mac_acquire\n"));
/* main_unix.cpp, line 815 */
**    if (vm_mac_acquire(0, RAMSize) == 0) {**
            D(bug("Could allocate RAM from 0x0000\n"));
            RAMBase = 0;
            memory_mapped_from_zero = true;
    }
    /* Put in by me */
    D(bug("OK - Leaving\n"));
#endif

```
It doesn't seem to get any further than the emboldened line, as no further output is given.

Which is running the function:
```

static inline int vm_mac_acquire(uint32 addr, uint32 size)
{
        return vm_acquire_fixed(Mac2HostAddr(addr), size);
}

```
Now, to trace what **vm_acquire_fixed()** does, added in debug bits and pieces there, and got thus far:
```
if (mmap((caddr_t)addr, size, VM_PAGE_DEFAULT, the_map_flags, fd, 0) == (void *)MAP_FAILED)
```
My debugging prints with strace output shows:
```

Attempt mmap()
	if (mmap((caddr_t)addr, size, VM_PAGE_DEFAULT, the_map_flags, fd, 0) == (void *)MAP_FAILED)
        if (mmap((caddr_t)0, 16777216, 3, 114, -1, 0) == (void *)-1)
[{WIFSIGNALED(s) && WTERMSIG(s) == SIGSEGV}], 0) = 6422
--- SIGCHLD (Child exited) @ 0 (0) ---
exit_group(-1)                          = ?

```
And ltrace output shows:
```

Attempt mmap()
	if (mmap((caddr_t)addr, size, VM_PAGE_DEFAULT, the_map_flags, fd, 0) == (void *)MAP_FAILED)
        if (mmap((caddr_t)0, 16777216, 3, 114, -1, 0) == (void *)-1)
 <unfinished ...>
--- SIGCHLD (Child exited) ---
+++ exited (status 255) +++

```
So you may be right that something is stopping the application from mapping to 0 address.

And setting /proc/sys/vm/mmap_min_addr = 0 does not seem to resolve the issue. (In Hardy, it is set to 65536 too, so I think you are looking up the wrong tree, perhaps).

Regards
Iain

---

### Post by ibuclaw on 2009-12-14
You know what - I think I've cracked it :)

```

--- SheepShaver-2.3-orig/src/Unix/main_unix.cpp	2006-05-09 20:53:31.000000000 +0100
+++ SheepShaver-2.3/src/Unix/main_unix.cpp	2009-12-14 19:53:54.000000000 +0000
@@ -811,7 +811,8 @@ int main(int argc, char **argv)
 		RAMSize = 8*1024*1024;
 	}
 	memory_mapped_from_zero = false;
-#if REAL_ADDRESSING && HAVE_LINKER_SCRIPT
+/* Don't run if PAGEZERO_HACK is undefined */
+#if REAL_ADDRESSING && HAVE_LINKER_SCRIPT && PAGEZERO_HACK
 	if (vm_mac_acquire(0, RAMSize) == 0) {
 		D(bug("Could allocate RAM from 0x0000\n"));
 		RAMBase = 0;

```
At least it get to the "Cannot open ROM file" message, which is exactly the same as what I get on Hardy.

I considered this solved. But will need someone else to confirm (as I have nothing to test against).

Regards
Iain

---

### Post by afrodeity on 2009-12-14
Gosh, that's some coding skill you have there. I take it I apply the patch against the source like the previous one? :)

---

### Post by ibuclaw on 2009-12-15
> **afrodeity said:**
> Gosh, that's some coding skill you have there. I take it I apply the patch against the source like the previous one? :)

Yep, you can do, and it should apply just fine.
If you want to apply against a new extract of the tarball source though, I've taken down the previous attachments and just bunged them all into this big one here.

Regards
Iain

---

### Post by afrodeity on 2009-12-15
Hooray, it works, well almost. Oldworld quits in startup. There's still a problem with memory allocation, but maybe we can fix it.

```

SheepShaver
SheepShaver V2.3-Pre (Dec 15 2009) by Christian Bauer and Mar"c" Hellwig
Reading ROM file...
WARNING: Cannot open /dev/dsp (Device or resource busy)
Using ESD audio output
Detected CPU features: MMX SSE SSE2 SSE3 SSE4
PowerPC CPU emulator by Gwenole Beauchesne
SIGSEGV
  pc 0x780b2e3d
  ea 0x40000000
 r0 00000000   r1 25ffa0f0   r2 00000000   r3 4084a340
 r4 408031a0   r5 00006706   r6 ffffd3ce   r7 00001efc
 r8 00000002   r9 20066890  r10 ffffffff  r11 00001f00
r12 ffff0000  r13 00020000  r14 00000020  r15 00000039
r16 20066890  r17 40000000  r18 408031a0  r19 40849862
r20 00001f6c  r21 26000190  r22 20000000  r23 00000000
r24 40849840  r25 00000020  r26 00000000  r27 ffff9481
r28 00000000  r29 40ce2488  r30 40c60000  r31 68fff000
 f0 0.00000   f1 0.00000   f2 0.00000   f3 0.00000
 f4 0.00000   f5 0.00000   f6 0.00000   f7 0.00000
 f8 0.00000   f9 0.00000  f10 0.00000  f11 0.00000
f12 0.00000  f13 0.00000  f14 0.00000  f15 0.00000
f16 0.00000  f17 0.00000  f18 0.00000  f19 0.00000
f20 0.00000  f21 0.00000  f22 0.00000  f23 0.00000
f24 0.00000  f25 0.00000  f26 0.00000  f27 0.00000
f28 0.00000  f29 0.00000  f30 0.00000  f31 0.00000
 lr 40ce2488  ctr 00000000   cr 40101f2f  xer 00000000
 pc 40ce2488 fpscr 00000000
### Statistics for block predecode
Total block predecode count : 24833
Total emulation time : 7.0 sec
Total predecode time : 0.0 sec (0.3%)


```

---

### Post by afrodeity on 2009-12-15
Hahah, its running fine with the Newworld Rom.

There's probably newer code in the CVS, but the server's been down whole week.

```

cvs -d :pserver:anoncvs@cvs.cebix.net:/home/cvs/cebix checkout BasiliskII
cvs -d :pserver:anoncvs@cvs.cebix.net:/home/cvs/cebix checkout SheepShaver 

```

mathieudel [reports]("http://www.emaculation.com/forum/viewtopic.php?t=5886&highlight=ubuntu") that he compiled by adding

#include <limits.h>

to the sys_unix.cpp file, but not sure if this was on Karmic.

If you still need a ticket to the New World mail me privately.;)

UPDATE: The ** may not be necessary,its just starting, will know when I reboot.

---

### Post by lubod on 2009-12-22
@tinivole: Thanks very much for the two patches! 

I did manage to apply your latest one, gcc4+pagezero.patch.gz to the 20060514 tar.bz2 source archive to get a running binary. This is built for amd64 (aka x86_64) systems.

@afrodeity:
This build was crashing on me with an Old World ROM and older Mac OS (7.5.5) too, but turning on the "Ignore Illegal Memory Accesses" option in the "Memory/Misc." tab of SheepShaver seems to have stabilized it quite a bit. No extensive testing yet to prove it is completely stable, but it gets through startup ok. 

For fastest performance, hold down Shift during startup. (You do remember starting with Extensions off, right?) Then you can customize a small but still manageable set of them to turn back on with Extensions Manager.

My build 20060514 with tinivole's patch is in a amd64 .deb so it can be installed with minimal hassle and no further compilation. It also puts in the necessary files to enable launching SheepShaver from the Gnome Applications menu, point and click style. After it is installed, there should be an entry under Applications/System called SheepShaver with the proper icon.

I was going to post it in a PPA, but it seems that requires a source package generated by debuild and its related utilities, and I just built my .deb by hand from the output of dpkg -b so I will have to learn how the complete debuild process rather than the manual shortcut works first. File can be downloaded from:

[http://members.dslextreme.com/~lubod/sheepshaver-2.3.0.20060514.1-0ubuntu1-amd64.deb](http://members.dslextreme.com/~lubod/sheepshaver-2.3.0.20060514.1-0ubuntu1-amd64.deb)

The 32 bit build (not built by me, just adding the link in case anyone missed it elsewhere):

[http://www.mediafire.com/download.php?km05zohjfm5](http://www.mediafire.com/download.php?km05zohjfm5)

P.S.

There is now what I'd call a semi-official build in the PPA below: (not directly supported by Ubuntu, but built by one of the knowledgeable packagers, Marc Deslaurier)

[https://launchpad.net/~mdeslaur/+archive/ppa/+packages]("https://launchpad.net/~mdeslaur/+archive/ppa/+packages")

---

### Post by billy314 on 2010-02-14
Sorry to revive an old dead thread (assumably), but when I try applying the patch I get this:
```
billy@billy-desktop:~/Desktop$ sudo zcat gcc4+pagezero.patch.gz | patch -p0
[sudo] password for billy: 
patching file SheepShaver-2.3-orig/src/include/ether_defs.h
Reversed (or previously applied) patch detected!  Assume -R? [n] y
patching file SheepShaver-2.3-orig/src/kpx_cpu/src/cpu/ppc/ppc-cpu.cpp
Hunk #1 FAILED at 256.
Hunk #2 FAILED at 540.
Hunk #3 FAILED at 562.
Hunk #4 FAILED at 585.
Hunk #5 FAILED at 596.
Hunk #6 FAILED at 606.
Hunk #7 FAILED at 656.
Hunk #8 FAILED at 691.
Hunk #9 FAILED at 767.
Hunk #10 FAILED at 811.
10 out of 10 hunks FAILED -- saving rejects to file SheepShaver-2.3-orig/src/kpx_cpu/src/cpu/ppc/ppc-cpu.cpp.rej
patching file SheepShaver-2.3-orig/src/kpx_cpu/src/cpu/ppc/ppc-cpu.hpp
Hunk #1 FAILED at 360.
1 out of 1 hunk FAILED -- saving rejects to file SheepShaver-2.3-orig/src/kpx_cpu/src/cpu/ppc/ppc-cpu.hpp.rej
patching file SheepShaver-2.3-orig/src/kpx_cpu/src/cpu/ppc/ppc-dyngen-ops.cpp
Hunk #1 FAILED at 96.
Hunk #2 FAILED at 1268.
Hunk #3 FAILED at 1290.
3 out of 3 hunks FAILED -- saving rejects to file SheepShaver-2.3-orig/src/kpx_cpu/src/cpu/ppc/ppc-dyngen-ops.cpp.rej
patching file SheepShaver-2.3-orig/src/kpx_cpu/src/cpu/ppc/ppc-translate.cpp
Hunk #1 FAILED at 143.
Hunk #2 FAILED at 1570.
2 out of 2 hunks FAILED -- saving rejects to file SheepShaver-2.3-orig/src/kpx_cpu/src/cpu/ppc/ppc-translate.cpp.rej
can't find file to patch at input line 198
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- SheepShaver-2.3-orig/src/slirp/slirp.h    2006-04-29 11:54:12.000000000 +0100
|+++ SheepShaver-2.3/src/slirp/slirp.h    2009-12-12 13:41:48.000000000 +0000
--------------------------
File to patch: 

```Advice?

---

### Post by afrodeity on 2010-02-16
Here is a deb compiled on Karmic using the 2006 snapshot [http://www.mediafire.com/download.php?km05zohjfm5](http://www.mediafire.com/download.php?km05zohjfm5)

---

### Post by billy314 on 2010-02-16
Wow thanks!

And OMG Cosmic Osmo runs pretty well!  Games like this completely failed back when I was using sheepshaver on windows!

---

### Post by fraterf93 on 2010-05-22
Anyone know how I can compile and run this on Ubuntu 10.04 PPC?

---

