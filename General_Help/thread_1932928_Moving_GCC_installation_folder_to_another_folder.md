---
title: "Moving GCC installation folder to another folder"
date: 2012-02-28
forum: General Help
---

### Post by rbaleksandar on 2012-02-28
Hi, guys :)

  I'm using Ubuntu 10.04 LTS and just finished building and installing GCC 4.6.2. I could have easily added a repo and commit the update the easy and clean way, but decided to do it manually just for the fun of it AND to see what it take. Well, it lasted approximately 2-3 hours with around 100 000 files and more than 2GB hard disk space. :lolflag: I did a stupid mistake though. I forgot to configure it to be installed in the /usr/local as I usually do and it got installed in /home, where I unpacked the tarball along with MPC, GMP, MPFR and the ELF-library. I don't believe this should be a problem for using it but it still bothers me that I have it installed in /home. So the BIG question is - is there a way to change the installation folder of GCC ergo to copy all the files in another directory (in my case in /usr/local) and set the environment parameters of Ubuntu (lol don't know if these are called so - old Windows habbit :KS) so that it can be used without a problem? I really don't want to rebuild the whole thing and just wiping it out of my HDD will mean that all this was indeed in vain.

Thanks in advance!

---

