---
title: "loacate command help!"
date: 2010-09-19
forum: General Help
---

### Post by vinay nadig on 2010-09-19
hi, i have been using ubuntu 10.04 for a month now, one of the most useful feature that i have found is the locate command and i use it often to find my files if i have misplaced them.
one thing that i have observed is that locate command's database does not include mounted drives and other partitions in the same drive.. can any one help me with a tweak or workaround so that locate would include both mounted and other drives in its database??
Thnx in advance!! :)

---

### Post by Vaphell on 2010-09-19
look into /etc/updatedb.conf
prunepaths lists ignored dirs and by default /media is there, also prunefs ignores listed filesystems
[http://linux.die.net/man/5/updatedb.conf](http://linux.die.net/man/5/updatedb.conf)

my bet is once you modify that file according to your needs and run sudo updatedb, you'll get locate doing what you want


also you want to learn the find command - it's so powerful it's almost ridiculous :-) it's bruteforcish (doesn't have a database backup so it scans the disk when run) but it supports tons of criteria and it allows to perform an action on found objects right off the bat.

---

### Post by vinay nadig on 2010-09-19
yup!! u r right on spot! :D i took out the /media from the PRUNEPATH and the locate command works perfectly!!
Thanx a bunch for the help!! :D

and as for the find command, i don't use it much since its a bit slow. and i just started using linux last month so dunno much about commands.
thnx for the advice anyway.. :) hopefully i will learn fast.. :D
cheers!!

:guitar:

---

