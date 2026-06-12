---
title: "Installing tcsh without internet. Dependencies?"
date: 2011-04-09
forum: General Help
---

### Post by Pureferret on 2011-04-09
So recently my main PC which now has Ubuntu 10.04 LTS on it has had it's ethernet port die (rest in peace little buddy). And I need to install glut, and glut needs tcsh and tcsh needs *who knows what.*

I've been trying unproductively to download all of the dependencies that I can find in the config.log file but even that doesn't seem to work. I tried to install lcurses and it still reads as an error. 

Long story short: Can I get all the dependencies for tcsh, all in one place and just install them? Where could I find this list? Googling has turned up nothing for me, and nothing has come of asking my linux savvy friends.

---

### Post by ajgreeny on 2011-04-09
Assuming you ethernet has only just died, go through thre motions of installing using synaptic, but after marking all that is needed for installation, but insteqad of hitting the apply button go to **File->Save markings as**, and create a txt file of all the packages needed on your system.
Then it will be up to you to find them and install them all, easiest from a new folder made for the purpose, using the command ```
sudo dpkg -i *.deb
```which wil do everything together.

---

