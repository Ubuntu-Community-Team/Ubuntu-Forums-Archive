---
title: "Ubuntu sotware center help"
date: 2011-05-10
forum: General Help
---

### Post by goPlayYourGuitar on 2011-05-10
I just downloaded Ubuntu 11.04 last night.  Everything works great except for the Ubuntu software center.
When I open it, when I click on get software or installed software, that loading image pops up and nothing loads.  As of now it's been going or about an hour and a half.  How can I fix this?  Thanks in advance.

---

### Post by ajgreeny on 2011-05-10
Try refreshing your repositories with ```
sudo apt-get update
``` in terminal, then try software centre again.

You must shutdown software centre before using that command as there can only be one application using apt running for it to work.

---

### Post by goPlayYourGuitar on 2011-05-10
When I type sudo apt-get update, it says 

E: type '--2011-05-10 is not know on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read

What does this mean?

---

### Post by ajgreeny on 2011-05-11
It means that something went wrong when you tried to add and enable the medibuntu repositories on your system.

Hase a look at [http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php) and re-run the command shown on that page ```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```which will add and enable the repos again, hopefully correctly this time.

---

### Post by plucky on 2011-05-11
Op fixed it in other post [http://ubuntuforums.org/showthread.php?t=1755139](http://ubuntuforums.org/showthread.php?t=1755139)

---

