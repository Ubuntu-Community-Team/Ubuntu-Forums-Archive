---
title: "Help with special character sorting change for things like ls"
date: 2010-11-03
forum: General Help
---

### Post by Crispy2 on 2010-11-03
Hello,

I have been running a reliable old file server at home for quite some time running debian.

Recently I've built a new system using 1/6 of the power consumption and 4 x the diskspace.  I stuck Ubuntu 10.4 LTS on the server.  

I'm no newbie to linux but during transfering my files across and using du , ls etc to monitor progress I noticed a strange behavour.

Its best explained with an example.
```
old debian server:
serv2:/local_mounts/wd_250/watching# ls -1
! Links
!!MOVE_TO_WATCHING
Anime
Cartoons 'n' Puppet Shows
Cooking

New ubuntu server:
root@Serv3:/mounts/local/watch/watching# ls -1
Anime
Cartoons 'n' Puppet Shows
Cooking
! Links
!!MOVE_TO_WATCHING
```

Notice that the sort ignores the "!" and the white space.
I use the "!" system to keep special folders etc at the top of the display for ease of use and I really don't like this behavour.  However I am a bit at a loss to change it (if thats even possible).  du, df, sort any general command treats the list like this.  I can't find any aliases to this affect.

I am also having trouble get a decent keyword search for google so please point me in the right direction or just put me out of my misery by telling me this is not possible.

Thanks

---

### Post by Crispy2 on 2010-11-04
*bump*

---

### Post by Crispy2 on 2010-11-05
*bump*

---

### Post by Crispy2 on 2010-11-07
*bump*

---

### Post by Lou Lou on 2010-11-17
Hi,

I had many problems with ubuntu 10.04. 
Lots of them were solved with 10.04.1
And there is a newer version available.
Please test it, it may solve your problem.

---

### Post by Crispy2 on 2010-11-20
I doubt it.  I expect this has been like this for most versions of Ubuntu.  By all means can you not create a few files and type ls ?

Its not a bug.

I have found that on the old debian box if I su or su - to root then I lose the ability (output looks like second example).  However logging with ssh in ether a user or root directly looks like first example.

As I've mentioned I've ruled out aliases.  
I've looked the environment variables and I am a bit of a lose as where to look next.

---

