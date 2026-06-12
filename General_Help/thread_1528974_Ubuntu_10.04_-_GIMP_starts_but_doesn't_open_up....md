---
title: "Ubuntu 10.04 - GIMP starts but doesn't open up..."
date: 2010-07-11
forum: General Help
---

### Post by FusionSarson on 2010-07-11
Hi,

I hope this is in the right spot, and I have searched but haven't been able to find anything to help me out.

I installed GIMP recently, it worked for awhile, but now it will not open up even after the 'Starting GIMP...' appears. That goes and nothing happens. I've tried un-installing and installing via the software centre as well as via the terminal with no success. Will be happy to go through steps again if someone gives me some guidance. 

Any ideas are welcomed.

Thanks,
Alex

---

### Post by SteveDee on 2010-07-11
You could try opening a terminal window and typing: gimp

The Gimp should attempt to load, and if it fails you may see some info (or error message) in the terminal.

---

### Post by FusionSarson on 2010-07-12
It loads up when done via terminal, but not via the menu. Any ideas?

---

### Post by FusionSarson on 2010-07-12
This also comes out in terminal when opened via it;

username@computername:~$ gimp
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:7064): LibGimpBase-WARNING **: gimp: wire_read(): error
/usr/local/lib/gimp/2.0/plug-ins/helpbrowser: error while loading shared libraries: libgtkhtml-2.so.0: cannot open shared object file: No such file or directory

(gimp:7064): LibGimpBase-WARNING **: gimp: wire_read(): error
^Cgimp: terminated: Interrupt
/usr/local/lib/gimp/2.0/plug-ins/script-fu terminated: Interrupt

---

### Post by SteveDee on 2010-07-13
> **FusionSarson said:**
> This also comes out in terminal when opened via it;

username@computername:~$ gimp
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory....


I assume you have installed 2.6.8 (2.6.9 has a few serious bugs).

I'm not sure why the path is: /usr/local/lib/gimp as I'm running 10.04 and my path is: /usr/lib/gimp/2.0...

In a terminal type: whereis gimp
I get: gimp: /usr/bin/gimp /etc/gimp /usr/lib/gimp /usr/share/gimp /usr/share/man/man1/gimp.1.gz

Open System > Administration > Synaptic and Quick Search for: gimp

At the very least you should have:-
 - gimp  2.6.8-2ubuntu1.1
 - gimp-data
 - libgimp2.0

---

### Post by gwilym on 2011-03-07
I have the same problem. In my Ubuntu Software Manager it says I have Gimp 2.6.8 - however it won't start from the menu. When I start it from the terminal it goes ok but if I go to help -> about -> in Gimp it says I have version 2.2.11.

There is also a Gimp Shop splash scree that pops up.

Soooo....how do I get to it being the latest Gimp working from the menu?

Any help appreciated...

**Added later ..... Fixed...**

Following the instructions here did it ... [https://answers.launchpad.net/ubuntu/+source/gimp/+question/130374](https://answers.launchpad.net/ubuntu/+source/gimp/+question/130374)

---

