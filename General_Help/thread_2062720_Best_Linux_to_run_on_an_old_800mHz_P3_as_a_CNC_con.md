---
title: "Best Linux to run on an old 800mHz P3 as a CNC control?"
date: 2012-09-25
forum: General Help
---

### Post by 777funk on 2012-09-25
I have a CNC machine that runs on MSDOS software. Right now I have it on a Win 98 install that I click an icon to go into DOS. It works well. 

But I am wondering if I can run an ISA card CNC controller via a DOS emulator. 

I'd prefer to use some sort of Linux. 

It's a P3 800 MHz machine and I ONLY use it to run the CNC. It works great. But I would prefer to have it in an OS running virtual DOS if it's possible.

---

### Post by PaulInBHC on 2012-09-25
I don't know anything about your CNC but if DOSbox can run a game, it should run your software for the machine.

Is the Win98 on a stand alone box that connects to the CNC?

If so, do you have the Win98 install disc and software disc?

---

### Post by CatKiller on 2012-09-25
DOSEmu would be a better bet than DOSBox, but the only way you'll know for sure is to try it.

---

### Post by 777funk on 2012-09-25
just tried DOSemu and it opened my program! But I get an error. 

This software is a CNC controller. It communicates with an ISA Card that is cabled to a servo control box that drives the servo motors for the machine. 

When I open the software by cd-ing into directory containing this folder and type GCODE (exe file) at the prompt, it opens!! 

then I go to Machine/Main Menu/Run Machine/Select File (where I'd normally select a file to cut).

It says "cannot locate ramdrive".

What would this mean?

Side note: I *can* open files in the GCODE software if I go to open. This opens them as a text editor within the software.

---

### Post by 777funk on 2012-09-25
I have a P3 that has an ISA card (OLD) that controls a CNC machine. It has Win 98 on it now and I have to boot into MSDOS to run the software now. It's kind of cumbersome going from 98 to the DOS (waiting etc) and if something goes wrong it has to reboot. I'd like to have it in a DOSemu running in Linux.

Is there a good version for this old machine?

---

### Post by dragonfly41 on 2012-09-25
Recently I've been trying out different distros on an old Dell notebook.

Puppy linux might work for you

[http://208.109.22.214/puppy/viewtopic.php?t=40240&sid=36650af16d9d5699b779eaec123d3dbf](http://208.109.22.214/puppy/viewtopic.php?t=40240&sid=36650af16d9d5699b779eaec123d3dbf)

---

### Post by jerrrys on 2012-09-25
I wonder if you even need Linux in your case.  Could you use [FreeDOS]("http://www.freedos.org/") instead?

---

### Post by 777funk on 2012-09-25
> **jerrrys said:**
> I wonder if you even need Linux in your case.  Could you use [FreeDOS]("http://www.freedos.org/") instead?

I like to have a text editor handy to edit files, and I need to access the network to transfer files, but other than that I just run the machine from that computer. 

Would FreeDOS allow me to do that? Would it be inside my Win98 install.

---

### Post by josephmills on 2012-09-25
Debian will run on just about anything what so ever 

I have seen it run on a p2 with 64 mb of ram 

use 16 bits color in /etc/X11/XF86Config-4 instead of the default 24 bits

here is a dude with 
a Pentium 3 - 933 MHZ, 256 mb SDRAM, RIVA TNT 2 PRO 16 MB, 
running debian 

[http://www.youtube.com/watch?v=ImGgR2-ihZw](http://www.youtube.com/watch?v=ImGgR2-ihZw)

as noted above there is also puppy, arch would also be a nice choice

---

### Post by GreatDanton on 2012-09-25
Maybe you didn't see this: [http://www.linuxcnc.org/](http://www.linuxcnc.org/)

This is cnc version based on Ubuntu 10.04. This software is outstanding. I am not sure if it's going to work on your computer, but you can try it as live cd/usb.

Regards.

---

### Post by CatKiller on 2012-09-25
> **777funk said:**
> 

It says "cannot locate ramdrive".

What would this mean?
That your emulated DOS environment has not been set up in the same way as your previous DOS environment.

Presumably you had a RAM drive set up that your program expects to be there.

---

### Post by cortman on 2012-09-25
[My opinions]("http://cortman.wordpress.com/2012/09/16/what-distro-should-i-use-on-my-old-computer/") on Linux on old computers.

---

### Post by jerrrys on 2012-09-25
Maybe a mod can merge these.  Got any more on the same subject?

[http://ubuntuforums.org/showthread.php?t=2062460](http://ubuntuforums.org/showthread.php?t=2062460)

P.S.  Hay Captain Jack :)

---

### Post by meditatingfrog on 2012-09-25
If the native CNC Linux doesn't work you could try DOSBox to run the cnc's DOS program on a version of Ubuntu, just install fluxbox or something on it so it's lightweight.

---

### Post by oldos2er on 2012-09-25
Threads merged. Please don't start more than one thread per topic, according to the posting guidelines:

"Do not cross post, or post the same thing in multiple locations."

---

### Post by cortman on 2012-09-26
> **jerrrys said:**
> Maybe a mod can merge these.  Got any more on the same subject?

[http://ubuntuforums.org/showthread.php?t=2062460](http://ubuntuforums.org/showthread.php?t=2062460)

P.S.  Hay Captain Jack :)

Hey jerrrys :D

---

