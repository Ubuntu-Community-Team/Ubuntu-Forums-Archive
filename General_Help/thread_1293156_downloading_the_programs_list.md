---
title: "downloading the programs list"
date: 2009-10-16
forum: General Help
---

### Post by a7med93 on 2009-10-16
hi i have a ubuntu a fresh install but i don't have a internet connected to it at the moment 
what i want to do is to make a list of the programs in sympatic manager because it's not updated 
so i can download it "the list "from a different PC which has internet access

---

### Post by zvacet on 2009-10-16
You can try [Keryx.]("http://keryxproject.org/")

---

### Post by a7med93 on 2009-10-17
hi thx for replying 
but i just need the source list

---

### Post by Sam on 2009-10-17
Make your selection on Synaptic, then go to "File > Generate package download script"

Use this script on an internet-connected PC to download the packages.

Then on the offlice PC, do in Synaptic "File > Add downloaded packages" and choose the directory containing the downloaded packages.

---

### Post by a7med93 on 2009-10-17
thx for replying 
that what is what i want to do but my problem is that this is a fresh install that nevere connected to internet meaning my source list is old very old it barley have anything in it ,,,
in short i want to download the source list from a windows pc and then transfer it to my ubuntu
thx

---

### Post by drs305 on 2009-10-17
a7med93,

I'm having a bit of a problem trying to understand if you just want a sources.list or if you want a list of every available package for your system.

If you just want a sources.list, here is a link to an automated sources.list generator created by hyper_ch:

[http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/")


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by a7med93 on 2009-10-17
i want a list of every available package for my system.:)

---

### Post by Ekeluo on 2009-10-17
I totally understand you, you need the contents of **/var/lib/apt/** from  a pc with complete, up to date repos. Try to make sure the sources are the ones you want though. Just paste the contents in your own **/var/lib/apt**. It'll probably show you that u need updates immediately. I'll also recommend you copy the /etc/apt/sources.list (and maybe any other .list files present) and edit the sources as you need.

---

### Post by Ekeluo on 2009-10-17
I checked out keryx and it seems to be a cleaner way of doing what you want. Recommended.

---

