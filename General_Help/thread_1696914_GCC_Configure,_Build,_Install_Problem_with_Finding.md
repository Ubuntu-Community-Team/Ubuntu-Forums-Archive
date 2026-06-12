---
title: "GCC Configure, Build, Install: Problem with Finding C Compiler"
date: 2011-02-28
forum: General Help
---

### Post by abedayyad on 2011-02-28
Dear All, 

In order to install and run some stats software, I needed to first install GCC. 

For reasons to with a horrible internet connection, which is common where in the country I'm in right now (Lebanon), I've had to download the compressed folder from the GNU website instead of installing the application using apt-get install. 

So I download the folders to a work computer with a slightly faster connection; I unlock the archive for GCC, and navigate to the folder using my console. All files are there, so far, so good. 

Within the folder I type ./configure and it begins to configure but comes up with the error that there is no C compiler in the $PATH. 

Have I missed something here? Am I not supposed to build GCC which then will act as a C compiler? Why would I need a C compiler in order to install a C compiler? 


   Thanks, as always, for the help,

---

### Post by oldos2er on 2011-02-28
Instead of getting software from GNU, get it from packages.ubuntu.com. You might want to look at Keryx for doing this: [http://keryxproject.org/](http://keryxproject.org/)

The build-essential package will give you gcc basics.

---

### Post by abedayyad on 2011-03-30
Hey thanks for this. I only just saw it now, but thanks!!

---

