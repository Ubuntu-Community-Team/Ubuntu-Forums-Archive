---
title: "Problem on LFS"
date: 2010-03-25
forum: General Help
---

### Post by RFS on 2010-03-25
Hey, 
I a big linux-geek and i'm working on a Linux From Scratch v6.6

I'm in the chapter 6.4 already, and i have a problem, i can't enter to the chroot environment and this is the problem below :
> 
]# chroot "$LFS" /tools/bin/env -i \
>     HOME=/root TERM="$TERM" PS1='\u:\w\$ ' \
>     PATH=/bin:/usr/bin:/sbin:/usr/sbin:/tools/bin \
>     /tools/bin/bash --login +h
chroot: cannot run command `/tools/bin/env': No such file or directoryCan anyone of you give me some help please ?
Thx

---

