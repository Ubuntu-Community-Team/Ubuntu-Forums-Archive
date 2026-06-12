---
title: "Ati Driver Update"
date: 2006-01-30
forum: General Help
---

### Post by DazarGaidin on 2006-01-30
Im new, and i am liking this OS.  Only thing is (and windows did this as well so its ok :D), it recognized my ati card as radeon 9200 when its a 9250.  It works for most things but i know in my favorite game (which is how i decided on ubuntu cause i found a thread detailing the steps to run that game) i had to update to the correct 9250 or wouldnt display in windows.  To avoid complications i wanted to just get it done now.  So i download ati driver from thier website hoping it would work its magic like before.  I did the installation after my journey learning the command line a bit and all finally seems to go ok except at the end it tells me to 'save your X Windows configuration file, then run aticonfig, then reboot" (paraphrasing)

Where is my X windows Config file, and  how to save it?

Mucho thanks for a great [EDIT: FRUSTRATING] OS package :)

---

### Post by DazarGaidin on 2006-01-30
I tried to run the aticonfig thing and i guess its a no go there anyway

integrity@store:/usr/X11R6/bin$ ./aticonfig
./aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory

Well i got bored and rebooted, and nothing is changed.  I got a little ati icon in my applications menu that does nothing when i click it.  Any thoughts?

---

### Post by Horndog on 2006-01-30
Try this:

```


sudo ./aticonfig


```

...and if that doesn't work go [here.]("http://ubuntuforums.org/showthread.php?p=423589")

---

### Post by DazarGaidin on 2006-01-30
Ok i went to that page and it must assume a great deal of crap, cause i get alllllll kinds of errors, no such directories and files and other things.   Its like i follow his instructions step by step but we are doing 2 different things. 

Its crazy you have to do 20 steps just to update a frickin video driver.  I mean, ubuntu had the ability to install the older driver why doesnt it have the ability to just install the better one or a newer one??

---

### Post by Horndog on 2006-01-30
That's ATI's fault they are not open source drivers, but It worked on my system. Did you install the essential files as directed? Why don't you ask about your problem on that thread. They would be better at trouble shooting this problem.

---

