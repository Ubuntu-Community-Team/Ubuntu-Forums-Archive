---
title: "Trying to compile mc"
date: 2009-11-20
forum: General Help
---

### Post by ray field on 2009-11-20
Since I want to use Midnight Commander to access Samba shares, and Samba support is disabled in the distributed version, I downloaded the source to attempt to compile it with the option `--with-samba'.  I've followed the directions in [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo), eg, 

```
sudo apt-get install build-essential checkinstall
```

but from within the directory /usr/local/src/mc-4.6.2~git20080311/src, when I issue 
```

./configure

```
I get
```

bash: ./configure: No such file or directory
```

what am I missing?

---

### Post by mc4man on 2009-11-20
A few things
As far as a ./configure you're 1 directory too deep, at this prompt you'll probably get a configure
/usr/local/src/mc-4.6.2~git20080311

You may want to consider a newer source, see here 
[http://www.midnight-commander.org/downloads](http://www.midnight-commander.org/downloads)

After extracting look in the main folder for an install file, read

Running this first may also be helpful, at source folder prompt, not src prompt
./configure --help

After running a ./configure <options, if any>, scroll back thru and look at any warnings or "no's" to see if there's anything you need to address

Ex. of the prompt you want for configure and make with recent source 
> 
doug@doug-laptop:~/Downloads/[COLOR="Blue"]mc-4.7.0-pre4$[/COLOR] ./configure --help

---

### Post by ray field on 2009-11-20
Thanks for the reply.  Somehow there was no configure file in the package I d/l'd, so I snared mc-4.7.0-pre4.tar.gz and started with that.  this time 
```

./configure --with-samba
```

proceeded.  I redirected output into a file, and got these warnings 

```
raphael@SwannU:/usr/local/src/mc-4.7.0-pre4$ ./configure --with-samba >jonah
configure: WARNING: doxygen not found - will not generate any doxygen documentation
config.status: WARNING:  'intl/Makefile.in' seems to ignore the --datarootdir setting
config.status: WARNING:  'po/Makefile.in.in' seems to ignore the --datarootdir setting
config.status: WARNING:  'Makefile.in' seems to ignore the --datarootdir setting
```

nevertheless I tried to make & then did 

```
sudo checkinstall
```

when I try mc, I get

```
raphael@SwannU:/usr/local/src/mc-4.7.0-pre4$ mc
Segmentation fault
```

---

