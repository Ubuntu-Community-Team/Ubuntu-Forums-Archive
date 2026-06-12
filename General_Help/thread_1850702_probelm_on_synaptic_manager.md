---
title: "probelm on synaptic manager"
date: 2011-09-27
forum: General Help
---

### Post by yogie.pratama on 2011-09-27
hei, i`m a newbie on Ubuntu. i just installed the 11.04 and i got trouble when launch the synaptic manager and i got this message:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

i also have problem on accessing ubuntu software center bacause of proxy problem.

Reaaly need your help!:confused:

Thxb4.

---

### Post by garvinrick4 on 2011-09-27
Open a terminal and copy and paste these one at a time.

```
sudo rm /var/lib/apt/lists/* -vf 
```
```
sudo apt-get clean all 
```
```
sudo apt-get update
```

---

### Post by yogie.pratama on 2011-09-27
Wow, It`s really helpful. now i can open the synaptic manager again. 
Thx A Lot Sir!

---

### Post by garvinrick4 on 2011-09-27
Good and welcome to the Forums, enjoy your Ubuntu Linux yogie.pratama. We have a Yogie here
in the States also with a friend named BooBoo. He likes Picanic baskets and is known to hang around
JellyStone park. 
 You come in and ask all the questions you need to yogie.pratama there are a lot of nice users hang
around the halls of these Forums.

---

