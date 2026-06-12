---
title: "Tried to instal gcc-4.5 messed stuff up."
date: 2011-06-09
forum: General Help
---

### Post by MoralExpl on 2011-06-09
Morning, all.

I needed gcc 4.5 for some compining things, unfortunatly I only had 4.4.4 Running 10.04. Anyway, I went over to [http://packages.ubuntu.com/maverick/gcc-4.5](http://packages.ubuntu.com/maverick/gcc-4.5) and started installing the .deb packages. I realized this will take ages, and I didn't have much time. I stopped installing the packages (only got 3 installed) and this is where things went downhill fast. I installed (dpkg -i):
gcc-4.5_4.5.3-1ubuntu2_amd64.deb
libc6_2.13-2ubuntu1_amd64.deb 
binutils_2.21.52.20110606-1ubuntu1_amd64.deb 

Now, when ever I apt-get update etc it complains about there being 6 broken packages. 

You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  binutils: Depends: libstdc++6 (>= 4.6) but 4.4.3-4ubuntu5 is installed
  libc-dev-bin: Depends: libc6 (< 2.12) but 2.13-2ubuntu1 is installed
  libc6: Depends: libc-bin (= 2.13-2ubuntu1) but 2.11.1-0ubuntu7.8 is installed
  libc6-dev: Depends: libc6 (= 2.11.1-0ubuntu7.8) but 2.13-2ubuntu1 is installed
  libc6-i386: Depends: libc6 (= 2.11.1-0ubuntu7.8) but 2.13-2ubuntu1 is installed
  libnih1: Depends: libc6 (< 2.12) but 2.13-2ubuntu1 is installed
E: Unmet dependencies. Try using -f.


So, I try running apt-get -f install, and it wants to remove nearly every application/library I have.

Full list here: [http://paste.ubuntu.com/622454/](http://paste.ubuntu.com/622454/)

What the hell did I just do, and what can I do to fix this. 

I was thinking about just upgrading to 10.10 then onto the 11 version. But it complains that some packages aren't installed correctly etc.

Thanks for your time. Let me know if you need any more info.

---

### Post by MoralExpl on 2011-06-09
bump

---

### Post by box2 on 2011-06-12
try downloading the current 10.04 versions of those .debs that you installed over and dpkg install those instead.  you could also try telling crime to shut up, works for some.

---

### Post by katykat on 2011-06-13
> **MoralExpl said:**
> Morning, all.


You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  binutils: Depends: libstdc++6 (>= 4.6) but 4.4.3-4ubuntu5 is installed
  libc-dev-bin: Depends: libc6 (< 2.12) but 2.13-2ubuntu1 is installed
  libc6: Depends: libc-bin (= 2.13-2ubuntu1) but 2.11.1-0ubuntu7.8 is installed
  libc6-dev: Depends: libc6 (= 2.11.1-0ubuntu7.8) but 2.13-2ubuntu1 is installed
  libc6-i386: Depends: libc6 (= 2.11.1-0ubuntu7.8) but 2.13-2ubuntu1 is installed
  libnih1: Depends: libc6 (< 2.12) but 2.13-2ubuntu1 is installed
E: Unmet dependencies. Try using -f.

What the hell did I just do, and what can I do to fix this. 

I was thinking about just upgrading to 10.10 then onto the 11 version. But it complains that some packages aren't installed correctly etc.

  



Ok. 

My experience with Jaunty to Meerkat, where I have applied the brakes (no crap CSS /'CLOUD' desktop for me, I'd rather go to Arch and start fresh.)

You have experienced DPKG depencey hell. 
At a certain point NOTHING, and I do mean NOTHING will stop the idiocy.
EXCEPT, and its late and my Lin machine is in Win doing file transfers the russian way (to each his need, from each his abilities...)

There are to collections of data. One I beleive is in var/dpkg somewhere and if you delete the incmplete package it will go away.  Someone on a working system SHOULD be able to point out that thile. Needs careful  editing.  


The second solution is more drastic and involves yanking the package data entirtely out of the repository data and is much more troublesome. 

Hopefully someone will be along with the exact instructions. 

After a while APT gets so tangled up it simply cannot be trusted.

---

