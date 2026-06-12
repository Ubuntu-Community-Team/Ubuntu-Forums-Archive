---
title: "Problem Installing GLIB 2.5.6"
date: 2010-07-14
forum: General Help
---

### Post by gettingbored on 2010-07-14
So I'm trying to install Screem HTML editor on my freshly installed copy of Ubuntu 10.04 and I'm having some problems. I downloaded the tar.gz file from their site. Then I looked up how to install it and installed the build-essentials etc. When I went to install Screem I moved the tar.gz to the /usr/local/src directory and extracted it. Then I opened up the terminal and moved to the directory and ran ```
'./configure'
``` and it said this: 

```

checking for GLIB - version >= 2.5.6... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error:
*** GLIB 2.5.6 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/.

```So I went to [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/) and looked around for GLIB 2.5.6 and couldn't find it. So I googled it and found a mirror of it at [http://www.filewatcher.com/m/glib-2.5.6.tar.bz2.2294351.0.0.html](http://www.filewatcher.com/m/glib-2.5.6.tar.bz2.2294351.0.0.html) and I downloaded it. Then I did the same with GLIB that I did with Screem and installed it by first running 
```
./configure
```and then
```
make
```All went well and I rebooted my system. Then I went back to install Screem and it says I still don't have GLIB...

Any help?

---

### Post by gettingbored on 2010-07-15
Bump

---

### Post by eronisko on 2010-08-03
Hi, had the same problem. What you need is to install the **glib2-devel** package. That got me through that error, but unfortunately there are more unmet requirements in my case :-)

---

### Post by luigi_mb on 2010-08-03
> **gettingbored said:**
> So I'm trying to install Screem HTML editor on my freshly installed copy of Ubuntu 10.04 and I'm having some problems. I downloaded the tar.gz file from their site. Then I looked up how to install it and installed the build-essentials etc. When I went to install Screem I moved the tar.gz to the /usr/local/src directory and extracted it. Then I opened up the terminal and moved to the directory and ran ```
'./configure'
``` and it said this: 

```

checking for GLIB - version >= 2.5.6... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error:
*** GLIB 2.5.6 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/.

```So I went to [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/) and looked around for GLIB 2.5.6 and couldn't find it. So I googled it and found a mirror of it at [http://www.filewatcher.com/m/glib-2.5.6.tar.bz2.2294351.0.0.html](http://www.filewatcher.com/m/glib-2.5.6.tar.bz2.2294351.0.0.html) and I downloaded it. Then I did the same with GLIB that I did with Screem and installed it by first running 
```
./configure
```and then
```
make
```All went well and I rebooted my system. Then I went back to install Screem and it says I still don't have GLIB...

Any help?

Probably the default configuration assumes the files will be installed in /usr/local/... . Sometimes this creates problems because /usr/local/lib is not on the library load path.  Try to configure both screem and glib sources with

```

./configure --prefix=/usr

```


/luigi

---

