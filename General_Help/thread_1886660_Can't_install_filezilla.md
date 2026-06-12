---
title: "Can't install filezilla"
date: 2011-11-25
forum: General Help
---

### Post by molipha on 2011-11-25
Hi,

I'm trying to install filezilla using the following:
**sudo add-apt-repository ppa:n-muench/programs-ppa**
**sudo apt-get update**
[B]sudo apt-get install filezilla
[/B](from [http://www.upubuntu.com/2011/07/how-to-install-filezilla-350-on-ubuntu.html](http://www.upubuntu.com/2011/07/how-to-install-filezilla-350-on-ubuntu.html))

The installation chokes returning the following:
ubuntu@ubuntu:~$ sudo apt-get install filezilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 filezilla : Depends: libwxbase2.8-0 (>= 2.8.11.0) but it is not installable
             Depends: libwxgtk2.8-0 (>= 2.8.11.0) but it is not installable
E: Unable to correct problems, you have held broken packages.

Thanks for any help.

---

### Post by crazy bird on 2011-11-25
> I'm trying to install filezilla using the following:
**sudo add-apt-repository ppa:n-muench/programs-ppa**
**sudo apt-get update**
**sudo apt-get install filezilla**
(from [http://www.upubuntu.com/2011/07/how-to-install-filezilla-350-on-ubuntu.html](http://www.upubuntu.com/2011/07/how-to-install-filezilla-350-on-ubuntu.html)) 
Perfect! That's not the problem!
 
>  
The following packages have unmet dependencies:
filezilla : Depends: libwxbase2.8-0 (>= 2.8.11.0) but it is not installable
Depends: libwxgtk2.8-0 (>= 2.8.11.0) but it is not installable
E: Unable to correct problems, you have held broken packages. 
Those 2 packages causes the problem.
 
 
> libwxbase2.8-0 (>= 2.8.11.0)
You have version 2.8.0 but you need at least version 2.8.11.0 to get Filezilla installed.
 
> libwxgtk2.8-0 (>= 2.8.11.0)
You have version 2.8.0 but you need at least version 2.8.11.0 to get Filezilla installed.
 
 
For upgrading libwxbase:
[http://packages.ubuntu.com/search?keywords=libwxbase&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=libwxbase&searchon=names&suite=all&section=all)
 
For upgrading libwxgtk:
[http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=names&keywords=libwxgtk](http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=names&keywords=libwxgtk)

---

### Post by raja.genupula on 2011-11-25
> **molipha said:**
> Hi,

I'm trying to install filezilla using the following:
**sudo add-apt-repository ppa:n-muench/programs-ppa**
**sudo apt-get update**
[B]sudo apt-get install filezilla
[/B](from [http://www.upubuntu.com/2011/07/how-to-install-filezilla-350-on-ubuntu.html](http://www.upubuntu.com/2011/07/how-to-install-filezilla-350-on-ubuntu.html))

The installation chokes returning the following:
ubuntu@ubuntu:~$ sudo apt-get install filezilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 filezilla : Depends: libwxbase2.8-0 (>= 2.8.11.0) but it is not installable
             Depends: libwxgtk2.8-0 (>= 2.8.11.0) but it is not installable
E: Unable to correct problems, you have held broken packages.

Thanks for any help.

try to do 
```
sudo apt-get install -f
```

---

### Post by HermanAB on 2011-11-25
However, everything Filezilla does can be done with Nautilus, Konqueror or Dolphin and you are bound to have one of those installed already.

---

### Post by Bucky Ball on 2011-11-25
How come you didn't install from Synaptic? Get same errors? Are you running 11.10?

---

### Post by molipha on 2011-11-25
> **Bucky Ball said:**
> How come you didn't install from Synaptic? Get same errors? Are you running 11.10?

Yes, I'm running 11.10. I tried installing from software center but it told me I have package dependency issues.

---

### Post by molipha on 2011-11-25
> **HermanAB said:**
> However, everything Filezilla does can be done with Nautilus, Konqueror or Dolphin and you are bound to have one of those installed already.

Thanks, I'm going to try these.

---

### Post by oldtimer7777 on 2011-11-25
Which version of Ubuntu are you running?  

Can you upload your source.list file so we can see how you have that configured? 

Have you added any -other- PPA's recently? 

> **molipha said:**
> Hi,

I'm trying to install filezilla using the following:
**sudo add-apt-repository ppa:n-muench/programs-ppa**
**sudo apt-get update**
[B]sudo apt-get install filezilla
[/B](from [http://www.upubuntu.com/2011/07/how-to-install-filezilla-350-on-ubuntu.html](http://www.upubuntu.com/2011/07/how-to-install-filezilla-350-on-ubuntu.html))

The installation chokes returning the following:
ubuntu@ubuntu:~$ sudo apt-get install filezilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 filezilla : Depends: libwxbase2.8-0 (>= 2.8.11.0) but it is not installable
             Depends: libwxgtk2.8-0 (>= 2.8.11.0) but it is not installable
E: Unable to correct problems, you have held broken packages.

Thanks for any help.

---

