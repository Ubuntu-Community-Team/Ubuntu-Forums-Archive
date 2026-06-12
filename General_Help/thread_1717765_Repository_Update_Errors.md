---
title: "Repository Update Errors"
date: 2011-03-30
forum: General Help
---

### Post by joelstitch on 2011-03-30
Im getting a few errors when updating the repository and I dont know how to fix it. I need help. This is what Im getting:

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

[QUOTE]Failed to fetch [http://wicd.longren.org/dists/feisty/Release.gpg](http://wicd.longren.org/dists/feisty/Release.gpg)  Something wicked happened resolving 'wicd.longren.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://wicd.longren.org/dists/feisty/all/i18n/Translation-en_CA.bz2](http://wicd.longren.org/dists/feisty/all/i18n/Translation-en_CA.bz2)  Something wicked happened resolving 'wicd.longren.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://wicd.longren.org/dists/feisty/all/binary-amd64/Packages.gz](http://wicd.longren.org/dists/feisty/all/binary-amd64/Packages.gz)  Something wicked happened resolving 'wicd.longren.org:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.[/QUOTE]

[IMG]http://img24.imageshack.us/img24/8040/screenshot3ov.png[/IMG]

---

### Post by 3Miro on 2011-03-30
Somehow you are looking for repositories for Feisty Fawn that came out 4 years ago and is no longer supported.

How did this happen?

---

### Post by joelstitch on 2011-03-30
> **3Miro said:**
> Somehow you are looking for repositories for Feisty Fawn that came out 4 years ago and is no longer supported.

How did this happen?

No idea. I'm guessing from following instructions to install other applications...

---

### Post by 3Miro on 2011-03-30
WICD is include in the Ubuntu repos by default, you should not have followed extra instructions. Try going to System -> Admin -> Software Sources and disable everything "fiesty".

---

### Post by joelstitch on 2011-03-30
> **3Miro said:**
> WICD is include in the Ubuntu repos by default, you should not have followed extra instructions. Try going to System -> Admin -> Software Sources and disable everything "fiesty".

I did, and now Im getting this:

> Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by 3Miro on 2011-03-30
What it gives you is the last repository it did not manage to resolve. Do you have
```
http://ca.archive.ubuntu.com/ubuntu/...id/Release.gpg
```
listed in the Software Sources?

.gpg is a "signature" file, it is not a repository and should not accessed when trying to update.

---

### Post by joelstitch on 2011-03-30
I didnt see it .

---

### Post by philinux on 2011-03-30
> **joelstitch said:**
> No idea. I'm guessing from following instructions to install other applications...

Open a terminal. Post back what this says.

```
cat /etc/apt/sources.list
```

---

### Post by joelstitch on 2011-03-30
This is what I got. 
> # deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
# deb [http://wicd.longren.org](http://wicd.longren.org) feisty all
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty universe



---

### Post by 3Miro on 2011-03-30
That one shouldn't be in there:
```
deb http://archive.ubuntu.com/ubuntu jaunty universe
```
Try removing this one form the Software Sources.

If it is not there, you can open the file with gedit:
```
gksudo gedit /etc/apt/sources.list
```
and then add # in front of the last line. However, BE VERY CAREFUL, you don't want to accidentally edit anything else.

---

### Post by joelstitch on 2011-03-30
Im getting this now:

> Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by 3Miro on 2011-03-30
Are you sure you copy/pasted everything that you got from philinux's command. Just to make sure, can you do it again.

```
cat /etc/apt/sources.list
```

Look specifically at the bottom.

---

### Post by joelstitch on 2011-03-30
Here you go:

> # deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
# deb [http://wicd.longren.org](http://wicd.longren.org) feisty all
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty universe
pag@pag-laptop:~$ ^C
pag@pag-laptop:~$ gksudo gedit /etc/apt/sources.list
pag@pag-laptop:~$ gksudo gedit /etc/apt/sources.list
pag@pag-laptop:~$ clear

pag@pag-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse


---

### Post by 3Miro on 2011-03-30
Unfortunately I cannot see anything wrong with this. The error is about a .gpg file which is a "signature" key file. You can check the Authentication part of the software resources, but I other than that, I don't know what else can happen.

I don't have access to 10.04 right now, but I will try to get a source.list file for comparison.

---

### Post by Elfy on 2011-03-30
the tualatrix ppa source list is likely to be in 

/etc/apt/sources.list.d/

so looking at the sources.list file will be no help.

Not actually got access to a debian machine at all to be anymore help at the moment.

Edit - Have a look in there to see what ppa's you've got source lists for

```
ls /etc/apt/sources.list.d
```

---

### Post by matt_symes on 2011-03-30
Hi

There is a guy here

[http://ubuntuforums.org/showthread.php?t=1716523](http://ubuntuforums.org/showthread.php?t=1716523)

having the same problem. 

I will not be able to help till tomorrow so if you find a fix please help him. 

Cheers guys.

Kind regards

---

### Post by 3Miro on 2011-03-30
forestpiskie, shouldn't everything in source.list.d appear under software sources in Synaptic? If so, it should just be disabled from there.

---

### Post by Elfy on 2011-03-30
> **3Miro said:**
> forestpiskie, shouldn't everything in source.list.d appear under software sources in Synaptic? If so, it should just be disabled from there.

Yep - but the OP'll not be able to see it nor edit it from the /etc/apt/sources.list as they each have their own.

And a lot of these ppas all seem to have more or less the same name - or at least from memory they do - I always found it easier to go look at the file.

I agree that the easiest thing is to disable from software sources if the OP can find the right one to disable.

They could also always start again with a new one - [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by joelstitch on 2011-03-30
> **forestpiskie said:**
> the tualatrix ppa source list is likely to be in 

/etc/apt/sources.list.d/

so looking at the sources.list file will be no help.

Not actually got access to a debian machine at all to be anymore help at the moment.

Edit - Have a look in there to see what ppa's you've got source lists for

```
ls /etc/apt/sources.list.d
```

This is what Im getting: 

> lucid-partner.list       ubuntu-tweak-stable.list
lucid-partner.list.save  ubuntu-tweak-stable.list.save


---

### Post by 3Miro on 2011-03-30
> **joelstitch said:**
> This is what Im getting:

Go to System -> Admin -> Synaptic Package Manager and then select Settings -> Repositories. From the category "Other Software", you should disable "Ubuntu tweaks" or whatever the name is. This should be the easiest way to get things working.

---

### Post by joelstitch on 2011-03-30
> **3Miro said:**
> Go to System -> Admin -> Synaptic Package Manager and then select Settings -> Repositories. From the category "Other Software", you should disable "Ubuntu tweaks" or whatever the name is. This should be the easiest way to get things working.

Would that disable the Ubuntu Tweaks application?

---

### Post by joelstitch on 2011-03-30
> **3Miro said:**
> Go to System -> Admin -> Synaptic Package Manager and then select Settings -> Repositories. From the category "Other Software", you should disable "Ubuntu tweaks" or whatever the name is. This should be the easiest way to get things working.

I unchecked everything on **Other Software** (only 2 things) and now I get this:

> Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by 3Miro on 2011-03-31
> **joelstitch said:**
> Would that disable the Ubuntu Tweaks application?

It shouldn't disable anything.

Are you sure you have internet connection working on this computer. The link that you post does contain an URL address, can you access that (it should be a file with some hex symbols)

---

### Post by joelstitch on 2011-03-31
Of course I have internet.thats how Im answering your questions.

This is what the address have :

> -----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.6 (GNU/Linux)

iD8DBQBL2cDzQJdur0N9BbURAmk2AJ9ungOjKn0ektAH87KhRIHht+1cDQCfck7P
ZoIb2P0v2PEqa4Az8KnIIW4=
=b/mY
-----END PGP SIGNATURE-----

---

### Post by TheDexter1111 on 2011-03-31
> **joelstitch said:**
> Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...id/Release.gpg]("http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg") [SIZE=3][COLOR=Red]**[SIZE=2][COLOR=Black]Something wicked happened!![/COLOR][/SIZE]!**[/COLOR][/SIZE]

lolz

I may not be able to help, but i seem to be having troubles with the repos at the moment aswell... just simple packages missing like bmpanel2, obmenu, pypanel etc.. sudo apt-get install commands come back with something like 'no file found' are you having trouble installing basic packages through sudo aptitude?

---

### Post by joelstitch on 2011-03-31
I have no problems installing stuff packages with sudo aptitude

---

### Post by joelstitch on 2011-04-29
I'm still getting errors. Now I'm getting these:

> W: Failed to fetch [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.


---

