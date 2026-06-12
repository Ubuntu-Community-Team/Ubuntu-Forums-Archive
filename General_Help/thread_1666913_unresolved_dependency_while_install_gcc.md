---
title: "unresolved dependency while install gcc"
date: 2011-01-14
forum: General Help
---

### Post by Wiel on 2011-01-14
Hello,

I tried to install gcc-4.5 as follows:
sudo aptitude install gcc-4.5
I got the following output:

The following NEW packages will be installed:
  binutils{a} cpp-4.5{a} gcc-4.5 libc-dev-bin{a} libc6-dev{a} libcloog-ppl0{a} libelfg0{a} 
  libgmpxx4ldbl{a} libmpc2{a} libppl-c2{a} libppl7{a} linux-libc-dev{a} manpages-dev{a} 
The following packages will be upgraded:
  libc-bin libc6 
2 packages upgraded, 13 newly installed, 0 to remove and 2 not upgraded.
Need to get 26.6MB of archives. After unpacking 59.5MB will be used.
The following packages have unmet dependencies:
  libc6-i386: Depends: libc6 (= 2.12.1-0ubuntu10) but 2.12.1-0ubuntu10.1 is to be installed.
The following actions will resolve these dependencies:

      Remove the following packages:                              
1)      flashplugin-installer                                     
2)      ia32-libs                                                 
3)      lib32asound2                                              
4)      lib32bz2-1.0                                              
5)      lib32gcc1                                                 
6)      lib32ncurses5                                             
7)      lib32stdc++6                                              
8)      lib32v4l-0                                                
9)      lib32z1                                                   
10)     libc6-i386                                                
11)     nspluginwrapper                                           

      Leave the following dependencies unresolved:                
12)     kubuntu-restricted-addons recommends flashplugin-installer

If I agree with this actions to resolve the dependencies, wich funcionality I will lose or ....

Thanks very much,
WIel

kubuntu 10.10 , almost fresh install.

---

