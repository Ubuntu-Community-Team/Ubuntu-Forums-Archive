---
title: "Shake, libXi.so.6 and XESetWireToEventCookie"
date: 2010-04-07
forum: General Help
---

### Post by fuzzylogic1 on 2010-04-07
Hey :)

Just updated my laptop to Lucid and finally got 64bit working... great

Problem is I use shake and I can't seem to get it working. I've looked at other posts that give ideas on how to sort this out which I have followed but all I seem to get is the message 

/usr/nreal/shake-v4.10.060/bin/shkx.exe: symbol lookup error: /usr/lib32/libXi.so.6: undefined symbol: XESetWireToEventCookie

Any ideas? ldd /usr/lib32/libXi.so.6 below

linux-gate.so.1 =>  (0xf77a7000)
	libX11.so.6 => /usr/nreal/shake-v4.10.0606/lib/libX11.so.6 (0xf7695000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf766e000)
	libc.so.6 => /lib32/libc.so.6 (0xf7514000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7510000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf750a000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf7506000)
	/lib/ld-linux.so.2 (0xf77a8000)


Ta

Fzz

---

### Post by elf128 on 2010-05-01
Hi. Yesterday i upgrade my ubuntu and have the same bug.
Here is my solution:
 * go to here [http://packages.ubuntu.com/karmic/i386/libxi6/download](http://packages.ubuntu.com/karmic/i386/libxi6/download) and download libxi6_1.2.1-2ubuntu1_i386.deb
 * DON'T INSTALL IT. This is old version of libXi and your system allready has newer. You need this version only to run shake.
 * uncompress libXi.so.6.0.0 in to /your path to shake/lib
 * make symbolic link libXi.so.6 => libXi.so.6.0.0
 * run Shake
 * Enjoy.

---

### Post by verdesmeraldo on 2010-06-30
> **elf128 said:**
> Hi. Yesterday i upgrade my ubuntu and have the same bug.
Here is my solution:
 * go to here [http://packages.ubuntu.com/karmic/i386/libxi6/download](http://packages.ubuntu.com/karmic/i386/libxi6/download) and download libxi6_1.2.1-2ubuntu1_i386.deb
 * DON'T INSTALL IT. This is old version of libXi and your system allready has newer. You need this version only to run shake.
 * uncompress libXi.so.6.0.0 in to /your path to shake/lib
 * make symbolic link libXi.so.6 => libXi.so.6.0.0
 * run Shake
 * Enjoy.


Hi

I'm a new user of Linux Ubuntu and I just installed shake. I have the same problem about libXi.so.6 and I followed the steps suggested by you. The only problem is that trying to make a symbolic link I receive the massage - /usr/nreal/Shake/lib/libXi.so.6.0.0': File exists

As I said I'm new to Linux, and what I try to do is this - ln -s /usr/lib/libXi.so.6 /usr/nreal/Shake/lib/libXi.so.6.0.0

Is it correct to create a symbolic link this way or I am down the wrong path?

Thank you ever so much for your help!

---

### Post by Liametc on 2010-07-20
I LOVE YOU ELF128!!!! :p

---

