---
title: "can't wrap my head around ndiswrapper"
date: 2011-03-19
forum: General Help
---

### Post by orrymr on 2011-03-19
I need to use this program to get my wireless card working on Ubuntu. I have the drivers, and they install fine with ndiswrapper, once ndiswrapper is installed (makes sense). Now, once this is done, I need to insert the kernel module [aside: I'm not really sure what this means - what does it mean?] hence the command:
```
 sudo modprobe ndiswrapper
```
So far I think I'm doing things right... right?

Here is where things start going wrong; I get the following output:
```
 orry@ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Could not read '/lib/modules/2.6.35-22-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory
orry@ubuntu:~$ 

```
Basically, I have no idea what's gone wrong. The ndiswrapper.ko file is missing from \kernel\ubuntu\ndiswrapper, which I'm assuming is probably not a good thing. I doubt anyone could simply send this file to me, as I'm further assuming that this file is compiled upon installation of ndiswrapper (or should be).

I'm as lost as a mentally challenged meerkat in the karoo desert.


(help)

---

### Post by ChuckyDuckster on 2011-03-19
Hello,

Sorry to hear your ndiswrapper story, I have been there before. I have had good luck though with ndisgtk (A nice frontend that will hopefully take care of these issues for you).

Good luck!
Chucky

---

### Post by orrymr on 2011-03-19
I dunno...

Am I right in saying that a .ko file should be created upon installation?

---

### Post by iDrago on 2011-04-02
I managed to solve my problem. The answer [here]("http://ubuntuforums.org/showthread.php?p=10629109#post10629109").

---

