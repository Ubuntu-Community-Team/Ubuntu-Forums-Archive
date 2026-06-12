---
title: "Cannot install anything any more"
date: 2006-03-01
forum: General Help
---

### Post by Timokl on 2006-03-01
Hi there, 

today I tried to install the Moodle package from the repositories. But due to a user inflicted error :)  during the installation, the process failed. I removed the package and re-installed it with Synaptic. But during this second install, the process suddenly hanged. (I think because I entered a wrong information concerning the MySQL database server in need.) I had to do a "hard shut down" by pressing the power button.

Now, I cannot install any programm any more. No matter whether with Synaptic, apt-get, or dpkg -- I only come as far as the following message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

Whenever I type *sudo dpkg --configure -a* into a terminal window, I get the following reply:

```
Richte moodle ein (1.5.2-1ubuntu1) ... 
```

But then nothing happens, only is constantly at 100% onwards.

How can I "kill" that installation process? No need to install that particular package the Debian way. I've set up Moodle some times on a web server, so I should be able to do it this way on my local machine, too. :-)

Any help is highly appreciated!

Bye,
Timo

---

### Post by Timokl on 2006-03-01
I managed to solve the problem with aptitude. \\:D/ 

Why didn't I think of that before???

---

### Post by earobinson on 2006-03-01
could you what you did with aptitude to solve the problem?

---

