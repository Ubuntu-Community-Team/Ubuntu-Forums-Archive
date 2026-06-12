---
title: "Memory scan on CD?"
date: 2010-10-22
forum: General Help
---

### Post by Corfy on 2010-10-22
One of the things I found really handy about the Live Ubuntu CDs is they had the option to run a memory scan on the computer. As the head of an IT department of one person in charge of maintaining 60 computers, that capability has helped me more than twice.

I think the options when running off CD/USB were Install Ubuntu, Test Ubuntu, run a memory scan, or boot off the harddrive. However, starting with Lucid and continuing with Maverick, the only options on the Live CD/USB seem to be install or try (although the memory scan is available on my Grub menu after Ubuntu is installed, unfortunately, most of the computers I am responsible for at work are Windows only).

Is there a way to start the memory scan when running a Live Lucid or Maverick CD/USB?

---

### Post by matt_symes on 2010-10-22
Hi,

Maybe these will help.

[http://manpages.ubuntu.com/manpages/gutsy/man1/memtest.1.html](http://manpages.ubuntu.com/manpages/gutsy/man1/memtest.1.html)

[http://www.howtogeek.com/howto/16666/diagnose-hardware-problems-with-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/16666/diagnose-hardware-problems-with-an-ubuntu-live-cd/)

[http://www.makeuseof.com/tag/memtest-awesome-tool-test-computers-memory-errors/](http://www.makeuseof.com/tag/memtest-awesome-tool-test-computers-memory-errors/)

Kind regards

---

### Post by Hippytaff on 2010-10-22
You could use the live cd of the version that had the mem test :-)

but it's very possible I'm missing the point :-s

---

### Post by gmargo on 2010-10-22
On the LiveCD (desktop edition), when it starts to boot, hold down the left shift key.  You will then be presented with a "boot:" prompt.   Enter 'memtest' and hit return.  This will start the usual memory test.  Alternatively, wait for the screen color to change to brown, then hit return, which will bring up the list of options instead of autobooting.

If you use the Alternate CD or the Server CD, you will be presented with a list of options including the memory test.

---

### Post by Corfy on 2010-10-22
> **Hippytaff said:**
> You could use the live cd of the version that had the mem test :-)

but it's very possible I'm missing the point :-s

Actually, that is what I have been doing, but I've gotten used to using LiveUSB (rather than a LiveCD), and I didn't feel like buying a new flash drive just to carry an old version of Ubuntu.

> **gmargo said:**
> On the LiveCD (desktop edition), when it starts to boot, hold down the left shift key.  You will then be presented with a "boot:" prompt.   Enter 'memtest' and hit return.  This will start the usual memory test.  Alternatively, wait for the screen color to change to brown, then hit return, which will bring up the list of options instead of autobooting.

If you use the Alternate CD or the Server CD, you will be presented with a list of options including the memory test.

Thanks! I figured there was a way, but I couldn't figure it out.

---

