---
title: "Lucid/ATI memory leak, a problem with GLX 1.4  ????"
date: 2010-07-25
forum: General Help
---

### Post by WhatTheHell? on 2010-07-25
(my speech, or actions will have "**>>>**" indicator)

Ubuntu 10.04.1 LTS

**>>>**This is what's going on.  ram usage will get really high like this:

top - 20:19:35 up  2:52,  3 users,  load average: 1.94, 2.23, 2.22
Tasks: 187 total,   4 running, 183 sleeping,   0 stopped,   0 zombie
Cpu(s): 68.7%us, 10.3%sy,  0.0%ni, 21.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
_Mem:   4124600k total,  3980068k used,   144532k free,   191228k buffers_
Swap: 10586792k total,     8292k used, 10578500k free,   838184k cached

**>>>** then get bumped back down to 2.5ish gb and go back up again

top - 20:37:00 up  3:10,  4 users,  load average: 2.70, 2.43, 2.31
Tasks: 185 total,   3 running, 182 sleeping,   0 stopped,   0 zombie
Cpu(s): 71.9%us,  9.8%sy,  0.0%ni, 18.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
_Mem:   4124600k total,  2825632k used,  1298968k free,   131932k buffers_
Swap: 10586792k total,     8684k used, 10578108k free,   653772k cached

*******************
**>>>**[http://ubuntuforums.org/showthread.p...ht=memory+leak]("http://ubuntuforums.org/showthread.php?t=1460215&highlight=memory+leak")
**>>>**Then tried installing htop and running it and got

bash: alias: }`: not found
razux@razux-core:~$ sudo apt-get install htop
...
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
razux@razux-core:~$

**>>>**htop failed to instal
*********

**>>>**Cannot remove fglrx
************
**>>>**I have this?  [https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)

**>>>**Trying glxinfo | grep "GLX version"

razux@razux-core:~$ glxinfo | grep "GLX version"
GLX version: 1.4

**>>>**trying to revert
razux@razux-core:~$ sudo apt-get install ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ppa-purge
razux@razux-core:~$ sudo ppa-purge ppa:ubuntu-x-swat/x-updates
sudo: ppa-purge: command not found
razux@razux-core:~$ 

**>>>**trying 
**>>>**sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
**>>>**sudo apt-get update
**>>>**sudo apt-get dist-upgrade


********************************
>>>reboot, running in low graphics mode, the display drives aren't working or removed.

**>>>**stable?  waiting 15+ min

top - 20:43:35 up 3 min,  2 users,  load average: 0.26, 0.49, 0.24
Tasks: 186 total,   1 running, 185 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.5%us,  4.3%sy,  0.2%ni, 86.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4124600k total,   [COLOR=DarkRed]611032k used[/COLOR],  3513568k free,    69756k buffers
Swap: 10586792k total,        0k used, 10586792k free,   269080k cached
  

**>>>**after 10 min = stable

top - 21:11:11 up 31 min,  2 users,  load average: 0.00, 0.02, 0.05
Tasks: 166 total,   1 running, 165 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.2%us,  0.2%sy,  0.0%ni, 99.5%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   4124600k total,  [COLOR=DarkRed] 605996k used[/COLOR],  3518604k free,    70136k buffers
Swap: 10586792k total,        0k used, 10586792k free,   269092k cached
**>>>**(decrease)
************
**>>>**reinstalling   
**>>>**sudo apt-get install ppa-purge
**>>>**and
**>>>**sudo ppa-purge ppa:ubuntu-x-swat/x-updates


"...Unpacking replacement fglrx ..."

**>>>**980764k used

**>>>**REBOOT
*************

top - 21:20:19 up 1 min,  2 users,  load average: 2.35, 0.84, 0.30
Tasks: 186 total,   1 running, 185 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.9%us,  4.4%sy,  0.1%ni, 30.5%id, 55.8%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   4124600k total,   _754796k used_,  3369804k free,    60992k buffers
Swap: 10586792k total,        0k used, 10586792k free,   285296k cached

**>>>**after 14 min increase by 90ish mb

top - 21:34:52 up 15 min,  2 users,  load average: 0.03, 0.10, 0.15
Tasks: 165 total,   2 running, 163 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.0%us,  0.8%sy,  0.0%ni, 98.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4124600k total,  _ 839008k used,_  3285592k free,    69908k buffers
Swap: 10586792k total,        0k used, 10586792k free,   315368k cached



razux@razux-core:~$ glxinfo | grep "GLX version"
GLX version: 1.4
**>>>**DAMNIT!  wtf?

top - 22:10:40 up 51 min,  2 users,  load average: 2.05, 1.92, 1.77
Tasks: 170 total,   2 running, 168 sleeping,   0 stopped,   0 zombie
Cpu(s): 71.0%us,  2.5%sy,  0.0%ni, 26.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4124600k total, _ 2703304k used,_  1421296k free,    86920k buffers
Swap: 10586792k total,        0k used, 10586792k free,   543716k cached

****************

**>>>**[https://bugs.launchpad.net/ubuntu/+s...er/+bug/565981]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/565981")
**>>>**ok,.... supposedly this bug is fixed

**>>>**...help?

---

### Post by WhatTheHell? on 2010-07-25
Wow, 12 hours and not a single reply....   So no one has any idea?

---

