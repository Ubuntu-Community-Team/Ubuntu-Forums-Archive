---
title: "Failed to fec"
date: 2009-10-19
forum: General Help
---

### Post by karimruan on 2009-10-19
I get this error when downloading from play/getdeb:

W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg)  Could not resolve 'archive.ubuntustudio.org'

W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntustudio.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.


I understand that it is saying that archive.ubuntustudio.org is not there, or is not responding. How do I get past this, these two sites have debs i can't find anywhere else!

---

### Post by mac9416 on 2009-10-19
Apparently all the software that was in archive.ubuntustudio.org was moved to the official repos a while back. I would suggest you remove the UbuntuStudio lines from your /etc/apt/sources.list, and see if you can still get the packages you were looking for.

Good luck!

---

### Post by mechro on 2009-10-19
Phew! for a minute there I thought Father Jack had drunk his last drop! ;)

---

### Post by karimruan on 2009-10-19
Alright, I removed the ubuntu studio repository from my sources list. Do I need to replace it with anything?

---

### Post by mac9416 on 2009-10-19
You may want to enable the "universe" or "multiverse" sections that may not be enabled. A great explanation of those is provided here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by karimruan on 2009-10-19
Okay I checked out that link, and think I got more insight to the problem. When my computer tries to check for new, removed, or updated software, it is failing to fetch on most of the 43 files, and then exits abruptly, giving no other output. This is a fresh install, so I haven't done much tweaking except for converting ubuntu to ubuntu studio (9.04 to 9.04).

---

### Post by mac9416 on 2009-10-19
So you're still having trouble? Could you post the output of the command you're getting errors on? Thanks.

---

### Post by karimruan on 2009-10-19
Okay, here is what I get as output:

They are attachements, screenshots.

I went to System>admin>software sources. So I don't get any terminal output. Is there a command that can be used to get some valuable terminal output?

Here is my /etc/apt/sources.list:

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

---

### Post by mac9416 on 2009-10-19
OK, go to System>Administration>Software sources then to the "Third-party Software" tab. Then uncheck any lines beggining with "cdrom://". Everything should work from there.

---

### Post by karimruan on 2009-10-21
There is nothing beginning with that in my third party tab. 
INSERT EDIT: I unchecked the cdrom part on the main page, not the third party page, which does not have the option. Still not working. END INSERT EDIT.

Maybe there is some kind of terminal output I could somehow get that would provide more details as to what the problem is? If only I could get the output that I get captured, but it goes by to fast. Maybe download something from playdeb.net and click on SHOW FOR INDIVIDUAL FILES:

This is what I am trying to do, but most of the files fail to fetch and it closes out too fast, and no option that I can see to keep it open. Isn't there a way to do everything GUI based in the terminal?

I really don't need the games, but every little part of my system that doesn't work bothers me ALOT! I have an obsession with it running perfect.

---

### Post by karimruan on 2009-10-21
When trying to edit software sources in Sys>admin>software sources, I get a message saying the software sources are old or out of date. I am told to reload them, so i do. I guess this is updating the sources. WHen it fails, I get this output:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2)  
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages.bz2)  
Some index files failed to download, they have been ignored, or old ones used instead.

What does this mean?

---

