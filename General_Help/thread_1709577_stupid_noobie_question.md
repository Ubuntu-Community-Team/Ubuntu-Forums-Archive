---
title: "stupid noobie question"
date: 2011-03-18
forum: General Help
---

### Post by Itqan on 2011-03-18
yeah i know this is a pretty stupid question but here:-
can i install any software on my computer using a live CD/DVD?
i mean like if i have ubuntu 9.04's live DVD and i want to install mesa 3d on it so can i do it?

and how do you guys install softwares :P. i just extracted the .tar.bz2 folder and thre were many more folders in it? where's is the installer?

and does ubuntu need a running internet to work and install software?

thanxx im a greenhorn at linux. :P

---

### Post by Megaptera on 2011-03-18
You can install Ubuntu from the live CD, but I don't think you can install new software on to the live CD. If running a live session (having booted into the Ubuntu CD) all changes are lost when you log out / shut down.
To install new software Ubuntu needs to be installed on your hard drive either alone or alongside Windows (dual boot) or within Windows (Wubi).

To install software as a newbie the easiest ways are:either go to Software Centre (within live CD or installed Ubuntu) or via terminal or Deb package. Tar method is a bit trickier.

Hope this helps?

---

### Post by 3Miro on 2011-03-18
- You can install software using a liveCD, however, you should remember that you are running everything off the RAM and hence you are limited on what you can do. Furthermore, any changes that you make will be lost after reboot.

- Ubuntu installers are .deb files, you can double-click on a .deb file and it will install. A .tar.gz file is probably the source code for a program, you will have to compile it to run, but you don't want to do that. Compiling is not a recommended way of doing things in Ubuntu (especially if you are not familiar with Linux). Find a .deb file for your specific version of Ubuntu.

- You don't need an active Internet connection to install things in Ubuntu, although it is recommended that you do. You can download the packages (.deb files) somewhere else and then install them on your system manually. If you want to get something form the official Ubuntu software repository, there is a way to do that.

- mesa3d will probably require special drivers. Nvidia cards and many ATI cards require proprietary drivers and due to licensing issues, Ubuntu doesn't come with those by default. You will have to install Ubuntu on your HDD, then install the driver (from the driver utility), then reboot. Since 9.04 is oldish, unless you have an Intel video cars, you will not be able to use mesa3d off of a liveCD.

- Ubuntu 9.04 has only a month of support left. You should be using 10.04 or 10.10.

---

### Post by highspider on 2011-03-18
[COLOR=Red]the above posts are the best. [/COLOR]

The basic to install a linux program with out a package manager is ---[COLOR=Green] this is for [/COLOR][COLOR=Green]future reference [/COLOR]
  [COLOR=Red]Don't mess around till you have more experience![/COLOR]

```

./configure 
sudo make install 

```And In the root dir of the uncompressed files there is usually a README or INSTALL file that if opened with a editor will till you the install

Some day when fell comfortable with ubuntu you will end up wanting a NEWER version of something not in the repos for package manger or software center.  

When installing from a source  code aka tarballs SOME times you find that you need tons of other software-sources, headers, libraries ect.  This makes it way TOO HARD for new learners.

---

### Post by Itqan on 2011-03-18
thanxx every one!

---

### Post by Megaptera on 2011-03-18
You're welcome!

---

