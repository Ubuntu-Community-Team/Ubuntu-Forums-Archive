---
title: "installing googsystray"
date: 2010-02-28
forum: General Help
---

### Post by obscureflame on 2010-02-28
hi im really new to Linux, i'm using jolicloud but as i understand it the base is Ubuntu. I have been trying to install googsystray and its compressed as a tar. I have fallowed the instructions shown below but to no result.
"Linux

Dependency: Python 2.6
Dependency: Pygtk 2.14
Download and untar the .tar.gz source archive.
'sudo python ./setup.py install'"

i am probably doing something wrong. Here's how i've interpret it: i checked in synaptic for python 2.6 and is installed, i checked for pygtk but could not find it...i read somewhere that it's part of the python(pls correct if i'm wrong and i would really apreciate a way to install if that's the problem), so i downloaded the file and it was stored under downloads, i then right clicked and pressed extract(so now i have extracted folder under downloads) and finally i opened the terminal and typed 'sudo python ./setup.py install' and i get an output of "python: can't open file './setup.py': [Errno 2] No such file or directory"??? so then i read on another page that i needed to "navigate to the folder where you have extracted Googsystray" but did not explain wt that meant or how to do it.. so i just typed this in the terminal "/home/jolicloud/Downloads" and then 'sudo python ./setup.py install' to the same result:( so then i tried "/home/jolicloud/Downloads/googsystray-1.1.4" which resulted in the same thing...i will really apreciate help wh this, tnx

---

### Post by mick222 on 2010-02-28
there's a .deb file for googsystray. You can dowload it here [http://linux.softpedia.com/progDownload/googsystray-Download-50805.html](http://linux.softpedia.com/progDownload/googsystray-Download-50805.html)
Much easier to install if your system is based on ubuntu.By the way jolicloud looks quite nice .

---

### Post by obscureflame on 2010-02-28
OMG tnx so much! this completly fixed. And yes it's really nice. I have an asus 1005pe and was using eeebuntu on it, but decided to give jolicloud a try and i'm quite pleased lol but again tnx for your help. lol would of never gotten such a fast answer from microsoft haha oh! now that i know i should go for deb extensions i found the lates version googsystray, the link is here for anyone that may need it [http://sourceforge.net/projects/googsystray/files/](http://sourceforge.net/projects/googsystray/files/)

---

