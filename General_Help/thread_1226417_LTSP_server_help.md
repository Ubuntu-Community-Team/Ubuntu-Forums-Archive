---
title: "LTSP server help"
date: 2009-07-29
forum: General Help
---

### Post by Psycho.mario on 2009-07-29
What are the minimum hardware requirements for a thin client which boots from an LTSP server? Does the thin client just need PXE bootable network card, Screen, Keyboard and RAM, or does it need more than that?

Thanks

---

### Post by Psycho.mario on 2009-07-30
Bump

---

### Post by wojox on 2009-07-30
Looks like your headed in the right direction.

This should help:

[http://wiki.ltsp.org/twiki/bin/view/Ltsp/LTSPTerminal](http://wiki.ltsp.org/twiki/bin/view/Ltsp/LTSPTerminal)

---

### Post by bluenova on 2009-07-30
Clients
Older hardware
There are three things to consider when trying to re-use existing hardware: 

CPU 

Network 

Thin client memory 

Video card 

CPU
For using the default, secure mode of LTSP, you'll need to have a slightly faster CPU. Any 533 MHz or better CPU should provide acceptable performance. 

If you have slower clients, in the range of 233 MHz to 533 MHz, you may be able to use them, if you're willing to reduce the security of your thin client network. More information on this is available in the chapter on LDM. 

Network
A thin client boots over the network, using a small program called a network boot loader. This network boot loader is sometimes located on the card itself, or, for older cards without one, the user can provide one on a floppy or CDRom which can be used to boot the thin client. 

Three common network boot loaders which can be used are: 

PXE: This one is the most common, and many network cards and motherboards with built-in network cards support this. If you have one of these, you'll be able to boot without any problems. 

Etherboot/gPXE: For older cards that don't have PXE included on them, you can use the Free Software equivalent, Etherboot, or it's newer replacement, gPXE. This excellent alternative to PXE can either be booted from a floppy, memory stick, or CDRom, or, if you're handy with electronics, be burned onto a EPROM if your card has a socket for one. More information on the project can be found at [http://www.etherboot.org](http://www.etherboot.org), and you can download ready-to-use Etherboot images at [http://www.rom-o-matic.org](http://www.rom-o-matic.org). 

Yaboot: For Macintosh PowerPC machines (iMac's and later), you can use the built in Yaboot network boot. 

Thin client memory
The bare minimum for a thin client to work is about 48MB, but it will be unusably slow, so it is recommended to install at least 128MB Ram, with 256MB Ram if you can spare it. This will really help speed up thin clients. 

Video Card
Typically, any video card that uses the PCI bus and has 16 MB or more of memory, should make a reasonable client. 

Credit to:
[http://www.ltsp.org/~sbalneav/LTSPManual.html#tc-hardware](http://www.ltsp.org/~sbalneav/LTSPManual.html#tc-hardware)

You should really read the whole of that manual, really tells you everything you wanted to know about ltsp.

---

### Post by Psycho.mario on 2009-07-30
Thanks a lot, the hardware i am going to try this on exceeds the requirements here, so it should be fine

---

### Post by SlugSlug on 2009-07-30
> **Psycho.mario said:**
> What are the minimum hardware requirements for a thin client which boots from an LTSP server? Does the thin client just need PXE bootable network card, Screen, Keyboard and RAM, or does it need more than that?

Thanks

thats all it needs - and they connect to an ltsp/dhcp server server

---

