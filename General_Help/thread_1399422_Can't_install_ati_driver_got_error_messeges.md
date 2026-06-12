---
title: "Can't install ati driver got error messeges"
date: 2010-02-05
forum: General Help
---

### Post by aviramof on 2010-02-05
i have downloaded ati-driver-installer-10-1-x86.x86_64.run my ubuntu version is 8.10 intrepid desktop and as i understand it it has x.org 6 something version not 7 plus so after running the command 
```

sudo sh ./ati-driver-installer-10-1-x86.x86_64.run

```i have choesen Generate Distribution Specific Driver Package Option then i noticed that there is no ubuntu in this list however there is a way to build a pacage using the commands
```

sudo sh ./ati-driver-installer-10-1-x86.x86_64.run -listpkg

sudo sh ./ati-driver-installer-10-1-x86.x86_64.run --buildpkg Ubuntu/intrepid

```but then i get this:
```
            ; do execstack -q $i; execstack -c $i; done
/bin/sh: execstack: not found
/bin/sh: execstack: not found
/bin/sh: execstack: not found
/bin/sh: execstack: not found
/bin/sh: execstack: not found
/bin/sh: execstack: not found
/bin/sh: execstack: not found
/bin/sh: execstack: not found
make: *** [binary-install/xorg-driver-fglrx] Error 127
dpkg-buildpackage: failure: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.b21983

```what should i do now?

p.s if i'm writing in the wrong place at least let me know about it

thanks in advance.

---

### Post by dcstar on 2010-02-06
> **aviramof said:**
> i have downloaded ati-driver-installer-10-1-x86.x86_64.run my ubuntu version is 8.10 intrepid desktop and as i understand it it has x.org 6 something version not 7 plus so after running the command 
........

What is wrong with the driver in the Ubuntu repositories?

---

### Post by aviramof on 2010-02-06
well it's old the catalyst is not very good and the dual view option don't really work as they should for instance i have chosen big screen left on display two so first of all what is the 
big screen is it the dual view or the computer screen any way on my computer screen i see all the menus on the tv nothing but let's say i press clean by name everything  on desktop goes to the dual view screen which is on the right and that is the good option the one that i can handle and see movies with if it's working ok it doesn't always work as it is now as for rest they are more difficult to use or even impossilbe so what i want is latest driver version 
8.69 which is 10.1 version i guess and not 8.54.3 which i don't know what version she is.

thanks in advance.

---

### Post by aviramof on 2010-02-06
well it's old the catalyst is not very good and the dual view option don't really work as they should for instance i have chosen big screen left on display two so first of all what is the 
big screen is it the dual view or the computer screen any way on my computer screen i see all the menus on the tv nothing but let's say i press clean by name everything  on desktop goes to the dual view screen which is on the right and that is the good option the one that i can handle and see movies with if it's working ok it doesn't always work as it is now as for rest they are more difficult to use or even impossilbe so what i want is latest driver version 
8.69 which is 10.1 version i guess and not 8.54.3 which i don't know what version she is.

and there are'n many options in this catalyst it's pretty basic.

thanks in advance.

---

### Post by ragsx on 2010-02-15
Exact same problem here using:
Ubuntu/Intrepid
Linux 2.6.27-17-generic #1 SMP

Executed command:
  sh ati-driver-installer-10-1-x86.x86_64.run --buildpkg Ubuntu/intrepid

error:

  make: *** [binary-install/xorg-driver-fglrx] Error 127
  dpkg-buildpackage: failure: debian/rules binary gave error exit status 2
  Removing temporary directory: fglrx-install.LQ9502

Reason why not using the Ubuntu drivers:[INDENT]They are old and Restricted Drivers don't work when i click Activate unless i go back to kernel 2.6.27-11.
[/INDENT]Any idea how to solve it?

---

### Post by ragsx on 2010-02-15
Solved the problem using Intrepid repositories instead of the latest Ati driver doing this:

  apt-get remove --purge xserver-xorg-video-radeon

  apt-get remove --purge fglrx-kernel-source

  apt-get install fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx xorg-driver-fglrx-dev

  After restarting X everything is working.

I took that from [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/293012](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/293012)  , post #9.

---

### Post by Chilly_Willy on 2012-02-09
> **ragsx said:**
> 
...

I took that from [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/293012](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/293012)  , post #9.

Thanks, direct link: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/293012/comments/9](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/293012/comments/9)

---

### Post by sffvba[e0rt on 2012-02-09
*Back to **sleep** old thread.*


404

---

