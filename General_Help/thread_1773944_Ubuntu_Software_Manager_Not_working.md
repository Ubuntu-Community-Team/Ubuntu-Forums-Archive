---
title: "Ubuntu Software Manager Not working"
date: 2011-06-02
forum: General Help
---

### Post by alexduhgreat on 2011-06-02
Hey guys im kind of a noob with linux and I know theres lots of other threads about this problem but non really seem to help me.
I get this when trying ```
sudo apt-get update
```

E: Type '“deb' is not known on line 60 in source list /etc/apt/sources.list
E: The list of sources could not be read.

 any help would be greatly appreciated

---

### Post by TeoBigusGeekus on 2011-06-02
```
gksu gedit /etc/apt/sources.list
```
What does line No60 say?

---

### Post by alexduhgreat on 2011-06-03
> **TeoBigusGeekus said:**
> ```
gksu gedit /etc/apt/sources.list
```What does line No60 say?

“deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free main”

---

### Post by neitshade on 2011-06-03
I've just had the same problem after a clean reinstall. For some reason (possibly my internet connection which my ISP is busy fixing) some things don't appear to have been installed properly.
I eventually fixed the problem by opening Synaptic Package Manager and clicking on "Mark All Upgrades", then on "Apply".
I'm a noob too, so I have no idea why that worked, but it did!

---

### Post by Raakashan on 2011-10-20
Ok, I did the sudo apt-get update through terminal and it seemed to work at first but when i went back in and did it again i got this at the very end of the process

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_packages
E: The package lists or status file could not be parsed or opened.

Also i tried the Synaptic thing and Synaptic Software Manager won't load, it gives me the same error.

---

### Post by Rubi1200 on 2011-10-20
> **Raakashan said:**
> Ok, I did the sudo apt-get update through terminal and it seemed to work at first but when i went back in and did it again i got this at the very end of the process

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_packages
E: The package lists or status file could not be parsed or opened.

Also i tried the Synaptic thing and Synaptic Software Manager won't load, it gives me the same error.
Hi and welcome to the forums :)

In future, please start your own thread for such issues rather than posting in (by Internet standards) an old thread.

In any event, open a terminal and run the following commands:
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```
The first command removes corrupted package lists, the second refreshes them.

---

