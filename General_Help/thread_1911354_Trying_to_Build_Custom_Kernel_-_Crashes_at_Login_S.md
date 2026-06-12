---
title: "Trying to Build Custom Kernel - Crashes at Login Screen"
date: 2012-01-18
forum: General Help
---

### Post by GuitarRocker2562 on 2012-01-18
I am trying to build a kernel based off of the latest stable kernel 3.2.1 on a dell netbook. It builds and installs fine but when I boot I can only get to the login screen before my system freezes. As soon as I click anything int he login screen it drops to a text mode with no clear errors and freezes. Any ideas? I'm running Ubuntu 11.10.

---

### Post by GuitarRocker2562 on 2012-01-18
Anyone?

---

### Post by xyzzyman on 2012-01-18
Bumping your thread after only 2 hours is quite unnecessary.

Are you using sources from kernel.org, kernel.org w/ubuntu mainline patches or ubuntu's 3.2.1 sources with all of ubuntu's patches?

Do you get an error when you then run startx from the prompt? It would also help if you could post your dmesg output.

---

### Post by GuitarRocker2562 on 2012-01-18
Just the vanilla kernel from kernel.org. Where can I get the Ubuntu patches. I didn't see an Ubuntu sources for the 3.2.1 kernel. I don't get to a prompt. It's more like a panic screen / log but it doesn't have any errors. This is my first time trying to build my own kernel so if you know a good source explaining how to do this it would be greatly appreciated. I just want the 3.2.1 kernel optimized for my system with all the extras taken out (like drivers I don't use)

---

### Post by xyzzyman on 2012-01-19
[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-9.16](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-9.16)

It's the 3.2.0 tar, but then you can apply the patch file that's there. The patch file also rebases it to 3.2.1. The best is to compile it fully, and have it working then start removing stuff. That's how I learned a few months ago.

NOTE: Make sure to extract the patch file. I must not understand .gz files as it looks like an actual patch file with human readable text, but then if you extract it, you get an >11MB file as opposed to just 2.6MB's.

This is how I build mine. It has to be changed when you update the sources, and it's geared towards me optimizing for my core2 (I do have a very stripped .config. My initrd drops from 19.6MB's down to 7.3MB's.)

```

#Enter linux directory

cd /linux-xxxxxx

#make debian/rules as executable

chmod -Rv +x debian/rules

#make debian/scripts directory executable

chmod -Rv +x debian/scripts/

#To create a new flavour, just clone from generic flavor, here is how, adjust as necessary

cp debian.master/config/amd64/config.flavour.generic debian.master/config/amd64/config.flavour.core2

#Copy the abi related files from existing generic flavor and tweak to reflect the newly created flavor. Change the code to match the /abi/xxxxx entry in your source.

cp debian.master/abi/3.0.0-12.20/amd64/generic debian.master/abi/3.0.0-12.20/amd64/core2
cp debian.master/abi/3.0.0-12.20/amd64/generic.modules debian.master/abi/3.0.0-12.20/amd64/core2.modules
sed -i s/getall\ amd64\ generic\ server\ virtual/getall\ amd64\ generic\ server\ virtual\ core2/g debian.master/etc/getabis
sed -i s/\=\ generic\ server\ virtual/\=\ generic\ server\ virtual\ core2/g debian.master/rules.d/amd64.mk
cp debian.master/control.d/vars.generic debian.master/control.d/vars.core2
sed -i s/\"Generic\"/\"core\ core2\"/g debian.master/control.d/vars.core2


#Modify Makefile for optimization
#edit arch/x86/Makefile and arch/x86/Makefile_32.cpu if you want to tweak the march and mtune params of gcc

vi Makefile

vi arch/x86/Makefile

vi arch/x86/Makefile_32.cpu

#In the main makefile, I changed HOSTCC and HOSTCXX to look as follows

HOSTCC       = gcc -march=core2 -mtune=core2 -pipe
HOSTCXX      = g++ -march=core2 -mtune=core2 -pipe

#In other makefiles, replace generic with native in the line for your arch, probably doesn't make any noticeable difference

#Clean and do the kernel configuration, (just give y only to the newly created flavor when executing editconfigs)

fakeroot debian/rules clean
fakeroot debian/rules updateconfigs
fakeroot debian/rules editconfigs

#Clean before building

fakeroot debian/rules clean

#Build headers

skipabi=true skipmodule=true fakeroot debian/rules binary-indep

#The following builds the newly created flavor. Note I added no_dumpfile=yes as it was not building the dumpfile.

time skipabi=true skipmodule=true no_dumpfile=yes fakeroot debian/rules binary-core2

#Wait for sometime (depends on speed of your processor). No need to tweak concurrency settings, which are taken care automatically. Install the newly built debs as follows after going one directory above

cd ..

sudo dpkg -i linux-headers-* linux-image-*
```

When you want to make changes to the .config, start at the command fakeroot debian/rules editconfigs

Not all drivers are better compiled into the kernel as opposed to modules though. My intel wifi won't turn on unless it's a module, and my onboard realtek card reader if it's compiled in makes itself sda instead of sdb. Not a big deal but it confused me at first. If you wind up with weird errors later, you'll always want to boot and duplicate inside of an ubuntu provided kernel before posting for help or submitting bug reports.

If you are expecting a performance increase from removing drivers that's not going to happen. All you might do is see some increase in boot speeds. I compile in a custom DSDT file so I do the optimizations, otherwise I would be using ubuntu provided.

---

