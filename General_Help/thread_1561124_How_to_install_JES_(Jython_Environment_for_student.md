---
title: "How to install JES (Jython Environment for students)"
date: 2010-08-25
forum: General Help
---

### Post by w1ll1am on 2010-08-25
Hello I have Ubuntu 10.04 and i am taking a programming class and I can not figure out how to get this to work.

I downloaded JES from [http://code.google.com/p/mediacomp-jes/](http://code.google.com/p/mediacomp-jes/) for linux and I do not know what to do from there I has to be compiled i guess but i do not know how to do that can anyone help please.

---

### Post by GregBrannon on 2010-08-25
Is there a readme file in the archive you downloaded?  If so, what does it say to do?

---

### Post by w1ll1am on 2010-08-26
I have done everything I installed JRE (java runtime environment) and all of its associated packages
 
 
sudo apt-get sun-java6-jre sun-java6-plugin sun-java6-fonts 
 
I have the JES unzipped in my home directory and when I go into that directory from the terminal I have to run 
 
./JES.sh
 
I do this and the program comes up to load and then goes away with this error message
 
Cannot access JESConfig file,JESConfig.txt
java.io.FileNotFoundException: /home/william/JESConfig.txt (no such file or directory)
 
Traceback (innermost last):
   File "source/JESProgram.py", line 19, in ?
   File "/home/willaim/jes-4-3-nojava/Source/JESLogBuffer.py", line 14, in ?
AttributeError: java package 'java.lang' has no attribute 'AbstractStringBuilder'

---

### Post by w1ll1am on 2010-08-26
Okay I got it to work now I had to install all kinds of java stuff from synaptic I know have 
 
javacc
sun-java6-bin
sun-java6-jre
sun-java6-plugin
sun-java6-fonts
java-common
jython
openjdk-6-jre
jython-gcj
 
There are alot more packages that get installed to make these work but if these are selected then the others will be automaticlly selected also
 
 
Now I have JES files in /usr/bin/jython/jes-4-3-nojava I want to be able to make a launcher for the JES.sh file located in that folder but everytime i try nothing happens i tried the following
 
application and application in terminal
 
sh /usr/bin/jython/jes-4-3-nojava/JES.sh
/usr/bin/jython/jes-4-3-nojava/JES.sh
 
I also tried to move everything into my home folder still the same thing anythoughts

---

