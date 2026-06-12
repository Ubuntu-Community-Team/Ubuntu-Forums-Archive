---
title: "APT fails after fixing disk"
date: 2012-07-22
forum: General Help
---

### Post by Sun_Blood on 2012-07-22
Hi,

I just had some major corruptions on my /root partition that made it impossible to start the system. So I did a fsck on it from recovery and now the system starts like normal. :D

But there was apparently some files that could not be restored correctly(or have bin written to during corruption) and one of them is for apt so now I can't upgrade or reinstall package.

Any suggestions on how to fix this?

```
root@*****:~# aptitude upgrade
The following packages will be upgraded: 
  apport bzr cron gamin gstreamer0.10-plugins-base:i386 gstreamer0.10-x:i386 language-pack-en 
  language-pack-gnome-en libgamin0 libgnutls-dev libgnutls-openssl27 libgnutls26 libgnutls26:i386 
  libgnutlsxx27 libgstreamer-plugins-base0.10-0:i386 libgtk-3-0 libgtk-3-bin libgtk-3-common libjpeg-turbo8 
  libjpeg-turbo8:i386 libpango1.0-0 libpango1.0-0:i386 libtiff4 libtiff4:i386 postfix python-apport 
  python-bzrlib python-gamin python-problem-report xkb-data 
30 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/10,9 MB of archives. After unpacking 2 152 kB will be used.
Do you want to continue? [Y/n/?] 
Preconfiguring packages ...              
(Reading database ... 
dpkg: warning: files list file for package `apt-utils' missing, assuming package has no files currently installed.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `libv4lconvert0:i386' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
                                         
root@****:~# 
```

---

### Post by Laiquendi on 2012-07-22
Try to run this:
```
run sudo dpkg --configure
```later on you may try:
```
sudo apt-get install -f
```or a combo:
```
sudo dpkg --configure -a --force-all
```If it won't work you may have lost some data, files ,etc. which had held vital informations for apt-get. Try to rebuild them or something like that.
Sorry for spare solution, but I don't understand fully what has happen due to this coruption.

---

### Post by Sun_Blood on 2012-07-22
Sadly it didn't help. The problem is that the system think the package is installed and working correctly so it will not try to reinstall even with -f

I don't even understand if it is the apt-utils or libv4lconvert0:i386 that fails from reading the error message. And both packages is so embedded in the system so trying to remove them and reinstall seams impossible.

---

### Post by jmfal on 2012-07-22
Welcome to Ubuntu Forums

Run this in a terminal
```
  sudo apt-get update   
```

and post the results if there are errors

---

### Post by Sun_Blood on 2012-07-22
> **jmfal said:**
> Welcome to Ubuntu Forums

Run this in a terminal
```
  sudo apt-get update   
```

and post the results if there are errors


Sadly no errors.

---

### Post by sandyd on 2012-07-22
Sounds like your apt-utils file list is corrupted or missing
Removing it, and reinstalling will regenerate it. (ignore errors in the first line, it is just to make sure there is no apt-utils list there already)
```

sudo mv /var/lib/dpkg/info/apt-utils.list /opt/apt-utils.list.backup
sudo apt-get update
sudo apt-get install --reinstall apt-utils

```

---

### Post by jmfal on 2012-07-22
Try rebooting into the recovery kernal in the grub screen

run>>dpkg fix broken packages
follow prompts 
if requested to run command manually it will probably be one of these:
```
  sudo dpkg --configure -a
                sudo apt-get install -f  
```

resume normal boot
attempt what you are doing again

---

### Post by Sun_Blood on 2012-07-22
> **sandyd said:**
> Sounds like your apt-utils file list is corrupted or missing
Removing it, and reinstalling will regenerate it. (ignore errors in the first line, it is just to make sure there is no apt-utils list there already)
```

sudo mv /var/lib/dpkg/info/apt-utils.list /opt/apt-utils.list.backup
sudo apt-get update
sudo apt-get install --reinstall apt-utils

```

I think you are correct but it didn't work.
First of all I don't have the file /var/lib/dpkg/info/apt-utils.list so I could not move it. But I do have an md5 file, should I remove it?

And doing the reinstall gave me the same error

```
root@****:~# apt-get install --reinstall apt-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 46 not upgraded.
Need to get 0 B/191 kB of archives.
After this operation, 0 B of additional disk space will be used.
Selecting previously unselected package apt-utils.
(Reading database ... 
dpkg: warning: files list file for package `apt-utils' missing, assuming package has no files currently installed.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `libv4lconvert0:i386' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@****:~# 

```

---

### Post by Sun_Blood on 2012-07-22
> **jmfal said:**
> Try rebooting into the recovery kernal in the grub screen

run>>dpkg fix broken packages
follow prompts 
if requested to run command manually it will probably be one of these:
```
  sudo dpkg --configure -a
                sudo apt-get install -f  
```

resume normal boot
attempt what you are doing again

Do I need to be in recovery? Then I must move the computer(server) so I'll try it later.

---

### Post by sandyd on 2012-07-22
> **Sun_Blood said:**
> I think you are correct but it didn't work.
First of all I don't have the file /var/lib/dpkg/info/apt-utils.list so I could not move it.
And doing the reinstall gave me the same error

```
root@****:~# apt-get install --reinstall apt-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 46 not upgraded.
Need to get 0 B/191 kB of archives.
After this operation, 0 B of additional disk space will be used.
Selecting previously unselected package apt-utils.
(Reading database ... 
dpkg: warning: files list file for package `apt-utils' missing, assuming package has no files currently installed.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `libv4lconvert0:i386' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@****:~# 

```
hmm. Apt being fussy again I see.

Run
```

ls /var/cache/apt/archives/apt-utils*

```If there is only one file, 

Try
```

sudo dpkg -i --force all /var/cache/apt/archives/apt-utils*deb
```Else, post the output.

Should work this time - I deleted mine to check.

---

### Post by Sun_Blood on 2012-07-22
> **sandyd said:**
> hmm. Apt being fussy again I see.

Run
```

ls /var/cache/apt/archives/apt-utils*

```If there is only one file, 

Try
```

sudo dpkg -i --force all /var/cache/apt/archives/apt-utils*deb
```Else, post the output.

Should work this time - I deleted mine to check.

ls command gave
```
/var/cache/apt/archives/apt-utils_0.8.16~exp12ubuntu10.2_amd64.deb

```

So I did the next command and it gave this
```
root@*****:~# dpkg -i --force all /var/cache/apt/archives/apt-utils*deb
Selecting previously unselected package apt-utils.
(Reading database ... 
dpkg: warning: files list file for package `apt-utils' missing, assuming package has no files currently installed.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `libv4lconvert0:i386' contains empty filename

```

Fussy for sure :)

---

### Post by sandyd on 2012-07-22
> **Sun_Blood said:**
> ls command gave
```
/var/cache/apt/archives/apt-utils_0.8.16~exp12ubuntu10.2_amd64.deb

```So I did the next command and it gave this
```
root@*****:~# dpkg -i --force all /var/cache/apt/archives/apt-utils*deb
Selecting previously unselected package apt-utils.
(Reading database ... 
dpkg: warning: files list file for package `apt-utils' missing, assuming package has no files currently installed.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `libv4lconvert0:i386' contains empty filename

```Fussy for sure :)
that can't be good.
You have multiple corrupt package files

This might take a while, so you have to be patitent alright?
We will have to manually delete each and every corrupted list file, and reinstall it (the command give should have worked if libv4lconvert wasn't corrupted as well)

```

sudo rm /var/lib/dpkg/info/libv4l-0:i386.list

``````

sudo dpkg -i --force all /var/cache/apt/archives/libv4lconvert*i386.deb /var/cache/apt/archives/apt-utils*deb
```

---

### Post by Sun_Blood on 2012-07-22
Is it only the Microsoft solution left then? (reinstall OS)

I was hoping not to do that...

---

### Post by Sun_Blood on 2012-07-22
> **sandyd said:**
> that can't be good.
You have multiple corrupt package files

This might take a while, so you have to be patitent alright?
We will have to manually delete each and every corrupted list file, and reinstall it (the command give should have worked if libv4lconvert wasn't corrupted as well)

```

sudo rm /var/lib/dpkg/info/libv4l-0:i386.list

``````

sudo dpkg -i --force all /var/cache/apt/archives/libv4lconvert*i386.deb /var/cache/apt/archives/apt-utils*deb
```

A BIG gold star to you my friend! :KS
That made it work again =)

---

### Post by retroquark on 2013-06-15
Phew. This also worked for me. The list file for language-pack-en was corrupt somehow. But deleting the list-file at least allowed apt(or dpkg) to continue..

What I get now, also after the package was reinstalled, is "files list file for package 'language-pack-en' missing; assuming package has no files currently installed"

..anyone know of a way to rebuild the list-file? Or if this "assuming package has no files installed" thing is going to cause apt-tools to install things(or refuse to install dependencies) later on?

---

