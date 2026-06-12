---
title: "SunVox Music program"
date: 2010-10-21
forum: General Help
---

### Post by amigammon on 2010-10-21
I have little experience installing linux/unix programs from off the web. I have downloaded an archive for a program called SunVox and it's website gives little instruction on how to install it. I am used to sudo on the terminal and Ubuntu Software Center and Synaptic Package Monitor. Here are the installation instructions:

	SunVox - Multiplatform Modular Music Creation Studio
User Manual

Introduction to SunVox
Installation and system requirements
Graphical user interface (GUI) description
Keyboard shortcuts
Synthesizers, filters and effects
SunVox song structure
Pattern editor
Pattern editor: standard effects
Configuration

This manual is not yet complete. But i working on it now. Please send any your comments and issues to [email]nightradio@gmail.com[/email]. Thank you for your understanding.


Introduction to SunVox

SunVox is a small, fast and powerful music sequencer (tracker) with modular synthesizers. It is a tool for those people who want to compose music anywhere. SunVox available for desktop PC (Windows, Linux, Mac OS X), pocket computers (Windows Mobile, PalmOS, iPhone/iPad) and netbooks.

Key features:
Modular interface.
Highly optimized synth algorithms.
Flexible architecture: SunVox can working on variuos devices. For example: PDA with slow CPU - 16bit sound (fixed point arithmetic); or big PC with powerfull CPU: 32bit sound (floating point arithmetic).
Supported platforms: Windows, Linux (x86/x86_64), Mac OS X, PalmOS, WindowsCE (Windows Mobile), iPhone/iPad.


Installation and system requirements
LINUX
System requirements:
* Pentium processor or higher;
* 256 mb of RAM or higher;
* Any Linux distribution (x86 or x86_64);
* SDL library (version 1.2 or later);
* ALSA.
Unpack archive with SunVox.
Run sunvox.
That's it. I am unable to move  sunvox file into my /usr/bin directory. If I try to run it from where it is it a window opens up momentarily (less than a second) and then nothing. Any ideas or suggestions? 

Thank you.

---

### Post by Gaelyn on 2010-10-26
I was having the same issues under 10.04.  In speaking with the program writer we went through a few things:

1) Confirm the .ini file is in the same location as the program (this should be default if you just unpacked the zip into your home directory)

2) Try running from the terminal.  After going to the proper directory in the terminal, type ./sunvox and it will give you an output error message.  Most likely it will show some error over the ALSA device.

3) Edit the ini for the audiodevice to either be 1,0 or 0,1 or default.  I used default and it worked like a charm, no issues in loading and using after that.

Cheers!:guitar:

---

