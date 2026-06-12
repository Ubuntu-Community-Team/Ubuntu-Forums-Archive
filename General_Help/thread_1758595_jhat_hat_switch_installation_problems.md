---
title: "jhat hat switch installation problems"
date: 2011-05-14
forum: General Help
---

### Post by billfish1881 on 2011-05-14
I'm a linux newbie who had an experienced friend get me set up with using jhat for X-plane. I just installed natty and I'm trying to do it again myself with no luck. I downloaded the jhat.tar.gz file and extracted it into my home folder into /bin/jhat. I'm trying to install it now and am running into problems:


billfish@billDesktop:~$ cd ~/bin/jhat
billfish@billDesktop:~/bin/jhat$ ./configure
bash: ./configure: No such file or directory
billfish@billDesktop:~/bin/jhat$ make
cc    -c -o jhat.o jhat.c
cc   jhat.o   -o jhat
billfish@billDesktop:~/bin/jhat$ make install
make: *** No rule to make target `install'.  Stop.
billfish@billDesktop:~/bin/jhat$ sudo make install
[sudo] password for billfish: 
make: *** No rule to make target `install'.  Stop.
billfish@billDesktop:~/bin/jhat$ 

i found this procedure after an exhaustive google search, but I am obviously making a dreadful mistake. The readme file that comes with jhat is not much help:
- Install xautomation[1].
- Edit the script xplane.sh to match your joystick.
- make
- Install to wherever you like (and adjust the paths in xplane.sh appropriately).
- Enjoy!

And yes, i installed xautomation with synaptic and used the same xplane.sh file i had edited and had working previously. 
I am out of my league here without my friend around to throw me a line. Any help would be appreciated.

---

