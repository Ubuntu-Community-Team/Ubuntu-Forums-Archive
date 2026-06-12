---
title: "E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)"
date: 2010-12-15
forum: General Help
---

### Post by lifestreammm on 2010-12-15
I just got Hardy Heron to run on my computer, and I am already having problems. What did I do wrong? I installed ubuntu-restricted-packages from the add/remove applications, and then it gave some error messages (to do with 'java'-installation if I remember correctly). Now I cannot open add/remove applications anymore. It gives the message: [INDENT]Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
[/INDENT]I'm able to do th 'sudo apt-get update', I then get the message:[INDENT]W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/INDENT]I don't know how to use this thing called 's, and iynaptic' or where to find it, and I don't know how to check the correctness of '/etc/apt/sources.list' either. But I'm willing to learn if needed.

Or is there something else I could do?

thanks for any help
lifestreammm, 
who is not too happy about ubuntu right now

---

### Post by philinux on 2010-12-15
Welcome to the forums.

Open a terminal.
Use copy and paste.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
```

Hardy Heron is an older release. Did you try the newer 10.04 LTS or 10.10.

---

### Post by lifestreammm on 2010-12-15
Thanks Phil.

I just did. This is what I get:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
gpg: requesting key 0C5A2783 from hkp server keyserver.ubuntu.com
gpg: key 0C5A2783: public key "Medibuntu Packaging Team <admin@lists.medibuntu.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1

But add/remove applications still doesn't work though. 
Or do I need to restart or something?

Lifestreammm

---

### Post by lifestreammm on 2010-12-15
No, I did not try the newer versions like 10.04 LTS or 10.10.
Shoudn't Hardy work fine? 

Lifestreammm

---

### Post by philinux on 2010-12-15
> **lifestreammm said:**
> Thanks Phil.

I just did. This is what I get:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
gpg: requesting key 0C5A2783 from hkp server keyserver.ubuntu.com
gpg: key 0C5A2783: public key "Medibuntu Packaging Team <admin@lists.medibuntu.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1

But add/remove applications still doesn't work though. 
Or do I need to restart or something?

Lifestreammm

Ok thats fixed that. Copy and paste this in and post back any errors in full. Make sure to close all applications like update manager software center and synaptic.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by philinux on 2010-12-15
For version end of life info see this.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history)

8.04 Desktop supported till April 2011.

---

### Post by lifestreammm on 2010-12-15
Thank you.

Getting same error messages:

    E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
    E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I've got no programs running. What next?

L

---

### Post by philinux on 2010-12-15
> **lifestreammm said:**
> Thank you.

Getting same error messages:

    E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
    E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I've got no programs running. What next?

L

Open a terminal.

First
```
killall aptitude && killall apt-get
```

And

```
killall dpkg && killall frontend
```

Finally.

```
sudo dpkg --configure -a
```

---

### Post by lifestreammm on 2010-12-15
[INDENT]tomennele@tomennele-laptop:~$ killall aptitude && killall apt-get
aptitude: no process killed

tomennele@tomennele-laptop:~$ killall dpkg && killall frontend
dpkg(13116): Operation not permitted
dpkg: no process killed

tomennele@tomennele-laptop:~$ sudo dpkg --configure -a
[sudo] password for tomennele: 
dpkg: status database area is locked by another process
[/INDENT]??

Lifestreammm

---

### Post by philinux on 2010-12-15
> **lifestreammm said:**
> [INDENT]tomennele@tomennele-laptop:~$ killall aptitude && killall apt-get
aptitude: no process killed

tomennele@tomennele-laptop:~$ killall dpkg && killall frontend
dpkg(13116): Operation not permitted
dpkg: no process killed

tomennele@tomennele-laptop:~$ sudo dpkg --configure -a
[sudo] password for tomennele: 
dpkg: status database area is locked by another process
[/INDENT]??

Lifestreammm

```
sudo killall dpkg && sudo killall frontend
```

---

### Post by lifestreammm on 2010-12-15
tomennele@tomennele-laptop:~$ sudo dpkg --configure -a
[sudo] password for tomennele: 
dpkg: status database area is locked by another process
tomennele@tomennele-laptop:~$ sudo killall dpkg && sudo killall frontend
frontend: no process killed

tomennele@tomennele-laptop:~$  sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (>= 6.22-0ubuntu1~8.04.1); however:
  Package sun-java6-bin is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-plugin

I guess now something's getting clearer...

And now?

L

---

### Post by philinux on 2010-12-15
> **lifestreammm said:**
> tomennele@tomennele-laptop:~$ sudo dpkg --configure -a
[sudo] password for tomennele: 
dpkg: status database area is locked by another process
tomennele@tomennele-laptop:~$ sudo killall dpkg && sudo killall frontend
frontend: no process killed

tomennele@tomennele-laptop:~$  sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (>= 6.22-0ubuntu1~8.04.1); however:
  Package sun-java6-bin is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-plugin

I guess now something's getting clearer...

And now?

L

```
sudo apt-get install sun-java6-bin && sudo dpkg --configure -a
```

---

### Post by lifestreammm on 2010-12-15
[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  sun-java6-jre
Suggested packages:
  binfmt-support sun-java6-fonts
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  sun-java6-bin
The following packages will be upgraded:
  sun-java6-jre
1 upgraded, 1 newly installed, 0 to remove and 196 not upgraded.
2 not fully installed or removed.
Need to get 0B/36.1MB of archives.
After this operation, 103MB of additional disk space will be used.
Do you want to continue [Y/n]? 
[/INDENT]I said "Y". I get a screen which I cannot get out of:

 Configuring sun-java6-bin &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618; 
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618; 
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618; 
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618; 
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618; 
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618; 
 &#9474;     form, any other machine readable materials including, but not         &#9618; 
 &#9474;     limited to, libraries, source files, header files, and data files),
etc, etc...

It has an <Ok> "button", which I cannot press. No mouse click or hitting return-key works. I don't know how to get out of this screen.

L

---

### Post by philinux on 2010-12-15
I think press the tab key to move the cursor to "OK" accept the license. Or it's the updown left right keys. Dang memory.

---

### Post by lifestreammm on 2010-12-15
That did it. (feel a bit silly for not trying tab-button though ;) 
Add/remove works again.
Thanks loads Phil!
Lifestreammm.

---

### Post by philinux on 2010-12-15
> **lifestreammm said:**
> That did it. (feel a bit silly for not trying tab-button though ;) 
Add/remove works again.
Thanks loads Phil!
Lifestreammm.

Ok Great. Use the Thread Tools button to mark the thread as Solved. This helps other users with similar problems.

You need to look at my post regarding versions as 8.04 come to end of life in April next year.

---

### Post by niravrathod on 2011-08-17
TNX for help me.. dude..!!

---

