---
title: "rar software package ( deb) for 8.10 Intrepid ?"
date: 2011-01-21
forum: General Help
---

### Post by uncle-c on 2011-01-21
Hi,
I still use Intrepid 8.10 on one of my older machines and have tried, but in vain, to install some rar compression software from the repos. It seems as if the specified repo for 8.10 is now end of life Would anyone know of where I could download a .deb file containing an older version of rar which would install correctly on by box ? 

thanks 
uc

---

### Post by smurphy_it on 2011-01-21
sudo apt-get install unrar unrar-free

Doesn't install ?

---

### Post by Verbeck on 2011-01-21
try  [http://old-releases.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/](http://old-releases.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/)

---

### Post by uncle-c on 2011-01-21
Thanks gents but I already have unrar installed. I'm looking for software that will create a compressed rar archive.

edit : Guys I was getting this error when trying to install on command line :

```

unclec:~/Desktop$ sudo dpkg -i rar_3.8.0-2_i386.deb
dpkg: syntax error: unknown user `postfix' in statoverride file

```

A quick search on the forums revealed that /var/lib/dpkg/statoverride needed some editing. Problem sorted. Thanks all the same.

---

### Post by psusi on 2011-01-21
8.10 is obsolete and no longer supported.  You need to upgrade immediately, though you can't even do that because 9.04 is also no longer supported.  You will need to start fresh and install 10.04 or 10.10.

---

