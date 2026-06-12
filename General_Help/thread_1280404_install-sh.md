---
title: "install-sh ??"
date: 2009-10-02
forum: General Help
---

### Post by NawafLol on 2009-10-02
Hey !

i got a pace of software that i want to install but i don't know how ?

its in ( install-sh ) !

the link of the file is here : [COLOR=#222222][http://www.uclinux.org/pub/uClinux/utilities/xcopilot-0.6.6-uc0.tar.gz](http://www.uclinux.org/pub/uClinux/utilities/xcopilot-0.6.6-uc0.tar.gz)

i'm new at ubuntu trying to work around with uClinux !

my OS is 9.04 !
[/COLOR]

---

### Post by NawafLol on 2009-10-02
Hmmm anyone  !

---

### Post by wojox on 2009-10-02
```
chmod 755 install.sh
```

```
sudo ./install.sh
```

---

### Post by NawafLol on 2009-10-02
tried the :

i typed cd /home/nawaflol/Desktop/xcopilot-0.6.6-uc0 chmod 755 install.sh

that worked !

but with the : sudo ./install.sh

 couldn't execute it !

---

### Post by Lars Noodén on 2009-10-02
Look at the README file that comes with the tarball.

In a perfect world: 
```

cd  /tmp/
wget http://www.uclinux.org/pub/uClinux/utilities/xcopilot-0.6.6-uc0.tar.gz
tar zxf xcopilot-0.6.6-uc0.tar.gz
cd xcopilot-0.6.6-uc0
less COPYING
less README
less debian/README.debian
less INSTALL
./configure || echo -e "\0117\0110\0040\0104\0101\0122\0116."
make && sudo make install

```

That code has not been maintained in years, you may not want to do that to your system.  Your C kung fu should be good before messing with it.

XCopilot is an emulator for the 3Com/USRobotics Pilot/PalmPilot/PalmIII.
What is it that you are really wanting to accomplish through use of that program?

---

### Post by NawafLol on 2009-10-02
Will in short words uClinux !

i'm have been learning c programming for a while on widnows when i switch to linux i liked it ! 

so i want to learn system programming with linux system calls and all of that !

I'm still a newibe !

i got a new book about linux kernel system programming 

and how about playing around with uClinux for start !

---

### Post by Lars Noodén on 2009-10-02
If you are interested in system calls, then [systrace](http://www.provos.org/index.php?/archives/59-Systrace-1.6g-released.html) might be worth looking at.

uClinux is good for embedded devices and microcontrollers.
[https://mailman.uclinux.org/mailman/listinfo/uclinux-dev](https://mailman.uclinux.org/mailman/listinfo/uclinux-dev)
[http://sourceforge.net/projects/uclinux/files/](http://sourceforge.net/projects/uclinux/files/)

You'll get better information from the mailing list above regarding the specifics.  Then you can use Ubuntu as your development platform and Kdevelop, Emacs, Eclipse, or Netbeans for your IDE.

---

### Post by NawafLol on 2009-10-03
I Knew that uClinux was Designed for Embedded systems with no ( MMS ) !

Anyhow i will give it a shot with _Systrac _,I Just want to port a linux version to a machine of some sort ! Or make my own distro in the hard go way .

i know its a long way to learn linux programming ,but i have the C Kung Fu (I Think :$) for it !

---

### Post by Lars Noodén on 2009-10-04
> **NawafLol said:**
> 
Anyhow i will give it a shot with _Systrac _,I Just want to port a linux version to a machine of some sort ! Or make my own distro in the hard go way .

Making your own (Ubuntu-based) distro is covered here:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

The easiest next step in that direction, after playing with systrace to work with system calls, might be to get used to [busybox](http://www.busybox.net/), then after that [qemu-arm](http://qemu-forum.ipi.fi/viewforum.php?f=20).

Porting is a bigger challenge.  Later, you can look at porting to Sparc, MIPS or ARM.  qemu can emulate ARM.  There are large distros like Maemo, Google's android or gNewSense.  Or small like uClinux, dd-wrt or [OpenWrt](http://openwrt.org/)

> **NawafLol said:**
> 
i know its a long way to learn linux programming ,but i have the C Kung Fu (I Think :$) for it !

Then you will have a lot of fun and be able to do cool things!

---

