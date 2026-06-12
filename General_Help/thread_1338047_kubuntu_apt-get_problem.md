---
title: "kubuntu apt-get problem"
date: 2009-11-26
forum: General Help
---

### Post by adkinsbf on 2009-11-26
I am new to Linux and have successfully installed Kubuntu 9.10, dual booting with Windows (no problem with that).  In fact, I was impressed that the application installed so smoothly.  After several days of using Kubuntu, I received error messages suggesting to me that apt-get, which I understand to be a component of KPackageKit, has somehow been corrupted.  My difficulty is that I cannot figure out how to correct the problem without re-installing Kubuntu.  But I would rather know how to fix the problem.

The three error messages that I have gotten are the following:

"E:  The list of sources could not be read"
"E:  Malformed line 54 in source list /etc/apt/sources.list"
"No package cache is available.  The package needs to be rebuilt.  This should have been done by the backend automatically."

I have consulted a half-dozen Ubuntu books and have tried to search online for help, but in the latter case I either have been using the wrong search terms or nobody has posted this problem.

I did attempt repairing broken packages using the recovery menu (several times) and rebuilding the sources list, using instructions I found online, but in the first instance nothing seemed to happen and in the second instance I received one or more of the above error messages.

I would welcome ideas for correcting this problem -- I am unable to download any program updates or enhancements because of the apt-get issue.  Feel free to contact me by e-mail at the address posted with this forum and to post here.

Regards,
Ben

---

### Post by solar george on 2009-11-26
Please post your /etc/apt/sources.list

---

### Post by adkinsbf on 2009-11-27
The following is a listing of the content of my Kubuntu /etc/apt/sources.list text file.  Note that the very last line in the file is a result of my copying the Linux WordPerfect application to my /home directory, so it could well be the source of the error message I am receiving that refers to line 54 in sources.list.  If so, what should I do next to correct the problem?:

# deb cdrom:[Kubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb /home/ben/Programs/wordperfect-8 Runme

Regards,
Ben

---

### Post by solar george on 2009-11-27
```
The following is a listing of the content of my Kubuntu /etc/apt/sources.list text file. Note that the very last line in the file is a result of my copying the Linux WordPerfect application to my /home directory, so it could well be the source of the error message I am receiving that refers to line 54 in sources.list. If so, what should I do next to correct the problem?:

```
Yep thats the error you're seeing, remove that line and then reload your package lists to get apt-get working again.

Are you sure you want to run wordperfect? AFAICT it is a very outdated application?

---

### Post by adkinsbf on 2009-11-28
I will remove that line from the file.  Just to make sure I do it correctly, I assume that it requires logging in as sudo, then changing permissions so that I can write to the file, deleting the line.

The next step I'm not sure of either.  Do I simply save the file back to the /apt/get location, or is something else required?

---

### Post by raktarok on 2009-11-28
> **adkinsbf said:**
> I will remove that line from the file.  Just to make sure I do it correctly, I assume that it requires logging in as sudo, then changing permissions so that I can write to the file, deleting the line.

The next step I'm not sure of either.  Do I simply save the file back to the /apt/get location, or is something else required?

just do this from a terminal.
```
gksudo gedit /etc/apt/sources.list
```
Then remove the line, and save the file in its current location.You don't need to login as root or change permissions.

---

### Post by adkinsbf on 2009-11-28
In response to the command gksudo gedit /etc/apt/sources.list, my Kubuntu session responded that gedit is not installed.  Is gedit not a default application within Kubuntu?

After reviewing "man" pages and Ubuntu books, and a few false starts, I tried the following command:  "gksudo kate".  Then I opened sources.list in "Kate," deleted line 54, and successfully saved the file with that change.  Previously I had opened "Kate" without gksudo and unsuccessfully attempted the same procedure.

The error messages that have been repeatedly popping up on my desktop about the error in sources.list have stopped, and I have successfully used the "update" command.  So the problem seems to be solved.

But -- please let me know if I have solved only part of the problem and other difficulties lurk in the system.

Thanks for your patience in guiding me through this -- I would never have found the solution on my own hook.  I would eventually have deleted the boot loader and reinstalled Kubuntu.  :KS

Best Wishes,
Ben

---

### Post by solar george on 2009-11-28
> In response to the command gksudo gedit /etc/apt/sources.list, my Kubuntu session responded that gedit is not installed. Is gedit not a default application within Kubuntu?

Yes gedit is a gnome command (so you'd find it on Ubuntu not Kubuntu) while kate is the KDE (Kubuntu) eqivalent.

---

### Post by raktarok on 2009-11-28
oops.. sorry adkinsbf, I did not notice earlier that you were using kubuntu..anyway, glad to hear that you solved the problem.. Have fun with kubuntu!

---

### Post by mastodon88 on 2010-01-21
totally new to linux but lovin it so far, im having a similar issue, tho when i run gksudo kate it says i need to install gksudo,  and when i try to install it i get the package error saying

Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing globus-gass-copy-progs (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.


so i followed your instructions and found the sources.list in 
etc/apt and it reads:

#deb cdrom:[Kubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse


i dont have the line that ben has that you guys told him to delete, yet i get the same package error, any ideas?

btw my name is ben too, any help appreciated 
thanks guys

btw running kubuntu karmic 9.10

---

### Post by solar george on 2010-01-21
OK, that appears to be a different problem entirely.
First, as you're on kubuntu you should do kdesudo kate not gksudo.

For the apt problem try;
```
sudo apt-get update
```
If that fails or package installation continues to fail try;
```
sudo rm -Rv /var/lib/apt/lists/*
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get update
```

---

### Post by mastodon88 on 2010-01-21
ok it seems to have fixed it thank you,

---

