---
title: "trying to install ted the wprd procssor on ubuntu 10.04"
date: 2012-03-09
forum: General Help
---

### Post by mferarri on 2012-03-09
Trying to install "Ted - the word processor". I downloaded the sourcefile and did the make command like it says on the website: [http://www.nllgg.nl/Ted/]("http://www.nllgg.nl/Ted/"). I get a stream of error messages down the bottom. see below. what am i doing wrong?

```
mike@computer:~/Downloads/ted/Ted-2.21$ ls
appFrame  appUtil  bitmap  docBuf  docFont  gpl.txt  guiInterface  include  ind  lib  Makefile  Ted  ted-2.21-1.spec  tedPackage  utilPs
mike@computer:~/Downloads/ted/Ted-2.21$ make
cd appUtil && make
make[1]: Entering directory `/home/mike/Downloads/ted/Ted-2.21/appUtil'
gcc -g -O2    -I../include -I.   -c -o sioFlate.o sioFlate.c
sioFlate.c:15:21: error: zlib.h: No such file or directory
sioFlate.c:29: error: expected specifier-qualifier-list before ‘z_stream’
sioFlate.c: In function ‘sioInFlateSkipHeader’:
sioFlate.c:171: error: ‘Z_DEFLATED’ undeclared (first use in this function)
sioFlate.c:171: error: (Each undeclared identifier is reported only once
sioFlate.c:171: error: for each function it appears in.)
sioFlate.c: In function ‘sioInFlateReadBytes’:
sioFlate.c:249: error: ‘z_stream’ undeclared (first use in this function)
sioFlate.c:249: error: ‘d_stream’ undeclared (first use in this function)
sioFlate.c:249: error: ‘FlateInputStream’ has no member named ‘fisZstream’
sioFlate.c:254: error: ‘FlateInputStream’ has no member named ‘fisExhausted’
sioFlate.c:264: error: ‘FlateInputStream’ has no member named ‘fisInputPosition’
sioFlate.c:264: error: ‘FlateInputStream’ has no member named ‘fisInputCapacity’
sioFlate.c:266: error: ‘FlateInputStream’ has no member named ‘fisInputCapacity’
sioFlate.c:266: error: ‘FlateInputStream’ has no member named ‘fisInputPosition’
sioFlate.c:268: error: ‘FlateInputStream’ has no member named ‘fisInputBuffer’
sioFlate.c:268: error: ‘FlateInputStream’ has no member named ‘fisInputPosition’
sioFlate.c:272: error: ‘FlateInputStream’ has no member named ‘fisSisFlate’
sioFlate.c:273: error: ‘FlateInputStream’ has no member named ‘fisInputBuffer’
sioFlate.c:275: error: ‘FlateInputStream’ has no member named ‘fisExhausted’
sioFlate.c:277: error: ‘FlateInputStream’ has no member named ‘fisInputPosition’
sioFlate.c:278: error: ‘FlateInputStream’ has no member named ‘fisInputCapacity’
sioFlate.c:280: error: ‘FlateInputStream’ has no member named ‘fisInputBuffer’
sioFlate.c:284: error: ‘Z_NO_FLUSH’ undeclared (first use in this function)
sioFlate.c:285: error: ‘Z_OK’ undeclared (first use in this function)
sioFlate.c:287: error: ‘Z_STREAM_END’ undeclared (first use in this function)
sioFlate.c:290: error: ‘FlateInputStream’ has no member named ‘fisExhausted’
sioFlate.c:296: error: ‘FlateInputStream’ has no member named ‘fisInputPosition’
sioFlate.c: In function ‘sioInFlateClose’:
sioFlate.c:318: error: ‘z_stream’ undeclared (first use in this function)
sioFlate.c:318: error: ‘d_stream’ undeclared (first use in this function)
sioFlate.c:318: error: ‘FlateInputStream’ has no member named ‘fisZstream’
sioFlate.c:321: error: ‘FlateInputStream’ has no member named ‘fisExhausted’
sioFlate.c:330: error: ‘Z_OK’ undeclared (first use in this function)
sioFlate.c: In function ‘sioInFlateOpen’:
sioFlate.c:342: error: ‘z_stream’ undeclared (first use in this function)
sioFlate.c:342: error: ‘d_stream’ undeclared (first use in this function)
sioFlate.c:350: error: ‘FlateInputStream’ has no member named ‘fisSisFlate’
sioFlate.c:351: error: ‘FlateInputStream’ has no member named ‘fisInputPosition’
sioFlate.c:352: error: ‘FlateInputStream’ has no member named ‘fisInputCapacity’
sioFlate.c:353: error: ‘FlateInputStream’ has no member named ‘fisExhausted’
sioFlate.c:355: error: ‘FlateInputStream’ has no member named ‘fisZstream’
sioFlate.c:357: error: ‘alloc_func’ undeclared (first use in this function)
sioFlate.c:357: error: expected ‘;’ before numeric constant
sioFlate.c:358: error: ‘free_func’ undeclared (first use in this function)
sioFlate.c:358: error: expected ‘;’ before numeric constant
sioFlate.c:359: error: ‘voidpf’ undeclared (first use in this function)
sioFlate.c:359: error: expected ‘;’ before numeric constant
sioFlate.c:362: error: ‘Z_OK’ undeclared (first use in this function)
sioFlate.c: At top level:
sioFlate.c:391: error: expected specifier-qualifier-list before ‘z_stream’
sioFlate.c: In function ‘sioOutFlateFlushBytes’:
sioFlate.c:409: error: ‘z_stream’ undeclared (first use in this function)
sioFlate.c:409: error: ‘c_stream’ undeclared (first use in this function)
sioFlate.c:409: error: ‘FlateOutputStream’ has no member named ‘fosZstream’
sioFlate.c:410: error: ‘FlateOutputStream’ has no member named ‘fosOutputBuffer’
sioFlate.c:412: error: ‘FlateOutputStream’ has no member named ‘fosSosFlate’
sioFlate.c:415: error: ‘FlateOutputStream’ has no member named ‘fosOutputBuffer’
sioFlate.c: In function ‘sioOutFlateWriteBytes’:
sioFlate.c:426: error: ‘z_stream’ undeclared (first use in this function)
sioFlate.c:426: error: ‘c_stream’ undeclared (first use in this function)
sioFlate.c:426: error: ‘FlateOutputStream’ has no member named ‘fosZstream’
sioFlate.c:431: error: ‘FlateOutputStream’ has no member named ‘fosUncompressedSize’
sioFlate.c:432: error: ‘FlateOutputStream’ has no member named ‘fosGzipEmbedded’
sioFlate.c:433: error: ‘FlateOutputStream’ has no member named ‘fosAdlerCrc’
sioFlate.c:433: error: ‘FlateOutputStream’ has no member named ‘fosAdlerCrc’
sioFlate.c:445: error: ‘Z_NO_FLUSH’ undeclared (first use in this function)
sioFlate.c:446: error: ‘Z_OK’ undeclared (first use in this function)
sioFlate.c: In function ‘sioOutFlateClose’:
sioFlate.c:465: error: ‘z_stream’ undeclared (first use in this function)
sioFlate.c:465: error: ‘c_stream’ undeclared (first use in this function)
sioFlate.c:465: error: ‘FlateOutputStream’ has no member named ‘fosZstream’
sioFlate.c:478: error: ‘Z_FINISH’ undeclared (first use in this function)
sioFlate.c:479: error: ‘Z_OK’ undeclared (first use in this function)
sioFlate.c:479: error: ‘Z_STREAM_END’ undeclared (first use in this function)
sioFlate.c:498: error: ‘FlateOutputStream’ has no member named ‘fosGzipEmbedded’
sioFlate.c:500: error: ‘FlateOutputStream’ has no member named ‘fosAdlerCrc’
sioFlate.c:500: error: ‘FlateOutputStream’ has no member named ‘fosSosFlate’
sioFlate.c:501: error: ‘FlateOutputStream’ has no member named ‘fosUncompressedSize’
sioFlate.c:501: error: ‘FlateOutputStream’ has no member named ‘fosSosFlate’
sioFlate.c: In function ‘sioFlateWriteGzipHeader’:
sioFlate.c:513: error: ‘Z_DEFLATED’ undeclared (first use in this function)
sioFlate.c: In function ‘sioOutFlateOpen’:
sioFlate.c:530: error: ‘z_stream’ undeclared (first use in this function)
sioFlate.c:530: error: ‘c_stream’ undeclared (first use in this function)
sioFlate.c:538: error: ‘FlateOutputStream’ has no member named ‘fosSosFlate’
sioFlate.c:539: error: ‘FlateOutputStream’ has no member named ‘fosGzipEmbedded’
sioFlate.c:541: error: ‘FlateOutputStream’ has no member named ‘fosZstream’
sioFlate.c:543: error: ‘alloc_func’ undeclared (first use in this function)
sioFlate.c:543: error: expected ‘;’ before numeric constant
sioFlate.c:544: error: ‘free_func’ undeclared (first use in this function)
sioFlate.c:544: error: expected ‘;’ before numeric constant
sioFlate.c:545: error: ‘voidpf’ undeclared (first use in this function)
sioFlate.c:545: error: expected ‘;’ before numeric constant
sioFlate.c:547: error: ‘FlateOutputStream’ has no member named ‘fosAdlerCrc’
sioFlate.c:548: error: ‘FlateOutputStream’ has no member named ‘fosUncompressedSize’
sioFlate.c:552: error: ‘FlateOutputStream’ has no member named ‘fosAdlerCrc’
sioFlate.c:552: error: ‘Z_NULL’ undeclared (first use in this function)
sioFlate.c:554: error: ‘Z_DEFAULT_COMPRESSION’ undeclared (first use in this function)
sioFlate.c:554: error: ‘Z_DEFLATED’ undeclared (first use in this function)
sioFlate.c:555: error: ‘MAX_WBITS’ undeclared (first use in this function)
sioFlate.c:555: error: ‘MAX_MEM_LEVEL’ undeclared (first use in this function)
sioFlate.c:555: error: ‘Z_DEFAULT_STRATEGY’ undeclared (first use in this function)
sioFlate.c:556: error: ‘Z_OK’ undeclared (first use in this function)
sioFlate.c:568: error: ‘FlateOutputStream’ has no member named ‘fosOutputBuffer’
sioFlate.c:580: error: ‘FlateOutputStream’ has no member named ‘fosGzipEmbedded’
sioFlate.c:581: error: ‘FlateOutputStream’ has no member named ‘fosSosFlate’
make[1]: *** [sioFlate.o] Error 1
make[1]: Leaving directory `/home/mike/Downloads/ted/Ted-2.21/appUtil'
make: *** [lib/appUtil.a] Error 2

```

---

### Post by CaseyC on 2012-03-09
I see they have .deb files listed on the site, could you download one of those and use the deb installer to install it? 

I am not sure your level of expertise in Ubuntu, so I included this link, I do not mean to insult your intelligence by doing so. 

[http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm)

---

### Post by idoitprone on 2012-03-09
> **CaseyC said:**
> I see they have .deb files listed on the site, could you download one of those and use the deb installer to install it? 

I am not sure your level of expertise in Ubuntu, so I included this link, I do not mean to insult your intelligence by doing so. 

[http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm)

+1 because if you compile and install, your package manager will not know the program exist. Basically you are unable to completely remove the program or at time do not upgrade properly

---

### Post by mferarri on 2012-03-09
> **CaseyC said:**
> I see they have .deb files listed on the site, could you download one of those and use the deb installer to install it? 

I am not sure your level of expertise in Ubuntu, so I included this link, I do not mean to insult your intelligence by doing so. 

[http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm)

```
mike@computer:~/Downloads$ sudo dpkg -i ted-2.21-i386.deb 
dpkg: error processing ted-2.21-i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 ted-2.21-i386.deb
```


i dont know where to find the amd64 version?

also, i don't know if the amd version is here?:[http://www.nllgg.nl/Ted/]("http://www.nllgg.nl/Ted/")

---

### Post by dragonfly41 on 2012-03-09
ted 2.21 is found in Synaptic Package Manager on my 32 bit ubuntu 10.10 setup.

---

### Post by idoitprone on 2012-03-09
[https://help.ubuntu.com/community/32bit_and_64bit#How_to_Make_32-bit_Applications_Work_on_a_64-bit_Operating_System](https://help.ubuntu.com/community/32bit_and_64bit#How_to_Make_32-bit_Applications_Work_on_a_64-bit_Operating_System)

you need 32 bit libraries to run 32bit apps on 64bit system.

this requires the ia-32lib package. I do not know how to use or the dependencies to install it because it has always been installed for me when I install wine. Yes i am that lazy. Srry I cannot help anymore

may those later errors are because you have not install the proper compile dependencies. The list is long than this
> [B]sioFlate.c:15:21: error: zlib.h: No such file or directory
[/B] sioFlate.c:29: error: expected specifier-qualifier-list before &#8216;z_stream&#8217; sioFlate.c: In function &#8216;sioInFlateSkipHeader&#8217;: sioFlate.c:171: error: &#8216;Z_DEFLATED&#8217; undeclared (first use in this function)```
[B]sudo apt-get install zlib1g-dev libncurses5-dev
sudo apt-get install [/B]libpcre3-dev libxpm-dev libtiff4-dev libpng-dev libgtk2.0-dev


```[http://ubuntuforums.org/showthread.php?t=1632027](http://ubuntuforums.org/showthread.php?t=1632027)
then try to recompile, thus will make that program 64 bit and u dont need ia32 libs

rant: that developer should friken list all his damn **dependencies** it painful to compile

---

### Post by mferarri on 2012-03-09
> **idoitprone said:**
> [https://help.ubuntu.com/community/32bit_and_64bit#How_to_Make_32-bit_Applications_Work_on_a_64-bit_Operating_System](https://help.ubuntu.com/community/32bit_and_64bit#How_to_Make_32-bit_Applications_Work_on_a_64-bit_Operating_System)

you need 32 bit libraries to run 32bit apps on 64bit system.

this requires the ia-32lib package. I do not know how to use or the dependencies to install it because it has always been installed for me when I install wine. Yes i am that lazy. Srry I cannot help anymore

may those later errors are because you have not install the proper compile dependencies. The list is long than this
```
[B]sudo apt-get install zlib1g-dev libncurses5-dev
sudo apt-get install [/B]libpcre3-dev libxpm-dev libtiff4-dev libpng-dev libgtk2.0-dev


```[http://ubuntuforums.org/showthread.php?t=1632027](http://ubuntuforums.org/showthread.php?t=1632027)
then try to recompile, thus will make that program 64 bit and u dont need ia32 libs

rant: that developer should friken list all his damn **dependencies** it painful to compile

thanks, but im still getting errors.

```
mike@computer:~/Downloads/ted/Ted-2.21$ make
cd appUtil && make
make[1]: Entering directory `/home/mike/Downloads/ted/Ted-2.21/appUtil'
gcc -g -O2    -I../include -I.   -c -o sioFlate.o sioFlate.c
gcc -g -O2    -I../include -I.   -c -o sioFd.o sioFd.c
gcc -g -O2    -I../include -I.   -c -o sioEndian.o sioEndian.c
gcc -g -O2    -I../include -I.   -c -o sioDebug.o sioDebug.c
gcc -g -O2    -I../include -I.   -c -o sioCgiIn.o sioCgiIn.c
gcc -g -O2    -I../include -I.   -c -o sioBlocked.o sioBlocked.c
gcc -g -O2    -I../include -I.   -c -o sioBase85.o sioBase85.c
gcc -g -O2    -I../include -I.   -c -o sioBase64.o sioBase64.c
gcc -g -O2    -I../include -I.   -c -o regexp.o regexp.c
regexp.c:8:21: error: pcre.h: No such file or directory
regexp.c: In function ‘regCompile’:
regexp.c:50: error: ‘pcre’ undeclared (first use in this function)
regexp.c:50: error: (Each undeclared identifier is reported only once
regexp.c:50: error: for each function it appears in.)
regexp.c:50: error: ‘rval’ undeclared (first use in this function)
regexp.c:57: error: ‘PCRE_UTF8’ undeclared (first use in this function)
regexp.c:68: error: ‘PCRE_CONFIG_UTF8’ undeclared (first use in this function)
regexp.c:73: error: ‘PCRE_CONFIG_UNICODE_PROPERTIES’ undeclared (first use in this function)
regexp.c:97: warning: incompatible implicit declaration of built-in function ‘free’
regexp.c: In function ‘regFindLeftToRight’:
regexp.c:112: error: ‘pcre_extra’ undeclared (first use in this function)
regexp.c:112: error: expected expression before ‘)’ token
regexp.c: In function ‘regFindRightToLeft’:
regexp.c:135: error: ‘PCRE_ERROR_NOMATCH’ undeclared (first use in this function)
regexp.c:137: error: ‘PCRE_ANCHORED’ undeclared (first use in this function)
regexp.c:145: error: ‘pcre_extra’ undeclared (first use in this function)
regexp.c:145: error: expected expression before ‘)’ token
make[1]: *** [regexp.o] Error 1
make[1]: Leaving directory `/home/mike/Downloads/ted/Ted-2.21/appUtil'
make: *** [lib/appUtil.a] Error 2
mike@computer:~/Downloads/ted/Ted-2.21$ make
cd appUtil && make
make[1]: Entering directory `/home/mike/Downloads/ted/Ted-2.21/appUtil'
gcc -g -O2    -I../include -I.   -c -o regexp.o regexp.c
regexp.c:8:21: error: pcre.h: No such file or directory
regexp.c: In function ‘regCompile’:
regexp.c:50: error: ‘pcre’ undeclared (first use in this function)
regexp.c:50: error: (Each undeclared identifier is reported only once
regexp.c:50: error: for each function it appears in.)
regexp.c:50: error: ‘rval’ undeclared (first use in this function)
regexp.c:57: error: ‘PCRE_UTF8’ undeclared (first use in this function)
regexp.c:68: error: ‘PCRE_CONFIG_UTF8’ undeclared (first use in this function)
regexp.c:73: error: ‘PCRE_CONFIG_UNICODE_PROPERTIES’ undeclared (first use in this function)
regexp.c:97: warning: incompatible implicit declaration of built-in function ‘free’
regexp.c: In function ‘regFindLeftToRight’:
regexp.c:112: error: ‘pcre_extra’ undeclared (first use in this function)
regexp.c:112: error: expected expression before ‘)’ token
regexp.c: In function ‘regFindRightToLeft’:
regexp.c:135: error: ‘PCRE_ERROR_NOMATCH’ undeclared (first use in this function)
regexp.c:137: error: ‘PCRE_ANCHORED’ undeclared (first use in this function)
regexp.c:145: error: ‘pcre_extra’ undeclared (first use in this function)
regexp.c:145: error: expected expression before ‘)’ token
make[1]: *** [regexp.o] Error 1
make[1]: Leaving directory `/home/mike/Downloads/ted/Ted-2.21/appUtil'
make: *** [lib/appUtil.a] Error 2

```

---

### Post by idoitprone on 2012-03-09
did you install the second line?

```
sudo apt-get install libpcre3-dev libxpm-dev libtiff4-dev libpng-dev libgtk2.0-dev
```

installing libpcre3-dev get rid of that problem

or find the correct package

```
apt-cache search libpcre
```install the one that has libpcre and dev

if you did install
use
make clean
then run make again

---

### Post by mferarri on 2012-03-09
> **idoitprone said:**
> did you install the second line?

```
sudo apt-get install libpcre3-dev libxpm-dev libtiff4-dev libpng-dev libgtk2.0-dev
```

installing libpcre3-dev get rid of that problem

or find the correct package

```
apt-cache search libpcre
```install the one that has libpcre and dev

if you did install
use
make clean
then run make again

thanks idiotprone,i totally overlooked that eh? i can be a bit daft sometimes. im so glad i got it working now! it's my very first application compiled from source in ubuntu. so thanks to everyone that replied for making my new experience in linux easier, especially iditoprone.:popcorn:

i've got ted installed on my comp now.

---

### Post by idoitprone on 2012-03-09
> **mferarri said:**
> thanks idiotprone,i totally overlooked that eh? i can be a bit daft sometimes. im so glad i got it working now! it's my very first application compiled from source in ubuntu. so thanks to everyone that replied for making my new experience in linux easier, especially iditoprone.:popcorn:

i've got ted installed on my comp now.

dont say tat last line cuz i am little creeped out. Ironically, tat my name

---

### Post by mferarri on 2012-03-09
lol!

---

