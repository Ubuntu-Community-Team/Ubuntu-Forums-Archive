---
title: "apt-get problem"
date: 2010-02-19
forum: General Help
---

### Post by gniss on 2010-02-19
I installed and then removed vsftpd. Now, every time I use apt-get I get error messages as listed below. Can anyone tell me what is going on, how to fix or diagnose this program? Thanks.

[INDENT]sudo apt-get remove vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  vsftpd
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 475kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 37489 files and directories currently installed.)
Removing vsftpd ...
dpkg: error processing vsftpd (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/INDENT]

---

### Post by madverb on 2010-02-19
Try sudo aptitude remove

---

### Post by gniss on 2010-02-19
I get the same results:

[INDENT]sudo aptitude remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  vsftpd 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/144kB of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  vsftpd: Depends: update-inetd but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
vsftpd

Score is 121

Accept this solution? [Y/n/q/?] Y
The following packages will be REMOVED:
  vsftpd{a} 
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 475kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 37489 files and directories currently installed.)
Removing vsftpd ...
dpkg: error processing vsftpd (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
[/INDENT]

---

### Post by RedSingularity on 2010-02-19
Go to /var/apt/cache/archives and delete everything in that folder except the folder named partial.  Then try installing and removing again.

---

### Post by Primefalcon on 2010-02-19
```
sudo apt-get -f install
```

---

### Post by gniss on 2010-02-19
Thanks but still same results:

[INDENT]hm@minerals:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  vsftpd
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 475kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 37489 files and directories currently installed.)
Removing vsftpd ...
dpkg: error processing vsftpd (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)[/INDENT]

---

### Post by Primefalcon on 2010-02-19
```
sudo rm -Rf /var/lib/dpkg/info/* /var/cache/apt/archives/*
```
let's try clearing out your cache then...

---

### Post by gniss on 2010-02-19
Afraid I have really screwed things up now:

hm@minerals:/var/cache/apt/archives$ sudo apt-get remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  vsftpd
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
E: Archive directory /var/cache/apt/archives/partial is missing.

---

### Post by RedSingularity on 2010-02-19
Just add that directory again.

sudo touch /var/cache/apt/archives/partial

---

### Post by gniss on 2010-02-19
Still with problems:

hm@minerals:~$ sudo touch /var/cache/apt/archives/partial
[sudo] password for hm: 
hm@minerals:~$ sudo apt-get install vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vsftpd is already the newest version.
The following extra packages will be installed:
  update-inetd
The following NEW packages will be installed:
  update-inetd
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
E: Archive directory /var/cache/apt/archives/partial is missing.

---

### Post by Primefalcon on 2010-02-19
touch will create a file called that... so if you create that file just remove it first

```
sudo rm /var/cache/apt/archives/partial
```

then create a directory called partial

```
sudo mkdir /var/cache/apt/archives/partial
```

---

### Post by SkyNet2029 on 2010-02-19
I would suggest this since the error messages indicate that you have a package which is partially installed.
 
```
apt-get install vsftpd
``` 
let it do its install then
```
apt-get remove vsftpd --purge
```
```
apt-get -f install
```

---

### Post by gniss on 2010-02-19
I still get the same error message:

[INDENT]hm@minerals:~$ sudo apt-get install vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vsftpd is already the newest version.
The following extra packages will be installed:
  update-inetd
The following NEW packages will be installed:
  update-inetd
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
E: Archive directory /var/cache/apt/archives/partial is missing.
hm@minerals:~$ sudo apt-get remove vsftpd --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  vsftpd
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
E: Archive directory /var/cache/apt/archives/partial is missing.
hm@minerals:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  vsftpd
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
E: Archive directory /var/cache/apt/archives/partial is missing.
hm@minerals:~$ [/INDENT]

---

### Post by Primefalcon on 2010-02-19
> **gniss said:**
> I still get the same error message:

Just create it...

```
sudo mkdir /var/cache/apt/archives/partial
```

---

### Post by gniss on 2010-02-19
hm@minerals:~$ sudo mkdir /var/cache/apt/archives/partial
mkdir: cannot create directory `/var/cache/apt/archives/partial': File exists

---

### Post by Primefalcon on 2010-02-20
> **gniss said:**
> hm@minerals:~$ sudo mkdir /var/cache/apt/archives/partial
mkdir: cannot create directory `/var/cache/apt/archives/partial': File exists
As I said if you ran the touch command you need to remove the file and then create the directory

```
sudo rm /var/cache/apt/archives/partial
```
then
```
sudo mkdir /var/cache/apt/archives/partial
```

then just do what skynet said

---

