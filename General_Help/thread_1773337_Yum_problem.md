---
title: "Yum problem?"
date: 2011-06-01
forum: General Help
---

### Post by Skybucks100 on 2011-06-01
Hi,
I went to go and install HyperVW and then this came up:
```

root@PW-SERVER:~# sh ./hypervm-install-master.sh --virtualization-type=xen/openvz/NONE
Setting up Install Process
No package php available.
No package wget available.
No package zip available.
No package unzip available.
Nothing to do
installing php failed. Please fix yum/up2date.

```
I entered this code:
```

sh ./hypervm-install-master.sh --virtualization-type=xen/openvz/NONE

```
What do I do about this? I installed Yum and I am logged in as root

Any help would be awesome!

Thanks!

---

### Post by katykat on 2011-06-01
Yum is the fedora (redhat?) equivalent of apt-get. 

Fedora and Ubuntu often have different paths, though in this case it looks like both systems would have those utils in /usr/bin

Probably debian cannot figure out dependencies, but this a shell script, not an RPM - so its possible the shell script is making certain assumptions if yum was needed to get it.

However, the simplest method is to check /usr/bin to make sure those utilities are there, and if not 
apt-get install (them).

Dont use yum.
(Except if you are on fedora, where it works better than apt).

---

### Post by Skybucks100 on 2011-06-02
> **katykat said:**
> Yum is the fedora (redhat?) equivalent of apt-get. 

Fedora and Ubuntu often have different paths, though in this case it looks like both systems would have those utils in /usr/bin

Probably debian cannot figure out dependencies, but this a shell script, not an RPM - so its possible the shell script is making certain assumptions if yum was needed to get it.

However, the simplest method is to check /usr/bin to make sure those utilities are there, and if not 
apt-get install (them).

Dont use yum.
(Except if you are on fedora, where it works better than apt).
Hi,
I did do the sudo apt-get install for all of them and I still get the same error. Is there something i'm doing wrong? :confused:

Thanks!

---

### Post by katykat on 2011-06-02
The shell script is short and the first part is simply using yum to install the basic utilities.   However, yum seems to work fine in Meerkat, and runs the script.   Make sure you chmod it to 775 (chmod 775 filename.sh) as it downloads without execute permissions.  You probably have got that far already.   The next step is to sudo the command, or as I normally do, run as root, especially for programs like this.   As root, it will download a program-install.zip containing some PHP scripts.    It appears they are PHP4. And apparently made for a Redhat system as they appear be generating some strange errors besides the 'deprecated function' errors from the version differences.   See if there is anyone on their forums, or if it is still supported.   The scripts really need to be updated to a newer PHP.   Oh, yes. When I run that complete command line I also get the missing packages error. Weird, because they are there.

---

### Post by katykat on 2011-06-02
The shell script is short and the first part is simply using yum to install the basic utilities.   However, yum seems to work fine in Meerkat, and runs the script.   Make sure you chmod it to 775 (chmod 775 filename.sh) as it downloads without execute permissions.  You probably have got that far already.   The next step is to sudo the command, or as I normally do, run as root, especially for programs like this.   As root, it will download a program-install.zip containing some PHP scripts.    It appears they are PHP4. And apparently made for a Redhat system as they appear be generating some strange errors besides the 'deprecated function' errors from the version differences.   See if there is anyone on their forums, or if it is still supported.   The scripts really need to be updated to a newer PHP.   Oh, yes. When I run that complete command line I also get the missing packages error. Weird, because they are there.

---

