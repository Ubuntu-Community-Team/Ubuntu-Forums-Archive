---
title: "how to install ndswrapper without internet"
date: 2009-10-29
forum: General Help
---

### Post by nathang1392 on 2009-10-29
my friend has an hp mini and no way to get to the internet. how can he install without the internet? and um, dont really know how to compile from source. if you suggest that, include instructions.

---

### Post by nathang1392 on 2009-10-29
also i have a working laptop and a jump drive so if there is anything i can do with that please let me know.

---

### Post by dvlchd3 on 2009-10-29
Download source:

[http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)

copy onto flash drive, copy into Ubuntu home directory

```

tar zxvf ndiswrapper-1.55.tar.gz
cd ndiswrapper-1.55
./configure
make
make install

```

ndiswrapper is now installed.

---

### Post by nathang1392 on 2009-10-29
i got all the way to make install and then i got make:*** [install] error 2

---

### Post by starcannon on 2009-10-29
ndiswrapper is available on the CD if I remember correctly. 
Insert CD, make sure the CD is available as a repo in System>Administration>Software Sources
Then start System>Administration>Synaptic package manager, search for ndiswrapper, install, and it should grab all its dependencies from the CD as well. You will also need the windows inf file to finish making his network device available. 

GL and HF

---

### Post by nathang1392 on 2009-10-29
> **starcannon said:**
> ndiswrapper is available on the CD if I remember correctly. 
Insert CD, make sure the CD is available as a repo in System>Administration>Software Sources
Then start System>Administration>Synaptic package manager, search for ndiswrapper, install, and it should grab all its dependencies from the CD as well. You will also need the windows inf file to finish making his network device available. 

GL and HF

mini has no cd drive. (netbook)

---

