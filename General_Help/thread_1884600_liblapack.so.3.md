---
title: "liblapack.so.3"
date: 2011-11-21
forum: General Help
---

### Post by joy_stat on 2011-11-21
Hi,
  
 I am trying to use the Eigensoft package on Ubuntu 11.10. I downloaded the software from [http://www.hsph.harvard.edu/faculty/alkes-price/files/eig4.2.tar.gz](http://www.hsph.harvard.edu/faculty/alkes-price/files/eig4.2.tar.gz) and followed the steps mentioned in the README file but somehow whenever I type in the command ./smartpca inside the bin folder I get a error:

./smartpca: error while loading shared libraries: liblapack.so.3: cannot open shared object file: No such file or directory

I checked  and found I have liblapack.so.3gf instead of liblapack.so.3 and same for the other dependency (libblas):

I used 
sudo ln -s /usr/lib/liblapack.so.3gf /usr/lib/liblapack.so.3
sudo ln -s /usr/lib/libblas.so.3gf /usr/lib/libblas.so.3

I tried ./smartpca again and this time it gave me another similar error:

./smartpca: error while loading shared libraries: libgfortran.so.1: cannot open shared object file: No such file or directory

Can anyone give me a solution please? 

Thanks a ton,

-Joey

---

### Post by azmyth on 2011-11-21
sudo apt-get install apt-file
apt-file update
apt-file search 'libgfortran.so.' 

This will come back with a libgfortran.so.3. Guess you could try the link trick but IDK you may end up with issues come compile time. Looks like the SW was written based on older versions of various deps.

---

### Post by joy_stat on 2011-11-21
I tired the commands you suggested but the same error keeps coming out.

When I used apt-file search 'libgfortran.so.' I get the following results

gcc-snapshot: /usr/lib/gcc-snapshot/lib/libgfortran.so.3
gcc-snapshot: /usr/lib/gcc-snapshot/lib/libgfortran.so.3.0.0
gcc-snapshot: /usr/lib/gcc-snapshot/lib32/libgfortran.so.3
gcc-snapshot: /usr/lib/gcc-snapshot/lib32/libgfortran.so.3.0.0
lib32gfortran3: /usr/lib32/libgfortran.so.3
lib32gfortran3: /usr/lib32/libgfortran.so.3.0.0
lib32gfortran3-dbg: /usr/lib/debug/usr/lib32/libgfortran.so.3.0.0
libgfortran3: /usr/lib/x86_64-linux-gnu/libgfortran.so.3
libgfortran3: /usr/lib/x86_64-linux-gnu/libgfortran.so.3.0.0
libgfortran3-armel-cross: /usr/arm-linux-gnueabi/lib/libgfortran.so.3
libgfortran3-armel-cross: /usr/arm-linux-gnueabi/lib/libgfortran.so.3.0.0
libgfortran3-armhf-cross: /usr/arm-linux-gnueabihf/lib/libgfortran.so.3
libgfortran3-armhf-cross: /usr/arm-linux-gnueabihf/lib/libgfortran.so.3.0.0
libgfortran3-dbg: /usr/lib/debug/usr/lib/x86_64-linux-gnu/libgfortran.so.3.0.0
libgfortran3-dbg-armel-cross: /usr/lib/debug/usr/arm-linux-gnueabi/lib/libgfortran.so.3.0.0
libgfortran3-dbg-armhf-cross: /usr/lib/debug/usr/arm-linux-gnueabihf/lib/libgfortran.so.3.0.0
libhfgfortran3-armel-cross: /usr/arm-linux-gnueabi/lib/arm-linux-gnueabihf/libgfortran.so.3
libhfgfortran3-armel-cross: /usr/arm-linux-gnueabi/lib/arm-linux-gnueabihf/libgfortran.so.3.0.0
libhfgfortran3-dbg-armel-cross: /usr/lib/debug/usr/arm-linux-gnueabi/lib/arm-linux-gnueabihf/libgfortran.so.3.0.0

Since it asks for libgfortran.so.1 I tried making a link but to no avail.

Thanks,

 -Joey

---

### Post by joy_stat on 2011-11-22
So..I fixed the problem at last...

I looked at the Makefile and saw that it was calling gfortran

FC = gfortran

which wasn't there on my file system...

I change it to FC = gfortran-4.4 and recompiled the porgram using

make clobber 
make install

and it's working fine.

Thanks,

-Joey

---

### Post by kostyachest on 2012-05-02
Had the same problem, the fix worked for me too. Thank you for posting!

---

### Post by elansary on 2013-04-19
could u please say exactly how did u fix the error because I am having the same error and I dont know linux that so what is the makefile and wher i can find it

---

### Post by oldos2er on 2013-04-19
Hi elansary, please start a new thread for your question, as recommended by the posting guidelines:

If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

