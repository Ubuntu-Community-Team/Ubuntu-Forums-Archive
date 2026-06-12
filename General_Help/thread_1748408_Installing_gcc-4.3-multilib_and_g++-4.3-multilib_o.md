---
title: "Installing gcc-4.3-multilib and g++-4.3-multilib on Ubuntu 11.04"
date: 2011-05-03
forum: General Help
---

### Post by subbot on 2011-05-03
worked fine on 10.10...any suggestions?
```

$ sudo apt-get install gcc-4.3-multilib g++-4.3-multilib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gcc-4.3-multilib
E: Couldn't find any package by regex 'gcc-4.3-multilib'
E: Unable to locate package g++-4.3-multilib
E: Couldn't find any package by regex 'g++-4.3-multilib'

```

---

### Post by Yakir on 2011-05-17
Exact same problem. 11.04 (natty), any ideas?

---

### Post by mc4man on 2011-05-17
Petty simple - basic method
start with these 2 package pages
[http://packages.ubuntu.com/maverick/gcc-4.3-multilib](http://packages.ubuntu.com/maverick/gcc-4.3-multilib)
[http://packages.ubuntu.com/maverick/g++-4.3-multilib](http://packages.ubuntu.com/maverick/g++-4.3-multilib)

Create a folder and download each to it
Also look on each page for any dependency that is an = vs >=
Go to that package's page, download it also to the folder 

Again, if there are any = deps on that package's page then go to that package and download. You need to grab all the ='s or you'll get 'broken packages' when trying to install the group which is no big deal, you'll be told what you're missing (*stop when there are no more ='s seen

Once you have them all you can cd to the folder and run 
```
sudo dpkg -i *.deb
```

To note - dpkg will not install any missing dep.'s, even if available from your sources. In this case there are several, you may already have installed, you may not 
( What you saw on the various package pages as >=, for those you'll use the natty versions
If you wish to prevent this minor little setback than before running the above command first install either the 4.5 or 4.4 versions of both of gcc and g++ multilib, this way all add. deps be be in place.

You need to gather 7 packages from maverick, here's the list for i386

> gcc-4.3-multilib_4.3.5-3ubuntu1_i386.deb
gcc-4.3_4.3.5-3ubuntu1_i386.deb
gcc-4.3-base_4.3.5-3ubuntu1_i386.deb
g++-4.3_4.3.5-3ubuntu1_i386.deb           
g++-4.3-multilib_4.3.5-3ubuntu1_i386.deb 
cpp-4.3_4.3.5-3ubuntu1_i386.deb  
libstdc++6-4.3-dev_4.3.5-3ubuntu1_i386.deb


---

### Post by bbuerger on 2011-05-19
Hi,

I tried this with a 64 bit 11.04 and the compiler is not linking correct.

Error:
/usr/bin/ld: cannot find -lgcc_s
Even with gcc -L/usr/lib/gcc/x86_64-linux-gnu/4.3 c.c it produces this error.

Any hints?

---

### Post by Uxorious on 2011-05-23
> **bbuerger said:**
> I tried this with a 64 bit 11.04 and the compiler is not linking correct.

Error:
/usr/bin/ld: cannot find -lgcc_s
Even with gcc -L/usr/lib/gcc/x86_64-linux-gnu/4.3 c.c it produces this error.

Same problem here.
It looks like the files are installed alright:
/usr/lib/gcc/x86_64-linux-gnu/4.3/libgcc.a
/usr/lib/gcc/x86_64-linux-gnu/4.3/libgcc_eh.a
/usr/lib/gcc/x86_64-linux-gnu/4.3/libgcc_s.so
/usr/lib/gcc/x86_64-linux-gnu/4.3/32/libgcc.a
/usr/lib/gcc/x86_64-linux-gnu/4.3/32/libgcc_eh.a
/usr/lib/gcc/x86_64-linux-gnu/4.3/32/libgcc_s.so
/usr/lib/gcc/x86_64-linux-gnu/4.3/libgcc_s_32.so

Any help would indeed be appreciated.

---

### Post by Uxorious on 2011-05-23
> **Uxorious said:**
> Same problem here.
It looks like the files are installed alright:
/usr/lib/gcc/x86_64-linux-gnu/4.3/libgcc.a
/usr/lib/gcc/x86_64-linux-gnu/4.3/libgcc_eh.a
/usr/lib/gcc/x86_64-linux-gnu/4.3/libgcc_s.so
/usr/lib/gcc/x86_64-linux-gnu/4.3/32/libgcc.a
/usr/lib/gcc/x86_64-linux-gnu/4.3/32/libgcc_eh.a
/usr/lib/gcc/x86_64-linux-gnu/4.3/32/libgcc_s.so
/usr/lib/gcc/x86_64-linux-gnu/4.3/libgcc_s_32.so

Any help would indeed be appreciated.

Of course, after 5 more minutes of digging, I found the problem.

The 3 so files in that directory are symlinks ... and they are broken.
  libgcc_s.so -> /lib/libgcc_s.so.1
  libgomp.so -> ../../../libgomp.so.1
  libstdc++.so -> ../../../libstdc++.so.6

Simply change them manually like this:
  libgcc_s.so -> /lib/x86_64-linux-gnu/libgcc_s.so.1
  libgomp.so -> ../../../x86_64-linux-gnu/libgomp.so.1
  libstdc++.so -> ../../../x86_64-linux-gnu/libstdc++.so.6

---

### Post by vittynoz@yahoo.es on 2012-01-18
I'm newer with Ubuntu. I've Oneiric 11.1 and I've the same issue.
Can someone explain step by step how to install these libraries?

I don't know if I can use the packages of Maverick packages?
I don't know how to consult the dependences of each packages?
I try to install it using trial-error method but I can't. I appreciate so much your help.

---

