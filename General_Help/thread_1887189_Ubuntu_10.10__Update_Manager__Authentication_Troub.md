---
title: "Ubuntu 10.10:  Update Manager:  Authentication Trouble"
date: 2011-11-26
forum: General Help
---

### Post by tinker123 on 2011-11-26
Hi;

I'm running Ubuntu 10.10.    The update manager came up the other day.  However, when I hit the "Authenticate" button, nothing happens --- I've let it sit for about 5 min?

How can I fix this?

Thanks

---

### Post by BC59 on 2011-11-26
Maybe is a problem with your repositories

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo gedit /etc/apt/sources.list
```


comment with hash (#) the repositories who believe they could have problem and

```
sudo apt-get update
```

---

### Post by tinker123 on 2011-11-26
I'm that familiar with various repositories  I'm pasting my sources.list below.  Do any of the listing look problematic?

Thanks either way

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted universe multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed restricted main multiverse universe #Added by software-properties
deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository

---

### Post by BC59 on 2011-11-26
Just try to comment with hush the 8 last PPAs. Then save and update.

If the problem is not there you redo it.

---

### Post by BC59 on 2011-11-26
Well I just googled a little bit and seems that your problem is caused by a bug.

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/822131](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/822131)

Maybe the problem started after an update, so as a workaround to the bug, you could reboot and logon using the previous kernel.
Then try to see if Update Manager is working.

---

### Post by tinker123 on 2011-11-26
> **BC59 said:**
> Well I just googled a little bit and seems that your problem is caused by a bug.

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/822131](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/822131)

Maybe the problem started after an update, so as a workaround to the bug, you could reboot and logon using the previous kernel.
Then try to see if Update Manager is working.

I have NO idea how to do that.  I went to that page and the issue seems slightly different from mine as well as being for a different version of Ubuntu.

Still, it gave me an idea.

I logged back in as "root" and ran update manager without a problem.   

I guess I will have to wait until the next update to see if it is an ongoing problem.

Thanks for the help.

---

### Post by tinker123 on 2012-05-09
This problem seems to have taken care of itself.

That problem was that whenever I tried to run the update manager in 10.10 the authentication dialog box would shake when I pressed authenticate and do nothing.

I was still able to update via apt-get on the command line.

About a week or so, ago, the update manager started giving me a message saying that 10.10 had reached the end of its support life and that I would get no more updates.

I upgraded.   No more problem with the authentication button and dialog box in the update manager.

I'm guessing the good folks at Ubuntu turned something off for 10.10 before they started displaying a message that their support for it was over.

---

