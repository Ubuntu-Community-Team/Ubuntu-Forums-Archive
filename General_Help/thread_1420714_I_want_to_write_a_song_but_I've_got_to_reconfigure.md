---
title: "I want to write a song but I've got to reconfigure!!!!!"
date: 2010-03-03
forum: General Help
---

### Post by briantroy on 2010-03-03
Howdy all

does any one know how to configure Alsa?
I've read every thing and tried every thing but get know results. 
Just 

 Compiling drivers...
--------------------------------------------------------------------------------------
rm -f .depend *.o snd.map*
rm -f modules/*.o modules/*.ko
make[1]: Entering directory `/usr/src/Alsa-1.0.22.1/alsa-driver-1.0.22.1/include'
Makefile:6: ../Makefile.conf: No such file or directory
make[1]: *** No rule to make target `../Makefile.conf'.  Stop.
make[1]: Leaving directory `/usr/src/Alsa-1.0.22.1/alsa-driver-1.0.22.1/include'
make: *** [clean] Error 1
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: in `/usr/src/Alsa-1.0.22.1/alsa-driver-1.0.22.1':
configure: error: C compiler cannot create executables
See `config.log' for more details.

--------------------------------------------------------------------------------------
-  alsa-driver-1.0.22.1 configure failed
--------------------------------------------------------------------------------------
root@64studio:/home/brian/Desktop# 

I've tried installing new different compilers but get the same result.
I am launching a script that I found on this forum.
I've also tried to get it reconfigred using the step by step meathod but it won't reconfigure. 
Ultimatly I would like to get my Tascam us-428 to interface with aurdour so I can produce music. 
I guess I need to be a computer programer befor being a musician.
I did sort of  get the tascam to operate when I rewrote the udev rules file, but the midi didn't work and the tascam out put sound card would not hook up. 
Any way if any one knows how to reconfigure to the newest alsa 1.0.22.1 upgrade that would be a start. 
currently I'm using 64studio with alsa 1.0.18a

thanks for reading my post 

briantroy

---

