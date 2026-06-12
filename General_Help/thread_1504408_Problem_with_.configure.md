---
title: "Problem with ./configure"
date: 2010-06-08
forum: General Help
---

### Post by eNdeRam on 2010-06-08
I'm trying to compile nmap and i keep getting this error when i run ./configure. im a nub and dont understand what its calling for. Any help is welcome.

output from terminal

sean@ubuntu:~/etc/nmap/nmap-5.21$ ./configure
checking whether NLS is requested... yes
checking build system type... ./config.guess: unable to guess system type

This script, last modified 2009-06-10, has failed to recognize
the operating system you are using. It is advised that you
download the most up to date version of the config scripts from

  [http://git.savannah.gnu.org/gitweb/?p=config.git;a=blob_plain;f=config.guess;hb=HEAD](http://git.savannah.gnu.org/gitweb/?p=config.git;a=blob_plain;f=config.guess;hb=HEAD)
and
  [http://git.savannah.gnu.org/gitweb/?p=config.git;a=blob_plain;f=config.sub;hb=HEAD](http://git.savannah.gnu.org/gitweb/?p=config.git;a=blob_plain;f=config.sub;hb=HEAD)

If the version you run (./config.guess) is already up to date, please
send the following data and any information you think might be
pertinent to <config-patches@gnu.org> in order to provide the needed
information to handle your system.

config.guess timestamp = 2009-06-10

uname -m = i686
uname -r = 2.6.32-22-generic
uname -s = Linux
uname -v = #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010

/usr/bin/uname -p = 
/bin/uname -X     = 

hostinfo               = 
/bin/universe          = 
/usr/bin/arch -k       = 
/bin/arch              = 
/usr/bin/oslevel       = 
/usr/convex/getsysinfo = 

UNAME_MACHINE = i686
UNAME_RELEASE = 2.6.32-22-generic
UNAME_SYSTEM  = Linux
UNAME_VERSION = #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010
configure: error: cannot guess build type; you must specify one


P.S. wasnt sure if i should have posted here or the security board...sorry if its the wrong place

---

### Post by darolu on 2010-06-08
Seems that the headers confuse your ./configure.guess, the online documentation or readme file should have a set of options so you can specify the needed values manually, read them all.. if you want/need to compile.

The nmap program is in the repositories though, you can install with:
```
sudo apt-get install nmap
```

Or download the .deb file from: [http://packages.ubuntu.com/lucid/nmap](http://packages.ubuntu.com/lucid/nmap)

---

### Post by eNdeRam on 2010-06-08
ok thanks i guess...
just wanted to most updated version
any chance u know when the repo version will get updated?

---

