---
title: "Breezy, Konqueror, upgrade problems"
date: 2006-03-30
forum: General Help
---

### Post by thorndike on 2006-03-30
Good morning folks,

At the request of the customer, KDE was installed on the server to enable their in-house backup guy to easily examine and swap their external backup disks.

I had a few hotplug issues with Hoary, so I ended up upgrading to Breezy. Unfortunately, that seemed to fix the hotplug issue, but installed several others. The main issue is this:

Something is wrong with KDE. When I plug in the external backup disk, the disk is installed via hotplugging, but when I right click on it to mount it, mount isn't even an option. Also, when I try to open it to look at the contents, KDE prompts me with the screen to select which application I want to open it with. Konqueror isnt even on the list. So I tried to install konqueror. This is what I get:

The following packages have unmet dependencies:
gksu: Depends: libgksu1.2-0 (>= 1.3.3) but 1.3.1-1ubuntu6 is to be installed
Depends: libgksuui1.0-1 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


So of course I try the apt-get -f install and get this:

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
gksu

When I continue I get this:

(Reading database ... 48970 files and directories currently installed.)
Removing gksu ...
/var/lib/dpkg/info/gksu.prerm: line 5: /usr/sbin/gconf-schemas: No such file or directory
dpkg: error processing gksu (--remove):
subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
gksu
E: Sub-process /usr/bin/dpkg returned an error code (1)


This is an endless loop that I am unable to get out of. Any and all help would be appreciated.

Thanks.

Thorndike

---

### Post by localzuk on 2006-03-30
It sounds like a semi-botched upgrade to me.

Could you tell us how you upgraded and post the contents of your /etc/apt/sources.list file here?

---

### Post by thorndike on 2006-03-30
My sources.list file:

# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe

deb [http://kubuntu.org/packages/kde35/](http://kubuntu.org/packages/kde35/) breezy main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy-updates universe multiverse




As was presented on one of the forums here, I upgraded by changing hoary to breezy in the sources.list file then updating and upgrading.

Thorndike

---

### Post by thorndike on 2006-03-31
Well, I fixed the problem.

All I had to do was to rename the gksu.prerm file.  Once this file was not seen by the OS, it updated and upgraded perfectly.

Now if I could only figure out why it occurred....

Thorndike

---

