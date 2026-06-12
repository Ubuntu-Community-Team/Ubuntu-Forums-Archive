---
title: "Initscripts and resolvconf producing errors"
date: 2012-08-20
forum: General Help
---

### Post by zcacogp on 2012-08-20
Hello, 

I'm having problems with my desktop computer; it's a 64-bit AMD machine with Ubuntu 12.04 on it. I ran apt-get update && apt-get upgrade yesterday and it produced some errors, but I (foolishly) didn't look into them. This morning it has refused to boot into a graphical shell; it shows the 'Ubuntu' load screen after GRUB, with the five dots progressing to the right, but then immediately drops to a command prompt. 

Suspecting it has lost the graphics driver somehow I ran: 

# sudo apt-get update 
# sudo apt-get remove --purge nvidia-*

... and was given this as an error message: 

```

Do you want to continue [Y/n]? 
Setting up initscripts (2.88dsf-13.10ubuntu11.1) ...
update-rc.d: /etc/init.d/ondemand: file does not exist
dpkg: error processing initscripts (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initscripts
E: Sub-process /usr/bin/dpkg returned an error code (1)
ogp@desktop:~$ 

```

From memory, this looks like the error that I was given yesterday when I updated the machine, so I suspect it is relevant. I have subsequently tried to re-install nvidia, using: 

# sudo apt-get install nvidia-current

... and had this set of error messages again: 

```

Setting up initscripts (2.88dsf-13.10ubuntu11.1) ...
update-rc.d: /etc/init.d/ondemand: file does not exist
dpkg: error processing initscripts (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of resolvconf:
 resolvconf depends on initscripts (>= 2.88dsf-13.10); however:
  Package initscripts is not configured yet.
dpkg: error processing resolvconf (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 initscripts
 resolvconf
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

To my eyes (and I am no more than a beginner!) this looks like it is failing to run initiscripts as it isn't configured, and it is looking for a file (/etc/init.d/ondemand) which doesn't exist. This file is to do with the clock speed of the CPU, which I know I changed many months ago but has worked fine since then. 

Is all this relevant to the fact that my machine won't now run a graphical shell? If not, what can I do to get that graphical shell back? 

Thanks, in advance, for any help. 


Oli.

---

### Post by zcacogp on 2012-08-22
OK, all now OK. Solved by copying the /etc/init.d/ondemand file from another machine into the relevant place and then re-running update and upgrade. This solved the errors and everything updated correctly. (Interestingly, another machine lost this file as well - I suspect that some update routine somewhere causes this file to be deleted and hence this problem.) 

The issue with the screen drivers was that they were either corrupted or removed as well. Having replaced the deleted file (as above) allowed nvidia-current to be re-installed and everything is OK. 

I've updated this thread in case anyone else struggles with the same problem. 


Oli.

---

