---
title: "Nvidia 8600 driver in 9.04"
date: 2009-10-27
forum: General Help
---

### Post by Liveforthenight on 2009-10-27
Need some help with the driver for an Nvidia 8600.  It crapped out on me about an hour ago, I just upgraded to Jaunty and the driver was working for a few hours.  Then it just stopped.  It is now telling me that i am not using the Nvidia X driver and that typing nvidia x-config will fix the problem.  This does not work, in fact it causes my computer to run in "low graphics" mode from which I can not fix anything.  I have it running off my cpu, i think, and need some help here.

---

### Post by bondmatt on 2009-10-27
I have a Nvidia 8600 gs chipset but I run 8.04 LTS 64bit. I use drivers off Nvidias website.

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

This is a guide from this forum on installing the driver. Alternatively, there is also program that can be installed through synaptic called Envy that installs graphics drivers. However, I didnt find it foolproof. 

Once in a while when there is a big kernel update I have found that I need to reinstall the Nvidia driver but it is easy, quick, and always works. Every other method or wizard I used never managed to be all three (Envy is very easy to use, I just managed to irreversibly - given my lack of linux finesse - screw it up once).

[http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+proprietary+drivers](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+proprietary+drivers)

Best of luck,
- MJB

---

### Post by Liveforthenight on 2009-10-27
Thank you for the reply, but i have already tried this.  It STILL does not use the nvidia driver
I have an older version installed, but it won't work.
How do i go about editing my x-org whatever to make it so that this thing works?
I just did what the page you suggested tells me to Bond, nothing changed here.  I am really in a bind.  will someone please help

---

### Post by Liveforthenight on 2009-10-27
Still trying to make this thing work, I have been using hints from
here
[http://ubuntuforums.org/showthread.php?t=1036788](http://ubuntuforums.org/showthread.php?t=1036788)
and from 
[http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+proprietary+drivers](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+proprietary+drivers)

neither of these threads have helped me fix this problem

I am still getting the error that I am not using the Nvidia X server thing

my system is unable to find nvidia xconfig and is still using an older version of the driver

---

### Post by Liveforthenight on 2009-10-27
Ok, now I have followed a very nice and detailed How To page
this has actually gotten the new driver up and running on my machine, but it is now running in ultra low res mode, if anyone could explain what I have done wrong I would appreciate it

---

