---
title: "sudo apt-get update error"
date: 2011-02-20
forum: General Help
---

### Post by jezzyjez on 2011-02-20
Hi I'm getting an error when typing in 

```
sudo apt-get update
```

I receive:

```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

```

I'm running Umbuntu 10.10 and am quite new to all this

Any help would be great!

Jez

---

### Post by Rubi1200 on 2011-02-20
Hi and welcome to the forums :-)

Are you also running Synaptic or Ubuntu Software Center when running that command?

Close all instances of package managers and then try the command again.

---

### Post by jezzyjez on 2011-02-20
Thanks.

I have no windows open but have run them recently, I checked the processes with system monitor and no instances of these programs showed up.

The closest thing I could see was 'update-notifier' which is 'sleeping'.

---

### Post by Rubi1200 on 2011-02-20
Try logging out and back in again, then run the command.

You can also post this:

```
cat /etc/apt/sources.list
```

---

### Post by jezzyjez on 2011-02-20
Logging in and logging out gave the same error.

I ran the above code and got:

```
#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Lubuntu 10.10 _Maverick Meerkat_ - i386 (20101010)]/ maverick main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse

```

Then ran the get update again and recieved the same error. What did the last bit of code actually do?

---

### Post by Rubi1200 on 2011-02-20
Sometimes you might have third party repositories causing problems, but this does not appear to be the case here (reason for checking the output of the command).

What does this command show:
```
 sudo dpkg --configure -a
```

You can also try opening Synaptic and using the Reload function then close and try from the terminal again.

---

### Post by ultimateD1 on 2011-02-20
i am having problems with sudo apt-get update as well but my error is...



'E:Type 'main' is not known on line 4 in source list /etc/apt/sources.list.d/tualatrix-ppa-maverick.list'

any suggestions? thanks

---

### Post by jezzyjez on 2011-02-20
Ok the configure code ran without error but produced no messages.

Upon reloading in synaptic (and pausing at 100 of 108 packages) a popup box appeared with:

Please insert the disc labelled:
Lubuntu 10.10 _Maverick Meerkat_ - i386 (20101010)
in drive /cdrom/

This is confusing as I am running Ubuntu 10.10 and have never used Lubuntu.

I inserted my Ubuntu 10.10 disc and this reproduced the same error I cancelled and the following error log was displayed:

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```
Failed to fetch cdrom://Lubuntu 10.10 _Maverick Meerkat_ - i386 (20101010)/dists/maverick/main/i18n/Translation-en.bz2  
Failed to fetch cdrom://Lubuntu 10.10 _Maverick Meerkat_ - i386 (20101010)/dists/maverick/main/i18n/Translation-en_GB.bz2  
Failed to fetch cdrom://Lubuntu 10.10 _Maverick Meerkat_ - i386 (20101010)/dists/maverick/restricted/i18n/Translation-en.bz2  
Failed to fetch cdrom://Lubuntu 10.10 _Maverick Meerkat_ - i386 (20101010)/dists/maverick/restricted/i18n/Translation-en_GB.bz2  
Failed to fetch cdrom://Lubuntu 10.10 _Maverick Meerkat_ - i386 (20101010)/dists/maverick/Release  
Failed to fetch http://ppa.launchpad.net/jeremysaunders/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/jeremysaunders/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/stevenrwalter/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/stevenrwalter/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

I then ran sudo apt-get update again

which ran through with muliple hits then produced the lines:

```
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
Media Change: Please insert the disc labelled
 'Lubuntu 10.10 _Maverick Meerkat_ - i386 (20101010)'
in the drive ‘/cdrom/’ and press enter

```

after pausing on 90% working.

---

### Post by Rubi1200 on 2011-02-20
Okay, that is a bit odd. Try this, go to Synaptic > Settings > Repositories and make sure there is no check mark next to the installable from CD-ROM.

Try Reload again and see what happens.

Also, run this in the terminal:
```
ps -e | grep apt
```
Perhaps there is some process keeping apt open (other than what you have open of course)

---

### Post by jezzyjez on 2011-02-20
Went to the window and there is no tick next to the cd

However I looked in other software and cdrom:[Lubuntu 10.10 . . .

is there. Could this be the problem child??

Should I remove it?

Jez

---

### Post by Rubi1200 on 2011-02-20
> **jezzyjez said:**
> Went to the window and there is no tick next to the cd

However I looked in other software and cdrom:[Lubuntu 10.10 . . .

is there. Could this be the problem child??

Should I remove it?

Jez
Could be; I see no harm in removing it especially if you know you have never used Lubuntu. Curious to know how it got there though.

If doing this and Reload does not work, try rebooting and then give it another go. If some process is locking apt rebooting should sort it out.

---

### Post by jezzyjez on 2011-02-20
Ok I removed this and restarted the computer.

Then did a reload in synaptic then ran the update in terminal again and it completed successfully with no errors.

I have no idea how it got there though?! 

Thankyou very much for your help

---

### Post by Rubi1200 on 2011-02-20
> **jezzyjez said:**
> Ok I removed this and restarted the computer.

Then did a reload in synaptic then ran the update in terminal again and it completed successfully with no errors.

I have no idea how it got there though?! 

Thankyou very much for your help
No problem, you are more than welcome :-)

Glad things worked out in the end.

---

