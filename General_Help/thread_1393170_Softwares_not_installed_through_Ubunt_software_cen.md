---
title: "Softwares not installed through Ubunt software center &amp; through Linux app finder.com"
date: 2010-01-29
forum: General Help
---

### Post by kasaram.gowtham on 2010-01-29
[COLOR=Black]Dear sirs,
I'm new guy to Ubuntu, and using the latest version 9.10.
I have a problem that when I want to install new soft wares through Ubuntu software center/Linux app findr.com there is a dialogue box like 

(If trying through Linux app finder.com)
E: Problem syncing the file - sync (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
E:_cache->open() failed, please report.

(If trying with Ubunt soft center)
This is a serious problem inform immediately (so and so)
E: Problem syncing the file - sync (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

Please tell me how can I rectify my system with this problem
[/COLOR]

---

### Post by raktarok on 2010-01-29
Hi there,

Please try these commands in the terminal and see if you can install programs. Post errors,if any.

```
sudo apt-get autoclean 
sudo apt-get autoremove
```

---

### Post by kasaram.gowtham on 2010-01-29
sudo apt-get autoclean autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done

After this I'm trying to install OOo base through Linux app finer.com
 
Changes applied
 Not all changes and updates succeeded. For further details of the failure, please expand the 'Details' panel below.

dpkg: parse error, in file '/var/lib/dpkg/available' near line 13318 package 'parted'
failed name:

E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:
dpkg: parse error, in file '/var/lib/dpkg/abailable near line 13318 package 'parted':
filed name

---

### Post by kasaram.gowtham on 2010-01-29
when I use sudo apt-get  auto remove

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-headers-2.6.31-14
  linux-headers-2.6.31-14-generic
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
After this operation, 82.0MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: parse error, in file '/var/lib/dpkg/available' near line 13318 package 'parted':
 field name `
E: Sub-process /usr/bin/dpkg returned an error code (2)
silpa@silpa-desktop:~$

---

### Post by raktarok on 2010-01-29
Try this now:

```
 sudo dpkg --clear-avail
```

the autoremove part isn't necessary, actually.

---

### Post by kasaram.gowtham on 2010-01-29
> **raktarok said:**
> Try this now:

```
 sudo dpkg --clear-avail
```

the autoremove part isn't necessary, actually.
silpa@silpa-desktop:~$ sudo dpkg --clear-avail
silpa@silpa-desktop:~$ 

No changes occured

---

### Post by raktarok on 2010-01-29
can you install packages now?

---

### Post by kasaram.gowtham on 2010-01-29
> **raktarok said:**
> can you install packages now?
No sir,
When I am trying to install through Linux app finder.com

after some process this following message displayed

E: /var/cache/apt/archives/openjdk-6-jre-headless_6b16-1.6.1-3ubuntu1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar')
E: /var/cache/apt/archives/openoffice.org-java-common_1%3a3.1.1-5ubuntu1_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/java/openoffice/ScriptFramework.jar')
E: /var/cache/apt/archives/openoffice.org-base_1%3a3.1.1-5ubuntu1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/basis3.1/program/libabpli.so')

---

### Post by kasaram.gowtham on 2010-01-29
> **kasaram.gowtham said:**
> No sir,
When I am trying to install through Linux app finder.com

after some process this following message displayed

E: /var/cache/apt/archives/openjdk-6-jre-headless_6b16-1.6.1-3ubuntu1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar')
E: /var/cache/apt/archives/openoffice.org-java-common_1%3a3.1.1-5ubuntu1_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/java/openoffice/ScriptFramework.jar')
E: /var/cache/apt/archives/openoffice.org-base_1%3a3.1.1-5ubuntu1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/basis3.1/program/libabpli.so')
After closing all windows the final dialog box as follows

Software index is broken

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by kasaram.gowtham on 2010-01-29
> **kasaram.gowtham said:**
> After closing all windows the final dialog box as follows

Software index is broken

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
Finally I am trying to update my system through Update manager 
but the same problem is occured like

E: Unable to write mmap - msync (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by raktarok on 2010-01-29
Try these, as suggested.

sudo apt-get -f install
sudo apt-get update

---

### Post by kasaram.gowtham on 2010-01-29
> **raktarok said:**
> Try these, as suggested.

sudo apt-get install -f
sudo apt-get update
silpa@silpa-desktop:~$ sudo apt-get install -f
Reading package lists... Error!
E: Unable to write mmap - msync (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
silpa@silpa-desktop:~$

---

### Post by raktarok on 2010-01-29
ok. try these, in order:

```
sudo apt-get -f install
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
```

---

### Post by kasaram.gowtham on 2010-01-29
> **kasaram.gowtham said:**
> silpa@silpa-desktop:~$ sudo apt-get install -f
Reading package lists... Error!
E: Unable to write mmap - msync (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
silpa@silpa-desktop:~$
When I type the command sudo apt-get update
after a long process ....

ended with the following few lines 

Fetched 11.0MB in 6min 4s (30.2kB/s)                                                                                                   
Reading package lists... Error!
E: Problem syncing the file - sync (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
silpa@silpa-desktop:~$

---

### Post by kasaram.gowtham on 2010-01-29
> **raktarok said:**
> ok. try these, in order:

```
sudo apt-get -f install
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
```
silpa@silpa-desktop:~$ sudo apt-get -f install
Reading package lists... Error!
E: Unable to write mmap - msync (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
silpa@silpa-desktop:~$ sudo apt-get clean
silpa@silpa-desktop:~$ sudo apt-get autoclean
Reading package lists... Error!
E: Unable to write mmap - msync (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
silpa@silpa-desktop:~$

---

### Post by raktarok on 2010-01-29
This is frustruating!

Follow the instructions on this page and see if it helps

[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/56499](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/56499)

Try this one first, I have not told you this one:
```

sudo dpkg --configure -a
```

---

### Post by kasaram.gowtham on 2010-01-29
> **kasaram.gowtham said:**
> silpa@silpa-desktop:~$ sudo apt-get install -f
Reading package lists... Error!
E: Unable to write mmap - msync (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
silpa@silpa-desktop:~$
still the following message occurred while trying to install new software

Software index is broken

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by kasaram.gowtham on 2010-01-29
> **kasaram.gowtham said:**
> still the following message occurred while trying to install new software

Software index is broken

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
Thank you very much for trying to clarify my doubts (although I am new to Ubuntu). But still the problems is continuous.

Anyway thanking you

---

### Post by raktarok on 2010-01-29
Any luck with this so far? 

Also, post the contents of the file /etc/apt/sources.list. That's the file that stores info about your software sources and repositories. I don't think there's a problem with the file, but let's have a look. Do this from a terminal and copy the contents of the file here:

```
gksudo gedit /etc/apt/sources.list
```

Also, try these, in this order and see if there is any change
```

sudo aptitude clean
sudo aptitude -f install 
sudo aptitude clean
sudo aptitude update
```

Good luck, once again.

---

### Post by joyous on 2010-06-02
Hi friends,

I am facing serious problem while i am trying to install new software through ubuntu software center or synaptic maneger or through terminal. All times i am getting the following message ..............
"E: Type 'usage:' is not known on line 51 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."

I am using ubuntu 9.10 Karmic...

Please help me to resolve this problem.

Thanks
joy

---

### Post by joyous on 2010-06-02
sorry Boss,
I have solved the problem by editing sources.list file........what i have done is just to comment out those lines unknown to package manager.. that's all
Thanks.
joy

---

