---
title: "How to Compile ?"
date: 2006-06-27
forum: General Help
---

### Post by ThaDoctor99 on 2006-06-27
Hi, I wandered if any you would like to share some info with me on how to compile...


Greetings Tobias

---

### Post by Gustav on 2006-06-27
That depends on what you want to compile.

If it's a standard source tarball (end with .tar.gz, .tgz or tar.bz), doing it like this might work:

1. extract the file:```
tar xvfz <filename>.tar.gz
```
(If it's tar.gz or tgz do it like this, if it's tar.bz use 'xvfj' instead of 'xvfz')

2. go to the new directory:```
cd <filename>
```

3. prepare the compilation:```
./configure
```(here it may tell you that it need some libraries, install them via synaptic)

4. compile:```
make
```

5. install the program:```
sudo checkinstall
```

You must have the package build-essentials for this to work. If it isn't installed install it via synaptic or apt-get

---

### Post by ThaDoctor99 on 2006-06-27
If i want to install php on my computer ?
Which format will be best to download and install in this way ?
The tar.gz format ?

---

### Post by Ramses de Norre on 2006-06-27
Why don't you use the version from the repo's?
If you really want to compile I'd take the .tar.bz2 version if available (basically the same as the .tar.gz but a little stronger comprimated) otherwise the .tar.gz.

---

### Post by ThaDoctor99 on 2006-06-27
I have tried to make it work several times, but it seems it never really want to work, and never as I want it to.
Somebody can help me from the gruond and then forwood ?

---

### Post by Ramses de Norre on 2006-06-27
Download the .tar.bz2 and run tar -xjf file.tar.bz2 (substitute the j with a z if it's .gz).
That will create a folder named to the application with the source inside, go to that directory (cd directory_name).
Read the README and INSTALL files for any special things on compiling (probably not).
Run ./configure and check the output carefully, there shouldn't be any errors or missing components (install those components otherwise)
Run make
install checkinstall
Run sudo checkinstall
Finished =)

---

### Post by ThaDoctor99 on 2006-06-28
I would like to ask all of you have to compile a Pascal compiler on a linux system as I really would like to study the Pascal language, all the help I have got this far have been helpful, and also the nice website [www.linuxsurvival.com](www.linuxsurvival.com) have been of great help, at least to learn to basic syntax of the shell...
PLease help me with this.


Greetings Tobias

---

### Post by thasheep on 2006-06-28
gpc (GNU Pascal Compiler) is in the repos - you won't need to compile it.
```
sudo apt-get install gpc
```

---

### Post by ThaDoctor99 on 2006-06-28
I think in fact i got that one installed, just that I dont know the pathname :-/

---

### Post by thasheep on 2006-06-28
I'm pretty sure gpc adds pascal support to gcc (GNU compiler collection). I've never used pascal but i'd try (after 'apt get install gpc')
```
gcc -o myfile myfile.pas
```

---

### Post by ThaDoctor99 on 2006-06-29
I have a free compiler on my windows system which I could also download and compile to my linux system, I only need to learn to compile then, also I need to compile to get php to work I think.
I found linuxsurvival.com but they do not have support for that I think.


Greetings Tobias

---

### Post by ThaDoctor99 on 2006-06-29
I have now installed the Free Pascal compiler on my system, but ofcause I cant find it.
It should be installed - i think - under /usr but it seems not to be there.
Anybody can help me ?

---

