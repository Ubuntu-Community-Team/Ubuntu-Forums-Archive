---
title: "Cannot install mercurial"
date: 2009-09-29
forum: General Help
---

### Post by RoyT on 2009-09-29
I have tried using apt-get and easy_install. Please see log below.

mylogin@my-laptop:~$ hg -help
The program 'hg' is currently not installed.  You can install it by typing:
sudo apt-get install mercurial
You will have to enable the component called 'universe'
bash: hg: command not found
mylogin@my-laptop:~$ sudo apt-get install mercurial
[sudo] password for rtouzeau: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mercurial is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mercurial has no installation candidate
mylogin@my-laptop:~$ easy_install -U mercurial
error: can't create or remove files in install directory

The following error occurred while trying to add or remove files in the
installation directory:

    [Errno 13] Permission denied: '/usr/local/lib/python2.6/dist-packages/test-easy-install-3996.write-test'

The installation directory you specified (via --install-dir, --prefix, or
the distutils default setting) was:

    /usr/local/lib/python2.6/dist-packages/

Perhaps your account does not have write access to this directory?  If the
installation directory is a system-owned directory, you may need to sign in
as the administrator or "root" account.  If you do not have administrative
access to this machine, you may wish to choose a different installation
directory, preferably one that is listed in your PYTHONPATH environment
variable.

For information on other options, you may wish to consult the
documentation at:

  [http://peak.telecommunity.com/EasyInstall.html](http://peak.telecommunity.com/EasyInstall.html)

Please make the appropriate changes for your system and try again.

mylogin@my-laptop:~$ sudo easy_install -U mercurial
Searching for mercurial
Reading [http://pypi.python.org/simple/mercurial/](http://pypi.python.org/simple/mercurial/)
Reading [http://www.selenic.com/mercurial](http://www.selenic.com/mercurial)
Reading [http://mercurial.selenic.com/](http://mercurial.selenic.com/)
Best match: mercurial 1.3.1
Downloading [http://mercurial.selenic.com/release/mercurial-1.3.1.tar.gz](http://mercurial.selenic.com/release/mercurial-1.3.1.tar.gz)
Processing mercurial-1.3.1.tar.gz
Running mercurial-1.3.1/setup.py -q bdist_egg --dist-dir /tmp/easy_install-LC6QlL/mercurial-1.3.1/egg-dist-tmp-OBmpf3
mercurial/base85.c:12:20: error: Python.h: No such file or directory
mercurial/base85.c: In function ‘b85prep’:
mercurial/base85.c:23: warning: implicit declaration of function ‘memset’
mercurial/base85.c:23: warning: incompatible implicit declaration of built-in function ‘memset’
mercurial/base85.c: At top level:
mercurial/base85.c:28: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mercurial/base85.c:76: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
mercurial/base85.c:141: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘methods’
mercurial/base85.c:150: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘initbase85’
error: Setup script exited with error: command 'gcc' failed with exit status 1

---

### Post by sedawk on 2009-09-29
In the file /etc/apt/sources.list there are different
sources listed where you can download packages from.

It looks like you have to uncomment the "universe" entries if you
want to install mercurial.

```

sudo cp /etc/apt/sources.list /root/sources.list.bkup
#EDIT via GUI:
gksu gedit /etc/apt/sources.list
#or EDIT via command line:
sudo vi /etc/apt/sources.list

```

---

### Post by RoyT on 2009-09-29
Thanks. Problem is fixed. (I did not know what that "universe" message meant.)

---

### Post by enricogiurin on 2009-10-13
> **sedawk said:**
> In the file /etc/apt/sources.list there are different
sources listed where you can download packages from.

It looks like you have to uncomment the "universe" entries if you
want to install mercurial.



I had the same problem but un-commenting  all the "universe" entries didn't help. I solved that problem installing python 2.6 dev using:

 **sudo apt-get install python-dev**


After that I was able to complete the installation of mercurial 1.3.1 using the command 

 **sudo easy_install -U mercuria**l

---

