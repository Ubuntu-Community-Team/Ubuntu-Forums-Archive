---
title: "compileing kernel 2.6.35-22-genaric with high memory enabled"
date: 2010-12-17
forum: General Help
---

### Post by leeper69 on 2010-12-17
Hi
   I am trying to compile a kernel with high memory support. I have downloaded and installed the source files and muddled my way through the directions given on  [http://blog.avirtualhome.com/2010/11/06/how-to-compile-a-ubuntu-10.10-mavric-kernel](http://blog.avirtualhome.com/2010/11/06/how-to-compile-a-ubuntu-10.10-mavric-kernel) and have made it up to the last step in the compile section create the flavour depend files when I type skipabi=true skipmodule=true fakeroot debian/rules binary.core4 in terminal I get the following error message make:*** no rule to make target 'binary.core4' stop. help if you can be gentle to me this is my first time.

Sorry the correct command is skipabi=true skipmodule=true fakeroot debian/rules binary-core4 
the - between bianry and core4 is what I was doing wrong I finally got the compile to work. and have installed  kernel 2.6.35-23-core4 in UBUNTU 10.10
next I used the root terminal to change my memory settings. 
first I changed to the /usr/src/linux-headers-2.6.35-23-core4 directory ( to change your settings change to the /usr/src directory then type ls-l this will list the directory's for your system the cd to the directory you want to change your settings in.) next type make menuconfig ( this will open a script that will open the ncursor editor where your changes to the kernel can be made. then changes for high memory can be followed from the web page [http://blog.aviryualhome.com/2010/04/17/configuration-tips-for-the-ubuntu-lucid-kernel/](http://blog.aviryualhome.com/2010/04/17/configuration-tips-for-the-ubuntu-lucid-kernel/)  GOOD LUCK! hope this helps someone fighting to compile the kernel with high memory.

---

