---
title: "broke my apt-get?"
date: 2011-12-02
forum: General Help
---

### Post by Imnotroot on 2011-12-02
i tried to install the code block dpk packages using the sudo dpkg -i *.dep command however i now seem to have a problem.

It tells me i have unsolved dependencies, and that i should fixe those with sudo apt-get -f install.

here is the output:

```


root@pavilion:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libc6-i386 lib32gcc1 dkms patch
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  codeblocks-contrib codeblocks-dev libwxsmithlib-dev
The following NEW packages will be installed:
  libwxsmithlib-dev
The following packages will be upgraded:
  codeblocks-contrib codeblocks-dev
2 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
3 not fully installed or removed.
Need to get 0 B/3,837 kB of archives.
After this operation, 2,314 kB of additional disk space will be used.
Do you want to continue [Y/n]?  Y

(Reading database ... 180388 files and directories currently installed.)
Preparing to replace codeblocks-contrib 10.05-1 (using .../codeblocks-contrib_10.05-2_amd64.deb) ...
Unpacking replacement codeblocks-contrib ...
dpkg: error processing /var/cache/apt/archives/codeblocks-contrib_10.05-2_amd64.deb (--unpack):
 trying to overwrite '/usr/include/wxSmithContribItems/wxchart/wxchart-1.0/include/wx/axis.h', which is also in package codeblocks-contrib-common 10.05-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to replace codeblocks-dev 10.05-1 (using .../codeblocks-dev_10.05-2_amd64.deb) ...
Unpacking replacement codeblocks-dev ...
dpkg: error processing /var/cache/apt/archives/codeblocks-dev_10.05-2_amd64.deb (--unpack):
 trying to overwrite '/usr/include/codeblocks/scripting/sqplus/SqPlusConst.h', which is also in package codeblocks-headers 10.05-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libwxsmithlib-dev (from .../libwxsmithlib-dev_10.05-2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libwxsmithlib-dev_10.05-2_amd64.deb (--unpack):
 trying to overwrite '/usr/include/wxsmith/contrib/include/wx/propgrid/advprops.h', which is also in package wxsmith-headers 10.05-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/codeblocks-contrib_10.05-2_amd64.deb
 /var/cache/apt/archives/codeblocks-dev_10.05-2_amd64.deb
 /var/cache/apt/archives/libwxsmithlib-dev_10.05-2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)




```

Anyone know how i can fix this?

Thanks in advance!

---

### Post by Imnotroot on 2011-12-03
anybody? :(

---

### Post by rayian on 2011-12-03
You could try installing the three packages manually.
sudo apt-get install the three packages listed above.
 
Worth a try

---

### Post by BC59 on 2011-12-03
Run
```
sudo dpkg --configure -a

```

and then

```
sudo apt-get -f install
```

to ensure if the packages are completely installed and configured.

---

### Post by BC59 on 2011-12-03
And don't forget to run

```
sudo apt-get autoremove
```

to clean the unnecessary packages.

---

### Post by Imnotroot on 2011-12-03
sudo dpkg --configure -a

gives me the following output:

```

sudo dpkg --configure -a

dpkg: dependency problems prevent configuration of codeblocks-dev:
 codeblocks-dev depends on libcodeblocks0 (= 10.05-1); however:
  Version of libcodeblocks0 on system is 10.05-2.
dpkg: error processing codeblocks-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of codeblocks-contrib:
 codeblocks-contrib depends on libwxsmithlib0 (= 10.05-1); however:
  Version of libwxsmithlib0 on system is 10.05-2.
 codeblocks-contrib depends on codeblocks (= 10.05-1); however:
  Version of codeblocks on system is 10.05-2.
dpkg: error processing codeblocks-contrib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwxsmithlib0-dev:
 libwxsmithlib0-dev depends on libwxsmithlib-dev (= 10.05-2); however:
  Package libwxsmithlib-dev is not installed.
dpkg: error processing libwxsmithlib0-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 codeblocks-dev
 codeblocks-contrib
 libwxsmithlib0-dev

```

---

### Post by BC59 on 2011-12-03
> **Imnotroot said:**
> sudo dpkg --configure -a

gives me the following output:

```

sudo dpkg --configure -a

dpkg: dependency problems prevent configuration of codeblocks-dev:
 codeblocks-dev depends on libcodeblocks0 (= 10.05-1); however:
  Version of libcodeblocks0 on system is 10.05-2.
dpkg: error processing codeblocks-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of codeblocks-contrib:
 codeblocks-contrib depends on libwxsmithlib0 (= 10.05-1); however:
  Version of libwxsmithlib0 on system is 10.05-2.
 codeblocks-contrib depends on codeblocks (= 10.05-1); however:
  Version of codeblocks on system is 10.05-2.
dpkg: error processing codeblocks-contrib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwxsmithlib0-dev:
 libwxsmithlib0-dev depends on libwxsmithlib-dev (= 10.05-2); however:
  Package libwxsmithlib-dev is not installed.
dpkg: error processing libwxsmithlib0-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 codeblocks-dev
 codeblocks-contrib
 libwxsmithlib0-dev

```

Look if you can unblock the dpkg

```
sudo rm -rf /var/lib/apt/lists/partial/*
```

---

### Post by Imnotroot on 2011-12-03
no error when i run that command however running sudo dpkg --configure -a after that still gives the same error

---

### Post by BC59 on 2011-12-03
Try then

```
sudo apt-get -f install
```

and

```
sudo apt-get update
```

---

### Post by Imnotroot on 2011-12-03
Grrrr!

```

    @pavilion:~$ sudo rm -rf /var/lib/apt/lists/partial/*
    @pavilion:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libc6-i386 lib32gcc1 dkms patch
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  codeblocks-contrib codeblocks-dev libwxsmithlib-dev
The following NEW packages will be installed:
  libwxsmithlib-dev
The following packages will be upgraded:
  codeblocks-contrib codeblocks-dev
2 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
3 not fully installed or removed.
Need to get 0 B/3,837 kB of archives.
After this operation, 2,314 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 180388 files and directories currently installed.)
Preparing to replace codeblocks-contrib 10.05-1 (using .../codeblocks-contrib_10.05-2_amd64.deb) ...
Unpacking replacement codeblocks-contrib ...
dpkg: error processing /var/cache/apt/archives/codeblocks-contrib_10.05-2_amd64.deb (--unpack):
 trying to overwrite '/usr/include/wxSmithContribItems/wxchart/wxchart-1.0/include/wx/axis.h', which is also in package codeblocks-contrib-common 10.05-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to replace codeblocks-dev 10.05-1 (using .../codeblocks-dev_10.05-2_amd64.deb) ...
Unpacking replacement codeblocks-dev ...
dpkg: error processing /var/cache/apt/archives/codeblocks-dev_10.05-2_amd64.deb (--unpack):
 trying to overwrite '/usr/include/codeblocks/scripting/sqplus/SqPlusConst.h', which is also in package codeblocks-headers 10.05-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libwxsmithlib-dev (from .../libwxsmithlib-dev_10.05-2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libwxsmithlib-dev_10.05-2_amd64.deb (--unpack):
 trying to overwrite '/usr/include/wxsmith/contrib/include/wx/propgrid/advprops.h', which is also in package wxsmith-headers 10.05-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/codeblocks-contrib_10.05-2_amd64.deb
 /var/cache/apt/archives/codeblocks-dev_10.05-2_amd64.deb
 /var/cache/apt/archives/libwxsmithlib-dev_10.05-2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by BC59 on 2011-12-03
Try this

```
sudo rm -rf /var/cache/apt/archives/*
```

and then```
sudo apt-get update
```

---

### Post by Imnotroot on 2011-12-03
that worked, now what?

---

### Post by BC59 on 2011-12-03
Now run again the 

```
sudo dpkg --configure -a
```

and

```
sudo apt-get -f install
```

to ensure your system is ok

---

### Post by Imnotroot on 2011-12-03
no luck :(

```

peter@pavilion:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of codeblocks-dev:
 codeblocks-dev depends on libcodeblocks0 (= 10.05-1); however:
  Version of libcodeblocks0 on system is 10.05-2.
dpkg: error processing codeblocks-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of codeblocks-contrib:
 codeblocks-contrib depends on libwxsmithlib0 (= 10.05-1); however:
  Version of libwxsmithlib0 on system is 10.05-2.
 codeblocks-contrib depends on codeblocks (= 10.05-1); however:
  Version of codeblocks on system is 10.05-2.
dpkg: error processing codeblocks-contrib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwxsmithlib0-dev:
 libwxsmithlib0-dev depends on libwxsmithlib-dev (= 10.05-2); however:
  Package libwxsmithlib-dev is not installed.
dpkg: error processing libwxsmithlib0-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 codeblocks-dev
 codeblocks-contrib
 libwxsmithlib0-dev
peter@pavilion:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libc6-i386 lib32gcc1 dkms patch
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  codeblocks-contrib codeblocks-dev libwxsmithlib-dev
The following NEW packages will be installed:
  libwxsmithlib-dev
The following packages will be upgraded:
  codeblocks-contrib codeblocks-dev
2 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
3 not fully installed or removed.
Need to get 3,837 kB of archives.
After this operation, 2,314 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://nl.archive.ubuntu.com/ubuntu/ oneiric/universe codeblocks-contrib amd64 10.05-2 [3,418 kB]
Get:2 http://nl.archive.ubuntu.com/ubuntu/ oneiric/universe codeblocks-dev amd64 10.05-2 [220 kB]
Get:3 http://nl.archive.ubuntu.com/ubuntu/ oneiric/universe libwxsmithlib-dev amd64 10.05-2 [199 kB]
Fetched 3,837 kB in 4s (841 kB/s)      
(Reading database ... 180388 files and directories currently installed.)
Preparing to replace codeblocks-contrib 10.05-1 (using .../codeblocks-contrib_10.05-2_amd64.deb) ...
Unpacking replacement codeblocks-contrib ...
dpkg: error processing /var/cache/apt/archives/codeblocks-contrib_10.05-2_amd64.deb (--unpack):
 trying to overwrite '/usr/include/wxSmithContribItems/wxchart/wxchart-1.0/include/wx/axis.h', which is also in package codeblocks-contrib-common 10.05-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to replace codeblocks-dev 10.05-1 (using .../codeblocks-dev_10.05-2_amd64.deb) ...
Unpacking replacement codeblocks-dev ...
dpkg: error processing /var/cache/apt/archives/codeblocks-dev_10.05-2_amd64.deb (--unpack):
 trying to overwrite '/usr/include/codeblocks/scripting/sqplus/SqPlusConst.h', which is also in package codeblocks-headers 10.05-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libwxsmithlib-dev (from .../libwxsmithlib-dev_10.05-2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libwxsmithlib-dev_10.05-2_amd64.deb (--unpack):
 trying to overwrite '/usr/include/wxsmith/contrib/include/wx/propgrid/advprops.h', which is also in package wxsmith-headers 10.05-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/codeblocks-contrib_10.05-2_amd64.deb
 /var/cache/apt/archives/codeblocks-dev_10.05-2_amd64.deb
 /var/cache/apt/archives/libwxsmithlib-dev_10.05-2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by BC59 on 2011-12-03
Is your computer 64 bits?

---

### Post by BC59 on 2011-12-03
Try this

```
sudo dpkg --force-all -P codeblocks-contrib_10.05-2_amd64.deb codeblocks-dev_10.05-2_amd64.deb libwxsmithlib-dev_10.05-2_amd64.deb
```

---

### Post by Imnotroot on 2011-12-03
```
sudo dpkg --force-all -P codeblocks-contrib_10.05-2_amd64.deb codeblocks-dev_10.05-2_amd64.deb libwxsmithlib-dev_10.05-2_amd64.deb
dpkg: error: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
```

yes my system is 64bit

---

### Post by BC59 on 2011-12-03
Ok let's see now

```
sudo dpkg --force-all -P codeblocks-contrib codeblocks-dev
```

---

### Post by Imnotroot on 2011-12-03
sudo dpkg --force-all -P codeblocks-contrib codeblocks-dev
(Reading database ... 180387 files and directories currently installed.)
Removing codeblocks-contrib ...
Removing codeblocks-dev ...

---

### Post by BC59 on 2011-12-03
Run again sudo dpkg --configure -a and sudo apt-get -f install

---

### Post by Imnotroot on 2011-12-03
sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libwxsmithlib0-dev:
 libwxsmithlib0-dev depends on libwxsmithlib-dev (= 10.05-2); however:
  Package libwxsmithlib-dev is not installed.
dpkg: error processing libwxsmithlib0-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libwxsmithlib0-dev

---

### Post by BC59 on 2011-12-03
Ok let's install libwxsmithlib-dev the same way

```
sudo dpkg --force-all -P libwxsmithlib-dev
```

---

### Post by Imnotroot on 2011-12-03
```

peter@pavilion:~$ sudo dpkg --force-all -P libwxsmithlib-dev
dpkg: warning: there's no installed package matching libwxsmithlib-dev
peter@pavilion:~$ sudo dpkg --force-all -P libwxsmithlib0-dev
(Reading database ... 180306 files and directories currently installed.)
Removing libwxsmithlib0-dev ...
peter@pavilion:~$ sudo dpkg --configure -a
peter@pavilion:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libc6-i386 lib32gcc1 dkms patch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
peter@pavilion:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dkms lib32gcc1 libc6-i386 patch
0 upgraded, 0 newly installed, 4 to remove and 2 not upgraded.
After this operation, 10.7 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 180303 files and directories currently installed.)
Removing dkms ...
Removing lib32gcc1 ...
Removing libc6-i386 ...
Removing patch ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

its fixed!

thanks a LOT for your help! marking as solved

---

### Post by BC59 on 2011-12-03
Well the dpkg was blocked very hard!

You are welcome.

---

