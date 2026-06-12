---
title: "Privateer Gold installation issues"
date: 2010-05-06
forum: General Help
---

### Post by charles-bronson on 2010-05-06
Hi there,

I recently came across the PrivateerGold project and wondered of how to install it on my ubuntu laptop. My attempts have failed so far.

uname info:

> 
someuser@somemachine: ~/Downloads$ uname -a
Linux somemachine 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
First I chmodded the downloaded PrivateerGold1.02.bz2.bin file:

> someuser@somemachine:~/Downloads$ chmod 755 PrivateerGold1.02.bz2.binSecond step was to run the install script:

> someuser@somemachine:~/Downloads$ ./PrivateerGold1.02.bz2.bin
Verifying archive integrity... All good.
Uncompressing Vegastrike Space Simulator 0.4.3 - Base................................. [MORE DOTS]In the end shell returns:

> /home/someuser/.setup1857: error while loading shared libraries: libgdk-1.2.so.0: cannot open shared object file: No such file or directoryIt obviously looks like as if the installation script is looking for some lib that isn't installed on the machine. Am I wrong or is this a rather old GDK lib of some sort that Ubuntu/Gnome no longer uses?

I also tried:

> someuser@somemachine:~/Downloads$ sudo apt-get install libgdk-1.2
[sudo] password for someuser: 

E: package libgdk-1.2 could not been found
Any idea of how to solve this issues?

Thanks.

---

### Post by rCXer on 2010-05-06
Have you tried [their forum](http://privateer.sourceforge.net/comlink/viewforum.php?f=1)?

---

