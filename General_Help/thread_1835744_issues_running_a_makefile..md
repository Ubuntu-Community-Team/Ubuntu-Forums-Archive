---
title: "issues running a makefile."
date: 2011-08-29
forum: General Help
---

### Post by dzee206 on 2011-08-29
im trying to run a makefile in order to give my phone an update it was never meant to get, [http://nuttybunny.wordpress.com/2011/05/22/this-is-it-webos-2-1-on-your-pixi-plus-gsm/](http://nuttybunny.wordpress.com/2011/05/22/this-is-it-webos-2-1-on-your-pixi-plus-gsm/)     <this is what im aiming for.

i tried doing this for several days now with no luck . this is as far as i can get.

********@ubuntu:~$ ls pixi
downloads  e4014e63a755ac02a63478047ad21d7e.tgz  fixi.tgz  Makefile
***********@ubuntu:~$ makeinstall
makeinstall: command not found
************@ubuntu:~$ ls pixi
downloads  e4014e63a755ac02a63478047ad21d7e.tgz  fixi.tgz  Makefile
**********@ubuntu:~$ make install
make: *** No rule to make target `install'.  Stop.
jennysoeung@ubuntu:~$ 

what am i doing wrong here?

---

### Post by searchfgold6789 on 2011-08-29
Usually you have to run 'make' before 'make install' (or 'sudo make install'). Also, you may have to run ./configure before that, but it doesn't look like it's required here. I'm surprised that the webpage didn't include 'make' in the instructions...

---

### Post by dzee206 on 2011-08-29
> **searchfgold6789 said:**
> Usually you have to run 'make' before 'make install' (or 'sudo make install'). Also, you may have to run ./configure before that, but it doesn't look like it's required here. I'm surprised that the webpage didn't include 'make' in the instructions...

do i need to install a package in order for make to work or something? ive gone over the directions almost 100 times on the site i linked but it still wont work, from how the directions are this process should of been a breeze.

---

### Post by searchfgold6789 on 2011-08-29
When you are trying to compile programs from source, which you are, it helps to install the package 'build-essential', but your real problem here might be that you have to run ```
make
``` before you run ```
make install
```Also, make sure the device is actually mounted.

---

### Post by dzee206 on 2011-08-29
> **searchfgold6789 said:**
> When you are trying to compile programs from source, which you are, it helps to install the package 'build-essential', but your real problem here might be that you have to run ```
make
``` before you run ```
make install
```Also, make sure the device is actually mounted.

thanks for the quick replies i think i got it now. what i was doing wrong was instead of doing "ls pixi" i did 'cd pixi" then make finally ran the makefile i wanted. i just hope this really works.

---

