---
title: "PSP help?"
date: 2009-12-12
forum: General Help
---

### Post by n4th4n on 2009-12-12
okay so I just got my new PSP , and i followed these instructions [https://help.ubuntu.com/community/PSP](https://help.ubuntu.com/community/PSP) for the qPSP program, but the tar.gz has no make file so what can I do to get it?

p.s Im using mint 8

---

### Post by jrock2012 on 2009-12-12
what are you need to it for ??
If it's just for video converting, Arista.. easy as pie. 
sudo apt-get install arista

---

### Post by slammer on 2010-01-05
extract tar 
cd qpspmanager-2.0.2
qmake-qt4

In the file ./src/isocompressor.h add "#include <cstdint>" after # include <iostream> so it looks like this:
 
	[COLOR="RoyalBlue"]#ifndef ISOCOMPRESSOR_H
	#define ISOCOMPRESSOR_H

	#include <QString>
	#include <iostream>
	# include <cstdint>

	class ISOCompressor[/COLOR]

In the makefile change:

[COLOR="Blue"]CXXFLAGS      = -pipe -O2 -Wall -W -D_REENTRANT $(DEFINES)[/COLOR] 

to

[COLOR="Blue"]CXXFLAGS      = -pipe -O2 -Wall -W -D_REENTRANT $(DEFINES) -std=c++0x[/COLOR] 


(this allows the program to compile)

make

install probably doesn't work so just copy the new binary

sudo cp ./bin/QPSPManager /usr/bin/

hope this helps.

---

