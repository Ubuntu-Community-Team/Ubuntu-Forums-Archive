---
title: "Problem in c++ program compilation even g++ already installed"
date: 2012-03-06
forum: General Help
---

### Post by arslanafzal321 on 2012-03-06
I'm trying to compile my c++ file in ubuntu but couldn't do it. The problem I'm getting is
I have g++ and gcc already installed in my ubuntu 10.11
For example if saved the file name as one.cpp 
and on terminal when i go to compile it and type it 
```
 g++ one.cpp -o one 
```I get in my terminal as below.
```
The program 'g++' can be found in following packages:
*g++
*pentium-builder
try sudo apt-get install <selected package>
```Even i typed the above command for both packages and it shows all my program already up to date.

Then even i try again i get the same result.
So what should i do? Please help. :confused:

---

### Post by electrojustin on 2012-03-06
Perhaps try checking /usr/bin to ensure the binaries are indeed there.

---

### Post by scottstensland on 2012-03-06
sudo apt-get install build-essential checkinstall

will give you the g++ compiler

---

### Post by arslanafzal321 on 2012-03-06
**@****electrojustin**
I have checked binaries and that is all i get below: I don't know what i have to check in it.
```
 bash                  dbus-daemon     initctl2dot  nano              pidof                    tar
bunzip2               dbus-uuidgen    ip           nc                ping                     tempfile
busybox               dd              kbd_mode     nc.openbsd        ping6                    touch
bzcat                 df              kill         netcat            plymouth                 true
bzcmp                 dir             less         netstat           plymouth-upstart-bridge  ulockmgr_server
bzdiff                dmesg           lessecho     nisdomainname     ps                       umount
bzegrep               dnsdomainname   lessfile     ntfs-3g           pwd                      uname
bzexe                 domainname      lesskey      ntfs-3g.probe     rbash                    uncompress
bzfgrep               dumpkeys        lesspipe     ntfs-3g.secaudit  readlink                 unicode_start
bzgrep                echo            ln           ntfs-3g.usermap   rm                       vdir
bzip2                 ed              loadkeys     ntfscat           rmdir                    vmmouse_detect
bzip2recover          egrep           login        ntfsck            rnano                    which
bzless                false           lowntfs-3g   ntfscluster       run-parts                ypdomainname
bzmore                fgconsole       ls           ntfscmp           sed                      zcat
cat                   fgrep           lsblk        ntfsdecrypt       setfacl                  zcmp
chacl                 findmnt         lsmod        ntfsdump_logfile  setfont                  zdiff
chgrp                 fuser           mkdir        ntfsfix           setupcon                 zegrep
chmod                 fusermount      mknod        ntfsinfo          sh                       zfgrep
chown                 getfacl         mktemp       ntfsls            sh.distrib               zforce
chvt                  grep            more         ntfsmftalloc      sleep                    zgrep
cp                    gunzip          mount        ntfsmove          static-sh                zless
cpio                  gzexe           mountpoint   ntfstruncate      stty                     zmore
dash                  gzip            mt           ntfswipe          su                       znew
date                  hostname        mt-gnu       open              sync
dbus-cleanup-sockets  init-checkconf  mv           openvt            tailf





```**@****scottstensland**
I have typed your command 
```
 sudo apt-get install build-essential checkinstall 
```and got an error as below;

```
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package build-essential
E: Unable to locate package checkinstall

```So what I have to do now? My problem is not yet solved. :o

---

### Post by mcclary on 2012-03-07
It sounds like your package database - in particular, the list of repositories - may be corrupted.  Before trying to fix that, go to the GUI for the package manager.  
(&quot;System->Administration->Synaptic Package Manager&quot;, at least on maverick).   

Try to install build-essential.  (I just did that and it was all I needed to get /usr/bin/g++ installed and working.)

If you get similar complaints using the GUI it's time to look into fixing any corruption.  Once you've got a g++ installed try this test: 

% cat > hello.cc
#include <iostream>
using namespace std;

main() {
     cout << "Hello, world!\n";
}
^D
% make hello
% ./hello

If you're using csh or tcsh don't forget to rehash after installing.

---

### Post by arslanafzal321 on 2012-03-13
The problem is solved.
I think the ubuntu setup was corrupt.
So i reinstalled it. then installed g++ and it worked.
Thank you all :guitar:

---

### Post by Mark Phelps on 2012-03-13
Glad to see you got it working.  So please use the Thread Tools at the top of this thread to mark this one as SOLVED.  thanks

---

### Post by arslanafzal321 on 2012-03-14
I did That. Thank you!

---

