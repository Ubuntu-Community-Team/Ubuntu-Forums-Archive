---
title: "Need some help with first Kernel Patch"
date: 2011-03-09
forum: General Help
---

### Post by 31632531 on 2011-03-09
Hello;

Trying to install [http://goo.gl/nPPnt](http://goo.gl/nPPnt) to add Mbox2 functionality to my computer (so I can finally get rid of osX all together) but I keep running into this error;

```
$:~/Downloads/mbox2-kernel$ make
make -C /lib/modules/2.6.35-28-generic/build M=/home/[user]/Downloads/mbox2-kernel modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/jason/Downloads/mbox2-kernel/card.o
/home/[user]/Downloads/mbox2-kernel/card.c: In function &#8216;snd_usb_create_streams&#8217;:
/home/[user]/Downloads/mbox2-kernel/card.c:227: error: dereferencing pointer to incomplete type
/home/[user]/Downloads/mbox2-kernel/card.c:232: error: dereferencing pointer to incomplete type
/home/[user]/Downloads/mbox2-kernel/card.c:232: error: dereferencing pointer to incomplete type
/home/[user]/Downloads/mbox2-kernel/card.c:232: error: dereferencing pointer to incomplete type
/home/[user]/Downloads/mbox2-kernel/card.c:237: error: dereferencing pointer to incomplete type
/home/[user]/Downloads/mbox2-kernel/card.c:238: error: dereferencing pointer to incomplete type
make[2]: *** [/home/[user]/Downloads/mbox2-kernel/card.o] Error 1
make[1]: *** [_module_/home/[user]/Downloads/mbox2-kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [all] Error 2

```

or this with sudo

```
$:~/Downloads/mbox2-kernel$ sudo make
make -C /lib/modules/2.6.35-28-generic/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [all] Error 2

```I've installed headers ...I'm not sure where to go from here?

Thanks in advance for any help.

---

### Post by mswamy78 on 2011-08-02
Hello,
Were you able to fix it? I am facing the same issue...Please let me know if you have any solution.
Thanks.

---

### Post by 31632531 on 2011-08-14
No I haven't.  Sorry.

---

### Post by sbraz on 2011-08-14
here it compiles just fine.

sounds like you need to install some dev packages first... i don't know which one(s)... i have TONS installed.

i have very little knowledge about these things, normally there's an "INSTALL" file which hints the required packages you have to install, but in this case there's nothing. [-X [-X [-X

by instinct i'd do this:
```
sudo apt-get install build-essential
```
then retry compiling.

---

### Post by sbraz on 2011-08-14
you also need a kernel 2.6.37+.

could you both post the output of this command?
```
uname -r
```

---

### Post by 31632531 on 2011-09-15
2.6.38-11-generic

---

