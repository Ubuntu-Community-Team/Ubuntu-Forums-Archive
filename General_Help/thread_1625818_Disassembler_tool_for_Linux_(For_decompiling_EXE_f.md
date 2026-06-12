---
title: "Disassembler tool for Linux (For decompiling EXE files)"
date: 2010-11-19
forum: General Help
---

### Post by dopefish7590 on 2010-11-19
Heya all... I was wondering if there is any disassembler tools for Ubuntu that I could use..? I am used to W32DASM for my hacking needs, but it does not seem to work under WINE.

For some background information, I am interested in getting an editor for Rise of the Triad working. The dev is no where to be seen, and before leaving, he gave a key that people could use to run the program, but that doesn't work anymore. So I was planning on disassembling the executable and changing the referencing in the program to jump out of the "Enter key" dialog and allow people to use the program again.

My programming skill is limited in this way, but I should be able to release a patched executable with some effort. But I can't seem to find a disassembler.

Thanks all!

---

### Post by santosh83 on 2010-11-19
> **dopefish7590 said:**
> Heya all... I was wondering if there is any disassembler tools for Ubuntu that I could use..? I am used to W32DASM for my hacking needs, but it does not seem to work under WINE.

For some background information, I am interested in getting an editor for Rise of the Triad working. The dev is no where to be seen, and before leaving, he gave a key that people could use to run the program, but that doesn't work anymore. So I was planning on disassembling the executable and changing the referencing in the program to jump out of the "Enter key" dialog and allow people to use the program again.

My programming skill is limited in this way, but I should be able to release a patched executable with some effort. But I can't seem to find a disassembler.

Thanks all!

Two disassemblers for Windows (PE format) are OllyDbg & RosAsm. The first is a debugger with a built-in disassembler, while the second is an assembler with a disassembler. I haven't tried either of these under WINE, but atleast RosAsm should work.

[http://www.ollydbg.de/](http://www.ollydbg.de/)
[http://betov.free.fr/](http://betov.free.fr/)

---

### Post by dopefish7590 on 2010-11-19
RosAsm is very nice... Thanks for the link. Ollie Debug has trouble loading many a Windows library, and shows some ASM, but many of the functions won't do anything due to the lack of libraries...

Maybe I could get W32DASM to work if I installed a font of something..? (It opens and disassembled files, but all I see are boxes, and it's disassembled, not just opened. (It's not like opening an executable in gedit). Any thoughts? :o

Thanks for the quick reply... :)

---

