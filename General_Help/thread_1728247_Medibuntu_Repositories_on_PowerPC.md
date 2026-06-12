---
title: "Medibuntu Repositories on PowerPC"
date: 2011-04-13
forum: General Help
---

### Post by 1984dc on 2011-04-13
Hello everyone.

I just tried to install the Medibuntu Repositories on my G5 power mac (running 10.10 powerpc64 flavour of ubuntu). I got the link from the following page;

[http://www.webupd8.org/2010/10/medibuntu-repository-is-available-for.html](http://www.webupd8.org/2010/10/medibuntu-repository-is-available-for.html)

But when i 
```

 sudo apt-get install app-install-data-medibuntu
```I get the error message [COLOR=Red]E: Unable to locate package app-install-data-medibuntu


[COLOR=Black]Any ideas as to whether i can even run these repositories from my system??

Many thanks.

Dc
[/COLOR][/COLOR]

---

### Post by stinkeye on 2011-04-13
It worked here. After running the first part of the guide.
eg enter each line one at a time
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list

cd && wget http://packages.medibuntu.org/pool/free/m/medibuntu-keyring/medibuntu-keyring_2008.04.20_all.deb && sudo dpkg -i medibuntu-keyring_2008.04.20_all.deb && rm medibuntu-keyring_2008.04.20_all.deb

sudo apt-get update
```

Then run
```
sudo apt-get install app-install-data-medibuntu
```

---

### Post by 1984dc on 2011-04-13
Hi Stinkeye ):P thanks for chipping in! Are you also running 10.10 Powerpc 64 release?

The first two lines of code work fine, but when i try to sudo apt-get update I get this;
```

Get:2 http://packages.medibuntu.org maverick Release [6,860B]
Fetched 7,057B in 1s (5,219B/s)                           
W: Failed to fetch http://packages.medibuntu.org/dists/maverick/Release   Unable to find expected entry  free/binary-powerpc/Packages in  Meta-index file (malformed Release file?)

```And when i 

```
sudo apt-get install app-install-data-medibuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package app-install-data-medibuntu

```Any ideas what i might be doing wrong?

Many thanks

Dc

---

### Post by earthpigg on 2011-04-13
[http://packages.medibuntu.org/dists/maverick/](http://packages.medibuntu.org/dists/maverick/)

```
[DIR]	Parent Directory	 	-
[ ]	Contents-amd64.gz	16-Feb-2011 14:21 	7.0K
[ ]	Contents-i386.gz	27-Mar-2011 16:43 	9.8K
[ ]	InRelease	27-Mar-2011 16:43 	6.9K
[ ]	Release	27-Mar-2011 16:43 	6.7K
[ ]	Release.gpg	27-Mar-2011 16:43 	197
[DIR]	free/	30-Apr-2010 22:25 	-
[DIR]	non-free/	30-Apr-2010 22:25 	-
```

I see i386 indicating 32-bit x86 architecture (usually found on Intel or AMD chips), and I see amd64 indicating 64-bit x86 architecture (usually found on Intel and AMD chips) - but I see no mention of PPC. 

Your computer cannot find what does not exist.

Sorry chief, but it looks like you will have to go another route.

EDIT: I wonder if Virtualbox OSE compiled for PPC can run x86 Ubuntu? It should. Wonky solution, but you could then watch youtube and all the other stuff inside of a Virtual (Intel) Machine on your physical PPC machine. Unless I am mistaken. If you want to give this indirect route a shot, let me know and I can help walk you through it.

EDIT2: I should get my hands on some old PPC machine to play around with. I bet there are lots of folks in the same boat you are, trying to keep that an machine useful and save it from the landfill that could benefit from some solid guidance...

---

### Post by earthpigg on 2011-04-13
nope, no VirtualBox for PPCs. :\

I did find these two projects, though:

[http://bochs.sourceforge.net/getcurrent.html](http://bochs.sourceforge.net/getcurrent.html)
[http://www.kju-app.org/](http://www.kju-app.org/)

neither project looks particularly healthy and alive, but you could give it a shot...

---

### Post by earthpigg on 2011-04-13
do you see bochs in the ubuntu software center?

> Bochs is a highly portable free IA-32 (x86) PC emulator written in C++, that runs on most popular platforms. It includes emulation of the Intel x86 CPU, common I/O devices, and a custom BIOS.

Bochs is capable of running most operating systems inside the emulation including GNU, GNU/Linux, *BSD, FreeDOS, MSDOS and Windows 95/NT.

this dude has old WinXP running on his PPC using Bochs, so you should be able to run Ubuntu x86 on top of your Ubuntu PPC install...

...If someone else using PPC wants to jump in here and tell me I'm insane, please do so. I'm just sharing what my next move would be, in the shoes of the OP.

[IMG]http://bochs.sourceforge.net/screenshot/SiteInWinInBochs.png[/IMG]

---

### Post by 1984dc on 2011-04-13
Many Thanks Earthpigg for clarifying that. I assumed that it might not work on my architecure. I will probably give bochs a try at some point in the not too distant future.

> EDIT2: I should get my hands on some old PPC machine to play around  with. I bet there are lots of folks in the same boat you are, trying to  keep that an machine useful and save it from the landfill that could  benefit from some solid guidance... It may be old, it may be outdated and unsupported (and always was to a certain extent) but I love My Powermac G5 and nearly 6 years down the line and I still have no complaints as it has never failed me  :biggrin: ...yet!

All the best

Dc

Edit 1: That screen-shot looks awesome! I wonder how far I can go with this??!! ( I wasn't really thinking about a headless machine as a possible answer, but it's definitely a way to access the repositories)

---

### Post by earthpigg on 2011-04-13
> **1984dc said:**
> 
Edit 1: That screen-shot looks awesome! I wonder how far I can go with this??!! ( I wasn't really thinking about a headless machine as a possible answer, but it's definitely a way to access the repositories)

not farther than within the virtual machine. you will be able to get the packages on your x86 virtual machine, but that doesn't mean they will work natively on your PPC without the virtual machine.

---

