---
title: "the annoying subprocess installed post-installation script returned error exit status"
date: 2011-01-07
forum: General Help
---

### Post by sysabod on 2011-01-07
[FONT=Times New Roman][SIZE=2]Hi all;
[/SIZE][/FONT][SIZE=2]       every time i tried to install,update,upgrade or anything related to apt-get, it keeps saying this:
[/SIZE]
```

update-alternatives: unknown argument `--quiet' 
 
Usage: update-alternatives --install <link> <name> <path> <priority> 
       update-alternatives --remove <name> <path> 
       update-alternatives --help 
<link> is the link pointing to the provided path (ie. /usr/bin/foo). 
<name> is the name in /usr/lib/opkg/alternatives/alternatives (ie. foo) 
<path> is the name referred to (ie. /usr/bin/foo-extra-spiffy) 
<priority> is an integer; options with higher numbers are chosen. 
 
dpkg: error processing fastjar (--remove): 
 subprocess installed pre-removal script returned error exit status 2 
update-alternatives: unknown argument `--quiet' 
 
Usage: update-alternatives --install <link> <name> <path> <priority> 
       update-alternatives --remove <name> <path> 
       update-alternatives --help 
<link> is the link pointing to the provided path (ie. /usr/bin/foo). 
<name> is the name in /usr/lib/opkg/alternatives/alternatives (ie. foo) 
<path> is the name referred to (ie. /usr/bin/foo-extra-spiffy) 
<priority> is an integer; options with higher numbers are chosen. 
 
dpkg: error while cleaning up: 
 subprocess installed post-installation script returned error exit status 2 
Errors were encountered while processing: 
 fastjar

```[SIZE=2]i did tried to remove fastjar package from ubuntu software center,but same error output, it is gonna drive me crazy.
I guess it is due to some power failure when i first installed the fastjar package and the apt database just marked it some evil symbol,whatsoever.

Well, there has got to be some people meet the same situation as me,how you guys fix it ? :popcorn:

Any thoughts on this :confused:? Thanks in advance![/SIZE]

---

### Post by untill on 2011-01-12
Same problem here.

---

