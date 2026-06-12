---
title: "ati graphic and problem"
date: 2011-11-13
forum: General Help
---

### Post by robocap on 2011-11-13
Hello

i installed ubuntu 11.10 64bit on my laptop.

also i download installer for radeon ati graphic of amd website.and install it.

then i reboot.
but my laptop have problem with several application now.

error :
error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

but this was not before install amd graphic.

```
lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M]

```


how may i solve it?
why run command lspci | grep VGA  ,display 2 graphic for me?

thanks

---

### Post by robocap on 2011-11-13
Hello

i could solve it by remove ati drivers on this ubuntu.

but how i install my graphic card without problem?

---

### Post by gandaran on 2011-11-13
> **robocap said:**
> Hello

i could solve it by remove ati drivers on this ubuntu.

but how i install my graphic card without problem?

Ati drivers are buggy on ubuntu 11.10, use the default installed  open source drivers instead, they should work okay.

---

### Post by robocap on 2011-11-13
how may i understand that graphic card is installed true or not?

thanks

---

### Post by gandaran on 2011-11-14
> **robocap said:**
> how may i understand that graphic card is installed true or not?

thanks
when you installed ubuntu did you have any problem with graphics?
if everything was working okay then you don't have to install drivers, just continue using ubuntu as it will use the open source video drivers.

---

### Post by wowcolombia1 on 2011-11-14
Hello there,i think Ubuntu comes with all the drivers you need :D,so if i was you i didnt play with the drivers.
Hope this helped
-Oswald Luis

---

### Post by Mark Phelps on 2011-11-14
> **wowcolombia1 said:**
> Hello there,i think Ubuntu comes with all the drivers you need :D,so if i was you i didnt play with the drivers.
Hope this helped
-Oswald Luis

Did you even bother reading what the OP said? 

He said he ALREADY installed the drivers. Telling him now NOT to do that is not of any help.

---

