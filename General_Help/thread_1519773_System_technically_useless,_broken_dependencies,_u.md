---
title: "System technically useless, broken dependencies, unable to update or diagnose."
date: 2010-06-28
forum: General Help
---

### Post by dago1 on 2010-06-28
I can't update, download packages, or even diagnose due to an elusive error.

[IMG]http://imgur.com/kFqJY.png[/IMG]


[IMG][IMG]http://imgur.com/tS8i2.png[/IMG][/IMG]


If I try to update or check using terminal I get this

[IMG]http://imgur.com/He9FZ.png[/IMG]

I even tried to restart in recovery mode to check for broken packages and I got this error:

"Atrribute Error: 'NoneType' object has no attribure 'reqReinstallPkgs'"
"E: Type '.' is not known on line 58 in source list /etc/apt/sources.list"
"E: The list of sources could not be read"

I usually find answers in the documentation but this time I'm really stumped. I am Running 64 bit Ubuntu 9.04.

---

### Post by teilnehmer on 2010-06-28
Could you post the output of
```
less /etc/apt/sources.list
```
This shows the content of the file that the alert claims to contain the error. 

The sources.list is the list of all the repositories where you get updates and new packages. Maybe something went wrong with that file. It should look similar to the extract here: 
```
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```

PS: "less" displays the content of the file. To exit that view, press "q".

---

### Post by RJARRRPCGP on 2010-06-28
Looks like a typo in sources.list.

---

### Post by dago1 on 2010-06-28
Here is the output of:
                       less /etc/apt/sources.list


 1 #deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
      2 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
      3 # newer versions of the distribution.
      4 
      5 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
      6 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
      7 
      8 ## Major bug fix updates produced after the final release of the
      9 ## distribution.
     10 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
     11 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
     12 
     13 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
     14 ## team. Also, please note that software in universe WILL NOT receive any
     15 ## review or updates from the Ubuntu security team.
     16 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
     17 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
     18 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
     19 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
     20 
     21 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
     22 ## team, and may not be under a free licence. Please satisfy yourself as to 
     23 ## your rights to use the software. Also, please note that software in 
     24 ## multiverse WILL NOT receive any review or updates from the Ubuntu
     25 ## security team.
     26 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
     27 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
     28 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
     29 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
     30 
     31 ## Uncomment the following two lines to add software from the 'backports'
     32 ## repository.
     33 ## N.B. software from this repository may not have been tested as
     34 ## extensively as that contained in the main release, although it includes
     35 ## newer versions of some applications which may provide useful features.
     36 ## Also, please note that software in backports WILL NOT receive any review
     37 ## or updates from the Ubuntu security team.
     38 # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
     39 # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
     40 
41 ## Uncomment the following two lines to add software from Canonical's
     42 ## 'partner' repository.
     43 ## This software is not part of Ubuntu, but is offered by Canonical and the
     44 ## respective vendors as a service to Ubuntu users.
     45 # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
     46 # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
     47 
     48 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
     49 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
     50 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
     51 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
     52 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
     53 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
     54 deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
     55 deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
     56 deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main
     57 
     58 .
     59 
     60 
     61 
     62 
     63 
     64 sudo apt-key add - 
     65 sudo apt-get update
     66 
     67 
     68 sudo apt-get install zsnes32
     69 
     70 
     71 
     72 
     73 
     74 sudo apt-key add - 
     75 sudo apt-get update
     76 sudo apt-get install zsnes32
     77 
     78 
     79 
(END)

---

### Post by teilnehmer on 2010-06-28
Everything after line 56 should not be in there. Erase these lines and save the file. After that, you should be fine. 

To edit that file, you'll have to open it with sudo, e.g. 
```
sudo gedit /etc/apt/sources.list
```

---

### Post by nothingspecial on 2010-06-28
You`ve messed up your sources list.

This is the default Jaunty one
```

deb cdrom:[Ubuntu 9.04 _Jaunty  Jackalope_ - Release Candidate amd64 (20090414.2)]/ jaunty main  restricted
deb http://archive.ubuntu.com/ubuntu jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu jaunty main restricted

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main  restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu jaunty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the  Ubuntu
## team. Also, please note that software in universe WILL NOT receive  any
## review or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu jaunty universe
# deb-src http://archive.ubuntu.com/ubuntu jaunty universe
# deb http://archive.ubuntu.com/ubuntu jaunty-updates universe
# deb-src http://archive.ubuntu.com/ubuntu jaunty-updates universe
# deb http://security.ubuntu.com/ubuntu jaunty-security universe
# deb-src http://security.ubuntu.com/ubuntu jaunty-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the  Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as  to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://archive.ubuntu.com/ubuntu jaunty multiverse
# deb-src http://archive.ubuntu.com/ubuntu jaunty multiverse
# deb http://archive.ubuntu.com/ubuntu jaunty-updates multiverse
# deb-src http://archive.ubuntu.com/ubuntu jaunty-updates multiverse
# deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
# deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
```Change it for that, and ask questions if you are unsure before you do it.

---

### Post by nothingspecial on 2010-06-28
> **teilnehmer said:**
> Everything after line 56 should not be in there. Erase these lines and save the file. After that, you should be fine. 

To edit that file, you'll have to open it with sudo, e.g. 
```
sudo gedit /etc/apt/sources.list
```

No, (S)he shouldn`t have gutsy and feisty stuff in there.

---

### Post by teilnehmer on 2010-06-28
Whoops, didn't look that closely. Thank you!

---

### Post by dago1 on 2010-06-28
I opened the source list file with:

sudo gedit /etc/apt/sources.list         thank you!  teilnehmer

I deleted everything and pasted the default list. Thank you! nothingspecial


How does one mess up the source list anyway? how can I prevent it from happening again?

---

### Post by nothingspecial on 2010-06-28
> **dago1 said:**
> 

How does one mess up the source list anyway? how can I prevent it from happening again?

It depends what you did.

My guess is that you followed a couple of out dated guides, which is why you had gutsy and feisty (very old versions of ubuntu) stuff in there, and then appended commands to it which should have been issued in the terminal.

You are using jaunty, only add software repositories that refer to jaunty, and if you upgrade to karmic or lucid, the same applies.

And only add software repositories to your sources, not lines of code.

---

### Post by nothingspecial on 2010-06-28
> **teilnehmer said:**
> Whoops, didn't look that closely. Thank you!

No problem, wasn`t trying to be funny, just helpful. :p

---

