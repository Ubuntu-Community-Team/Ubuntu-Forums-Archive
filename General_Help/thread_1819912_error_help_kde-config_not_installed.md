---
title: "error: help kde-config not installed"
date: 2011-08-06
forum: General Help
---

### Post by sinbowden on 2011-08-06
error: The important program kde-config was not found!

this is my output:
root@blaze:~# cd /home/mark/Downloads/kiso/kiso-0.8.3/
root@blaze:/home/mark/Downloads/kiso/kiso-0.8.3# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for kde-config... not found
configure: error: The important program kde-config was not found!
Please check whether you installed KDE correctly.

root@blaze:/home/mark/Downloads/kiso/kiso-0.8.3# sudo apt-get install kde-congig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package kde-congig
root@blaze:/home/mark/Downloads/kiso/kiso-0.8.3# cd
root@blaze:~# sudo apt-get install kde-congig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package kde-congig
root@blaze:~# kde
No command 'kde' found, did you mean:
 Command 'lde' from package 'lde' (universe)
 Command 'kde4' from package 'kdebase-runtime' (main)
 Command 'kdm' from package 'kdm' (main)
 Command 'kdf' from package 'kdf' (main)
 Command 'ode' from package 'plotutils' (universe)
 Command 'tde' from package 'devtodo' (universe)
 Command 'kded' from package 'kdelibs4c2a' (universe)
kde: command not found
root@blaze:~# sudo apt-get install kde
Reading package lists... Done
Building dependency tree       
Reading state information... Done                                                                                                              
Package kde is not available, but is referred to by another package.                                                                           
This may mean that the package is missing, has been obsoleted, or                                                                              
is only available from another source                                                                                                          

E: Package 'kde' has no installation candidate


----end----

pleas help?

---

### Post by sinbowden on 2011-08-07
I found out how to install and also realised i typed in the terminal "sudo apt-get install kde-congig" lol typo! 

here is the correct command for the terminal to install kde-config: ```
apt-get install kdelibs4c2a
```

---

### Post by badbane on 2012-05-31
I tried the above fix and it did not work. I have the same issue. but apt-get returns error that it can't find the package.

---

