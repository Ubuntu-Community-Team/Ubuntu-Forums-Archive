---
title: "Ubuntu 11.04 update problem"
date: 2011-06-21
forum: General Help
---

### Post by shamz_71 on 2011-06-21
it says

Software updates are available for this computer

Important security updates
Recommended updates

When is click on install
It stops with the message
"Requires installlation of untrustted packages"

---

### Post by kronick on 2011-06-21
you are missing some GPG keys, post your sudo apt-get update here

---

### Post by jerrrys on 2011-06-21
you have installed something without adding the "authorization key" to the software sources list.  maybe a ppa?

---

### Post by shamz_71 on 2011-06-22
> **kronick said:**
> you are missing some GPG keys, post your sudo apt-get update here

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by kronick on 2011-06-22
[QUOTE="alexfish"]try this

sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update


then test with

sudo apt-get update[/QUOTE]

try it, and post back

---

### Post by shamz_71 on 2011-06-22
> **kronick said:**
> try it, and post back

farooq@KhalidTank:~$ sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
sudo: aptitude: command not found

---

### Post by plucky on 2011-06-22
> **shamz_71 said:**
> farooq@KhalidTank:~$ sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
sudo: aptitude: command not found

Aptitude is not installed by default in Natty 

Try using apt-get instead ```
sudo apt-get -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
```

Good Luck

---

### Post by shamz_71 on 2011-06-23
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


After executing the command you told , igot the above message

---

### Post by plucky on 2011-06-24
> **shamz_71 said:**
> W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


After executing the command you told , igot the above message

The link in the error takes me [Here](http://www.ubuntu.com/usn/) which is not a repository.

Either your Repository server has the incorrect information or your sources.list is not correct.

1) Try changing your download server under "Software Sources" and see if that fixes the problem.

Or

2) post the output of ```
cat /etc/apt/sources.list
```


Good Luck

---

### Post by shamz_71 on 2011-06-24
> **plucky said:**
> The link in the error takes me [Here]("http://www.ubuntu.com/usn/") which is not a repository.

Either your Repository server has the incorrect information or your sources.list is not correct.

1) Try changing your download server under "Software Sources" and see if that fixes the problem.

Or

2) post the output of ```
cat /etc/apt/sources.list
```
Good Luck

I dont know how to change download server,
heres step 2 result


# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) natty universe
deb [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://ci.archive.ubuntu.com/ubuntu/](http://ci.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

---

### Post by plucky on 2011-06-24
> I dont know how to change download server,

Open **Synaptic Package Manager** and navigate to **Settings > Repositories** and that will open **Software Sources**

On the first page You can select another "Download Server".

You can also de-select the **Source Code** button as you don't need it unless you need to examine the code.

Then select Reload and see if that fixes the problem.

Good Luck

---

### Post by shamz_71 on 2011-06-25
I changed to US server and after RELOAD no error message ...
i dint get the update notification to update , so i still cant say if problem is fixed or not

---

### Post by shamz_71 on 2011-06-26
Problem Solved !!

---

