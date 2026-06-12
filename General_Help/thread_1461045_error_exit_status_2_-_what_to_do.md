---
title: "error exit status 2 - what to do?"
date: 2010-04-23
forum: General Help
---

### Post by Mistril Merendras on 2010-04-23
Hi, 

I was installing SMPLAYER when the power failed...now i get this error  message when trying to re-install the packages..

E: liblzo2-2: subprocess installed post-installation script returned  error exit status 2
E: mplayer-nogui: dependency problems - leaving unconfigured
E: mplayer: dependency problems - leaving unconfigured
E: smplayer: dependency problems - leaving unconfigured

I tried to restart in safe mode and repair broken packages...this didn't  solve it.

I tried to fix broken package in Synaptic...this didn't solve it

Can anyone give me a hint what to do?

Thanks in advance!

---

### Post by Mistril Merendras on 2010-04-27
i tried this: 

[COLOR=DarkGreen]apt-get --purge remove liblzo2-2

But then i get:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  liblzo2-2 mplayer mplayer-nogui
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 9,916kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 214088 files and directories currently installed.)
Removing mplayer ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing mplayer (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing mplayer-nogui ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing mplayer-nogui (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing liblzo2-2 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing liblzo2-2 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 mplayer
 mplayer-nogui
 liblzo2-2
E: Sub-process /usr/bin/dpkg returned an error code (1)

[/COLOR]

---

### Post by Mistril Merendras on 2010-04-27
But then i did this.......

gksudo nautilus

i went to the following location: [COLOR=DarkGreen]/var/lib/dpkg/info

I moved the files with liblzo2-2 in the name to the desktop (just to be safe)

And then i ran: [/COLOR][COLOR=DarkGreen]sudo apt-get --purge remove [/COLOR][COLOR=DarkGreen]liblzo2-2

And it F****** worked!


[/COLOR]

---

### Post by NSim on 2010-04-28
Great job..... it worked for me too! Thanks A LOT!

---

