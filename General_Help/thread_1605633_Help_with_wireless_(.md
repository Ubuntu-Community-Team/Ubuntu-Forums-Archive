---
title: "Help with wireless :("
date: 2010-10-25
forum: General Help
---

### Post by thomas.jerald on 2010-10-25
ok... so here's the problem: I'm new to linux, have been somewhat of a computer geek my whole life and thought it about time that I delved into the world of linux. So I installed ubuntu 10.04 on my computer. I love it. However, I can't get my wireless to work. In my dorms there are no ethernet hookups, so I have to use the wireless. I typed "sudo lshw -class network" into the root terminal. The important things that I figured out was the bus info: pci@0000:4:06.0 and the pysical id: 6 (not sure if the physical id is important but it sounds like it is). I then did a lspci and found that at bus 04:06.0 it is a RaLink Device 3060. I downloaded the .tar file for the driver. I could not find instructions for it online so I followed the ones for the rt2860 driver : 

[http://www.ab9il.net/linuxwireless/rt2860.html](http://www.ab9il.net/linuxwireless/rt2860.html)
[http://ubuntuforums.org/showthread.php?t=683085](http://ubuntuforums.org/showthread.php?t=683085)

I could not get it to work, It built ok and installed ok, but when I do the modprobe I get an error saying the device or resource is busy. Either that or that it cannot be found. One thing that I found weird was that I couldn't get it to build a 3060 driver, it would only build a 3562 one.

Again, I am new to linux, and if I am making a horribly easy newb mistake please forgive me. If you could please give me some suggestions on something that I might be doing wrong, or show me instructions on how to do it that would be great. 

Thanks,
Jerald



PS. I don't know if this is important, but my wireless card is a Rosewill RNX-N150PC

---

### Post by bryanfblareunion on 2010-10-25
Ah, yet another victim to Ubuntu's poor wireless compatability... 

Ubuntu seems to have many problems with wireless cards. I had that same problem, and I just reverted to an earlier kernel. You can try that and see if it works.

---

### Post by Hippytaff on 2010-10-25
You need to look into ndiswrapper

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

:-)

---

### Post by thomas.jerald on 2010-10-25
Ok... got it :)... I think that what it was was that I just needed to blacklist the other drivers... either way it's working now. Thanks

---

