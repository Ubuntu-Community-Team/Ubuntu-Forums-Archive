---
title: "Error while using Update Manager"
date: 2010-11-01
forum: General Help
---

### Post by redfox1160 on 2010-11-01
The following pops up when using Update Manager to update my system. I do not know how to fix this, and any help would be appreciated.
```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.12+build1+nobinonly-0ubuntu0.10.04.1_i386.deb
  Could not resolve 'security.ubuntu.com'


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea6-plugin_6b18-1.8.2-4ubuntu2_i386.deb
  Could not resolve 'security.ubuntu.com'


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea-6-jre-cacao_6b18-1.8.2-4ubuntu2_i386.deb
  Could not resolve 'security.ubuntu.com'


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-lib_6b18-1.8.2-4ubuntu2_all.deb
  Could not resolve 'security.ubuntu.com'


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b18-1.8.2-4ubuntu2_i386.deb
  Could not resolve 'security.ubuntu.com'


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre_6b18-1.8.2-4ubuntu2_i386.deb
  Could not resolve 'security.ubuntu.com'


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-common/postgresql-client-common_106ubuntu1_all.deb
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-common/postgresql-common_106ubuntu1_all.deb
  Could not resolve 'us.archive.ubuntu.com'



```

---

### Post by sohlinux on 2010-11-01
did you try sudo apt-get upgrade?

---

### Post by redfox1160 on 2010-11-01
I just did that (and sudo apt update) and now I get this when I check for updates with Update Manager:
```
Failed to fetch http://apt.wicd.net/dists/lucid/Release.gpg  Something wicked happened resolving 'apt.wicd.net:http' (-5 - No address associated with hostname)
Failed to fetch http://apt.wicd.net/dists/lucid/extras/i18n/Translation-en_US.bz2  Something wicked happened resolving 'apt.wicd.net:http' (-5 - No address associated with hostname)
Failed to fetch http://apt.wicd.net/dists/lucid/extras/binary-i386/Packages.gz  Something wicked happened resolving 'apt.wicd.net:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by sohlinux on 2010-11-01
have you got another package manager open at the same time?

if not then go into the ubuntu software centre and edit software sources and try another server. it should do the trick

---

### Post by redfox1160 on 2010-11-01
> **sohlinux said:**
> have you got another package manager open at the same time?

if not then go into the ubuntu software centre and edit software sources and try another server. it should do the trick

I changed the server to the main server and then reloaded my software sources and got this error:

```
Failed to fetch http://apt.wicd.net/dists/lucid/Release.gpg  Something wicked happened resolving 'apt.wicd.net:http' (-5 - No address associated with hostname)
Failed to fetch http://apt.wicd.net/dists/lucid/extras/i18n/Translation-en_US.bz2  Something wicked happened resolving 'apt.wicd.net:http' (-5 - No address associated with hostname)
Failed to fetch http://apt.wicd.net/dists/lucid/extras/binary-i386/Packages.gz  Something wicked happened resolving 'apt.wicd.net:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by sohlinux on 2010-11-01
> **redfox1160 said:**
> I changed the server to the main server and then reloaded my software sources and got this error:

```
Failed to fetch http://apt.wicd.net/dists/lucid/Release.gpg  Something wicked happened resolving 'apt.wicd.net:http' (-5 - No address associated with hostname)
Failed to fetch http://apt.wicd.net/dists/lucid/extras/i18n/Translation-en_US.bz2  Something wicked happened resolving 'apt.wicd.net:http' (-5 - No address associated with hostname)
Failed to fetch http://apt.wicd.net/dists/lucid/extras/binary-i386/Packages.gz  Something wicked happened resolving 'apt.wicd.net:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.
```

strange , what was you doing prior to the problem? do you by any chance have a proxy configured? you need to look at the apt-get conf file and check it .

if you paste it here we could have a look

---

### Post by gsgleason on 2010-11-01
Could not resolve 'us.archive.ubuntu.com'

You have a name resolution issue.  Please paste the output of:

nslookup security.ubuntu.com

---

### Post by sohlinux on 2010-11-01
is your general internet connection working on on this machine? I mean browser etc?

try wget to see if you can download from the terminal```
wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
```

if wget is not working then check your /etc/host file

it should read something like this

192.168.1.2	your_user_name	# Added by NetworkManager

127.0.0.1	localhost.localdomain	localhost

::1	your_user_name	localhost6.localdomain6	localhost6

127.0.1.1	your_user_name



# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by redfox1160 on 2010-11-02
> **sohlinux said:**
> strange , what was you doing prior to the problem? do you by any chance have a proxy configured? you need to look at the apt-get conf file and check it .

if you paste it here we could have a look

What file is that?

[QUOTE=gsgleason]Could not resolve 'us.archive.ubuntu.com'

You have a name resolution issue. Please paste the output of:

nslookup security.ubuntu.com[/QUOTE]

Here is the output:
```
eric@grossboys-laptop:~$ nslookup security.ubuntu.com
Server:		10.37.100.10
Address:	10.37.100.10#53

Non-authoritative answer:
Name:	security.ubuntu.com
Address: 91.189.92.166
Name:	security.ubuntu.com
Address: 91.189.88.37
Name:	security.ubuntu.com
Address: 91.189.92.167
```



[QUOTE=sohlinux]is your general internet connection working on on this machine? I mean browser etc?

try wget to see if you can download from the terminal[/QUOTE]

Yes, wget is working, and so is my internet connection


[URL="http://ubuntuforums.org/showthread.php?t=1606409"]
THIS[/URL] happened to me last week... I don't know if it could have caused this...

---

### Post by sohlinux on 2010-11-02
go into ubuntu software centre then edit - software sources then reset the authentication - then try an sudo apt-get install something

if that doesnt work then go into ubuntu software centre  again then edit software sources and tick the cd/dvd option - insert the ubuntu install cd/dvd and see if you can at least install from the cd/dvd this will tell us if the error is something to do with the host file or network

if that doesnt work open up /etc/apt/sources.list with gedit and paste in the code here

---

### Post by redfox1160 on 2010-11-02
> **sohlinux said:**
> go into ubuntu software centre then edit - software sources then reset the authentication - then try an sudo apt-get install something

if that doesnt work then go into ubuntu software centre  again then edit software sources and tick the cd/dvd option - insert the ubuntu install cd/dvd and see if you can at least install from the cd/dvd this will tell us if the error is something to do with the host file or network

if that doesnt work open up /etc/apt/sources.list with gedit and paste in the code here

I was able to install a program using apt-get. Here is the sources.list file:
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu lucid universe
deb-src http://archive.ubuntu.com/ubuntu lucid universe
deb http://archive.ubuntu.com/ubuntu lucid-updates universe
deb-src http://archive.ubuntu.com/ubuntu lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu lucid multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb http://archive.ubuntu.com/ubuntu lucid-security universe
deb-src http://archive.ubuntu.com/ubuntu lucid-security universe
deb http://archive.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-security multiverse

deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://apt.wicd.net lucid extras
deb http://blog.blackdown.de/static/debian/rhythmbox/ lucid main
deb-src http://blog.blackdown.de/static/debian/rhythmbox/ lucid main

deb http://blog.blackdown.de/static/debian/rhythmbox/ lucid main
deb-src http://blog.blackdown.de/static/debian/rhythmbox/ lucid main

```

---

### Post by sohlinux on 2010-11-02
sources file looks fine

did you try sudo apt-get update or sudo apt-get ugrade again? still the same error?

do you get a reply if you ping archive.ubuntu.com ?

```
ping archive.ubuntu.com
```

did you try turning off your firewall?

---

