---
title: "How does one Compile?"
date: 2012-06-07
forum: General Help
---

### Post by Neckrow on 2012-06-07
I got a linux driver, and my mate directed me to compile and try it as is. However I am shocked this is not a rightclick option xD Can anyone shed some light on the subject for me? Do I compile the whole folder or only the config.mk file? Thanks in advance.

-Dazed and confused

---

### Post by snowpine on 2012-06-07
Welcome to the forums!

Can you back up and tell us, what is the hardware? Where did you download the driver?

Most hardware should work "out of the box" in Ubuntu, but certain hardware may require tweaks, and we can help you best if you are specific. :)

A general guide to compiling is here: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by drmrgd on 2012-06-07
The first thing to check would be if there is an INSTALL or README text file in the folder. If so, there should be instructions on how to compile the package and what (if any) requirements there are in addition to the package you want to compile.  

If no, you'll have to fire up the terminal and compile by the command line as I don't believe there is a way to do it graphically.

---

### Post by sanderj on 2012-06-08
> **Neckrow said:**
> I got a linux driver, and my mate directed me to compile and try it as is. However I am shocked this is not a rightclick option xD Can anyone shed some light on the subject for me? Do I compile the whole folder or only the config.mk file? Thanks in advance.

-Dazed and confused

Compiling software is only a last-resort solution. Preferred / prio list:
- works out of the box
- works after activating a PPA
- works after installing a .deb
- works after installing some binary
- works after compiling

So why are you trying to do it?

Anyway, instruction for compilling:
1) unpack, and go into unpacked directory
2) "./configure"
3) "make"
4) "sudo make install"
No GUI. And: compiling your own software will often require extra libaries. Not an easy path to go. Therefor ... see above ;-)

---

### Post by oldos2er on 2012-06-08
> **Neckrow said:**
> I got a linux driver, and my mate directed me to compile and try it as is.

What driver, from where, and for what hardware? Which version of Ubuntu are you using?

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

