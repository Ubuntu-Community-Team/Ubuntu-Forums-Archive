---
title: "Amd64: 32bit vs. 64bit speed"
date: 2006-06-03
forum: General Help
---

### Post by OtonVM on 2006-06-03
If someone ever wondered if there is a speed difference between a fuly optimized and custom built system for amd64 (gentoo) and a normal 32bit ubuntu installation, here are the results of nbench:

[FONT="Impact"]**Gentoo:**[/FONT]
CFLAGS="-O2 -march=k8 -ffast-math -fomit-frame-pointer -pipe -funroll-loops -msse3"
ACCEPT_KEYWORDS="~amd64"

Results:
BYTEmark* Native Mode Benchmark ver. 2 (10/95)
Index-split by Andrew D. Balsa (11/97)
Linux/Unix* port by Uwe F. Mayer (12/96,11/97)

============================== ALL STATISTICS ===============================
**Date and time of benchmark run: Fri Jun  2 15:28:03 2006
**Sizeof: char:1 short:2 int:4 long:8 u8:1 u16:2 u32:4 int32:4
**System used for compilation:
**Linux gentoo 2.6.16-gentoo-r7-amd64 #1 Mon May 8 22:22:36 CEST 2006 x86_64 AMD
**C compiler: 4.1.0
**libc:
**Date of compilation: Fri Jun  2 15:27:19 CEST 2006
=============================================================================

TEST                : Iterations/sec.  : Old Index   : New Index
                    :                  : Pentium 90* : AMD K6/233*
--------------------:------------------:-------------:------------
NUMERIC SORT        :          1012.1  :      25.96  :       8.52
  Absolute standard deviation: 56.7815
  Relative standard deviation: 5.61045 %
  Number of runs: 9
  Number of arrays: 3
  Array size: 8111
Done with NUMERIC SORT

STRING SORT         :          183.84  :      82.14  :      12.71
  Absolute standard deviation: 0.60663
  Relative standard deviation: 0.329977 %
  Number of runs: 5
  Number of arrays: 2
  Array size: 8111
Done with STRING SORT

BITFIELD            :      3.4643e+08  :      59.43  :      12.41
  Absolute standard deviation: 632662
  Relative standard deviation: 0.182623 %
  Number of runs: 5
  Operations array size: 130
  Bitfield array size: 16384
Done with BITFIELD

FP EMULATION        :          174.84  :      83.90  :      19.36
  Absolute standard deviation: 0.43359
  Relative standard deviation: 0.247992 %
  Number of runs: 5
  Number of loops: 1
  Array size: 3000
Done with FP EMULATION

FOURIER             :           12532  :      14.25  :       8.01
  Absolute standard deviation: 34.7925
  Relative standard deviation: 0.27763 %
  Number of runs: 5
  Number of coefficients: 100
Done with FOURIER

ASSIGNMENT          :          35.914  :     136.66  :      35.45
  Absolute standard deviation: 0.127856
  Relative standard deviation: 0.356008 %
  Number of runs: 5
  Number of arrays: 1
Done with ASSIGNMENT

IDEA                :          3871.4  :      59.21  :      17.58
  Absolute standard deviation: 11.3398
  Relative standard deviation: 0.292914 %
  Number of runs: 5
  Array size: 4000
 Number of loops: 100
Done with IDEA

HUFFMAN             :          1825.4  :      50.62  :      16.16
  Absolute standard deviation: 3.62183
  Relative standard deviation: 0.198413 %
  Number of runs: 5
  Array size: 5000
  Number of loops: 100
Done with HUFFMAN

NEURAL NET          :          44.609  :      71.66  :      30.14
  Absolute standard deviation: 0.0117837
  Relative standard deviation: 0.0264157 %
  Number of runs: 5
  Number of loops: 1
Done with NEURAL NET

LU DECOMPOSITION    :            1256  :      65.07  :      46.98
  Absolute standard deviation: 6.5238
  Relative standard deviation: 0.519411 %
  Number of runs: 5
  Number of arrays: 4
Done with LU DECOMPOSITION

==========================ORIGINAL BYTEMARK RESULTS==========================
INTEGER INDEX       : 63.907
FLOATING-POINT INDEX: 40.504
Baseline (MSDOS*)   : Pentium* 90, 256 KB L2-cache, Watcom* compiler 10.0
==============================LINUX DATA BELOW===============================
CPU                 : AuthenticAMD AMD Athlon(tm) 64 Processor 3700+ 2200MHz
L2 Cache            : 1024 KB
OS                  : Linux 2.6.16-gentoo-r7-amd64
C compiler          : 4.1.0
libc                :
MEMORY INDEX        : 17.752
INTEGER INDEX       : 14.716
FLOATING-POINT INDEX: 22.465
Baseline (LINUX)    : AMD K6/233*, 512 KB L2-cache, gcc 2.7.2.3, libc-5.4.38
* Trademarks are property of their respective holder.

[FONT="Impact"]**Ubuntu:**[/FONT]
build-essential package, no optimizations or other

Results:
BYTEmark* Native Mode Benchmark ver. 2 (10/95)
Index-split by Andrew D. Balsa (11/97)
Linux/Unix* port by Uwe F. Mayer (12/96,11/97)

============================== ALL STATISTICS ===============================
**Date and time of benchmark run: Sat Jun  3 10:23:08 2006
**Sizeof: char:1 short:2 int:4 long:4 u8:1 u16:2 u32:4 int32:4
**System used for compilation:
**Linux ubuntu 2.6.15-23-k7 #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006 i686 GNU**C compiler: gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
**libc: libc-2.3.6.so
**Date of compilation: Sat Jun  3 09:45:13 CEST 2006
=============================================================================

TEST                : Iterations/sec.  : Old Index   : New Index
                    :                  : Pentium 90* : AMD K6/233*
--------------------:------------------:-------------:------------
NUMERIC SORT        :          1127.1  :      28.91  :       9.49
  Absolute standard deviation: 87.5008
  Relative standard deviation: 7.7632 %
  Number of runs: 13
  Number of arrays: 3
  Array size: 8111
Done with NUMERIC SORT

STRING SORT         :          185.52  :      82.90  :      12.83
  Absolute standard deviation: 1.10995
  Relative standard deviation: 0.598294 %
  Number of runs: 5
  Number of arrays: 2
  Array size: 8111
Done with STRING SORT

BITFIELD            :       3.653e+08  :      62.66  :      13.09
  Absolute standard deviation: 1.51864e+06
  Relative standard deviation: 0.415724 %
  Number of runs: 5
  Operations array size: 30
  Bitfield array size: 32768
Done with BITFIELD

FP EMULATION        :           111.8  :      53.65  :      12.38
  Absolute standard deviation: 0.141421
  Relative standard deviation: 0.126495 %
  Number of runs: 5
  Number of loops: 1
  Array size: 3000
Done with FP EMULATION

FOURIER             :           22590  :      25.69  :      14.43
  Absolute standard deviation: 35.5982
  Relative standard deviation: 0.157581 %
  Number of runs: 5
  Number of coefficients: 100
Done with FOURIER

ASSIGNMENT          :          20.008  :      76.13  :      19.75
  Absolute standard deviation: 0.0332861
  Relative standard deviation: 0.166365 %
  Number of runs: 5
  Number of arrays: 1
Done with ASSIGNMENT

IDEA                :          4748.4  :      72.63  :      21.56
  Absolute standard deviation: 4.6953
  Relative standard deviation: 0.0988817 %
  Number of runs: 5
  Array size: 4000
 Number of loops: 100
Done with IDEA

HUFFMAN             :          1494.6  :      41.45  :      13.23
  Absolute standard deviation: 1.33363
  Relative standard deviation: 0.0892286 %
  Number of runs: 5
  Array size: 5000
  Number of loops: 100
Done with HUFFMAN

NEURAL NET          :          32.257  :      51.82  :      21.80
  Absolute standard deviation: 0.0317147
  Relative standard deviation: 0.0983198 %
  Number of runs: 5
  Number of loops: 1
Done with NEURAL NET

LU DECOMPOSITION    :          1148.2  :      59.48  :      42.95
  Absolute standard deviation: 6.72666
  Relative standard deviation: 0.585865 %
  Number of runs: 5
  Number of arrays: 4
Done with LU DECOMPOSITION

==========================ORIGINAL BYTEMARK RESULTS==========================
INTEGER INDEX       : 56.535
FLOATING-POINT INDEX: 42.941
Baseline (MSDOS*)   : Pentium* 90, 256 KB L2-cache, Watcom* compiler 10.0
==============================LINUX DATA BELOW===============================
CPU                 : AuthenticAMD AMD Athlon(tm) 64 Processor 3700+ 2211MHz
L2 Cache            : 1024 KB
OS                  : Linux 2.6.15-23-k7
C compiler          : gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
libc                : libc-2.3.6.so
MEMORY INDEX        : 14.912
INTEGER INDEX       : 13.533
FLOATING-POINT INDEX: 23.816
Baseline (LINUX)    : AMD K6/233*, 512 KB L2-cache, gcc 2.7.2.3, libc-5.4.38
* Trademarks are property of their respective holder.

There you go.

---

### Post by Ivan Matveich on 2006-06-04
nbench will not reflect the "speed of the system" at all, really. You are just measuring what happens when you compile the same bits of C code in 32- and 64-bit modes.

A better test might be to put a dozen large applications in the startup items of your gnome session and measure how long it takes to load everything when you log in after a reboot....

---

### Post by chien on 2006-06-04
so which is better? 32 or 64? im not a genious and im not good at math, im guessing it is 64, but by how much? is it even noticeable the difference?

---

### Post by HanZo on 2006-06-04
I tried both... but could not tell a real diffeence... apart from 64bit having more issues with incompatible software (or did I miss someting?). Anyway... could be really interesting to know if there's really a difference...

---

### Post by OtonVM on 2006-06-04
Well, nbench is what I always used to test my systems. And it mostly reflected reality; in fact I don't see (feel) any difference between 32 or 64bit. Except that now I can see all those wmv's and all flash in firefox (since I dropped 64bit).

---

### Post by grsing on 2006-06-04
That's pretty much the feeling I got, too.  I eventually just gave up on 64bit, wasn't worth the trouble for the imperceptible speed gain (if there even was one).

---

### Post by Ivan Matveich on 2006-06-05
[QUOTE=chien]so which is better? 32 or 64? im not a genious and im not good at math, im guessing it is 64, but by how much? is it even noticeable the difference?[/QUOTE]

It depends on the application. High-end servers need a large address space, for instance, and numerical algorithms like wide operands. On the other hand, your word processor does not much care one way or the other. Desktop users should buy cheap processors like semprons and spend the difference on a bigger monitor or better speakers, in my opinion.

---

### Post by Ivan Matveich on 2006-06-05
[QUOTE=OtonVM]Well, nbench is what I always used to test my systems. And it mostly reflected reality; in fact I don't see (feel) any difference between 32 or 64bit. Except that now I can see all those wmv's and all flash in firefox (since I dropped 64bit).[/QUOTE]

In general, I agree with you. My point is that one can also invent microbenchmarks where the 64-bit version runs ten times faster than the 32-bit version. That tells you nothing about how long firefox will take to load a web page, or whatever.

---

### Post by OtonVM on 2006-06-06
[QUOTE=Ivan Matveich]In general, I agree with you. My point is that one can also invent microbenchmarks where the 64-bit version runs ten times faster than the 32-bit version. That tells you nothing about how long firefox will take to load a web page, or whatever.[/QUOTE]
Yeah, that was my point.
Anyway, I would never switch to a sempron or a celeron. Belive me, you really feel the difference there. No benchmarks are needed for that. Just transcoding. Or photoshop/gimp. Or youtube.

---

### Post by Kilz on 2006-06-06
You will also not notice if the program wasn't written for 64 bit, but just compiled to run on a 64 bit OS. Try running the 32 bit version of POV vs the 64 bit version. There is a 30% increase in speed.
For those that say they cant have firefox with flash, java, etc without a chroot or other hard setup they are also wrong. That may have been the case with Breezy, but you can add 32 bit applications to 64 bit Dapper without a chroot. That way you have the best of both worlds. 64 bit for programs that benefit from it, and 32 bit applications where they have not written 64 bit versions.
But no biggie, keep using a 32 bit operating system on a computer you probably paid extra for the 64 bit chip if you want to. Just realize that you are rationalizing what you have done.

---

### Post by OtonVM on 2006-06-06
[QUOTE=Kilz]You will also not notice if the program wasn't written for 64 bit, but just compiled to run on a 64 bit OS. Try running the 32 bit version of POV vs the 64 bit version. There is a 30% increase in speed.
For those that say they cant have firefox with flash, java, etc without a chroot or other hard setup they are also wrong. That may have been the case with Breezy, but you can add 32 bit applications to 64 bit Dapper without a chroot. That way you have the best of both worlds. 64 bit for programs that benefit from it, and 32 bit applications where they have not written 64 bit versions.
But no biggie, keep using a 32 bit operating system on a computer you probably paid extra for the 64 bit chip if you want to. Just realize that you are rationalizing what you have done.[/QUOTE]
Look, I have been using a fully compiled 64bit system (and I mean fully) for some time and now I can see there is no difference. Why wasting time with problems on 64bit when now I can simply use automatix? And about the money... I might have been lucky, but there was no big difference between my cpu and a sempron... 45eu max.

---

### Post by Kilz on 2006-06-06
[QUOTE=OtonVM]Look, I have been using a fully compiled 64bit system (and I mean fully) for some time and now I can see there is no difference. Why wasting time with problems on 64bit when now I can simply use automatix? And about the money... I might have been lucky, but there was no big difference between my cpu and a sempron... 45eu max.[/QUOTE]
You may not notice the difference, it doesn't matter to me if you do or do not notice the difference. You may have a 64 bit OS and no applications that were written to make use of that 64 bit capability. 45eu is still wasted money if all you are going to do is run a 32 bit OS on it. You should have saved your money and bought a 32 based processor.
Its like buying a race car, then putting 87 octane in it and driving under the speed limit to save gas. You might as well have bought a prius.

---

### Post by MeneK on 2006-06-06
Is there an easy way to migrate a Dapper-32bit system to Dapper-64bit without too much pain? Or the only way to do it is start again with a clean install?

Thanks!

---

### Post by OtonVM on 2006-06-06
[QUOTE=Kilz]You may not notice the difference, it doesn't matter to me if you do or do not notice the difference. You may have a 64 bit OS and no applications that were written to make use of that 64 bit capability. 45eu is still wasted money if all you are going to do is run a 32 bit OS on it. You should have saved your money and bought a 32 based processor.
Its like buying a race car, then putting 87 octane in it and driving under the speed limit to save gas. You might as well have bought a prius.[/QUOTE]
LOL! relax! 
The point of a 64bit cpu is not only in the fact that it is, in fact, a 64bit cpu, but in the architecture. It will be always faster that a 32bit. Don't ask me why, becouse the guy that explained this to me was a total geek and I didn't understand half of it, but the main point was that. And I assembled enough pc's to feel that. And I have no idea what a prius is, but I don't drive... My girlfriend is the capable here...8-)

---

### Post by panurge77 on 2006-06-06
At least for us gamers, 64 is the top, no matter if the game is running on 32. Yes, I believe in tom's hardware benchmarks ;)
[http://www23.tomshardware.com/cpu.html](http://www23.tomshardware.com/cpu.html)

---

### Post by jdong on 2006-06-06
[QUOTE=OtonVM]LOL! relax! 
The point of a 64bit cpu is not only in the fact that it is, in fact, a 64bit cpu, but in the architecture. It will be always faster that a 32bit. Don't ask me why, becouse the guy that explained this to me was a total geek and I didn't understand half of it, but the main point was that. And I assembled enough pc's to feel that. And I have no idea what a prius is, but I don't drive... My girlfriend is the capable here...8-)[/QUOTE]

Thank you :)

There have been a number of 64-bit myths floating around here. You might also want to look at some of the other 32-bit vs 64-bit threads.

Bottom line, unless you do something special that benefits from 64-bit, stick with 32-bit for compatibility reasons.

Just compiling source code into 64-bit binaries yields no significant change in performance (sometimes faster, sometimes slower, but never by a whole lot). **However**, software optimized for 64-bit execution (i.e. hand-tuned assembly, etc) will run significantly better given 64-bit mode. Also, if you have any software that benefits from using more than 4GB of RAM at a time, you will also benefit from 64-bit.


When you buy an AMD64 processor, you are getting your speed gains from the processor's design advantages over main competitors (Modern Intel chips except the Cores). Whether you're in 32-bit or 64-bit mode is not the main issue. So, you're **not wasting your money or limiting yourself** by using your AMD64 in 32-bit mode. I do that on most of my AMD64 machines.



As far as my speed experiences... Day to day tasks (web browsing, system startup, application performance of desktop programs) i feel no difference between 32-bit and 64-bit modes, except that the 64-bit kernel takes about 5 seconds longer to initialize to the splash screen (big whoop.) However, media encoding, certain codecs (libavcodec's mpeg4, libx264) get around a 10% performance boost in 64-bit mode. Even that is no big deal for me... when I start these tasks, they take around an hour or two to complete, so I honestly don't care that it finishes 7 minutes earlier in 64-bit mode :)


BTW, a Prius is a ultra compact Toyota car known for its absurdly high fuel economy, though at a tremendous price in performance :)

---

### Post by panurge77 on 2006-06-06
I too found it strange that the boot takes longer on 64 kernel. The difference was 10 secs here...

---

### Post by Kilz on 2006-06-06
[QUOTE=jdong]Thank you :)

There have been a number of 64-bit myths floating around here. You might also want to look at some of the other 32-bit vs 64-bit threads.

Bottom line, unless you do something special that benefits from 64-bit, stick with 32-bit for compatibility reasons.

Just compiling source code into 64-bit binaries yields no significant change in performance (sometimes faster, sometimes slower, but never by a whole lot). **However**, software optimized for 64-bit execution (i.e. hand-tuned assembly, etc) will run significantly better given 64-bit mode. Also, if you have any software that benefits from using more than 4GB of RAM at a time, you will also benefit from 64-bit.


When you buy an AMD64 processor, you are getting your speed gains from the processor's design advantages over main competitors (Modern Intel chips except the Cores). Whether you're in 32-bit or 64-bit mode is not the main issue. So, you're **not wasting your money or limiting yourself** by using your AMD64 in 32-bit mode. I do that on most of my AMD64 machines.



As far as my speed experiences... Day to day tasks (web browsing, system startup, application performance of desktop programs) i feel no difference between 32-bit and 64-bit modes, except that the 64-bit kernel takes about 5 seconds longer to initialize to the splash screen (big whoop.) However, media encoding, certain codecs (libavcodec's mpeg4, libx264) get around a 10% performance boost in 64-bit mode. Even that is no big deal for me... when I start these tasks, they take around an hour or two to complete, so I honestly don't care that it finishes 7 minutes earlier in 64-bit mode :)


BTW, a Prius is a ultra compact Toyota car known for its absurdly high fuel economy, though at a tremendous price in performance :)[/QUOTE]

Basically what I said, you can compile a OS or a program for 64 bits, but unless its written for it it isn't going to make that much of a difference. Comparing 32 bit programs compiled under 64 bit and posting it as "benchmarks" is deceptive at best.
There may be few programs out there now that give a real large boost, but more are being produced every day. Unless you are running a 64 bit OS there is no way to know what those advantages are because the move to 64 bits is moving faster all the time. What was true 6 months ago may not be true today, and for sure wont be true 6 months down the road.
You may be willing to give up 7 or 10 minutes here or there. But posts like this that say someone is moving to 32 bits may influence someone who may benefit from those time savings. They may not know if a program they are using could shave 2 or 3 hours off of the time like 64 bit POV can.

You can floor a prius and have great acceleration, the fuel savings is all in how you drive it.

---

### Post by OtonVM on 2006-06-06
You mean a kernel compiled within 64bit enviroment or just compiled for k8? Becouse I compiled it yesterday becouse of some usb problems and it booted as usual... no problem. That is: inside 32bit for k8.

EDIT: To this guy: *"I too found it strange that the boot takes longer on 64 kernel. The difference was 10 secs here..."*

---

### Post by OtonVM on 2006-06-06
[QUOTE=Kilz]Basically what I said, you can compile a OS or a program for 64 bits, but unless its written for it it isn't going to make that much of a difference. Comparing 32 bit programs compiled under 64 bit and posting it as "benchmarks" is deceptive at best.
There may be few programs out there now that give a real large boost, but more are being produced every day. Unless you are running a 64 bit OS there is no way to know what those advantages are because the move to 64 bits is moving faster all the time. What was true 6 months ago may not be true today, and for sure wont be true 6 months down the road.
You may be willing to give up 7 or 10 minutes here or there. But posts like this that say someone is moving to 32 bits may influence someone who may benefit from those time savings. They may not know if a program they are using could shave 2 or 3 hours off of the time like 64 bit POV can.

You can floor a prius and have great acceleration, the fuel savings is all in how you drive it.[/QUOTE]
Ok, can we please leave the prius metaphore out of this? Thank you...:D 

Look. You can only speculate on a large scale about what is going to happen in one year. That's a hell lot of time. I belive I will be running some nice laptop abroad preparing for some of my hardest exams ever... Maybe a 64bit system? Who knows? Will flash and all codecs be 64bit? I hope so... But until that moment I really can't afford spending so much time on all those tiny problems that arise on a 64bit system.
And if you are such an expert on POV or whatever similar, I belive you must also be informed on all that influences your work, starting from your hardware. Not from me, but from other people who do the same things as you and have experience in that.

---

### Post by jdong on 2006-06-06
[QUOTE=OtonVM]You mean a kernel compiled within 64bit enviroment or just compiled for k8? Becouse I compiled it yesterday becouse of some usb problems and it booted as usual... no problem. That is: inside 32bit for k8.

EDIT: To this guy: *"I too found it strange that the boot takes longer on 64 kernel. The difference was 10 secs here..."*[/QUOTE]

We mean any 64-bit kernel takes longer to initialize than a 32-bit kernel on the same system (not a 32-bit kernel compiled with k8 architecture optimizations).

It appears to only happen on some motherboards, as two of my three AMD64 boxes show this behavior.

---

### Post by panurge77 on 2006-06-06
I meant the diference between the k7 kernel on ubuntu x86 and the k8 on amd64, running on my Athlon 64 3200 on the AN8-E mobo... That was the first thing i noticed when switching to 32...

---

### Post by Kilz on 2006-06-06
[QUOTE=OtonVM]Ok, can we please leave the prius metaphore out of this? Thank you...:D 

Look. You can only speculate on a large scale about what is going to happen in one year. That's a hell lot of time. I belive I will be running some nice laptop abroad preparing for some of my hardest exams ever... Maybe a 64bit system? Who knows? Will flash and all codecs be 64bit? I hope so... But until that moment I really can't afford spending so much time on all those tiny problems that arise on a 64bit system.
And if you are such an expert on POV or whatever similar, I belive you must also be informed on all that influences your work, starting from your hardware. Not from me, but from other people who do the same things as you and have experience in that.[/QUOTE]
The only codecs you cant get running on a 64 bit system to my knowledge are wmv and wma. If you need those enjoy. I personal can do without proprietary Windoz formats thank you. Flash, java, and other plugins with firefox can be setup in less than an hour. Once done , that's it. Your choice [Chroot]("http://www.ubuntuforums.org/showthread.php?t=157412&highlight=chroot+script") or [no chroot]("http://www.ubuntuforums.org/showthread.php?t=90106&highlight=chroot+script"). Need the wma and wmv, use chroot. You will probably gain that hour or so back in no time.
Same hardware, same OS, same file, 32 bit pov vs 64 bit pov. 64 bit will be 30% faster. Average savings of 2 to 3 hours rendering.
That's just one program. You said a year, I compared 6 months. I also said 64 bit apps are coming out daily. If you replace your computer every 6 months to a year you are defiantly not an average user.

---

### Post by OtonVM on 2006-06-06
[QUOTE=panurge77]I meant the diference between the k7 kernel on ubuntu x86 and the k8 on amd64, running on my Athlon 64 3200 on the AN8-E mobo... That was the first thing i noticed when switching to 32...[/QUOTE]
Then I don't know about that. Sorry.

---

### Post by panurge77 on 2006-06-06
There are still the debs there are not official. I couldnt find any tcl/tk 8.5 for amd64. It's easily found on ubuntu forums for 386. Rhythmbox 9.4 was also easily found on the forums for 386, but I had to google it for amd64, not really a big a deal.  Also, those who are following quinnz repo for compiz/xgl will notice there's an obvious delay in porting debs to 64 and some of them sometimes are forgoten... libcairo for example is 1.1 for 386 and 1.0 for amd64. Yes, those are small things, but they counted when I was chose to have dapper final on x86 instead of sticking to 64. I like to have the newest and out of the official repos, the x86 world is still very larger.
Sorry to have gone off-topic.

---

### Post by Kilz on 2006-06-06
[QUOTE=panurge77]There are still the debs there are not official. I couldnt find any tcl/tk 8.5 for amd64. It's easily found on ubuntu forums for 386. Rhythmbox 9.4 was also easily found on the forums for 386, but I had to google it for amd64, not really a big a deal.  Also, those who are following quinnz repo for compiz/xgl will notice there's an obvious delay in porting debs to 64 and some of them sometimes are forgoten... libcairo for example is 1.1 for 386 and 1.0 for amd64. Yes, those are small things, but they counted when I was chose to have dapper final on x86 instead of sticking to 64. I like to have the newest and out of the official repos, the x86 world is still very larger.[/QUOTE]

Xgl is still to experimental for my tastes. There needs to be a year or so of work done to iron out the bugs IMHO. Some programs still have problems running with Xgl enabled. That some lib's for Xgl are not compiled as fast others at this stage is not a big surprise. There is constant work being done on it and some things suffer because of that.
I also believe that it will be a snowball effect with 64 bit , just like there was when the change from 16 to 32 bit happened. Yes I can remember back that far. I orignaly started out on a 386 sx.

---

### Post by panurge77 on 2006-06-06
Yes, I'm hoping to see the snowball rolling big next year. :rolleyes:

---

### Post by OtonVM on 2006-06-06
[QUOTE=Kilz]The only codecs you cant get running on a 64 bit system to my knowledge are wmv and wma. If you need those enjoy. I personal can do without proprietary Windoz formats thank you. Flash, java, and other plugins with firefox can be setup in less than an hour. Once done , that's it. Your choice [Chroot]("http://www.ubuntuforums.org/showthread.php?t=157412&highlight=chroot+script") or [no chroot]("http://www.ubuntuforums.org/showthread.php?t=90106&highlight=chroot+script"). Need the wma and wmv, use chroot. You will probably gain that hour or so back in no time.
Same hardware, same OS, same file, 32 bit pov vs 64 bit pov. 64 bit will be 30% faster. Average savings of 2 to 3 hours rendering.
That's just one program. You said a year, I compared 6 months. I also said 64 bit apps are coming out daily. If you replace your computer every 6 months to a year you are defiantly not an average user.[/QUOTE]
I use wmv and enjoy them, thank you. :) Actually, you took twice 6 months and pointed out the speed of developing of software, I took over from that. But that's beside the point. 
I'm not going to argue any more. Ok, I agree: POV faster. Ok, I agree: chroot. Not ok: I don't agree to all the **other** problems out there. I didn't spend  one or two hours in front of a piece of software for my ups that would not compile and correct the code a hundred times before it did. I spent like 5... I'm certanly no programmer and I have no idea what all the code means, but I can read "line 76: ; missing" or someting in the debug. And there were other problems I can't remeber anymore. Why? Because I don't care to remember them. I'm a linux leecher. I use it. I don't program it and I never will. And now I'm perfectly happy with my machine, wich is solid and runs like a charm.
Now it's getting late here and I need to catch an early train so good night to everyone reading. (even if it's not appropriate far a forum)
p.s.: I don't replace my pc every 6 months but I hope that one day I will. :D Buy I really think I'll need a laptop next year...

---

### Post by Ivan Matveich on 2006-06-08
Best 64-bit feature: you can mmap() your whole disk a million times!

That was the first thing I did with my new system, anyway...

---

### Post by OtonVM on 2006-06-08
[QUOTE=Ivan Matveich]Best 64-bit feature: you can mmap() your whole disk a million times!

That was the first thing I did with my new system, anyway...[/QUOTE]
Riiight... Thaks to wiki to explain what mmap is... But what can you do with it? Is it not a memory call...thingy? :))

---

### Post by bruce89 on 2006-06-08
Ivan was just pointing out that you can have more than 4GiB of memory on AMD64.

---

### Post by OtonVM on 2006-06-08
[QUOTE=bruce89]Ivan was just pointing out that you can have more than 4GiB of memory on AMD64.[/QUOTE]
Oh, yeah, well I guess so... That's above me... No idea about those details.

---

### Post by jdong on 2006-06-08
[QUOTE=bruce89]Ivan was just pointing out that you can have more than 4GiB of memory on AMD64.[/QUOTE]
You could always do that. On x86-64, one process may simultaneously address more than 4GiB (or 3GiB) of RAM.

---

### Post by HanZo on 2006-06-15
> or those that say they cant have firefox with flash, java, etc without a chroot or other hard setup they are also wrong. That may have been the case with Breezy, but you can add 32 bit applications to 64 bit Dapper without a chroot.
that's good news! didn't know that.

---

### Post by mike3k on 2006-09-11
> **jdong said:**
> Thank you :)
BTW, a Prius is a ultra compact Toyota car known for its absurdly high fuel economy, though at a tremendous price in performance :)

A Prius is **NOT** ultra compact - in fact it has more interior space than my old Corolla & the second generation Prius doesn't perform too badly. I love mine.

---

