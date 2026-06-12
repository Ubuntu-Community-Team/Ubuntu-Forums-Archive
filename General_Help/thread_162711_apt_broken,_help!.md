---
title: "apt broken, help!"
date: 2006-04-19
forum: General Help
---

### Post by casfindad on 2006-04-19
In an attempt to install the latest version of K3b from source (see [this thread]("http://www.ubuntuforums.org/showthread.php?t=162593")), it appears that I have broken apt. For example, here is what I get when I try to install kmymoney2

```

casey@SagamoreHill:/$ sudo apt-get install kmymoney2
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libofx2 libosp4
The following NEW packages will be installed:
  kmymoney2 libofx2 libosp4
0 upgraded, 3 newly installed, 0 to remove and 2 not upgraded.
Need to get 7696kB of archives.
After unpacking 18.8MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com breezy/main libosp4 1.5.1.0-2ubuntu2 [732kB]
Get:2 http://archive.ubuntu.com breezy/universe libofx2 1:0.8.0-3ubuntu8 [454kB]
Get:3 http://archive.ubuntu.com breezy/universe kmymoney2 0.8-6ubuntu2 [6510kB]                                                            
Fetched 7696kB in 44s (172kB/s)                                                                                                            

Preconfiguring packages ...
Authenticating /var/cache/apt/archives/libosp4_1.5.1.0-2ubuntu2_i386.deb ...
debsig: Origin Signature check failed. This deb might not be signed.

dpkg: error processing /var/cache/apt/archives/libosp4_1.5.1.0-2ubuntu2_i386.deb (--unpack):
 Verification on package /var/cache/apt/archives/libosp4_1.5.1.0-2ubuntu2_i386.deb failed!
Authenticating /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb ...
debsig: Origin Signature check failed. This deb might not be signed.

dpkg: error processing /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb (--unpack):
 Verification on package /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb failed!
Authenticating /var/cache/apt/archives/kmymoney2_0.8-6ubuntu2_i386.deb ...
debsig: Origin Signature check failed. This deb might not be signed.

dpkg: error processing /var/cache/apt/archives/kmymoney2_0.8-6ubuntu2_i386.deb (--unpack):
 Verification on package /var/cache/apt/archives/kmymoney2_0.8-6ubuntu2_i386.deb failed!
Errors were encountered while processing:
 /var/cache/apt/archives/libosp4_1.5.1.0-2ubuntu2_i386.deb
 /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb
 /var/cache/apt/archives/kmymoney2_0.8-6ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I get similar messages when I try to install other packages as well. Please help! If I can't fix this soon, I think I'm looking at a clean install tonight!

casfindad

---

### Post by apsalyers on 2006-04-19
Did you have to add a seperate apt repository for this software to your sources.list file?

---

### Post by casfindad on 2006-04-19
[QUOTE=apsalyers]Did you have to add a seperate apt repository for this software to your sources.list file?[/QUOTE]

No. I double-checked, and my sources.list file hasn't been changed since I tried to install K3b (which I think broke apt) or other applications (which revealed the apt errors).

---

### Post by apsalyers on 2006-04-19
[QUOTE=casfindad]No. I double-checked, and my sources.list file hasn't been changed since I tried to install K3b (which I think broke apt) or other applications (which revealed the apt errors).[/QUOTE]

Sorry, what I ment was have you added anything to the sources.list file between the last time you successfully installed a package and now?

---

### Post by casfindad on 2006-04-19
[QUOTE=apsalyers]Sorry, what I ment was have you added anything to the sources.list file between the last time you successfully installed a package and now?[/QUOTE]
Nope.

In case it's relevant, I noticed I have a file called "lock" in /var/lib/apt/lists.

casfindad

---

### Post by apsalyers on 2006-04-19
The message you are getting is like what you would get if you needed to import a public key to install certain software packages or use a repo.  See kubuntu.org for examples of having to install a key to install Amarok and KOffice newest versions.  My first thoughts would be to make a backup of sources.list to a new file, say sources.old, then make a new sources.list file with basic repositories and try again.  I can post/send a good one if you want.

---

### Post by casfindad on 2006-04-20
[QUOTE=apsalyers]The message you are getting is like what you would get if you needed to import a public key to install certain software packages or use a repo.  See kubuntu.org for examples of having to install a key to install Amarok and KOffice newest versions.  My first thoughts would be to make a backup of sources.list to a new file, say sources.old, then make a new sources.list file with basic repositories and try again.  I can post/send a good one if you want.[/QUOTE]

I think you may be right as to the cause of my problem, but unfortunately switching to a "basic" sources.list file didn't seem to fix things. Here is the source.list I used:

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted multiverse
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

I also tried using another sources.list file archived by automatix last month.

If I use either sources.list, and type "sudo apt-get update" followed by "sudo apt-get install kmymoney2", I get the same error as before. If I try typing "sudo apt-get install -f", I get
```
casey@SagamoreHill:/etc/apt$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

So I still have a broken apt system. :(

---

### Post by casfindad on 2006-04-20
I've solved the broken apt problem; see [this thread]("http://www.ubuntuforums.org/showthread.php?t=163172").

Thanks for your help, apsalyers.

casfindad

---

