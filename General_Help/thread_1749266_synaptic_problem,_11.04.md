---
title: "synaptic problem, 11.04"
date: 2011-05-04
forum: General Help
---

### Post by khaj_vah on 2011-05-04
Hello everyone, people i have messed something up when i run synaptic it says:

[SIZE=3]E: Type '<html>' is not known on line 1 in source list /etc/apt/sources.list.d/akirad.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
[/SIZE]
This problem appeared when i tried to install cinelerra and i didnt notice that the tutorial was for  7.** and so i messed up everything 
Please help i am new in here 
i am using ubuntu 11.04

---

### Post by ~Plue on 2011-05-04
From a quick look at the akirad ppa (which I'm guessing that you're using) they doesn't seem to offer natty specific builds, but that doesn't explain how a html tag got into the sources. See the contents of the file by *cat /etc/apt/sources.list.d/akirad.list* if you're curious..

To remove the repository from your sources, run from a terminal;```
sudo rm  /etc/apt/sources.list.d/akirad.list
sudo apt-get update
```

---

### Post by khaj_vah on 2011-05-04
thanks very much mate as i said i messed a lot :D but anyway u have solved this

---

### Post by ~Plue on 2011-05-04
You're welcome :)
Remember to mark the thread as [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

