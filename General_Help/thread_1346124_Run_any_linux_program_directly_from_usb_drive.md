---
title: "Run any linux program directly from usb drive"
date: 2009-12-04
forum: General Help
---

### Post by aCsbD6N5xj on 2009-12-04
Hi. Is there a way to run any linux program directly from usb drive?

Thx.

---

### Post by mike555 on 2009-12-04
There are a few here ...   [http://www.portools.com/](http://www.portools.com/)    ,  [http://hacktolive.org/wiki/Portable_Applications_%28Linux%29](http://hacktolive.org/wiki/Portable_Applications_%28Linux%29)

---

### Post by aCsbD6N5xj on 2009-12-04
Thx for the links but they don't have the software i need. I was thinking about running programs one would otherwise **install** on linux but directly from a usb drive, if it is ever possible. The software i have in mind is KeePassX. Then,  if i can run it portably, maybe i'll try TrueCrypt.

---

### Post by Sam on 2009-12-04
Put the .deb file(s) of your application in the USB drive. This should do the job.

---

### Post by aCsbD6N5xj on 2009-12-04
ok i'll try that. Will that also work under red hat linux? that's what they have at school *sigh*

---

### Post by aCsbD6N5xj on 2009-12-04
and where are the .deb files stored? when i dwl the installation files they come in tar.gz format

---

### Post by fluffman86 on 2009-12-04
.debs are installations files for debian based systems, not for red hat.  Even so, you pretty much need admin rights to run and install them, unless you just want to unpack them and then compile them.

Instead, I would recommend creating a source, bin, and lib folder in your thumbdrive.  Then, you can compile the source for programs manually, and set prefixes either during the ./configure or make stage, then make install it and it will store on your thumbdrive.  You then just have to be able to access the thumbdrive and run the program.  

Read more here:
[http://www.airs.com/ian/configure/configure_1.html](http://www.airs.com/ian/configure/configure_1.html)

Basically, for most linux programs:
```
wget http://www.example.com/files/source.tar.gz
tar -xvzf source.tar.gz
cd source
./configure --prefix /path/to/usb --exec-prefix /path/to/usb
make
make install
```
should do the trick.

You'll need to "sudo apt-get install build-essential" on ubuntu to get the necessary tools, first, and you may also need to play around with some of the commands.  For example, python uses:
```
./configure
make altinstall prefix=/path/to/dir exec-prefix=/path/to/dir
```
and you can usually find any nuances to the programs online.

Also, be sure to set your configure prefix paths to the root of the USB drive, and then your executables will automatically be created in /path/bin and the rest of the needed libraries will be in /path/lib

---

### Post by aCsbD6N5xj on 2009-12-07
thx for the reply. i knew nothing about that

> .debs are installations files for debian based systems, not for red hat. Even so, you pretty much need admin rights to run and install them, unless you just want to unpack them and then compile them.

2 bad it won't work at school then. that was basically why i wanted to use a few linux portable apps, like keepassX. guess i'll just stick to pcs and macs then.

---

