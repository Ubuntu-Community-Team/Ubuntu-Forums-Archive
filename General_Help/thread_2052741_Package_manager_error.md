---
title: "Package manager error"
date: 2012-09-03
forum: General Help
---

### Post by srharri9 on 2012-09-03
I'm getting an error message saying to run the package manager. Some packages may have unmet dependencies. When I try to run the package manager, I get this error:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


I don't know if it's related, but when I try to open the Ubuntu Software Center, the program loads but closes again within seconds. It doesn't load any icons or anything.

---

### Post by wojox on 2012-09-03
Clear it out and try again:
```
sudo rm /var/lib/apt/lists/* -vf && sudo apt-get update
```

---

### Post by srharri9 on 2012-09-03
I'm getting the same message.

Though, Software Center is working now.

---

### Post by wojox on 2012-09-03
> **srharri9 said:**
> I'm getting the same message.

Though, Software Center is working now.

That's weird. Half way there though. :p

---

### Post by srharri9 on 2012-09-03
That must have been a coincidence.

I am still looking for help here. 

I am still receiving these other error messages.

---

### Post by srharri9 on 2012-09-03
Whoops, double post

---

### Post by wojox on 2012-09-04
Have you tried:
```
sudo apt-get -f install
```

---

### Post by plucky on 2012-09-04
> I am still receiving these other error messages.


Are the messages different to the one above?

It would be nice to know what the error messages are,otherwise it is difficult for us to come up with a solution.

Good Luck

---

### Post by srharri9 on 2012-09-10
Software Center is having the same issue again. When I attempt to open it, the program pops up and begins to load, but very quickly (seconds) it disappears. I get no error messages of any kind with it.



When I try sudo apt-get -f install, I get this message in the terminal:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

______________________________________________________________

The error I was originally receiving, and I'm still getting is this: I have a red circle that pops up next to my clock at the top right of my screen. When I click on it, it says: 

"An error occurred, please run Package Manager from the right-click menu or apt-get ina a terminal to see what s wrong. The error message was: &#8216;Error:Opening the cache (E:Encountered a section with no Package: Header, E:Problem with MergeList/var/liv/apt/listsus.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.)&#8217;. This usually means that your installed packages have unmet dependencies."

______________________________________________________________

When I try to run package manager, I receive an error message after entering my password. It says:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E:_cache->open() failed, please report.

---

### Post by raja.genupula on 2012-09-10
open your terminal and try this

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

---

### Post by srharri9 on 2012-09-10
Everything seems to be working fine after that! Thanks, raja.

---

### Post by raja.genupula on 2012-09-12
you're welcome always :D

---

