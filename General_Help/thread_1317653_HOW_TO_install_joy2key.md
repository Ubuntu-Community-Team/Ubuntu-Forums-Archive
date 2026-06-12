---
title: "HOW TO install joy2key"
date: 2009-11-06
forum: General Help
---

### Post by aschwerin.moses on 2009-11-06
Hi,

I have 9.10 in my system and I am trying to use my gamepad (generic).

I have to install joy2key from [http://sourceforge.net/projects/joy2key/](http://sourceforge.net/projects/joy2key/)

I am not sure how to do that. In the read me file is says

> COMPILING & INSTALLATION
------------------------
(note: for the rest of this file, commands to be typed will be denoted '$ foo', 
where foo is to be typed in at the command and run)
- edit the makefile to your satisfaction
- type '$ make', (this will build the program)
- type '$ make install' (optional, will put joy2key in /usr/local/bin and 
	the joy2key man page in /usr/local/man/man1)

I have no idea how to do this, can someone please help me out...

---

### Post by michy99 on 2009-11-06
You can install joy2key from the repository. Open a terminal and enter```
sudo apt-get install joy2key
```

---

### Post by aschwerin.moses on 2009-11-06
Yes, i already tried that.. 

sorry i did not mention this...

sudo apt-get install joy2key will install  version joy2key-1.6.1 which does not work in 9.10

have to install 1.6.3 which is not updated in the repo. So have to install it manually which I am not sure how to do.


help help...

---

### Post by aschwerin.moses on 2009-11-07
no one here to help me create a make file?.. help :(

---

### Post by michy99 on 2009-11-07
First thing is try it with the default make file. If this is your first time compiling a program from source, you probably need to install the build-essential package. Also, checkinstall is a good idea.```
sudo apt-get install build-essential checkinstall
```Then make sure you have all the header files you need to compile joy2key.```
sudo apt-get build-dep joy2key
```Make sure you are in the joy2key directory and enter```
make
```When that is finished:```
sudo checkinstall
```Just accept the defaults and it should work. If not, post any error message you get.

---

### Post by aschwerin.moses on 2009-11-09
Thanks a lot. I was able to install it.

---

### Post by picknick on 2009-12-30
> **michy99 said:**
> Make sure you are in the joy2key directory and enter```
make
```When that is finished:```
sudo checkinstall
```Just accept the defaults and it should work. If not, post any error message you get.

I got a ps pad and I wanted to try it. I followed the instructions but I'm new at this so I couldn't go through these steps. I can't find the location of the "joy2key directory".

I've xubuntu 9.10 and my usb ports work properly.

Thanks,

picknick

---

