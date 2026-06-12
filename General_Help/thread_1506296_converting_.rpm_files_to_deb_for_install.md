---
title: "converting .rpm files to deb for install"
date: 2010-06-10
forum: General Help
---

### Post by LINUX-JJ on 2010-06-10
I have heard that tclient v2 is much better than the one that comes with ubuntu or even remmina and have found a rpm package for it.

I search and found I should use alien to convert to a deb so I can install; I am getting the following error :-


sudo alien -k tsclient-2.0.2-1.fc11.src.rpm
error: incorrect format: unknown tag
mkdir: cannot create directory `tsclient-2.0.2': File exists
nable to mkdir tsclient-2.0.2:  at /usr/share/perl5/Alien/Package.pm line 257.

I am running alien from the directory where the .rpm file is and while the extraction is done the creation of a deb file is not.

I am also running it as sudo user.

Any help ?

---

### Post by Mark Phelps on 2010-06-10
Don't know about your specific problem but I have found that, in general, using alien does not work well.  I ran across cases where the libraries needed had different names in the .deb system than in the .rpm system -- and alien was unable to make those changes.

It's generally a LOT better, if you can't find a .deb, to download the source and build the executable.

---

### Post by elliotn on 2010-06-10
Well alien worked for me before

---

### Post by LINUX-JJ on 2010-06-10
ok, thanks for the replies i am historically windows man and novice at linux; assuming the source files are what it extracted - but how on earth do i build an executable ?

---

### Post by ba_saish on 2010-06-11
if you have the source files try the following. 
Open a  terminnal, change directory (cd) into the folder that has the source code and run the following commands one by one. 

1. ./configure 
2. make
3. make install 

if these three run with out errors, you should have an executable at the end it.

---

### Post by ba_saish on 2010-06-11
if you have the source files try the following. 
Open a  terminnal, change directory (cd) into the folder that has the source code and run the following commands one by one. 

1. ./configure 
2. make
3. make install 

if these three run with out errors, you should have an executable at the end it.

---

