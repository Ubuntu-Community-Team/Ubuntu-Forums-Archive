---
title: "How to Fix Error 'E:Malformed line'"
date: 2012-09-17
forum: General Help
---

### Post by Myst1234 on 2012-09-17
Hi,

First of all I'd like to thank everyone for their support on this forum. This is my first post, but only because I've been able to simply search the forum and find every answer I've needed! :p 

But alas, not this time :(

I've searched the forum and it seems like a lot of people have "Malformed line XX" errors and they all have different solutions. So, here's mine, I have an error 'E:Malformed line 57 in source list etc/apt/source.list (dist parse)'

So I dropped in to take a look at my "Malformed Line" but don't understand what's wrong with it. And without further delay, here is my source --


# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner ***<---This the culprit?***
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner  ***<---Or is it this guy?***

In case it helps here's a run down of my setup -
Linux OS, Ubuntu 12.04 Desktop, Unity Interface, and I don't know if this matters but, I got the error after trying to install Skype 4.0 for Linux.

Thanks in advance for the help, and I'm endlessly grateful for all the continued support and help!!

):P

---

### Post by Cheesemill on 2012-09-17
Try replacing the bottom 2 lines with:
```
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner
```

---

### Post by Myst1234 on 2012-09-17
After some playing around, looking around and reading around I have come to a solution - 

```
deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner 
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
```These two lines at the bottom (56 & 57) were almost correct, except they were missin 'ubuntu' in them. So 

This
```
deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner 
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
```Should have been this 
```
deb [http://archive.canonical.com/ubuntu precise]("http://archive.canonical.com/precise") partner 
deb-src [http://archive.canonical.com/ubuntu precise]("http://archive.canonical.com/precise") partner
```

After I added the missing 'ubuntu' a quick sudo apt-get update and I was in business.

My  advice to anyone getting these errors is to look closely at your  source, because you will probably find something missing, misplaced or  just flat out wrong on the line you are getting the error for. 

):P

---

### Post by Myst1234 on 2012-09-17
> **Cheesemill said:**
> Try replacing the bottom 2 lines with:
```
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner
```

Thanks Cheesemill! I was literally posting the solution I found when your response came in :lolflag:

---

### Post by Cheesemill on 2012-09-17
A good site if you want to check your sources.list or generate a new one:

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by bodhi.zazen on 2012-09-17
When you get an error , easy to use sed

```
sed -n '37,37p' /etc/apt/source.list
```

This command will show only the malformed line.

---

