---
title: "General Question Regarding Versions"
date: 2010-03-03
forum: General Help
---

### Post by thomasthefinch on 2010-03-03
Hi folks.

I installed Linux for the first time on my laptop about two months ago.  Love it for every day business of browsing and typing, and just messing about.

I am a video editor by trade, so you can understand my need to run windows on a regular basis on another machine.  But here is my problem:

My editing machine, an absolute monster, has recently come a cropper in terms of the OS.  Vista, to be exact.  Now it's going to be a few weeks before I can get my hands on a copy of Windows 7 to install Avid on etc, so I'd like to install Linux on that machine, so it is at least usable.

It's a machine with 6 gig of ram, and I'm struggling to find a 64bit download link for Linux.  Now someone mentioned something to me that this doesn't matter on Linux, but I want to make sure.  I'm a very talented interface user of computers, in terms of programs, but terrible with anything overly technical in the workings of them.  If anyone could explain and point me in the right direction I'd be ridiculously appreciative.

---

### Post by jmszr on 2010-03-03
thomasthefinch,

You will find both 32-bit and 64-bit versions of Ubuntu here: [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

You will also find the 32 and 64-bit versions of Ubuntu 8.04 and 9.10 here if you click on "Alternative download options,........" :[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

---

### Post by Yellow Pasque on 2010-03-03
> Now someone mentioned something to me that this doesn't matter on Linux
Using 64-bit to get full access to your RAM? It sure does matter on Linux.

---

### Post by genothomas on 2010-03-03
Try Linux Mint for reducing bugs. It's same as ubuntu.
[http://www.linuxmint.com/](http://www.linuxmint.com/)

---

### Post by PoHandle on 2010-03-03
To download the 64-bit version of Ubuntu, go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and click on *Alternative download options*.  At the new set of options that appears, under *Choose the Architecture*, select the 64-bit version.

64-bit OS's **theoretically** run faster, because the processor works with 64 bits (8 bytes) at a time rather than 32 bits.  However, you will most likely not see the speed benefit, as most software is written for 32-bit operations and merely ported to 64-bit.

To visualize:
Let's say a 32-bit program sends an instruction to the processor like
00101110110100101010101010100000
A program that is just ported 64-bit rather than recoded to take advantage of the 64-bit capabilities will send an instruction like
00101110110100101010101010100000[COLOR="Red"]00000000000000000000000000000000[/COLOR]
Notice the first 32 bits are the same, but the following 32 is just trailing 0's.  It's as if those extra 32 bits are just wasted.

The only things I notice a significant speed boost in is boot speed, kernel/driver compilation, and certain memory-related tasks.

So it's really up to you if you'd want to use a 64-bit OS.

---

### Post by Yellow Pasque on 2010-03-03
> most software is written for 32-bit operations and merely ported to 64-bit.

Actually, I think most open-source software doesn't depend on a specific "bitness", leaving it to the compiler. Anything that uses long integers (video encoding, GIMP, etc.) will see marked improvement on 64-bit.

Also, on Ubuntu, 32-bit software (except the kernel) is not i686-optimized, so any app that can take advantage of SSE instructions will show improvement with 64-bit.

---

### Post by thomasthefinch on 2010-03-03
I'm completely lost now.

It's strange, I could tell you in depth how a DVD player works, compression, bit systems anything.  But apply it to the working of a computer and I'm stuck haha.

I'm installing 64 bit as we speak, will keep you all updated on any of the problems.  Thanks for the help.

Would once again like to say this is without question, exception or compromise, the best and most friendly, helpful community on the internet.

---

