---
title: "Ls (and other) problems"
date: 2009-09-09
forum: General Help
---

### Post by bbubble62 on 2009-09-09
Hi,

Since today I cannot run LS anymore on my ubuntu server, it reports :

   -bash: /bin/ls: No such file or directory

Same for ps, netsat, du and others, strange thing is that the group and owner changed (from root to 1107):

   -rwxr-xr-x 1 1107 1107  57896 2007-12-13 11:55 netstat

Any idea of what can have happened ??

-ben

---

### Post by Tsega on 2009-09-09
Hi I kinda have the a similar problem but yours looks quite fixable, I think there is a good suggestion here. 

[http://ubuntuforums.org/showthread.php?t=1248286&page=2#14](http://ubuntuforums.org/showthread.php?t=1248286&page=2#14)

There reason I really don't have a clue, my problem started when I wanted to add java environment variables.

---

### Post by bbubble62 on 2009-09-10
I do not believe this works, meanwhile I checked other commands and I found about 10 :
[INDENT]xc
du
find
killall
pstree
top
vdir
whereis
tcpd
libkrb4.so.2.0
[/INDENT]They all changed owner and group to 1107 (was root), this happened overnight.

I changed ls back to root / root, changed directory to /bin but still ls doesn't run, it always returns **-bash: /bin/ls: No such file or directory**

The install is a plain ubuntu 64 bit installation with vmware (two appliances running), has been running for 6 weeks without problems !

Any other ideas ?

:(

---

