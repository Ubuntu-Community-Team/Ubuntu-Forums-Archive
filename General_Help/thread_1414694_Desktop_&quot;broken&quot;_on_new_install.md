---
title: "Desktop &quot;broken&quot; on new install"
date: 2010-02-23
forum: General Help
---

### Post by gabe77 on 2010-02-23
Hello,

Just made a fresh install of ubuntu 9.10 on a celeron 2.0 with 1 GB ram.

After install I can start up and everything is normal, the ubuntu start up screen is displayed properly, the mouse cursor is normal but once the desktop is loaded it show a broken image that I cant make anything off. I do still see the mouse perfectly and can move it around without problems. I also see a really thin line to the left that contains a bit of the desktop properly displayed, I can just see the applications menu, but cant see enough to make out the options of the menu. Rest of desktop is a mishmash of lines and brown/black...

Does anybody know what this could be caused by and if there is a solution.

I was thinking that it had t do with the video drivers. Im using the mb intergrated videocard.

I would be thankful for any help!

---

### Post by mikewhatever on 2010-02-24
Hm ..., and the model of the card is...?

---

### Post by lotharmat on 2010-02-24
> **gabe77 said:**
> Hello,

Just made a fresh install of ubuntu 9.10 on a celeron 2.0 with 1 GB ram.

After install I can start up and everything is normal, the ubuntu start up screen is displayed properly, the mouse cursor is normal but once the desktop is loaded it show a broken image that I cant make anything off. I do still see the mouse perfectly and can move it around without problems. I also see a really thin line to the left that contains a bit of the desktop properly displayed, I can just see the applications menu, but cant see enough to make out the options of the menu. Rest of desktop is a mishmash of lines and brown/black...

Does anybody know what this could be caused by and if there is a solution.

I was thinking that it had t do with the video drivers. Im using the mb intergrated videocard.

I would be thankful for any help!

Please can you post the output of
```
lspci
```

This will tell us what video card you are using.

Also is there anything listed under **System -> Administration -> Hardware Drivers**?

---

### Post by gabe77 on 2010-02-24
Problem is that I can not see anything at all but the mousepointer.

So I cant look for anything.

The videocard is an: *embedded intel extreme graphics 2*

And the computer is a Dell Optiplex 170L -> [http://pcbroker.ro/temp/spec/dell_optix_170L.pdf](http://pcbroker.ro/temp/spec/dell_optix_170L.pdf)

Specifications :  Form Factor : microATX (9.60 inches by 8.20 inches [233.68 millimeters  by 208.28 millimeters]) Processor :  Support for an Intel® Pentium® 4 processor in a mPGA478 socket with a  400 / 533 / 800 MHz system bus  Support for an Intel® Celeron® D processor in a mPGA478 socket with a  400 / 533 MHz system bus  Memory :   Two 184-pin DDR DIMM sockets  Support for single-sided or double-sided DIMMs (DDR 400/333/266)  Chip Set : Support for an Intel® Pentium® 4 processor in a mPGA478  socket with a 400 / 533 / 800 MHz system bus  I/O Control : SMSC LPC47M172 LPC bus I/O controller Video : On Board Integrated 64mb SVGA Interfaces :  Four USB ports  One serial port  One parallel port  Board 10/100 network port  Two ATA IDE interfaces with UDMA 33, ATA-66/100 support  One Floppy diskette drive interface  PS/2 keyboard and mouse ports



Is there a way I can boot up in normal commandline instead of visual desktop to login and run the tests from there?


.

---

### Post by gabe77 on 2010-02-28
I hate to bump my own post, but did any of the info i posted help you out?

---

