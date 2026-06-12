---
title: "how to make sure i have the latest/updated packages"
date: 2006-03-08
forum: General Help
---

### Post by jeisma on 2006-03-08
hello!

trying ubuntu for the first time. during install i ignored this message:

"the network autoconfiguration was successful. however, no default route was set: the system does not know how to communicate with hosts on the internet. this will make it impossible to continue with the installation unless you have the first official Ubuntu CD-ROM, a 'netinst' CD-ROM, or packages available on the local network."

i am now able to login to my box running ubuntu. now what's next? how can i verify that i have the latest/updated packages?

how do i install tbird on ubuntu?

thanks!

---

### Post by Sef on 2006-03-08
> how do i install tbird on ubuntu?

Click on Applications -----> Click on Add Applications  ------> Password -----> Click on internet ------> Click on add programs ------> click on Thunderbird ------> Click Apply ----> Click Apply again.

---

### Post by Sutekh on 2006-03-08
[QUOTE=jeisma]
i am now able to login to my box running ubuntu. now what's next? how can i verify that i have the latest/updated packages?[/QUOTE]
Do you have internet on the Ubuntu box?  That message you encountered wasn't encouraging.

If you do though....

Open a **Terminal Window** in the Applications -> Accessories Menu
```
sudo apt-get update
sudo apt-get upgrade
```
Usually a little red circle thingy will pop up on the top panel reminding you that there are updates, those commands I gave you just force it to check.

[QUOTE=jeisma]
how do i install tbird on ubuntu?

thanks![/QUOTE]
Assuming you do have the internet, again from that Terminal window
```
sudo apt-get install mozilla-thunderbird
```

---

### Post by jeisma on 2006-03-08
[QUOTE=Sef]Click on Applications -----> Click on Add Applications  ------> Password -----> Click on internet ------> Click on add programs ------> click on Thunderbird ------> Click Apply ----> Click Apply again.[/QUOTE]

hello!

doing the above (thank you). i get this:

Application 'mozilla-thunderbird' not available.

The application cannot be found in your archive. This usually means that this is not available for your hardware platform.

What does this mean? what difference would it make if i install an app without going thru the add application applet? or what if i need to install an app that doesnt exist in the application list?

thank you!

---

### Post by jeisma on 2006-03-08
hi!

doing your intructions, i get:

$ sudo apt-get update
Reading package lists... Done

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

p$ sudo apt-get install mozilla-thunderbird
Reading package lists... Done
Building dependency tree... Done
Package mozilla-thunderbird is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-thunderbird has no installation candidate


what does these messages mean? 

i connect to the internet thru a proxy server. 


thank you!

---

### Post by Zlatan on 2006-03-08
try following: 
1. open help
2. find how to: add extra repositories
3. sudo apt-get update
4. sudo apt-get upgrade
5. sudo apt-get install mozilla-thunderbird

[QUOTE=jeisma]hi!

doing your intructions, i get:

$ sudo apt-get update
Reading package lists... Done

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

p$ sudo apt-get install mozilla-thunderbird
Reading package lists... Done
Building dependency tree... Done
Package mozilla-thunderbird is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-thunderbird has no installation candidate


what does these messages mean? 

i connect to the internet thru a proxy server. 


thank you![/QUOTE]

---

### Post by Mustard on 2006-03-08
I'm still wondering whether the internet connection is working properly.  The initial error messages seemed to indicate a problem with the 'default route'.

The error message installing thunderbird doesn't make a lot of sense, as thunderbird should be available in the default repositores, as its not part of universe or multiverse repositories.  I would think it would available from the actual installation CD (or so its description seems to imply).

I'd like to see your sources.list actually.

Can you paste the output of this command please?

```
cat /etc/apt/sources.list

#this should display the contents of the file called 'sources.list' 
#which is found in the /etc/apt/ folder
```

Another question.  Does your internet connection **only** work with a proxy configured or can it direct connect as well?

---

### Post by jeisma on 2006-03-08
hello!

find below my sources.list file with some lines uncommented hoping it would tell ubuntu where to get sources.

```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://ph.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://ph.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ph.archive.ubuntu.com/ubuntu breezy universe
deb-src http://ph.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ph.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

when i do 

```
sudo apt-get update
```

i get

```

Err http://security.ubuntu.com breezy-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err http://ph.archive.ubuntu.com breezy Release.gpg
  Temporary failure resolving 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com breezy-updates Release.gpg
  Temporary failure resolving 'ph.archive.ubuntu.com'
Err http://ph.archive.ubuntu.com breezy-backports Release.gpg
  Temporary failure resolving 'ph.archive.ubuntu.com'
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg  Temporary failure resolving 'ph.archive.ubuntu.com'
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg  Temporary failure resolving 'ph.archive.ubuntu.com'
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg  Temporary failure resolving 'ph.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg  Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list http://ph.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ph.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ph.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ph.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ph.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ph.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ph.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ph.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ph.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

being a newbie.. i find this cryptic..

i can only connect to the internet thru a proxy server. no direct connection.

thanks for your time everyone..

please help..


thank you!

---

### Post by Mustard on 2006-03-08
**Setting up apt-get to use a http-proxy**

```
gedit ~/.bashrc
```

add these lines to the bottom of your .bashrc file

```
http_proxy=http://yourproxyaddress:proxyport
export http_proxy
```

Save the file. Close your terminal window and then open another terminal window

Test proxy with sudo apt-get update and whatever networking tool you desire. I use firestarter to see active connections.

If you make a mistake and go back to edit the file again, remember to close the terminal and reopen it. It will not function with the new settings until you do.

The above was taken from this link....
[https://wiki.ubuntu.com/AptGetHowto](https://wiki.ubuntu.com/AptGetHowto)

---

### Post by jeisma on 2006-03-08
hello!

thank you so much! doing that i think apt-get is now able to connect to the internet.

```

~$ sudo apt-get update

Ign http://ph.archive.ubuntu.com breezy Release.gpg
Ign http://ph.archive.ubuntu.com breezy-updates Release.gpg
Ign http://ph.archive.ubuntu.com breezy Release
Ign http://ph.archive.ubuntu.com breezy-updates Release
Ign http://ph.archive.ubuntu.com breezy/main Packages
Ign http://ph.archive.ubuntu.com breezy/restricted Packages
Ign http://ph.archive.ubuntu.com breezy/main Sources
Ign http://ph.archive.ubuntu.com breezy/restricted Sources
Ign http://ph.archive.ubuntu.com breezy-updates/main Packages
Ign http://ph.archive.ubuntu.com breezy-updates/restricted Packages
Ign http://ph.archive.ubuntu.com breezy-updates/main Sources
Ign http://ph.archive.ubuntu.com breezy-updates/restricted Sources
Err http://ph.archive.ubuntu.com breezy/main Packages
  403 Forbidden
Err http://ph.archive.ubuntu.com breezy/restricted Packages
  403 Forbidden
Err http://ph.archive.ubuntu.com breezy/main Sources
  403 Forbidden
Err http://ph.archive.ubuntu.com breezy/restricted Sources
  403 Forbidden
Err http://ph.archive.ubuntu.com breezy-updates/main Packages
  403 Forbidden
Err http://ph.archive.ubuntu.com breezy-updates/restricted Packages
  403 Forbidden
Err http://ph.archive.ubuntu.com breezy-updates/main Sources
  403 Forbidden
Err http://ph.archive.ubuntu.com breezy-updates/restricted Sources
  403 Forbidden
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz  403 Forbidden
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz  403 Forbidden
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz  403 Forbidden
Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz  403 Forbidden
Reading package lists... Done
W: Couldn't stat source package list http://ph.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ph.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ph.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ph.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

but is being blocked by firewall or something (proxy powered by squid). what specifically should i request to the net admin so that proxy will allow kind of connection apt-get is requesting?

i may add, i understand there is a download limit of 2MB, would that matter?

also, with the above errors, via the firefox, i tried to download [http://ph.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://ph.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz), which went fine.

i tried wget -vc [http://ph.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://ph.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz), i get "ERROR 403: Forbidden."

enlighten me pls?


thank you so much (whew!) !

---

