---
title: "installing Kismet help me out ASAP"
date: 2010-07-07
forum: General Help
---

### Post by alperkayisi on 2010-07-07
Hi ,

I tried to install kismet on my ubuntu 10.04 But I couldn't do that. cuz when I type " make " command I got this error;

g++ -I/usr/include/ncurses -Wall -g -O2 -c dumpfile_tuntap.cc -o dumpfile_tuntap.o 
dumpfile_tuntap.cc: In member function ‘virtual int Dumpfile_Tuntap::OpenTuntap()’:
dumpfile_tuntap.cc:213: error: ‘Ifconfig_Delta_Flags’ was not declared in this scope
[COLOR=Red]**make: *** [dumpfile_tuntap.o] Error 1**[/COLOR]

./configure command works but has problem w make command. guys please help me out

---

### Post by Old_Grey_Wolf on 2010-07-07
Is there some reason you can't install the .deb for Kismet using Synaptic?

---

