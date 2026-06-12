---
title: "Quick question regarding pyrit"
date: 2011-10-04
forum: General Help
---

### Post by bombhills on 2011-10-04
Hey, sorry if this is in the wrong section, first time using this forum.

Running pyrit with opencl and c++.
core i5 (multithreading) and Radeon HD5470 

Just a quick question about setting the CPU limit in pyrit. On their site ([http://code.google.com/p/pyrit/wiki/Troubleshooting](http://code.google.com/p/pyrit/wiki/Troubleshooting)) it has the instructions "Open '.pyrit/config' and set 'limit_ncpus' to the number of physical CPU-cores."  I edited the **config.py** in the /pyrit/svn/pyrit/build/lib.linux-x86_64-2.6/cpyrit and /pyrit/svn/pyrit/cpyrit directories to set the number to two and it has had no effect, still showing 3 processors and the GPU. 

I'm probably just editing the wrong files, I'm just figuring linux out.

Thanks

---

### Post by Dangertux on 2011-10-04
> **bombhills said:**
> Hey, sorry if this is in the wrong section, first time using this forum.

Running pyrit with opencl and c++.
core i5 (multithreading) and Radeon HD5470 

Just a quick question about setting the CPU limit in pyrit. On their site ([http://code.google.com/p/pyrit/wiki/Troubleshooting](http://code.google.com/p/pyrit/wiki/Troubleshooting)) it has the instructions "Open '.pyrit/config' and set 'limit_ncpus' to the number of physical CPU-cores."  I edited the **config.py** in the /pyrit/svn/pyrit/build/lib.linux-x86_64-2.6/cpyrit and /pyrit/svn/pyrit/cpyrit directories to set the number to two and it has had no effect, still showing 3 processors and the GPU. 

I'm probably just editing the wrong files, I'm just figuring linux out.

Thanks


This really isn't the right place to ask this question -- this forum doesn't support or condone the cracking of WPA/WPA2 here.

You should check the documentation more thoroughly. Double check the syntax in your config file.

---

### Post by bombhills on 2011-10-04
I was trying out this software to see if I could use it and it worked.  Hearing that it was so easy to crack passwords led me to test it out myself which was originally where I gained interest in linux.  I've figure out a lot in setting up this program, now it's just annoying me that I can't figure this small thing out.
For the record I haven't used it on anyone but myself.

Like I said I'm new, would you be able to explain what you mean by checking the syntax?

---

### Post by bombhills on 2011-10-04
OK, I checked the syntax with the bash -n command, It's returning a syntax error... how do I correct this? It's on a line I haven't edited.
The error is:
config.py: line 26: syntax error near unexpected token `('
config.py: line 26: `def default_config():'

The section it's refering to is

def default_config():
    config = {'default_storage': 'file://', \
              'rpc_server': 'false', \
              'rpc_announce': 'true', \
              'rpc_announce_broadcast': 'false', \
              'rpc_knownclients': '', \
              'workunit_size': '75000', \
              'limit_ncpus': '2'}
    return config

above this it also list 
import os
import sys

Sorry for the basic questions...  I'll paste up the whole file if needed.  Greatly appreciate the help anyone can give me, this is frustrating.

---

### Post by bombhills on 2011-10-05
Anyone have an answer? sorry to bump this is just driving me crazy because I know it must be something ridiculously simple...

---

