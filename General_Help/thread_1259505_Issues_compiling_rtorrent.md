---
title: "Issues compiling rtorrent"
date: 2009-09-06
forum: General Help
---

### Post by scambro on 2009-09-06
Hello - I've installed rtorrent a few times before, but never compiled it on my own, so this was my first run at it.  I'm hitting a brick wall now.  Here's the history of my commands:

```

  866  sudo mkdir rtorrent
  867  cd rtorrent
  868  sudo svn co svn://rakshasa.no/libtorrent/trunk
  869  cd trunk
  870  sudo svn up
  871  cd libtorrent
  872  sudo ./autogen.sh
  873  sudo ./configure
  874  sudo make
  875  sudo make install
  876  cd ../rtorrent
  877  sudo ./autogen.sh
  879  sudo ./configure --with-xmlrpc-c
  880  sudo make
  881  sudo make install
```

rpc/libsub_rpc.a(xmlrpc.o): In function `rpc::XmlRpc::set_dialect(int)':
/home/rt/sources/rtorrent/trunk/rtorrent/src/rpc/xmlrpc.cc:535: undefined reference to `xmlrpc_registry_set_dialect'
/home/rt/sources/rtorrent/trunk/rtorrent/src/rpc/xmlrpc.cc:531: undefined reference to `xmlrpc_registry_set_dialect'
rpc/libsub_rpc.a(xmlrpc.o): In function `rpc::xmlrpc_list_entry_to_value(_xmlrpc_env*, _xmlrpc_value*, int)':
/home/rt/sources/rtorrent/trunk/rtorrent/src/rpc/xmlrpc.cc:102: undefined reference to `xmlrpc_read_i8'
rpc/libsub_rpc.a(xmlrpc.o): In function `rpc::object_to_xmlrpc(_xmlrpc_env*, torrent::Object const&)':
/home/rt/sources/rtorrent/trunk/rtorrent/src/rpc/xmlrpc.cc:368: undefined reference to `xmlrpc_i8_new'
rpc/libsub_rpc.a(xmlrpc.o): In function `rpc::xmlrpc_to_object(_xmlrpc_env*, _xmlrpc_value*, int, rpc::rt_triple<int, void*, void*>*)':
/home/rt/sources/rtorrent/trunk/rtorrent/src/rpc/xmlrpc.cc:248: undefined reference to `xmlrpc_read_i8'
collect2: ld returned 1 exit status
make[2]: *** [rtorrent] Error 1
make[2]: Leaving directory `/home/rt/sources/rtorrent/trunk/rtorrent/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/rt/sources/rtorrent/trunk/rtorrent/src'
make: *** [install-recursive] Error 1

```

  882  rtorrent

```
rtorrent: XMLRPC not supported.

Any ideas come to mind to check?  I've run through these steps several times, still getting the same error at the end of the make install step.  Thanks!

---

### Post by NoaHall on 2009-09-06
Try using "sudo apt-get install xmlrpc-c-dev"

If it fails with the same error again, try "sudo ldconfig" and run again.

---

### Post by scambro on 2009-09-06
> **NoaHall said:**
> Try using "sudo apt-get install xmlrpc-c-dev"

If it fails with the same error again, try "sudo ldconfig" and run again.
```

$ sudo apt-get install libxmlrpc-c-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting libxmlrpc-c3-dev instead of libxmlrpc-c-dev
libxmlrpc-c3-dev is already the newest version.

```

Then ran sudo ldconfig, no output.  Same command (sudo make install), same output :confused:

Thanks!

---

### Post by scambro on 2009-09-06
I found the following, which seems to be almost identical to my issue (although Gentoo).  However, I'm not sure I understand what the resolution means...  Can someone clarify what or how the last response means :)

[http://forums.gentoo.org/viewtopic-t-681137.html](http://forums.gentoo.org/viewtopic-t-681137.html)

---

### Post by Liolikas on 2009-09-06
But rtorrent should work now because you have xmlblabla

---

### Post by Liolikas on 2009-09-06
> **scambro said:**
> I found the following, which seems to be almost identical to my issue (although Gentoo).  However, I'm not sure I understand what the resolution means...  Can someone clarify what or how the last response means :)

[http://forums.gentoo.org/viewtopic-t-681137.html](http://forums.gentoo.org/viewtopic-t-681137.html)
That post is history...
Maybe read here:
[http://hi.baidu.com/justforfun/blog/item/c00a0924abf54e2fd5074269.html](http://hi.baidu.com/justforfun/blog/item/c00a0924abf54e2fd5074269.html)

---

### Post by rockstarrem on 2009-09-06
Hello,

Try running this command:

```

sudo apt-get build-dep rtorrent

```

After that, try building it.

---

### Post by scambro on 2009-09-06
> **Liolikas said:**
> That post is history...
Maybe read here:
[http://hi.baidu.com/justforfun/blog/item/c00a0924abf54e2fd5074269.html](http://hi.baidu.com/justforfun/blog/item/c00a0924abf54e2fd5074269.html)

Didn't find that page before in my searching, I'll back track and try those directions. 

I tried running rtorrent after the sudo ldconfig and got the same response that it didn't have XMLRPC.

Thanks!

---

### Post by rockstarrem on 2009-09-06
If you don't want to follow my above suggestion, doing the below should work the same...

```

sudo apt-get install libsigc++-2.0-dev libtorrent-dev libxmlrpc-c3-dev

```

Please note that you're just getting the programs necessary to install by doing it this way, this is not installing rtorrent.

---

### Post by scambro on 2009-09-06
> **rockstarrem said:**
> If you don't want to follow my above suggestion, doing the below should work the same...

```

sudo apt-get install libsigc++-2.0-dev libtorrent-dev libxmlrpc-c3-dev

```

Please note that you're just getting the programs necessary to install by doing it this way, this is not installing rtorrent.

Sorry - was trying a few things before replying directly to yours.  I ran the build-dep rtorrent, and ended up downloading that piece.  Afterwards, I re-ran the build steps to the same result.  I just ran the line above and here the output:

```

$ sudo apt-get install libsigc++-2.0-dev libtorrent-dev libxmlrpc-c3-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
libsigc++-2.0-dev is already the newest version.
libtorrent-dev is already the newest version.
libxmlrpc-c3-dev is already the newest version.

```

I'm scratching my head....  Thanks!

---

### Post by rockstarrem on 2009-09-06
Are you running ./configure again or are you just running make/make install? You'd need to run the ./configure again.

---

### Post by scambro on 2009-09-06
> **rockstarrem said:**
> Are you running ./configure again or are you just running make/make install? You'd need to run the ./configure again.

At first I ran just the make, but went back to the configure:
```

  916  sudo apt-get build-dep rtorrent
  917  rtorrent
  918  cd ..
  920  cd rtorrent
  922  cd trunk
  925  cd rtorrent
  926  ls
  927  sudo make
  929  sudo ./configure
  930  sudo make
  931  sudo make install
  932  rtorrent

Then I realized that I forgot the XMLRPC line:
  934  sudo ./configure --with-xmlrpc-c
  935  sudo make

```

---

### Post by rockstarrem on 2009-09-06
So since you've done that build-dep command you redid the ./configure --with-xmlrpc-c command? Sorry if it seems repetitive (my questioning), I just need to know.

---

### Post by scambro on 2009-09-06
> **rockstarrem said:**
> So since you've done that build-dep command you redid the ./configure --with-xmlrpc-c command? Sorry if it seems repetitive (my questioning), I just need to know.

Yeah, the above is from a history command.  Just to be sure I redid the two commands:

```

 1064  cd rtorrent/
 1065  sudo svn co svn://rakshasa.no/libtorrent/trunk
 1066  cd trunk
 1067  cd libtorrent
 1068  sudo apt-get build-dep rtorrent
 1069  sudo ./autogen.sh
 1070  sudo ./configure --with-xmlrpc-c
 1071  sudo make
 1072  sudo make install
 1073  cd ../rtorrent
 1074  sudo ./autogen.sh
 1075  sudo sudo ./configure --with-xmlrpc-c
 1076  sudo make
 1077  history


```
```

rpc/libsub_rpc.a(xmlrpc.o): In function `rpc::XmlRpc::set_dialect(int)':
/home/rt/sources/rtorrent/trunk/rtorrent/src/rpc/xmlrpc.cc:535: undefined reference to `xmlrpc_registry_set_dialect'
/home/rt/sources/rtorrent/trunk/rtorrent/src/rpc/xmlrpc.cc:531: undefined reference to `xmlrpc_registry_set_dialect'
rpc/libsub_rpc.a(xmlrpc.o): In function `rpc::xmlrpc_list_entry_to_value(_xmlrpc_env*, _xmlrpc_value*, int)':
/home/rt/sources/rtorrent/trunk/rtorrent/src/rpc/xmlrpc.cc:102: undefined reference to `xmlrpc_read_i8'
rpc/libsub_rpc.a(xmlrpc.o): In function `rpc::object_to_xmlrpc(_xmlrpc_env*, torrent::Object const&)':
/home/rt/sources/rtorrent/trunk/rtorrent/src/rpc/xmlrpc.cc:368: undefined reference to `xmlrpc_i8_new'
rpc/libsub_rpc.a(xmlrpc.o): In function `rpc::xmlrpc_to_object(_xmlrpc_env*, _xmlrpc_value*, int, rpc::rt_triple<int, void*, void*>*)':
/home/rt/sources/rtorrent/trunk/rtorrent/src/rpc/xmlrpc.cc:248: undefined reference to `xmlrpc_read_i8'
collect2: ld returned 1 exit status
make[3]: *** [rtorrent] Error 1
make[3]: Leaving directory `/home/rt/sources/rtorrent/trunk/rtorrent/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/rt/sources/rtorrent/trunk/rtorrent/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rt/sources/rtorrent/trunk/rtorrent'
make: *** [all] Error 2

```

---

### Post by rockstarrem on 2009-09-06
You ran ldconfig after? Not sure if it would do anything, but its worth a shot.

---

### Post by scambro on 2009-09-06
I had not, but I just did, same result.  I ran:
- sudo ldconfig
- sudo make
same output.  Then I tried:
- sudo ldconfig
- sudo ./configure --with-xmlrpc-c
- sudo make
same output.

I feel like I've done each of these steps a thousand times now, but any help is greatly appreciated.  Thanks!

---

### Post by rockstarrem on 2009-09-06
Okay, let's try manually compiling xmlrpc. First go into console and type this:

```

sudo apt-get remove libxmlrpc-c3-dev --purge

```

Now download this and configure, make, and install. 

[http://sourceforge.net/projects/xmlrpc-c/files/Xmlrpc-c%20Super%20Stable/1.06.35/xmlrpc-c-1.06.35.tgz/download](http://sourceforge.net/projects/xmlrpc-c/files/Xmlrpc-c%20Super%20Stable/1.06.35/xmlrpc-c-1.06.35.tgz/download)

---

### Post by scambro on 2009-09-06
Ack, well shoot:

sudo ./configure = good
sudo make:
```

g++ -shared -Wl,-soname,libxmlrpc_cpp.so.3  -o libxmlrpc_cpp.so.3.06 XmlRpcCpp.o
/usr/bin/ld: XmlRpcCpp.o: relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
XmlRpcCpp.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libxmlrpc_cpp.so.3.06] Error 1
make[2]: Leaving directory `/home/rt/sources/xmlrpc-c/xmlrpc-c-1.06.35/src/cpp'
make[1]: *** [cpp/all] Error 2
make[1]: Leaving directory `/home/rt/sources/xmlrpc-c/xmlrpc-c-1.06.35/src'
make: *** [src/all] Error 2

```

I'm googling this now to see if I can find a quick answer to get xmlrpc compiled.

---

### Post by rockstarrem on 2009-09-06
Well, I mean, I really don't believe its the problem but I'm trying to help the best I can, so I guess try not using sudo on configure. This particularly:

```

./configure
make
sudo make install

```

So just use sudo on make install.

I have no problems with the above, I did it exactly as I said.

---

### Post by scambro on 2009-09-06
I used sudo when I downloaded the files, so they have a root user, so I had to use suo when running the make or ./configure lines.  I'm not getting too far on my search to get this compiled now...

---

### Post by scambro on 2009-09-06
I'm about ready to toss my laptop through the window...  What about: [http://libtorrent.rakshasa.no/ticket/1593](http://libtorrent.rakshasa.no/ticket/1593)

I don't understand the overlapping version issue, how do I verify that?  I ran the following thinking this was perhaps what was being referred to.

Thanks! 

```

$ dpkg --list | grep 'xml*'
ii  docbook-xml                          4.5-5                                   standard XML documentation system, for software and sys
ii  libjinglexmllite0.3-0                0.3.11-3                                Libjingle XMLLite library
ii  libjinglexmpp0.3-0                   0.3.11-3                                Libjingle XMPP library
ii  libpixman-1-0                        0.12.0-1                                pixel-manipulation library for X and cairo
ii  libxml-parser-perl                   2.36-1.1build2                          Perl module for parsing XML files
ii  libxml-twig-perl                     1:3.32-1                                Perl module for processing huge XML documents in tree m
ii  libxml-xpath-perl                    1.13-6                                  Perl module for processing XPath
ii  libxml2                              2.6.32.dfsg-4ubuntu1.2                  GNOME XML library
ii  libxml2-utils                        2.6.32.dfsg-4ubuntu1.2                  XML utilities
ii  libxmlrpc-c3                         1.06.27-1                               A lightweight RPC library based on XML and HTTP for C a
ii  libxmlrpc-c3-dev                     1.06.27-1                               A lightweight RPC library based on XML and HTTP for C a
ii  libxmu6                              2:1.0.4-1                               X11 miscellaneous utility library
ii  libxmuu1                             2:1.0.4-1                               X11 miscellaneous micro-utility library
ii  libxpm4                              1:3.5.7-1                               X11 pixmap library
ii  php5-xmlrpc                          5.2.6-2ubuntu4.3                        XML-RPC module for php5
ii  python-4suite-xml                    1.0.2-5                                 An open-source platform for XML and RDF processing
ii  python-libxml2                       2.6.32.dfsg-4ubuntu1.2                  Python bindings for the GNOME XML library
ii  python-lxml                          2.1.1-1ubuntu1                          pythonic binding for the libxml2 and libxslt libraries
ii  xml-core                             0.11ubuntu1                             XML infrastructure and XML catalog file support

```

PS - I still can't get rtorrent to compile without those errors.

---

### Post by rockstarrem on 2009-09-06
Hmm, well run these:

```

sudo apt-get remove libxmlrpc-c3 --purge      
sudo apt-get remove libxmlrpc-c3-dev --purge

```

---

### Post by scambro on 2009-09-06
Ok, so one step at a time now :)

Done - removed, purged.

---

### Post by rockstarrem on 2009-09-06
Alright, now can you do that dpkg --list | grep 'xml*' command again and post the output?

---

### Post by scambro on 2009-09-06
```

$ dpkg --list | grep 'xml*'
ii  docbook-xml                          4.5-5                                   standard XML documentation system, for software and sys
ii  libjinglexmllite0.3-0                0.3.11-3                                Libjingle XMLLite library
ii  libjinglexmpp0.3-0                   0.3.11-3                                Libjingle XMPP library
ii  libpixman-1-0                        0.12.0-1                                pixel-manipulation library for X and cairo
ii  libxml-parser-perl                   2.36-1.1build2                          Perl module for parsing XML files
ii  libxml-twig-perl                     1:3.32-1                                Perl module for processing huge XML documents in tree m
ii  libxml-xpath-perl                    1.13-6                                  Perl module for processing XPath
ii  libxml2                              2.6.32.dfsg-4ubuntu1.2                  GNOME XML library
ii  libxml2-utils                        2.6.32.dfsg-4ubuntu1.2                  XML utilities
ii  libxmu6                              2:1.0.4-1                               X11 miscellaneous utility library
ii  libxmuu1                             2:1.0.4-1                               X11 miscellaneous micro-utility library
ii  libxpm4                              1:3.5.7-1                               X11 pixmap library
ii  php5-xmlrpc                          5.2.6-2ubuntu4.3                        XML-RPC module for php5
ii  python-4suite-xml                    1.0.2-5                                 An open-source platform for XML and RDF processing
ii  python-libxml2                       2.6.32.dfsg-4ubuntu1.2                  Python bindings for the GNOME XML library
ii  python-lxml                          2.1.1-1ubuntu1                          pythonic binding for the libxml2 and libxslt libraries
ii  xml-core                             0.11ubuntu1                             XML infrastructure and XML catalog file support

```

---

### Post by rockstarrem on 2009-09-06
Looks like it's removed. Try compiling the xmlrpc again.

---

### Post by scambro on 2009-09-06
Crap, same thing:

```

rpc/libsub_rpc.a(xmlrpc.o): In function `rpc::XmlRpc::set_dialect(int)':
/home/rt/sources/libtorrent_trunk/trunk/rtorrent/src/rpc/xmlrpc.cc:535: undefined reference to `xmlrpc_registry_set_dialect'
/home/rt/sources/libtorrent_trunk/trunk/rtorrent/src/rpc/xmlrpc.cc:531: undefined reference to `xmlrpc_registry_set_dialect'
rpc/libsub_rpc.a(xmlrpc.o): In function `rpc::xmlrpc_list_entry_to_value(_xmlrpc_env*, _xmlrpc_value*, int)':
/home/rt/sources/libtorrent_trunk/trunk/rtorrent/src/rpc/xmlrpc.cc:102: undefined reference to `xmlrpc_read_i8'
rpc/libsub_rpc.a(xmlrpc.o): In function `rpc::object_to_xmlrpc(_xmlrpc_env*, torrent::Object const&)':
/home/rt/sources/libtorrent_trunk/trunk/rtorrent/src/rpc/xmlrpc.cc:368: undefined reference to `xmlrpc_i8_new'
rpc/libsub_rpc.a(xmlrpc.o): In function `rpc::xmlrpc_to_object(_xmlrpc_env*, _xmlrpc_value*, int, rpc::rt_triple<int, void*, void*>*)':
/home/rt/sources/libtorrent_trunk/trunk/rtorrent/src/rpc/xmlrpc.cc:248: undefined reference to `xmlrpc_read_i8'
collect2: ld returned 1 exit status
make[3]: *** [rtorrent] Error 1
make[3]: Leaving directory `/home/rt/sources/libtorrent_trunk/trunk/rtorrent/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/rt/sources/libtorrent_trunk/trunk/rtorrent/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rt/sources/libtorrent_trunk/trunk/rtorrent'
make: *** [all] Error 2

```

---

### Post by rockstarrem on 2009-09-06
And you compiled xmlrpc? Not just rtorrent?

---

### Post by scambro on 2009-09-06
Yeah, here's the history:

```

 1524  sudo apt-get remove libxmlrpc-c3 --purge
 1525  sudo apt-get remove libxmlrpc-c3-dev --purge
 1526  dpkg --list | grep 'xml*'
 1527  cd xmlrpc/
 1529  cd advanced/
 1531  autoconf
 1532  ./configure --prefix=/usr
 1533  make
 1536  chmod a+x install-sh
 1537  sudo make install
 1538  dpkg --list | grep 'xml*'
 1539  cd ..
 1541  cd libtorrent
 1543  cd libtorrent-0.12.5
 1544  ./configure --prefix=/usr
 1545  make
 1547  sudo make install
 1548  cd ..
 1549  cd rtorrent/
 1550  cd rtorrent-0.8.5
 1551  ./configure --prefix=/usr --with-xmlrpc-c
 1552  make
 1553  sudo make install
 1554  rtorrent
 1555  history

```

---

### Post by rockstarrem on 2009-09-06
Try doing ldconfig again... all I can think of :/.

---

### Post by scambro on 2009-09-06
nothing different....

Thanks for all the help, my first adventure into compiling rtorrent code on ubuntu is not working out well.

---

### Post by rockstarrem on 2009-09-06
Can I ask why you need it compiled? Just wondering.

---

### Post by scambro on 2009-09-06
trying to setup one of the newer webgui's that uses the new XML communication.  Unfortunately, now I've broken it to a state where I can't just install it from the archive, oops...

---

### Post by rockstarrem on 2009-09-06
Well, how did you break the archives etc? Sometimes reinstalling the web gui might be easier.

Also, I can't get rutorrent working either if that's what your talking about :P.

---

### Post by scambro on 2009-09-06
Ha - well... In all of my attempts i used a combination of /usr/local/bin and /usr/bin.  I just installed from the archive and it went to proper place, but I was running the one I was trying to compile instead.  So now I can get the one from the archive to open up - as long as I remember which is which :)

Yeah - using rutorrent.  I can get it setup and launched, but I'm getting errors in the log saying I don't have rtorrent compiled with a version above 1.11 XMLrpc-c library.  It works, just all my numbers are fubar'd over 2GB.

---

### Post by lautarop on 2010-02-25
> **scambro said:**
> Ha - well... In all of my attempts i used a combination of /usr/local/bin and /usr/bin.  I just installed from the archive and it went to proper place, but I was running the one I was trying to compile instead.  So now I can get the one from the archive to open up - as long as I remember which is which :)

Yeah - using rutorrent.  I can get it setup and launched, but I'm getting errors in the log saying I don't have rtorrent compiled with a version above 1.11 XMLrpc-c library.  It works, just all my numbers are fubar'd over 2GB.


Hey man, so how did you fix this?

I'm having the same problem; what did you do?


edit: I got it working (don't know how actually) thx anyways

---

### Post by airtower on 2010-09-02
I have the issue as well, but cannot seem to resolve.

I followed the guide here: [http://chrispenner.info/blog/2010/07/20/installing-rtorrent-rutorrent-on-ubuntu-server-10-04-lts/](http://chrispenner.info/blog/2010/07/20/installing-rtorrent-rutorrent-on-ubuntu-server-10-04-lts/)

All went well until attempting to make rtorrent. Apparently when pulling xmlrpc-c, I got a version newer than when that guide was written. Foolishly, I deleted the src directory before running make clean and now I cannot make the correct version. I am attempting to compile 1.06.40 as that was the latest stable release when the guide was written.

Make kicks out with:

```


/usr/bin/ld: XmlRpcCpp.o: relocation R_X86_64_32 against `.rodata' can not be used when making a shared object; recompile with -fPIC
XmlRpcCpp.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libxmlrpc_cpp.so.3.06] Error 1
make[2]: Leaving directory `/home/brian/tmp/xmlrpc-c-1.06.40/src/cpp'
make[1]: *** [cpp/all] Error 2
make[1]: Leaving directory `/home/brian/tmp/xmlrpc-c-1.06.40/src'
make: *** [src/all] Error 2

```

I've tried backing out and running ldconfig multiple times, but no luck

---

