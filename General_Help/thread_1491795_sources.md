---
title: "sources"
date: 2010-05-24
forum: General Help
---

### Post by AllanP on 2010-05-24
Can somebody explain the difference in /etc/apt/sources.list and /var/lib/apt/lists?
I installed Picasa and did this:
wget [https://dl-ssl.google.com/linux/google-repo-setup.sh](https://dl-ssl.google.com/linux/google-repo-setup.sh)
bash google-repo-setup.sh

Why not add to sources.list
# Google repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

# Google testing repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free

???

---

### Post by spikoley on 2010-05-24
Somebody else will have to explain the difference between /etc/apt/sources.list and /var/lib/apt/lists.

Yes, you can add it manually to /etc/apt/sources.list.  I personally always do it that way.  It sounds like that script does it for you.  After updating sources.list you need to run *sudo apt-get update*.

---

### Post by plucky on 2010-05-24
> /etc/apt/sources.list

Tells dpkg where to find the repositories

> /var/lib/apt/lists

Contains the list of installed applications for each repository.(I think)

> Why not add to sources.list

You could do but as a third party repository it is probably located in /etc/apt/sources.list.d/ as is the Medibuntu repository.

Try ```
ls -l /etc/apt/sources.list.d/
``` and see what is located there. 

Good Luck

---

