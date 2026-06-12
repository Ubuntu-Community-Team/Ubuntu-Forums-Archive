---
title: "NCVIEW: missing shared library libnetcdf.so.3"
date: 2010-04-14
forum: General Help
---

### Post by ggrossi on 2010-04-14
I have installed ubuntu 9.1 (karmic koala), 64 bit, with all recent updates, but I have been using Ubuntu only since a few months ago so I do not have much experience on Ubuntu installation problems. 
I need to use the netcdf libraries which should be correctly installed ( the ncdump command ouptut states that netcdf library version "3.6.2" is installed). 
When I try to use ncview I get the following answer:

ncview: error while loading shared libraries: libnetcdf.so.3: cannot open shared object file: No such file or directory

Actually in /usr/lib64 I have found libnetcdf.so.4 but not the one ncview is apparently looking for.
Do you have any suggetions?
Thank you

Giovanna

---

### Post by treerink on 2011-02-26
I had the same. In my case the following went wrong: I had an somewhere else compiled ncview copy in my personal ~/bin/ ,but note ncview can be installed from the Synaptic Package Manager (with much later versions of libnetcdf.so.*). So the solution is: remove the ncview in ~/bin/ and use the one installed with the Synaptic Package Manager.

---

