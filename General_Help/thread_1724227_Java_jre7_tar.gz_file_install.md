---
title: "Java jre7 tar.gz file install?"
date: 2011-04-08
forum: General Help
---

### Post by neokyle on 2011-04-08
I downloaded the jre tar.gz file unzipped it i have a directory now what? Im helpless and clueless as to how to install this.

---

### Post by neokyle on 2011-04-08
I tried installing the java file in the bin folder and when i do java -version i get this.


java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory

Please someone help me :(

---

### Post by seawolf167 on 2011-04-08
See if there is a "README" file in the archive - if so, follow the listed files for how to install the package.

In general, you install tar.gz files with the following commands

```
tar xzvf *nameofzipfile*
cd [I]nameofzipfile
[/I]./configure
make
sudo make install
```

Is there any particular reason you don't want to install java from the repos?

---

### Post by oldos2er on 2011-04-08
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by el_gallo_azul on 2012-06-05
The Google link provided by oldos2er was just what I needed. Thank you.

---

