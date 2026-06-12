---
title: "DJL &quot;Wait for Archive Extraction&quot;??"
date: 2010-04-16
forum: General Help
---

### Post by Mercenary410 on 2010-04-16
its supposed to make things easier, but seems to just complicate game installs. whenever installing alien arena or a cube engine game i get an error coupled with the message "Wait for Archive Extraction" in the downloads tab under the repositories.

Heres the error i get:

 p, li { white-space: pre-wrap; }  Traceback (most recent call last):
   File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
     self.run()
   File "/home/tyler/Downloads/djl/djl/installe.py", line 83, in run
     inst.run()
   File "/home/tyler/Downloads/djl/djl/installe.py", line 146, in run
     fichier_tar = tarfile.open(addr_archive,'r:bz2')
   File "/usr/lib/python2.6/tarfile.py", line 1665, in open
     return func(name, filemode, fileobj, **kwargs)
   File "/usr/lib/python2.6/tarfile.py", line 1741, in bz2open
     raise ReadError("not a bzip2 file")
 ReadError: not a bzip2 file
 
 
 Please report it to the developer.


help pl0x :)

---

### Post by Mercenary410 on 2010-04-16
I also get this error when trying to launch alien arena after extracting:

   "Error with alienarena. 
Here is the error string: 

/home/tyler/.Games/jeux/alienarena/crx: error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory

djl will try to download this library: libXxf86dga.so.1

For more information, you can go to the menu 'Information/Show games's output'"




how can i get the 32 bit libs for ubuntu 9.1? i assume thats what its talking about, but i may be wrong :(

---

### Post by Mercenary410 on 2010-04-16
i got the missing 32 bit lib file, but now alien arena comes up with this error:

"Error with alienarena. 
Here is the error string: 

AL lib: oss.c:179: Could not open /dev/dsp: Device or resource busy


The sound card might be used by other processes.

For more information, you can go to the menu 'Information/Show games's output'"


wut...

---

### Post by Mercenary410 on 2010-04-17
fixed the issue with this fix:

"This is because of some Pulse Audio issues with OpenAL. But I've found a fix. If you also experience this error, edit the */etc/openal/alsoft.conf* file. To do this, open terminal and type"

        Code:
        gksu gedit /etc/openal/alsoft.conf 

"Now search for the line that looks like this (it's on line 70 on my Ubuntu Karmic PC):"

        Code:
        #drivers = alsa,oss,solaris,dsound,winmm,port,pulse,wave 

"and uncomment it (remove the "#" at the beginning of the line) and also, remove "pulse" from this list. Basically, after the change, this line should look like this:"

        Code:
        drivers = alsa,oss,solaris,dsound,winmm,port,wave 

"And save the file, then run crx again."

everything works now :)

---

