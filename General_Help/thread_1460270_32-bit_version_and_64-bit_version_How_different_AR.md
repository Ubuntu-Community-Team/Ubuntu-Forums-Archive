---
title: "32-bit version and 64-bit version: How different ARE they?"
date: 2010-04-22
forum: General Help
---

### Post by brucewagner on 2010-04-22
I'm curious...

How different are the 32-bit version and the 64-bit version...?

Are they identical in essence, and just compiled differently...?

Or are they very different...?   Almost like a different branch...?

I'm curious as to why some bugs would show up only on the 32-bit version, and others would show up only on the 64-bit version.

How different ARE they?

---

### Post by screaminj3sus on 2010-04-22
They are the same. Of course occasionally bugs will only effect one or the other version.

---

### Post by jondodson on 2010-04-22
As far as I know, which isn't very, the actual o/s functionality is the same, although 64 bit can deal with >4 Gb ram.  But some of the progs that run on them do seem to have some differences because I think they are at different stages of development.  For example, 32 bit flash is "finished" and stable and runs great, but 64 bit flash is still work in progress with Adobe and seems to have a few glitches, on my system at least.  The same thing might apply with different elements of "Out of the Box" drivers included in the 32 and 64 bit distros.  But I could be wrong.

---

### Post by Longinus00 on 2010-04-22
[http://en.wikipedia.org/wiki/X86_64#Architectural_features](http://en.wikipedia.org/wiki/X86_64#Architectural_features)

---

### Post by srs5694 on 2010-04-22
There are three levels of analysis:


[list]
[*]Source code -- The source code is identical for most parts of most programs, including the kernel. Some code fragments differ between platforms, though, because it's been optimized in assembly language, it's applicable only to certain platforms, or whatever. At a guess, I'd say that 95-99% of the source code that created any given Linux system is identical to an identically-configured system running another CPU. Similar comments apply to configuration files.
[*]Binary code -- Source code is usually compiled into a binary form. (Scripts are an exception to this rule.) A binary program file looks like gibberish to most people, but the gibberish is different for x86 vs. x86-64 (and even more different for PowerPC or other unrelated architectures). Thus, if you did a file-by-file comparison of two systems on different platforms using diff, you'd find few binary files that were identical. You would find identical scripts, configuration files, and ancillary support files like graphics. You might also find a few 32-bit binaries on 64-bit systems.
[*]User experience -- Here the two converge again. Despite the different binaries, programs' behaviors are determined by their source code, so 32-bit and 64-bit Ubuntu systems will behave almost identically. Exceptions include tools that are designed to work differently depending on platform (uname, for instance), bugs that are unique to one platform because of incorrect coding assumptions or compiler bugs, and software that doesn't compile at all on one platform or another (Adobe's Flash is still in Alpha on x86-64, for instance). Since x86-64 can run 32-bit binaries, this last problem can be worked around by installing a 32-bit binary on a 64-bit system; however, there aren't many open source programs for which this is still necessary. The x86-64 system will also be a little bit faster (10-20% by most benchmarks, although this varies depending on the program).
[/list]

---

### Post by jerome1232 on 2010-04-22
Not very.


In fact if you were to hop onto a 64 bit system, then hop onto a 32 bit system. An average user would notice no difference.

64 bit is faster at a few things and can address more physical ram. People say flash is buggier in 64 bit... but I've never seen it be any buggier than it is on a 32 bit machine.

At least Linux machines GET a 64 bit flash player, Adobe hasn't even started making 64 bit flash for Windows. :)

Why is 90% of the web still flash again? Flash needs to die.

---

### Post by srs5694 on 2010-04-22
> **jerome1232 said:**
> why is 90% of the web still flash again? Flash needs to die.

+10^10

---

### Post by akand074 on 2010-04-22
Putting it very simply. Its pretty much identical, same exact operating system, same features, same support. The only difference is that for processors that support 64 bit (just about all of them now) the operating system is much more efficient with RAM. You can sometimes see slight performance boosts, and when there is software that are also written in 64bit you get performance boosts in those applications. But I mean if you installed both of them on two different computers side by side you would not be able to tell the difference except when you try to install something each will need its own version generally.

---

### Post by kathy4scuba on 2010-04-23
I've installed Ubuntu 9.10 64 bit on my new Mac Mini.  I need to be able to run a 64 bit program.  My problem though is running programs that were compiled on 32 bit Linux.  I get the message:

error while loading shared libraries: libX11.so.6

This file on my machine is a 64 bit binary.  Is there any way to also have the 32 bit binary?  If so, how would I get it onto my machine? I've used the "Synaptic Package Manager" to install all of the 32 bit stuff I could find, but the X11 stuff still isn't there.

Any help would be much appreciated.

---

### Post by 3rdalbum on 2010-04-23
> **kathy4scuba said:**
> I've installed Ubuntu 9.10 64 bit on my new Mac Mini.  I need to be able to run a 64 bit program.  My problem though is running programs that were compiled on 32 bit Linux.  I get the message:

error while loading shared libraries: libX11.so.6

This file on my machine is a 64 bit binary.  Is there any way to also have the 32 bit binary?  If so, how would I get it onto my machine? I've used the "Synaptic Package Manager" to install all of the 32 bit stuff I could find, but the X11 stuff still isn't there.

Any help would be much appreciated.

You will need to get some 32-bit libraries using the [Getlibs]("http://ubuntuforums.org/showthread.php?t=474790") program. Run your 32-bit program using getlibs, the way that the example shows, and it will get the 32-bit libraries for you.

---

### Post by ambdeep on 2010-04-23
is it possible to upgrade a 32 bit os to a 64 bit os w/o formatting?

---

### Post by jerome1232 on 2010-04-23
> **ambdeep said:**
> is it possible to upgrade a 32 bit os to a 64 bit os w/o formatting?

Nope.

You can do some funky stuff with a 64 bit os and get a 32 bit environment and run 32 bit specific programs in it though.

---

### Post by WinterRain on 2010-04-23
If you have a capable computer with enough RAM, I would go 64bit. Runs as good or proboably better than 32bit. At least for me it does.

---

