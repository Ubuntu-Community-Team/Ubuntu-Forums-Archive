---
title: "Matlab R2010a and gcc"
date: 2011-01-16
forum: General Help
---

### Post by lowbagger on 2011-01-16
Hi,

Not sure if this is where I should be posting, so please let me know if I need to move to another spot.

I am running 11.04 (Natty, Satanic Edition :evil:) and trying to simulate circuits in Simulink.  I get errors and failures.

Tried this:  [https://help.ubuntu.com/community/MATLAB/R2010a#MEX%20functions](https://help.ubuntu.com/community/MATLAB/R2010a#MEX%20functions), but could not get Simulink to run a simulation.  Tells me the compiler is not supported.  I think it failed, despite what the page says (but please correct me if I'm wrong), because there is no output on the scope.

My plan was to install gcc 4.2.3 and change the link in /usr/bin to point to it.

I installed aptitude and followed the instructions on the above page, but the packages were not found.

I downloaded a tar of gcc 4.2.3 and tried installing from that, but the install failed after about half an hour of various warning and error messages.

I have the same version of Matlab on my work computer (XP) and it works fine, but I hate my work computer and this one is too old for Windows.

Could someone walk me through installing gcc 4.2.3 and getting it to work with Matlab?  Natty doesn't seem to like it at all.

Thanks,

L

---

### Post by amikebous on 2011-05-17
Hey I am having exactly the same problem. I am using executable matlab scripts and I cannot compile anymore. Have you found any solution?

---

### Post by rufus.wilson on 2011-05-28
Dear all,

I wrote this from several posts:
[http://www.trevorpounds.com/blog/?p=111](http://www.trevorpounds.com/blog/?p=111)
[http://whowhywhathow.blogspot.com/2011/01/compile-gcc-from-souce-on-ubuntu-10041.html](http://whowhywhathow.blogspot.com/2011/01/compile-gcc-from-souce-on-ubuntu-10041.html)
[http://misspent.wordpress.com/2011/04/26/compiling-g-4-1-on-ubuntu-natty-narwhal/](http://misspent.wordpress.com/2011/04/26/compiling-g-4-1-on-ubuntu-natty-narwhal/)


[LIST]
[*] Install dependancies
[/LIST]
```

sudo apt-get install g++ ia32-libs libc6-dev-i386 m4 flex bison libmpfr-dev libmpc-dev

```
[LIST]
[*]Obtain and untar gcc-4.2.3
[/LIST]
 ```

wget ftp://ftp.uvsq.fr/pub/gcc/releases/gcc-4.2.3/gcc-4.2.3.tar.gz
tar -xvf gcc-4.2.3.tar.gz

```
[LIST]
[*]Obtain and untar gmp-5.0.2
[/LIST]
 ```

wget ftp://ftp.gmplib.org/pub/gmp-5.0.2/gmp-5.0.2.tar.gz
tar -xvf gmp-5.0.2.tar.gz
mkdir gcc-4.2.3/gmp
mv gmp-5.0.2 gcc-4.2.3/gmp

```
[LIST]
[*]Obtain and untar mpfr-3.0.1
[/LIST]
 ```

wget http://www.mpfr.org/mpfr-current/mpfr-3.0.1.tar.gz
tar -xvf mpfr-3.0.1.tar.gz
mkdir gcc-4.2.3/mpfr
mv mpfr-3.0.1 gcc-4.2.3/mpfr

```
[LIST]
[*]Modify a file to make multilib looking for the correct libs
[/LIST]
 ```

cd gcc-4.2.3
sed 's/MULTILIB_OSDIRNAMES = \.\.\/lib64 \.\.\/lib/MULTILIB_OSDIRNAMES = ..\/lib ..\/lib32/g' ./gcc/config/i386/t-linux64 > ./gcc/config/i386/t-linux64_2
mv ./gcc/config/i386/t-linux64_2 ./gcc/config/i386/t-linux64

```
[LIST]
[*]Create directory for compiled gcc :
[/LIST]
 ```

mkdir ../gcc
cd ../gcc

```
[LIST]
[*]Configure
[/LIST]
 ```

../gcc-4.2.3/configure --program-suffix=-4.2 --enable-threads --enable-languages=c,c++ --enable-bootstrap --with-gmp=../gcc-4.2.3/gmp --with-mpfr=../gcc-4.2.3/mpfr

```It may be necessary to change the --host option if you are on a mac or other...

[LIST]
[*]Make using 2 cores (update depending on yours)
[/LIST]
 ```

make -j2

```
[LIST]
[*]Install
[/LIST]
 ```

sudo make install

```I just tried it on a Ubuntu 11.04 64bits fresh install so it should work !


[LIST]
[*]To get newer versions of GCC to work with matlab just do the following:
[/LIST]
```

cd /dir/to/matlab/folder/sys/os/glnxa64 # change glnxa64 to glnx86 for 32 bits
sudo mkdir old
sudo mv libstdc++.* libg2c.* libgcc_s* old
export LD_LIBRARY_PATH=/usr/lib32:/usr/lib:$LD_LIBRARY_PATH

```

Hope this helps,
Rufus

---

### Post by linuxinstalledfromhdd on 2011-05-28
Just so I can know, does this happen with 10.10?  I want to know so if people need this in the future I can simply refer them to an installation of 10.10.

---

### Post by rufus.wilson on 2011-05-28
@linuxinstalledfromhdd:
I don't have a 10.10 but from there [http://ubuntuforums.org/showthread.php?t=1652053](http://ubuntuforums.org/showthread.php?t=1652053) it seems gcc 4.2 is not available from synaptic. So I would think they need to do the same... (Maybe I'm wrong, as I said, I never had a 10.10)

Best regards,
Rufus

---

### Post by BestD on 2011-05-28
I had the same problem with 2010a, upgrading to 2011a solved it. No idea if that is possible for you.

---

### Post by rufus.wilson on 2011-05-29
> **BestD said:**
> I had the same problem with 2010a, upgrading to 2011a solved it. No idea if that is possible for you.

Could you explain how you got it to work ?

Cheers,
Rufus

---

