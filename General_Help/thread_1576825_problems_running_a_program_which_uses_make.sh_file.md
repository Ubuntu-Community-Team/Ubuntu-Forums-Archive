---
title: "problems running a program which uses make.sh file!!"
date: 2010-09-17
forum: General Help
---

### Post by ymann on 2010-09-17
I am  trying to install a program and at the point when I am required to execute the command "make clean" and then after "make all" , I obtain the following eror message:

ndoheric@nen-laptop:/opt/WAVEFORPGM/distribute$ make clean
cd ./MyTime; make clean
make[1]: Entering directory `/opt/WAVEFORPGM/distribute/MyTime'
rm -f *.o timedriver
make[1]: Leaving directory `/opt/WAVEFORPGM/distribute/MyTime'
cd ./src; make clean
make[1]: Entering directory `/opt/WAVEFORPGM/distribute/src'
rm -f core *.o plplotsyn plotgrid GridSearch4 sawm
make[1]: Leaving directory `/opt/WAVEFORPGM/distribute/src'
cd ./makegreen/src; make clean
make[1]: Entering directory `/opt/WAVEFORPGM/distribute/makegreen/src'
rm -f core *.o makegreen gbin2sac sac2gbin makedata degmin2dec makedisp
make[1]: Leaving directory `/opt/WAVEFORPGM/distribute/makegreen/src'
cd ./SAC2LINUX; make.sh clean
/bin/sh: make.sh: not found
make: *** [clean] Error 127

could someone tell me what to do????

---

### Post by amsterdamharu on 2010-09-17
What program are you trying to compile and install? Maybe it is in the repositories and can be installed with synaptic package manager.

Did you run ./configure before make? That usually tells you what's wrong with it.

---

### Post by kalos on 2010-09-17
> **ymann said:**
> 
cd ./SAC2LINUX; make.sh clean
/bin/sh: make.sh: not found
make: *** [clean] Error 127


Looks like it might be an typo in the makefile. Possibly make.sh should be make. (As far as I know, there's no standard make.sh program.

What exactly are your trying to do (what software are you trying to build)?

---

### Post by ymann on 2010-09-17
actually it is a program to process seismic data (called Waveform modeling and moment tensor inversion tool) in a package with name linux.tar.gz; and these are the instructions for installation:

gzip -d linux.tar.gz 
tar xf linux.tar
or on Solaris or SunOS gzip -d sun.tar.gz
tar xf sun.tar
 Make the executables cd ./distribution
make clean
make all

I am using a linux OS with kubuntu.

please help me find a solution.

---

### Post by amsterdamharu on 2010-09-18
It might help if we know where to download the file so we can see what exactly is going wrong.

All I could find is [http://earthquake.usgs.gov/research/software](http://earthquake.usgs.gov/research/software) but not sure what file you've got.

As said before, it might be some typo in the script.

---

