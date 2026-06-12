---
title: "WineASIO installation problems"
date: 2011-10-25
forum: General Help
---

### Post by Derek.Gildea on 2011-10-25
Hello folks,

I'm a music enthusiast into working with the software FL Studio. In order to record I need to use ASIO drivers, but I've run into problems installing WineASIO. For reference, I'm using what seems to be a fantastic instruction manual for moderate linux users [here.]("http://www.lucamazzilli.it/blog/2011/05/install-wineasio-0-9-0-on-ubuntu-11-04-deb-file-included/")

The main problem appears to be installing the asio.h file. I've found it searching through google and selecting the fourth link on[ this search.]("https://www.google.com/search?gcx=c&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=asio.h") 

When I try to make the asio.h file I get the following message.

> gcc -c -I. -I/usr/include -I/usr/include -I/usr/include/wine -I/usr/include/wine/windows    -m32 -g -O2 -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o asio.o asio.c
asio.c:39:24: fatal error: wine/debug.h: No such file or directory
compilation terminated.
make: *** [asio.o] Error 1


Can anyone advise me as to the problem?

Thanks!

Derek

---

### Post by oldtimer7777 on 2011-10-25
Why aren't you using the *.deb file instead?  That is the first recommended method they proscribe to accomplish this.

You shouldn't have to build it from source to get this to install. I just installed the Deb file, tested it, and it works fine.

Maybe you need to be using 32-bit Ubuntu 11.04 probably?

> **Derek.Gildea said:**
> Hello folks,

I'm a music enthusiast into working with the software FL Studio. In order to record I need to use ASIO drivers, but I've run into problems installing WineASIO. For reference, I'm using what seems to be a fantastic instruction manual for moderate linux users [here.]("http://www.lucamazzilli.it/blog/2011/05/install-wineasio-0-9-0-on-ubuntu-11-04-deb-file-included/")

The main problem appears to be installing the asio.h file. I've found it searching through google and selecting the fourth link on[ this search.]("https://www.google.com/search?gcx=c&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=asio.h") 

When I try to make the asio.h file I get the following message.



Can anyone advise me as to the problem?

Thanks!

Derek

---

### Post by PsyclonJohn on 2011-10-26
I've had this same issue trying to compile it using the terimal, but the deb shouldn't have any problems. However, wine isn't detecting the wineASIO drivers at all.

---

### Post by ursinha on 2011-11-18
Hi,

As telling him to use the deb doesn't fix his issue (;)), here's what I found that would allow you to compile. 

Thing there is the wine-dev package is missing. As soon as you install it, that error will go away. The package would be something like wine1.2-dev or wine1.3-dev, as soon as you try to apt-get install wine-dev, apt will tell you.

You might get another error regarding jack .h files as well, that generally means that you need to install the -dev version of the package to get the headers.

Hope this helps!

---

