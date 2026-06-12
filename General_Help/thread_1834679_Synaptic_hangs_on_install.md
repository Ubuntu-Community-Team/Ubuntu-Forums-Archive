---
title: "Synaptic hangs on install"
date: 2011-08-27
forum: General Help
---

### Post by TiredBird on 2011-08-27
I tried to run update-manager. After downloading the upgrades and beginning the installation, it hung at 'preparing foomatic-filters'. 

I tried several other things and was told that the dependancies are broken for foomatic-filters and that I need to reinstall them.

After unlocking dpkg, (sudo rm /var/lib/dpkg/lock), I attempted to fix foomatic-filters dependancies through an upgrade of same with Synaptic.

The last line on the terminal display is:

```
Unpacking replacement foomatic-filters ...
```

It just hangs there. (Processor activity is neglibible. I/O activity is zero.)

This is the same place the update-manager hung. 

There seems to be a catch-22 here. dpkg can't remove or reinstall foomatic-filters because there is a dependancy problem. But I can't fix the dependancy problem because it is causing dpkg to hang.

How do I solve this problem?

---

### Post by searchfgold6789 on 2011-08-27
In a terminal window:```
sudo dpkg --configure -a
```

---

### Post by TiredBird on 2011-08-27
> **searchfgold6789 said:**
> In a terminal window:```
sudo dpkg --configure -a
```
Did it. Got the following response:
```
Processing triggers for man-db ...
```
I followed that up with again attempting to delete foomatic-filters via Synaptic. I got the following error message:
```
E: foomatic-filters: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.
```
Thanks for taking the time to look at this. Do you have any other thoughts?

---

### Post by TiredBird on 2011-08-28
Does anyone have any suggestions?

---

### Post by jerrrys on 2011-08-28
do you do synaptic; i do synaptic

[https://help.ubuntu.com/community/SynapticHowto#How%20to%20force%20the%20installation%20of%20a%20package%20version](https://help.ubuntu.com/community/SynapticHowto#How%20to%20force%20the%20installation%20of%20a%20package%20version)

---

### Post by searchfgold6789 on 2011-08-29
how about ```
sudo apt-get install -f
```

---

### Post by phyast on 2011-09-09
I am having the same issue with foomatic-filters. apt-get hangs at:
Unpacking replacement foomatic-filters ...
Has there been any resolution or other ideas?

---

### Post by TiredBird on 2011-09-15
> **searchfgold6789 said:**
> how about ```
sudo apt-get install -f
```
I get the following:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
1 not fully installed or removed.
Need to get 140kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/main foomatic-filters 4.0.4-0ubuntu1 [140kB]
Fetched 140kB in 1s (113kB/s)            
Preconfiguring packages ...
(Reading database ... 215645 files and directories currently installed.)
Preparing to replace foomatic-filters 4.0.4-0ubuntu1 (using .../foomatic-filters_4.0.4-0ubuntu1_i386.deb) ...
Unpacking replacement foomatic-filters ...

```
Still hangs.

---

