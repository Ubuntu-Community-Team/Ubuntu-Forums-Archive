---
title: "problem in ECB installation - Emacs"
date: 2011-05-17
forum: General Help
---

### Post by bengaltiger on 2011-05-17
Hi,

I am using Ubuntu 11.04

When I try to install ECB, getting following error.

Any way to solve.

-------------------
sudo apt-get install ecb
[sudo] password for abcd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ecb : Depends: eieio (>= 1.1) but it is not installable
       Depends: semantic (>= 1.1) but it is not installable
       Depends: speedbar-beta (>= 1.1) but it is not installable or
                speedbar (>= 1.1) but it is not installable
       Depends: cedet-contrib (>= 1.1) but it is not installable
       Depends: cogre (>= 1.1) but it is not installable
E: Broken packages

----

Thanks
-BT

---

### Post by __Sun__ on 2011-05-17
Did you try:
```
sudo apt-get --fix-missing
```

---

### Post by bengaltiger on 2011-05-17
you mean..

sudo apt-get install ecb --fix-missing

tried no help.

-BT

---

### Post by bengaltiger on 2011-05-20
still looking some help / reply.

anybdy using ECB in emacs in Ubuntu 11?

Thanks,
BT

---

### Post by linuxinstalledfromhdd on 2011-05-20
~$ sudo apt-get install ecb
[sudo] password for linux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cedet-common cedet-contrib cogre ede eieio emacs emacs23 emacs23-bin-common
  emacs23-common libanthy0 libm17n-0 libotf0 m17n-contrib m17n-db semantic speedbar
Suggested packages:
  emacs23-el m17n-docs w3-el-e21
The following NEW packages will be installed:
  cedet-common cedet-contrib cogre ecb ede eieio emacs emacs23 emacs23-bin-common
  emacs23-common libanthy0 libm17n-0 libotf0 m17n-contrib m17n-db semantic speedbar
0 upgraded, 17 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.7MB of archives.

Everything installed wonderfully. 

I think it is possible your repositories are borked. 

sudo apt-get update
and see if you recieve any errors..

check your source.list file for any repositories that shouldn't be there. 
hash mark them out and reload

sudo apt-get update

---

### Post by sheepjxx on 2011-05-23
I have to say, I have the same problem. Can't install ecb in 11.04

---

### Post by monkeyking on 2011-05-25
I have the same issue, it would seem that cedet is not available in the repos in ubuntu 11.04
[https://launchpad.net/ubuntu/natty/+source/cedet](https://launchpad.net/ubuntu/natty/+source/cedet)

---

### Post by TonyGao on 2011-06-18
the same for me, is it a bug? Can any Emacs user give some helps?

---

### Post by monkeyking on 2011-06-18
I ended up installing cedet from the source, this was quite easy.

---

