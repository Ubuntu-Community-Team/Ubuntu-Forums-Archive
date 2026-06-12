---
title: "Apt-offline"
date: 2012-01-23
forum: General Help
---

### Post by nariub on 2012-01-23
apt-offline works

I have an offline (no internet connection) 10.04 server
and an online 10.04 workstation ..

installed apt-offline on the online workstation

**sudo apt-get install apt-offline**

which works fine

from */var/cache/apt/archives/*

copied the following two files to a usb-stick
[B]apt-offline_0.9.5_all.deb
python-argparse_1.1-1_all.deb
[/B]
sneakernet to the offline machine
install python then apt-offline onto the offline machine

and the piece i forgot originally..
set the offline machine to download all updates in the background.
if you set it to notify only, it will not populate the resulting zip file with .deb files..

now on the offline system
we create the sig file that says all the stuff we have..
**sudo apt-offline set ./hostname-date.sig**

you might have to do two here.
**sudo apt-offline set --upgrade-type dist-upgrade ./hostname-date-dist.sig**

the second one pulls the kernel updates for you.

copy the two sig files to your usb and sneakernet back over to the online system

[B]sudo apt-offline get ./hostname-date.sig --threads 5 --bundle hostname-date.zip

[/B]and if you have the second one[B]
sudo apt-offline get ./hostname-date-dist.sig --threads 5 --bundle hostname-date-dist.zip[/B]

the other online guides suggest adding bug reports for reading.. I did not..

copy the resulting zip files to your usb and sneakernet them back over to the offline system..  

on the offline system
[B]sudo apt-offline install ./hostname-date.zip
sudo apt-offline install ./hostname-date-dist.zip
[/B]
which will update the repo's and the cache..

update all the packages
[B]sudo apt-get upgrade
[/B]
and to update the kernel
**sudo apt-get dist-upgrade**

my update-manager gui still says it has been 432 days since my last update..
but it says she is up-to-date too..

if anyone comes up with a similar method to update this 10.04 to the upcoming 12.04 LTS  I would be happy to hear about it..

---

### Post by cortman on 2012-01-23
It'd be WAY simpler to just use Synaptic to generate a download script. See the links in my signature.

As far as upgrading the OS, I don't think you can jump upgrades like that (i.e, 10.04 to 12.04, etc.). And anyway it'd be best to back up your stuff and do a fresh installation.

---

### Post by nariub on 2012-01-23
thanks for the synaptic notes.

jumping from one LTS to the next is supported, or at least has been in the past.

---

### Post by cortman on 2012-01-24
> **nariub said:**
> thanks for the synaptic notes.

jumping from one LTS to the next is supported, or at least has been in the past.

You're right- after doing a little research, it looks like you CAN do skip-over upgrades like that. Sorry to be misleading!

---

### Post by nariub on 2012-01-24
Perhaps I have done something wrong..

it appears to be a two pass thing

create the sig offline
use the sig online to create a zip which only contains notifications no packages.
install the zip offline
.. apt-get upgrade doesnt have any cached debs to install
create another sig offline
use the second sig to create a second zip which now contains the debs
install the second zip offline
apt-get upgrade or dist-upgrade installs the packages..

---

### Post by riteshsarraf on 2012-01-24
@nariub

For a freshly installed box, with no APT Repository database, there's no way for the system to know what all packages can be installed/upgraded. So the first iteration of apt-offline only generates the Repository Database to download.

Once that is done, and is in sync on your box (in your case 10.04), then the OS is able to determine packages that need an upgrade (or can provide you with details on new packages that can be installed).

If you take a CD installation with no network connection ever made, the only repository that the OS is aware of is is the CDROM repository. apt-offline bridges that gap too, but it needs 2 iteration before it can normalize everything. :D


Hope that helps.

---

### Post by nariub on 2012-01-25
> **riteshsarraf said:**
> @nariub

For a freshly installed box, with no APT Repository database, there's no way for the system to know what all packages can be installed/upgraded. So the first iteration of apt-offline only generates the Repository Database to download.

Once that is done, and is in sync on your box (in your case 10.04), then the OS is able to determine packages that need an upgrade (or can provide you with details on new packages that can be installed).

If you take a CD installation with no network connection ever made, the only repository that the OS is aware of is is the CDROM repository. apt-offline bridges that gap too, but it needs 2 iteration before it can normalize everything. :D


Hope that helps.

thanks boss,
Thought I was doing it wrong. ;)

---

### Post by fagulhaspt on 2012-03-21
Could anyone help me: I'm having trouble using apt-offline to upgrade a freshly installed ubuntu11.10

The idea is to use apt-offline in a linux party so that the common packages and upgrades are done using local files

The question is already better explained in Stack overflow by some other person:

[http://stackoverflow.com/questions/9812539/using-apt-offline-on-ubuntu-fresh-install-for-linux-parties]("http://stackoverflow.com/questions/9812539/using-apt-offline-on-ubuntu-fresh-install-for-linux-parties")

Greetings, fagulhaspt

---

### Post by nariub on 2012-03-21
I don't know anything about the linux parties, nor did you provide sufficient description of a 'problem'.

if everyone is using the exact same version of ubuntu, you update one and then rsync the /var/cache/apt/archives/ directory to the other boxes and repeat the update..  

you could copy the contents of the archives to a disc and sneakernet it if everyone is in the same room..  

no offline update required 

..  I must be missing something ..

---

### Post by cortman on 2012-03-21
> **fagulhaspt said:**
> Could anyone help me: I'm having trouble using apt-offline to upgrade a freshly installed ubuntu11.10

The idea is to use apt-offline in a linux party so that the common packages and upgrades are done using local files

The question is already better explained in Stack overflow by some other person:

[http://stackoverflow.com/questions/9812539/using-apt-offline-on-ubuntu-fresh-install-for-linux-parties]("http://stackoverflow.com/questions/9812539/using-apt-offline-on-ubuntu-fresh-install-for-linux-parties")

Greetings, fagulhaspt

Hi, please start a new thread for your problem, and give a little more info. Thanks.

---

### Post by fagulhaspt on 2012-03-21
> **cortman said:**
> Hi, please start a new thread for your problem, and give a little more info. Thanks.

Ok, thanks for the reorientation :)

---

### Post by nariub on 2012-05-29
having a little trouble getting apt-offline working on 12.04

the **set** seems to work on the offline box

the **get** is getting 404-errors and file-not found when pulling the first update

the **install** says it syncs, but nothing seems to be changing.

Get errors look like these.
[SIZE=1]
ERROR: [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index.bz2](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index.bz2) - 404 - Not Found.                              
ERROR: [http://extras.ubuntu.com/ubuntu/dists/precise/InRelease](http://extras.ubuntu.com/ubuntu/dists/precise/InRelease) - 404 - Not Found.                              
ERROR: [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index.gz](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index.gz) - 404 - Not Found.                              
ERROR: [http://extras.ubuntu.com/ubuntu/dists/precise/InRelease.bz2](http://extras.ubuntu.com/ubuntu/dists/precise/InRelease.bz2) - 404 - Not Found.             
[/SIZE][SIZE=1]ERROR: [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index.lzma](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Index.lzma) - 404 - Not Found.                              
Downloading [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources.bz2).                              
ERROR: [http://extras.ubuntu.com/ubuntu/dists/precise/InRelease.gz](http://extras.ubuntu.com/ubuntu/dists/precise/InRelease.gz) - 404 - Not Found.                              
ERROR: [http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Index.bz2](http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Index.bz2) - 404 - Not Found.                              
ERROR: [http://archive.canonical.com/ubuntu/dists/precise/InRelease](http://archive.canonical.com/ubuntu/dists/precise/InRelease) - 404 - Not Found.                              
ERROR: [http://extras.ubuntu.com/ubuntu/dists/precise/InRelease.lzma](http://extras.ubuntu.com/ubuntu/dists/precise/InRelease.lzma) - 404 - Not Found.               
ERROR: [http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Index.gz](http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Index.gz) - 404 - Not Found.                              
ERROR: [http://archive.canonical.com/ubuntu/dists/precise/InRelease.bz2](http://archive.canonical.com/ubuntu/dists/precise/InRelease.bz2) - 404 - Not Found.    
ERROR: [http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Index.lzma](http://archive.canonical.com/ubuntu/dists/precise/partner/i18n/Index.lzma) - 404 - Not Found.                              
ERROR: [http://archive.canonical.com/ubuntu/dists/precise/InRelease.gz](http://archive.canonical.com/ubuntu/dists/precise/InRelease.gz) - 404 - Not Found.                              
ERROR: [http://archive.canonical.com/ubuntu/dists/precise/InRelease.lzma](http://archive.canonical.com/ubuntu/dists/precise/InRelease.lzma) - 404 - Not Found.                              
ERROR: [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Index.bz2](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Index.bz2) - 404 - Not Found.                              
Downloading [http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease](http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease).                              
ERROR: [http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Index.gz](http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Index.gz) - 404 - Not Found.                              
ERROR: [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Index.bz2](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Index.bz2) - 404 - Not Found.                              
ERROR: [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Index.bz2](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Index.bz2) - 404 - Not Found.                              
ERROR: [http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease](http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease) - 404 - Not Found.                              
ERROR: [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Index.gz](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Index.gz) - 404 - Not Found.                              
ERROR: [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Index.gz](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Index.gz) - 404 - Not Found.                              
ERROR: [http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Index.lzma](http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Index.lzma) - 404 - Not Found.                              
Downloading [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources.bz2).                              
ERROR: [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Index.gz](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Index.gz) - 404 - Not Found.                              
ERROR: [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Index.lzma](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Index.lzma) - 404 - Not Found.                              
Downloading [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources.bz2).                              
ERROR: [http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease.bz2](http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease.bz2) - 404 - Not Found.                              
ERROR: [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Index.lzma](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Index.lzma) - 404 - Not Found.                              
Downloading [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources.bz2).                              
ERROR: [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Index.lzma](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Index.lzma) - 404 - Not Found.                              
Downloading [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources.bz2).    [/SIZE]

        

I seem to be doing something wrong 
or did the command change between lucid and precise?

---

### Post by nariub on 2012-05-30
[http://www.debian-administration.org/article/648/Offline_Package_Management_for_APT](http://www.debian-administration.org/article/648/Offline_Package_Management_for_APT)

entry 48 from march


**apt-offline install --allow-unauthenticated ./XXXX.zip**

sweet we all back now.

---

