---
title: "Unable to resolve package errors"
date: 2009-11-30
forum: General Help
---

### Post by gwpritch on 2009-11-30
I have been trying to install K3b on ubuntu via apt-get. Most of the packages were installed fine, but at the end I got:

```
Setting up liblua50 (5.0.3-3) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing liblua50 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of liblualib50:
 liblualib50 depends on liblua50 (>= 5.0.3); however:
  Package liblua50 is not configured yet.
dpkg: error processing liblualib50 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs4c2a:
 kdelibs4c2a depends on liblua50 (>= 5.0.3); however:
  Package liblua50 is not configured yet.
 kdelibs4c2a depends on liblualib50 (>= 5.0.3); however:
  Package liblualib50 is not configured yet.
dpkg: error processing kdelibs4c2a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libk3b3:
 libk3b3 depends on kdelibs4c2a (>= 4:3.5.9); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libk3b3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of k3b:
 k3b depends on kdelibs4c2a (>= 4:3.5.9); however:
  Package kdelibs4c2a is not configureNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                No apport report written because the error message indicates its a followup error from a previous failure.
          No apport report written because MaxReports is reached already
                                                                        No apport report written because MaxReports is reached already
                                                      No apport report written because MaxReports is reached already
                                    d yet.
 k3b depends on libk3b3 (= 1.0.5+kde4svn935857+really1.0.5-3ubuntu5); however:
  Package libk3b3 is not configured yet.
dpkg: error processing k3b (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libk3b3-extracodecs:
 libk3b3-extracodecs depends on kdelibs4c2a (>= 4:3.5.9); however:
  Package kdelibs4c2a is not configured yet.
 libk3b3-extracodecs depends on libk3b3; however:
  Package libk3b3 is not configured yet.
dpkg: error processing libk3b3-extracodecs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 liblua50
 liblualib50
 kdelibs4c2a
 libk3b3
 k3b
 libk3b3-extracodecs
```

Now, I can't do anything with these packages. I've tried removing and reinstalling but I just keep getting the same errors.
Can anyone help?

---

### Post by NoaHall on 2009-11-30
Hm. Try running ```
sudo apt-get update && sudo apt-get dist-upgrade 
```

If that doesn't work, try ```
sudo dpkg --configure -a
```

---

### Post by gwpritch on 2009-11-30
Tried both but no joy. I just get an error and informed that the packages were left unconfigured.

---

### Post by NoaHall on 2009-11-30
Hm. Now try ```
sudo ldconfig
``` then run the commands again if installing doesn't work still.
If that doesn't work, try ```
 sudo apt-get clean && sudo apt-get autoclean && sudo apt-get autoremove
```

---

### Post by gwpritch on 2009-11-30
sudo ldconfig gives:
```

/sbin/ldconfig.real: file /usr/lib/libqt-mt.so.3.3 is truncated

/sbin/ldconfig.real: File /usr/lib/liblualib50.so.5.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/liblua50.so.5.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/liblua50.so.5 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/liblualib50.so.5 is empty, not checked.
/sbin/ldconfig.real: file /usr/lib/libqt-mt.so.3.3.8 is truncated

/sbin/ldconfig.real: file /usr/lib/libqt-mt.so.3 is truncated
```

sudo apt-get autoremove gives the same errors I started with.

---

### Post by NoaHall on 2009-11-30
Oh no... Not this problem. I've encountered it before with another user - I couldn't find a way to fix it, but to do a fresh install. 

Have you deleted any library files by hand, by any chance?

---

### Post by gwpritch on 2009-11-30
That's encouraging..lol.
No I actually was doing a minimal install, and everything was going great until I tried to install kde apps. Everything else still works fine, I just get these error messages whenever I use apt-get or synaptic...and of course the kde apps don't work

---

### Post by raktarok on 2009-11-30
Let's see if this can be solved...

Post the output of the following:
```
sudo ls /var/lib/dpkg/info/liblua50*
```

If the files exist, post the contents of the file ending in .postinst
```
sudo cat /var/lib/dpkg/info/liblua50.postinst 
```
Because of the "exec format error", there could be something wrong with this file.

**OR** before these steps, you could try this:
```
sudo dpkg --remove --force-remove-reinstreq liblua50
```
And then trying to reinstall again.

---

### Post by NoaHall on 2009-11-30
Okay, here's a list of things you could try -

```
sudo apt-get -f install K3b
sudo apt-get --fix-missing install k3b
cat /etc/apt/sources.list
```

The last one might be useful if you still have a problem.

---

### Post by gwpritch on 2009-11-30
Ok...I think I'm making progress I ran the following:.

```
sudo dpkg --remove --force-remove-reinstreq liblua50

```

then tried```
 sudo apt-get -f install
``` and got:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  liblua50
The following NEW packages will be installed:
  liblua50
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 83.9kB of archives.
After this operation, 143kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://ubuntu.mirror.iweb.ca jaunty/main liblua50 5.0.3-3 [48.7kB]
Get:2 http://ubuntu.mirror.iweb.ca jaunty/main liblualib50 5.0.3-3 [35.1kB]
Fetched 83.9kB in 0s (255kB/s)                         
Selecting previously deselected package liblua50.
(Reading database ... 73915 files and directories currently installed.)
Unpacking liblua50 (from .../liblua50_5.0.3-3_i386.deb) ...
Selecting previously deselected package liblualib50.
Preparing to replace liblualib50 5.0.3-3 (using .../liblualib50_5.0.3-3_i386.deb) ...
Unpacking replacement liblualib50 ...
dpkg (subprocess): unable to execute old post-removal script: Exec format error
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
Setting up liblua50 (5.0.3-3) ...

Setting up liblualib50 (5.0.3-3) ...

Setting up kdelibs4c2a (4:3.5.10.dfsg.1-1ubuntu8.2) ...

Setting up libk3b3 (1.0.5+kde4svn935857+really1.0.5-3ubuntu5) ...

Setting up libk3b3-extracodecs (1.0.5+kde4svn935857+really1.0.5-3ubuntu5) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: file /usr/lib/libqt-mt.so.3.3 is truncated

/sbin/ldconfig.real: file /usr/lib/libqt-mt.so.3.3.8 is truncated

/sbin/ldconfig.real: file /usr/lib/libqt-mt.so.3 is truncated


```

---

### Post by raktarok on 2009-11-30
Yeah, it would have worked too if you had removed the file /var/lib/dpkg/info/liblua50.postinst before trying that other command. 

Anyway, this new error seems to be an entirely different problem, and I don't have any good suggestions for this one. But you could try removing and installing the package **libqt3-mt**(which provides the file libqt-mt.so.3.3). Proceed carefully though, this may remove other packages in the process, and you will have to reinstall them again afterwards.

---

### Post by gwpritch on 2009-11-30
So I removed libqt3-mt which also removed the packages I was having trouble with. I reinstalled k3b and all packages were installed normally.
Thanks guys for all your help.

---

### Post by raktarok on 2009-11-30
Glad to hear that!

---

### Post by karlmp on 2009-12-01
|

---

