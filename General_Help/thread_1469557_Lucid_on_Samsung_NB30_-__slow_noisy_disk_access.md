---
title: "Lucid on Samsung NB30 -  slow noisy disk access"
date: 2010-05-02
forum: General Help
---

### Post by scotty64 on 2010-05-02
I have installed Kubuntu Lucid on my Samsung NB30 netbook. Got everything working, but the disk access seems extremely slow and noisy. Whenever larger files are being processed (software installation), the disk makes a kind of rattling sound - looks like the head is moving back and forth between two or more locations. The disk seems o.k. so far - no io errors under Linux and Windows XP boots without problems.
Any ideas ?

---

### Post by dino99 on 2010-05-02
is hddtemp installed ? if so: sudo dpkg-reconfigure hddtemp

---

### Post by scotty64 on 2010-05-04
> **dino99 said:**
> is hddtemp installed ? if so: sudo dpkg-reconfigure hddtemp

No, hddtemp is not installed.

---

### Post by scotty64 on 2010-05-04
I just tried laptop-mode-tools and enabled it - still the ugly harddisk rattling when Synaptic is in the "unpacking" and "preparing" phase of a package installation.

---

### Post by scotty64 on 2010-05-06
I think the problem is more related to Synaptic (probably a bug?) than disk access. I tried to install a large package (FlightGear) by using KpackageKit - no clicking disk, but a swift and easy installation.

---

### Post by Henns Wörst on 2010-05-08
I've exactly the same problem on a Samsung N140, I've already started two threads about it but no one else seems to have this problem. I have no solution for it, I don't even know, what the f* is wrong. I couldn't install Lucid gy upgrade either. I first thought it could have somathing to to with the Large Disc Acces Mode in BIOS but it didn't change a thing. Since a week or so every second day when booting the netbook checks its hdd, it's working normally till exactly 70% then it starts to get really slow, like 2% per minute or something. I'm thinking about going back to Karmic cos everything worked fine there but I don't want to be stuck on an old OS and since (almost) nobody seems to have the problem, I doubt there will be a fix of any kind :(

---

### Post by scotty64 on 2010-05-09
> **Henns Wörst said:**
> I've exactly the same problem on a Samsung N140...(
I am getting increasing doubts that this might be a more generic problem than just affecting Samsung users: I just installed a huge bunch of packages on my Dell XPS M1330 that I re-installed with Lucid now and Synaptic shows the same awful disk rattling. It is just less obvious as the Dell is faster than the Samsung netbook.

---

### Post by Henns Wörst on 2010-05-10
What kind of HDD does this Dell have? Inside the N140 is a Fujitsu MHZ 2160B drive. By the way I'm using Karmic again, works perfectly :confused:

---

### Post by scotty64 on 2010-05-10
> **Henns Wörst said:**
> What kind of HDD does this Dell have? Inside the N140 is a Fujitsu MHZ 2160B drive. By the way I'm using Karmic again, works perfectly :confused:
The Dell runs with a Western Digital, while the Samsung Netbook uses a Hitachi drive. All this is giving me more and more a feeling that we are talking about a generic problem - probably related to a bug in the debian package manager: I installed the latest Virtualbox 3.1.8 on the Dell today. Because the repository was not available - probably server overload - I downloaded the .deb and installed it manually by typing dpkg -i filename in a terminal. The package installed with the rattling disk, while interestingly Virtualbox itself accesses the large vdi disk image files without any problem.

---

### Post by th5th on 2010-05-10
> **scotty64 said:**
> The Dell runs with a Western Digital, while the Samsung Netbook uses a Hitachi drive. All this is giving me more and more a feeling that we are talking about a generic problem - probably related to a bug in the debian package manager: I installed the latest Virtualbox 3.1.8 on the Dell today. Because the repository was not available - probably server overload - I downloaded the .deb and installed it manually by typing dpkg -i filename in a terminal. The package installed with the rattling disk, while interestingly Virtualbox itself accesses the large vdi disk image files without any problem.

Hey scotty. I also have a Samsung NB30 but have not come across this problem. But I have installed all my packages using apt-get on the command line, which supports your theory that it is a bug in dpkg I guess. Does using apt-get eliminate the problem for you?

---

### Post by Henns Wörst on 2010-05-10
But shouldn't this problem be more common? Why can't I  find (almost) nothing about it? It could be like you said, that on fast machines one doesn't notice it that quickly, but there are thousands of users using (K)ubuntu on their notebooks, it *has* to have more impact than now

---

### Post by Henns Wörst on 2010-05-10
Since I'm already online, may I answer first? Using apt didn't change anything on my samsung, I'm hardly using the gui for installing packages.

---

### Post by th5th on 2010-05-10
> **Henns Wörst said:**
> Since I'm already online, may I answer first? Using apt didn't change anything on my samsung, I'm hardly using the gui for installing packages.

Yeah I realised apt-get is just a front end for dpkg, so if the problem is in dpkg it wouldn't make a difference. But I am not having the same problem... It could be a bad batch of drives? My disk does make the odd funny "ping" noise but it's much quieter than my main machine's Maxtor so I am not too worried :P

Sorry I can't be of greater help...

---

### Post by Henns Wörst on 2010-05-10
Yeah, well at least you're proving my point that this problem is not very common...O:)

---

### Post by scotty64 on 2010-05-12
> **th5th said:**
> It could be a bad batch of drives?
I do not think that this is the case here: I am having the problem with the Samsung running a Hitachi disk and the Dell running a Western Digital one. I wonder if it has something to do with caching and write / read optimization: The system needs to open the package and unpack it into a temp directory. Proper caching would load the entire package into memory and unpack it to the disk from there. But it looks to me like the disks head is constantly jumping (blockwise ?) between the location of the package on the disk and the place where to put the files.
I have enough RAM (4Gb), and write caching is enabled on the Harddisk.
Does anybody has any idea what could be done to analyse this problem ?
:confused:

---

### Post by scotty64 on 2010-05-15
I found the cause of the problem in this bug, that is indeed related to dpkg and the way how it synchronizes the filesystem:
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/570805](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/570805)
Installing the version of dpkg that is provided by Colin Watsons PPA [https://launchpad.net/~cjwatson/+archive/ppa](https://launchpad.net/~cjwatson/+archive/ppa) solved the problem.

---

### Post by Henns Wörst on 2010-05-18
May I ask if you actually tried it out yet? Does it really work?

---

### Post by scotty64 on 2010-05-18
> **Henns Wörst said:**
> May I ask if you actually tried it out yet? Does it really work?

Yes, the rattling disk problem disappeared from all three machines once the dpkg version from the PPA was installed - and it reduced the package installation time to a few seconds.... :)

---

### Post by Henns Wörst on 2010-05-18
Ha, great! Thank you! ):P

---

