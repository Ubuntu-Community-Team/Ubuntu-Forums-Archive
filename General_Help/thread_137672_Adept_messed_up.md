---
title: "Adept messed up"
date: 2006-02-28
forum: General Help
---

### Post by Optiker on 2006-02-28
I've posted this to Linux Questions, but thought I'd post here as well as this may be a little better targeted group.

Some time ago, when I was having trouble with my newly installed Kubuntu Breezy 5.10, somewhere in the process of trying to get it right with the help of folks on various forums, something went wrong with Adept. I got busy with other things, so wasn't able to pursue it, so left it. Now I am needing to install new packages, and need to fix the Adept problem.

When I try to run Adept, I get the error message dialog box title "Could not open Cache - Adept" with the error message...
---------------
The APT Database could not be opened! This may be caused by incorrect APT configuration or something similar. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.
---------------

When I ran apt-setup and selected /http as the source, it failed and I got the following message...
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Apt configuration &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; &#9474;
&#9474; Failed to access the Ubuntu archive &#9474;
&#9474; &#9474;
&#9474; While trying to access the Ubuntu archive using the information you &#9474;
&#9474; provided, the Ubuntu package management tool, apt, returned the &#9474;
&#9474; following error. The questions will be asked again. &#9474;
&#9474; &#9474;
&#9474; E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily &#9474;
&#9474; unavailable) E: Unable to lock the administration directory &#9474;
&#9474; (/var/lib/dpkg/), is another process using it?

Other than trying to run Adept and the console commands that gave these results, as far as I know, I wasn't using anything else that might be using the database. When I tried again and selected ftp as the source, it seemed to work and I got the following...
----------------------
Testing apt sources...
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Fetched 1B in 0s (1B/s)

Testing apt sources...
Hit [ftp://us.archive.ubuntu.com](ftp://us.archive.ubuntu.com) breezy Release.gpg
Hit [ftp://us.archive.ubuntu.com](ftp://us.archive.ubuntu.com) breezy Release
Hit [ftp://us.archive.ubuntu.com](ftp://us.archive.ubuntu.com) breezy/main Packages
Hit [ftp://us.archive.ubuntu.com](ftp://us.archive.ubuntu.com) breezy/restricted Packages
Reading package lists... Done
Hit [ftp://us.archive.ubuntu.com](ftp://us.archive.ubuntu.com) breezy Release.gpg
Hit [ftp://us.archive.ubuntu.com](ftp://us.archive.ubuntu.com) breezy Release
Hit [ftp://us.archive.ubuntu.com](ftp://us.archive.ubuntu.com) breezy/main Sources
Hit [ftp://us.archive.ubuntu.com](ftp://us.archive.ubuntu.com) breezy/restricted Sources
Reading package lists... Done

release v=5.10,o=Ubuntu,a=breezy,l=Ubuntu,c=restricted
release v=5.10,o=Ubuntu,a=breezy,l=Ubuntu,c=main
optiker@wd45992:~$
-------------------------

However, when I then tried to run Adept again, I got the same error message about not opening the cache as I did before I ran apt-setup.

When I tried to run apt-get update as isuggested in the original error message, I got the same cache error title with the following error message...
--------------------
The APT Database could not be opened! This may be caused by incorrect APT configuration or something similar. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.

E: Type 'http://packages.debian.org/stable/libs' is not known on line 2 in source list /etc/apt/sources.list
--------------------

Here's my sources list...
===============
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
[http://packages.debian.org/stable/libs](http://packages.debian.org/stable/libs)


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy main restricted

deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) breezy main restricted
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) breezy main restricted

deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) breezy main restricted
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) breezy main restricted
========================

I'm not very experienced with Linux, and don't know what to try next other than to clear the installation and start with a fresh install. Does anybody have any suggestions that I might try to avoid that? There were a variety of problems (for a newbie) with the first install that I don't want to go through again, but will if there's no other solution. I'm not real experienced, so any suggestions need to be pretty explicit, step-by-step for me to follow.

If I do have to clear it and start fresh, do I just delete all files on the partition and invoke a new installation from the CD? I can do that from Windows if I need to, from a Knoppix live CD, or from Kubuntu itself?

Thanks!
Optiker

---

### Post by gingermark on 2006-02-28
I think I got that original error message when Adept crashed once. I killed it + dpkg which was also running (using KSysGuard), rebooted and all was ok.

It's unlikely you have the same problem, after all you got some of the apt commands to work and probably have rebooted several times since the problem first surfaced.

Still, it might be worth as a first step to see if any processes are hanging about that might conflict with Adept (uch as Adept itself or dpkg).

Also, see if you can install something when using ftp. Something innocuous like KEdit, for example. (sudo apt-get install kedit). If that works, you might well be able to reinstall Adept, or even dpkg (although I think the latter might be risky).

Sorry I couldn't be more help, these are just some of my initial thoughts on the matter.

---

### Post by Optiker on 2006-02-28
Ginger....You're right..I have rebooted a number of times. But, I will try installing something simple like that and see what happens.

Thanks!
Optiker

---

### Post by Optiker on 2006-02-28
Ginger...Nope...tried to install Kedit and got the same error...doesn't lke line 2 of my sources list. Somebody on another forum suggested just commenting that 2nd line out. That occured to me, but didn't want to try, but with somebody else suggesting it, will try it.

Thanks again!
Optiker

---

### Post by Optiker on 2006-02-28
ginger...commented out that second line and all works well.

FYI

Optiker

---

### Post by gingermark on 2006-02-28
Yeah, sorry missed that. That line should beging with a "deb " in front of what you have.

I don't think that would be responsible for the lock errors though. Those are usually caused by another program affecting apt (for example, trying to apt-get install something when Adept is open would cause that error).

That's why I suggested using KSysGuard.

EDIT: Glad to see you got it working. That repository is a Debian one, which is probably not great to use, but as I say, if you have to put a "deb " in front of that line and it should work (assuming the rest is correct).

---

