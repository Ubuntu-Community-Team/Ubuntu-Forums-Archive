---
title: "i did a bad thing can you help me fix it; its really simple im just newbie"
date: 2009-09-03
forum: General Help
---

### Post by linux000019 on 2009-09-03
i read somewhere that it was safe to delete everything in the /usr/src directory, which i did after compiling the 2.6.31-rc8 kernel myself for the first time. alright well now im trying to install wireless STA and when i get to the make part,

root@ryan-laptop:/home/ryan# make -C /lib/modules/2.6.31-rc8-git2-mk/build M=`pwd` clean
make: *** /lib/modules/2.6.31-rc8-git2-mk/build: No such file or directory. Stop.
root@ryan-laptop:/home/ryan# 


alright im PRETTY SURE; although im still learning; that this is because this operation calls for the /usr/src/ linux header directory.

so my question is, how do i reinstall the headers for the customized 2.6.31-rc8 build?

can i do a command line operation to extract the information from my system or do i repeat the compiling process all over again (please no).

---

### Post by nikhilbhardwaj on 2009-09-03
[http://www.linuxfromscratch.org/lfs/view/6.4/chapter06/linux-headers.html](http://www.linuxfromscratch.org/lfs/view/6.4/chapter06/linux-headers.html)

these are instructions for installing headers

---

### Post by linux000019 on 2009-09-03
that didn't help

---

### Post by celticbhoy on 2009-09-03
Not 100% sure, but I would try and re-install from synaptic.

---

### Post by jaxxstorm on 2009-09-03
> **linux000019 said:**
> i read somewhere that it was safe to delete everything in the /usr/src directory, which i did after compiling the 2.6.31-rc8 kernel myself for the first time. alright well now im trying to install wireless STA and when i get to the make part,

root@ryan-laptop:/home/ryan# make -C /lib/modules/2.6.31-rc8-git2-mk/build M=`pwd` clean
make: *** /lib/modules/2.6.31-rc8-git2-mk/build: No such file or directory. Stop.
root@ryan-laptop:/home/ryan# 


alright im PRETTY SURE; although im still learning; that this is because this operation calls for the /usr/src/ linux header directory.

so my question is, how do i reinstall the headers for the customized 2.6.31-rc8 build?

can i do a command line operation to extract the information from my system or do i repeat the compiling process all over again (please no).

Please point me to the place you read its ok to delete everything from the /usr/src directory so I can tell them they're very wrong.

Try

```

sudo apt-get install --reinstall linux-headers
```

?

---

### Post by linux000019 on 2009-09-03
im not using the official kernel or headers.
i built from the august 2nd release of 2.6.31-rc8 then patched git2.

from the kernel/ppa/mainline repository i can download the 2.6.31-rc8 kernel headers and install them. 

is that enough for my purposes to build?

i found a google search saying to change the makefile to point to this directory so i think i can make it work.

also, 

does make-kpkg kernel_headers do something useful for my situation?


AND i customized the kernel when building i dont know if that effects the headers or not. i did optimizing for my system.

---

### Post by falconindy on 2009-09-03
If you customize your kernel, then yes you'll need custom headers to go along with it. I'm not sure what set of instructions you followed to compile your kernel, but they sound a little flaky. I recommended you follow the directions given on [this blog](http://blog.avirtualhome.com/2009/04/29/how-to-compile-a-kernel-for-ubuntu-jaunty/). My past experiences compiling kernels from kernel.org and using make-kpkg directly have all been negative -- mostly due to issues arising with my video drivers (nvidia) after reboot.

---

### Post by honey toast on 2009-09-03
So why not select repair broken packages upon boot? It may or may not help.

---

