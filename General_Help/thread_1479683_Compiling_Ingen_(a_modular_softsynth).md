---
title: "Compiling Ingen (a modular softsynth)"
date: 2010-05-10
forum: General Help
---

### Post by AxelMan0 on 2010-05-10
I have been trying all day to get this to work. I finally got it to configure, but the build still failed a few times. Each time I fixed it, but I've run into a problem I just can't figure out. It's looking for atom.lv2/atom.h and I cannot for the life of me figure out what this is. Forums, google, nothing seems to refer to this odd file. Oh and the project also compiles using ./waf.

./waf configure --lv2dir=/usr/lib/lv2  gives the following

```

zak@zak-laptop:~/src/drobilla-lad$ ./waf configure --lv2dir=/usr/lib/lv2
Checking for program gcc,cc                 : ok /usr/bin/gcc 
Checking for program cpp                    : ok /usr/bin/cpp 
Checking for program ar                     : ok /usr/bin/ar 
Checking for program ranlib                 : ok /usr/bin/ranlib 
Checking for gcc                            : ok  
Checking for program g++,c++                : ok /usr/bin/g++ 
Checking for g++                            : ok  
SLV2 Configuration 
Checking for redland >= 1.0.6               : ok 
Checking for jack >= 0.107.0                : ok 

Global configuration 
Install prefix                              : /usr/local 
Debuggable build                            : False 
Strict compiler flags                       : False 
Build documentation                         : False 

Jack clients                                : True 
Unit tests                                  : False 
Dynamic Manifest Support                    : False 
Default LV2_PATH                            : ~/.lv2:/usr/local/lib/lv2:/usr/local/lib/lv2 

Raul Configuration 
Checking for glib-2.0 >= 2.2                : ok 
Checking for gthread-2.0 >= 2.14.0          : ok 
Checking for header boost/shared_ptr.hpp    : ok 
Checking for header boost/weak_ptr.hpp      : ok 
Checking for header boost/utility.hpp       : ok 

Unit tests                                  : False 

FlowCanvas Configuration 
Checking for libgvc >= 2.8                  : ok 
Checking for gtkmm-2.4 >= 2.10.0            : ok 
Checking for libgnomecanvasmm-2.6 >= 2.6.0  : ok 

Auto-arrange                                : True 
Anti-Aliasing                               : True 

Patchage Configuration 
Checking for dbus-1                         : ok 
Checking for dbus-glib-1                    : ok 
Checking for libglademm-2.4 >= 2.6.0        : ok 
Checking for gtkmm-2.4 >= 2.11.12           : ok 
Checking for alsa                           : ok 

Install name                                : 'patchage' 
App human name                              : 'Patchage' 
Jack (D-Bus)                                : False 
LASH (D-Bus)                                : True 
Jack (libjack)                              : True 
Alsa Sequencer                              : True 

Redlandmm Configuration 
Checking for raptor >= 1.4.18               : ok 
Checking for redland >= 1.0.8               : ok 

Ingen Configuration 
Checking for gtkmm-2.4 >= 2.14.0            : ok 
Checking for jack >= 0.109.0                : ok 
Checking for libxml-2.0 >= 2.6.0            : ok 
Checking for libsoup-2.4 >= 2.4.0           : ok 
Checking for header ladspa.h                : ok 
Checking for liblo >= 0.25                  : fail 
Checking for function posix_memalign        : ok 

Jack                                        : True 
OSC                                         : False 
HTTP                                        : True 
LV2                                         : True 
LADSPA                                      : True 
GUI                                         : True 

'configure' finished successfully (1.186s)

```and now when I try and compile...

```

zak@zak-laptop:~/src/drobilla-lad$ ./waf
Waf: Entering directory `/home/zak/src/drobilla-lad/build'
[ 54/222] cxx: ingen/src/engine/AudioBuffer.cpp -> build/default/ingen/src/engine/AudioBuffer_1.o
[ 55/222] cxx: ingen/src/engine/BufferFactory.cpp -> build/default/ingen/src/engine/BufferFactory_1.o
../ingen/src/engine/AudioBuffer.cpp:22:27: error: atom.lv2/atom.h: No such file or directory
In file included from ../ingen/src/engine/AudioBuffer.hpp:25,
                 from ../ingen/src/engine/AudioBuffer.cpp:24:
../ingen/src/engine/ObjectBuffer.hpp:46:2: error: ISO C++ forbids declaration of &#8216;LV2_Atom&#8217; with no type

```There is more but it wouldn't all paste in this box for some reason so I only took the most important part at the beginning.

---

### Post by AxelMan0 on 2010-12-25
Problem seems to have been fixed

---

