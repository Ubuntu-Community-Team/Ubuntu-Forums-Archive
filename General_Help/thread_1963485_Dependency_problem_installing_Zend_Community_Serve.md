---
title: "Dependency problem installing Zend Community Server on Ubuntu 12.04"
date: 2012-04-22
forum: General Help
---

### Post by fara on 2012-04-22
[SIZE="3"][COLOR="Red"]Edit:[/COLOR] Seems this is a [problem with zend server repository]("http://goo.gl/hPYGQ"), and they will be working to fix it after 12.04 is officially released (after beta). So hopefully it would be fixed, but anyway I would appreciate if anyone has any workaround for it.[/SIZE]

Hi

I have a problem installing Zend Server CE (community edition) on my 32-bit box running Ubuntu 12.04

When I try:
```
sudo apt-get install zend-server-ce-php-5.3
```

I get the following:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 zend-server-ce-php-5.3 : Depends: php-5.3-common-extensions-zend-server but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

I also tried running:
```
sudo apt-get install php-5.3-common-extensions-zend-server
```

but failed with the following message:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 php-5.3-common-extensions-zend-server : Depends: php-5.3-imap-zend-server but it is not going to be installed
                                         Depends: php-5.3-pdo-pgsql-zend-server but it is not going to be installed
                                         Depends: php-5.3-pgsql-zend-server but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

trying to install each of them individually
```
sudo apt-get install php-5.3-imap-zend-server php-5.3-pdo-pgsql-zend-server php-5.3-pgsql-zend-server
```
also ended up with the following:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 php-5.3-imap-zend-server : Depends: libkrb53 (>= 1.4.2) but it is not going to be installed
 php-5.3-pdo-pgsql-zend-server : Depends: libpq4 (>= 8.1.4) but it is not going to be installed
 php-5.3-pgsql-zend-server : Depends: libpq4 (>= 8.1.4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

the same worked on my Ubuntu 11.10 without any problems, any idea what is going wrong? :-k

---

### Post by drdos2006 on 2012-04-22
Try :

sudo apt-get -f install

to see if the broken packages are installed.

regards

---

### Post by fara on 2012-04-23
> **drdos2006 said:**
> Try :

sudo apt-get -f install

to see if the broken packages are installed.

regards

Thanks for your reply.

tried that, no difference, and also tried:
```
sudo apt-get check
```
to check if there is any broken dependencies, but seems there's none
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
```

cheers

---

### Post by iamLeGaCyOne on 2012-05-03
:: FIRST POST! ::
I received the same error as the OP. However, I managed to painfully install Zend Server Community Edition 5.3.

**Problem: **Installing Zend Server CE fails because of unmet dependencies.
**Cause: **php-5.3-imap-zend-server & libpq4 references renamed dependency libkrb53
**Solution:** Manually change the dependency in the .deb file to libkrb5-3


[B]
Phase 1: Download the offending package
[/B]
Download manually the php-5.3-imap-zend-server & libpq4
```
sudo -i
apt-get download php-5.3-imap-zend-server
apt-get download libpq4
apt-get download zend-server-ce-php-5.3

```[B]Phase 2: Prepare to edit the offending package
[/B]First you need to download the handy dandy script from:
[http://ubuntuforums.org/showthread.php?t=636724](http://ubuntuforums.org/showthread.php?t=636724)

Copy the entire script as posted in the box
That's the one that starts with #!/bin/bash


```
gedit videbcontrol
```Paste code that you previously copied
Save & Exit

```
chmod +x videbcontrol

```**Phase3: Edit the offending packages**
```
./videbcontrol php-5.3-imap.zend-server_5.3.9+b261_i386.deb
```This will open the package in VI Editor.
Scroll down to "Depends:" 
Change libkr53 to libkr5-3; save and exit

If you know VI skip this - otherwise:
Use your arrow keys to get to libkr53.  When your cursor is over the 3 press I then - (dash) to change it to libkrb5-3.
Press shift [COLOR=Red]+[/COLOR] ;  (basically you want to type a semi colon : )
Press x then press [Enter] key

This process will create a file called php-5.3-imap.zend server_5.3.9+b261_i386.modified.deb
[B][I]
(repeat process for libpq4)
[/I][/B] 
** Phase 4: Install the modified package**s

```
gdebi php-5.3-imap.zend-server_5.3.9+b261_i386.modified.deb
```If you dont have gdebi type:
```
apt-get install gdebi
```
[COLOR=Red][B]gdebi php-5.3-imap.zend-server_5.3.9+b261_i386.modified.deb is going to fail! 

[/B][/COLOR]Install all the other required dependencies to get php-5.3-imap.zend-server_5.3.9+b261_i386.modified.deb to work:
```

dpkg -i php-5.3-imap.zend-server_5.3.9+b261_i386.modified.deb
dpkg -i libpq4_8.1.17-1_i386.modified.deb
dpkg -i zend-server-ce-php-5.3_5.6.0+b09_all.deb
apt-get -f install

```Run this!
```
gdebi php-5.3-imap.zend-server_5.3.9+b261_i386.modified.deb
```[B]

Phase 5: Finish installing Zend Server[/B]
```
apt-get install zend-server-ce-php-5.3
apt-get update

```Log into your server
[http://localhost:10081/ZendServer](http://localhost:10081/ZendServer)


If you keep getting errors it helps to try to manually install the dependency package and see why it is failing.  If it is failing because of libkrb53 still just modify it as we did the imap server file and install with gdebi. You might get a libssl package error. Download it with apt-get download and then check the error by running dpkg -i <filename> then repeat the steps if needs to be changed to libkrb5-3.

Good Luck!

*EDIT: Updated to add omission of libpq4 as suggest by RastaFeri - Thank you*

---

### Post by RastaFeri on 2012-05-03
i was reproducing iamLeGaCyOne's instructions and i was successful, but with one minor change - i had to duplicate the same steps concerning the package download php-5.3-imap-zend-server with the package called libpq4

after that the installation worked

thanks iamLeGaCyOne

---

### Post by iamLeGaCyOne on 2012-05-03
AHH!! that's what it was! I will note that in my instructions for future readers.

---

