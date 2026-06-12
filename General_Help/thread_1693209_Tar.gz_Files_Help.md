---
title: "Tar.gz Files Help"
date: 2011-02-22
forum: General Help
---

### Post by Noble720 on 2011-02-22
So, I'm pretty new to Ubuntu. I know all the software center and I already installed Audacity but now I'm trying to download the VST enabler for it. It comes as a tar.gz file and I have absolutely no idea how to install it. Any step by step help would be appreciated.

---

### Post by seawolf167 on 2011-02-22
Welcome to the forums!

Open a terminal, Applications -> Accessories -> Terminal

browse to the file location

```
cd /location/of/filename.tar.gz
```

the default firefox location is

```
cd ~/Downloads
```

extract the file

```
tar xvf filename.tar.gz
```cd to the created directory

```
cd filename/
```install the package

```
./configure
make
sudo make install
```

---

### Post by Diametric on 2011-02-22
Would there be any dependency issues with that method?  I'm still new too and am wondering if aptitude or nautilus should be used to make sure.  Just askin...

Cheers.

---

### Post by Noble720 on 2011-02-22
When I tried to extract the file I got the "Cannot connect to file: resolve failed" error message.

---

### Post by tjwoosta on 2011-02-22
Yes, there may be dependency requirements depending on the software your trying to compile. I have no experience with this particular software so that would be up to you to read the documentation. Usually source files come bundled with a README file that should tell you the requirements and the prefered method of compilation 
(seawolf is correct about ./configure, make, sudo make install but its not always exactly the same depending on the software, thats just the general method)

Heres a pretty detailed guide for compiling from source in ubuntu.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)


Of course this is all assuming that the .tar.gz that you have actually contains source that needs to be compiled, .tar.gz is simply an archive format that technically could contain anything (like a .zip or .rar)


EDIT: I believe the extraction command should be 

```
tar -zxvf filename.tar.gz
```

---

### Post by asmoore82 on 2011-02-22
This may cause some issues:
[quote=http://audacityteam.org/vst/]Because of licensing issues, VST support must be kept separate from Audacity. This "VST Enabler" is mostly open-source, but the source code to Steinberg's VST SDK is required, and this must be downloaded from Steinberg separately.[/quote]
[http://audacityteam.org/vst/](http://audacityteam.org/vst/)

---

