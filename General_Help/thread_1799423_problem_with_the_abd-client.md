---
title: "problem with the abd-client"
date: 2011-07-07
forum: General Help
---

### Post by piyushpandey on 2011-07-07
Hello guys

I am trying to connect using the nbd-client , but I am gettitng the following error:

piyush@piyush-desktop:~$ sudo nbd-client localhost 1024 /dev/nbd0
Error: Connect: Connection refused
piyush@piyush-desktop:~$ 


can you guys help me .


Actually I  am following this link and doing as it is explained step by step:

[http://code.google.com/p/mini2440/wiki/QEmuSDCardImage](http://code.google.com/p/mini2440/wiki/QEmuSDCardImage)


but I think this command is of no use :

**sudo modprobe dm-mod** 


as I have searched that the lm-mod is no longer used in the 10.04 and higher

versions of the ubuntu.

and also the following command is enough I think:

**sudo modprobe nbd** 


I am using the Ubuntu 10.04 lucid .


Please help me guys what is the problem.


Thank you

---

