---
title: "alternative compiler installation"
date: 2011-05-17
forum: General Help
---

### Post by cementtruck on 2011-05-17
Hello forum,

Could you help me to install an outdated compiler?  I am attempting to   use gcc 4.0.0.  I'm currently using ubuntu with gcc 4.5.2.  

Here is my most recent attempt:
1.  How do install the compiler?  (see below for details of other methods I couldn't get to work.)

...downloaded "[gcc-4.0.0.tar.bz2]("http://mirrors-us.seosue.com/gcc/releases/gcc-4.0.0/gcc-4.0.0.tar.bz2")" from GNU mirror @ 
[http://mirrors-us.seosue.com/gcc/releases/gcc-4.0.0/](http://mirrors-us.seosue.com/gcc/releases/gcc-4.0.0/)
...cannot get to install, likely overlooking one of many technical things I don't understand on installation


Thanks for your hep!


Details of failed attempts for step 1.
... terminal command "sudo apt-get install gcc" yields
 "Reading package lists... Done
 Building dependency tree       
 Reading state information... Done
 E: Unable to locate package gcc-4.0
 E: Couldn't find any package by regex 'gcc-4.0"
 
 ... in synaptic search "gcc-4.0" --> no results

---

### Post by potat on 2011-05-17
You've downloaded the source code; now you need to compile it.
Move the file to a new folder. Open up terminal and cd to that folder.

```
sudo apt-get install build-essential
```
will give you all the tools you need to compile.

Untar the file.
```
tar -xjvf gcc-4.0.0.tar.bz2
```

go into the INSTALL folder
```
cd gcc-4.0.0/INSTALL
```
All of the compiling, building, installing intstructions are there, in HTML format.

---

### Post by cementtruck on 2011-05-18
Thank you for the suggestion.  On the third round of the routine below I decided to install an older version of ubuntu instead of attempting to roll back the compiler:

while(1){
compiler install error
search internet for bug fix
implement bug fix
}

---

