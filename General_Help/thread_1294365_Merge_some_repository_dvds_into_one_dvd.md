---
title: "Merge some repository dvds into one dvd"
date: 2009-10-18
forum: General Help
---

### Post by sadeghi on 2009-10-18
Hello
I can not access internet at work for some reasons and i have downloaded 5 ubuntu repositories. now i have problems using them because i have no dvd-rom available.

I have 5 dvd iso, i can mount them using -o loop option and them i import them into synaptic, but each time synaptic asks me to insert the disk and though i have to mount the iso image again in the /media/cdrom mount point.

anyway, i want to merge my 5 dvd into 1 dvd so everytime that synaptics asks me for disk i can insert(mount) only 1 dvd and it can download all the packages with their dependencies. i read some instruction about how to make my own repositories and i think using them i can copy the contents of dvds somewhere and them make them into a one big directory that synaptics can accept them.

i fount this command useful, but i dont know how to use it to make a big repository from all my dvds, here is it:

dpkg-scanpackages binary /dev/null | gzip -9c > binary/Packages.gz

the link for above instruction is:
[http://mediakey.dk/~cc/howto-create-your-own-debian-or-ubuntu-package-repository/](http://mediakey.dk/~cc/howto-create-your-own-debian-or-ubuntu-package-repository/)
(the link buttion doesnt work for me);

thans in advance for any help

---

