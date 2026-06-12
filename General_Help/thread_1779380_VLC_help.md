---
title: "VLC help?"
date: 2011-06-10
forum: General Help
---

### Post by Jlbbly on 2011-06-10
hi, i'm new to the forums, but i didn't see any help on this subject, dealing with VLC, i'm completely green to Ubuntu and any help would be great, thanks.

[IMG]http://i51.tinypic.com/x10pcg.jpg[/IMG]

---

### Post by oldos2er on 2011-06-10
Have you run **sudo apt-get update** ?

---

### Post by Jlbbly on 2011-06-10
i did, and i get this every time...


W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Edit: i also can't uninstall or install anything via the Software center, if i click remove, it dose nothing, i don't even get a prompt for my pass.

---

### Post by Jlbbly on 2011-06-10
Bump

---

### Post by oldos2er on 2011-06-10
You should be able to install the key with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
```

---

### Post by john77eipe on 2011-06-10
Have a look at
[http://ubuntuforums.org/showthread.php?t=1236282](http://ubuntuforums.org/showthread.php?t=1236282)

might help.

---

### Post by Jlbbly on 2011-06-10
> **oldos2er said:**
> You should be able to install the key with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
``` i did this i guess it worked


> **oldos2er said:**
> Have you run **sudo apt-get update** ?

when i did this there was no problem with the key, but still getting the same errors with VLC and the Software Center...does anything think updating to 11.04 will work, i'd rather not wait 10 hours to update though. thanks =)

---

### Post by Jlbbly on 2011-06-10
Bump, no one? :sadface:

---

### Post by oldos2er on 2011-06-10
Be careful with bumping your post more than once in 24 hrs.

Do you have all repositories enabled?

---

### Post by DirtyPC on 2011-06-10
Try installing VLC to the latest from here: [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by StrayEddy on 2011-06-10
Post the errors you get, so we can analyse them.

---

### Post by sikander3786 on 2011-06-10
I guess you have tinkered a bit with the repository setup. We need to see the complete outputs of these commands first:

```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
```

And also these:

```
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
```

The last 2 commands are just to make sure that there are no broken/un-configured packages on your system.

While posting, click the # icon in post menu and paste your text in between the generated [code] tags to format your outputs like the one's in this post thus making them easy to read.

---

### Post by Jlbbly on 2011-06-10
> **oldos2er said:**
> Be careful with bumping your post more than once in 24 hrs.

Do you have all repositories enabled?

Sorry about this i'm new to the fourms.

> **sikander3786 said:**
> I guess you have tinkered a bit with the repository setup. We need to see the complete outputs of these commands first:

```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
```

And also these:

```
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
```

The last 2 commands are just to make sure that there are no broken/un-configured packages on your system.

While posting, click the # icon in post menu and paste your text in between the generated ```
 tags to format your outputs like the one's in this post thus making them easy to read.

when i do sudo apt-get update it updates, but after that no idea.
when i use this sudo dpkg --configure -a i got nothing.
when i tried sudo apt-get install -f it did nothing, except tell me that nothing is removed, upgraded, newly installed, and not upgraded.

 i did this command and got this cat /etc/apt/sources.list
[CODE]# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

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
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

```

when i used this one ls -l /etc/apt/sources.list.d

```
total 36
-rw-r--r-- 1 root root 140 2011-06-10 12:29 ferramroberto-vlc-maverick.list
-rw-r--r-- 1 root root 140 2011-06-10 12:05 ferramroberto-vlc-maverick.list.distUpgrade
-rw-r--r-- 1 root root 140 2011-06-10 04:02 ferramroberto-vlc-maverick.list.save
-rw-r--r-- 1 root root 287 2011-06-10 12:29 medibuntu.list
-rw-r--r-- 1 root root 287 2011-06-10 12:05 medibuntu.list.distUpgrade
-rw-r--r-- 1 root root 287 2011-06-10 04:02 medibuntu.list.save
-rw-r--r-- 1 root root 158 2011-06-10 12:29 mozillateam-firefox-stable-maverick.list
-rw-r--r-- 1 root root 158 2011-06-10 12:05 mozillateam-firefox-stable-maverick.list.distUpgrade
-rw-r--r-- 1 root root 158 2011-06-10 04:02 mozillateam-firefox-stable-maverick.list.save

```

---

### Post by sikander3786 on 2011-06-11
Go to Software Center > Edit > Software Sources > Other Software tab and disable all of 'ferramroberto-vlc' PPAs for the time being. Close this window and now run these commands and post the outputs as well.

```
sudo apt-get update && sudo apt-get install vlc
```

---

### Post by Jlbbly on 2011-06-11
> **sikander3786 said:**
> Go to Software Center > Edit > Software Sources > Other Software tab and disable all of 'ferramroberto-vlc' PPAs for the time being. Close this window and now run these commands and post the outputs as well.

```
sudo apt-get update && sudo apt-get install vlc
```

thank you it worked :D

But I'm still having an issue removing and installing stuff Via the Software Center, thank you though.

---

### Post by sikander3786 on 2011-06-11
You are Welcome :)

Regarding Software Center, it is the same error message or something else?

Try starting Software Center from the Terminal and post any errors.

```
software-center
```

---

### Post by Jlbbly on 2011-06-11
i did excatly what you said, but i got this when i tried to remove something

```
2011-06-11 05:57:22,221 - softwarecenter.backend - WARNING - _on_trans_error: org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.33'}): org.debian.apt.install-or-remove-packages

```

and when i tried to install something

```
2011-06-11 06:01:52,474 - softwarecenter.backend - WARNING - _on_trans_error: org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.33'}): org.debian.apt.install-or-remove-packages

```

---

### Post by Jlbbly on 2011-06-11
sorry for being a nuisance  , but any help would be awesome :P

---

### Post by sikander3786 on 2011-06-12
[QUOTE=Jlbbly]1. have you ever had an issue installing and removing stuff through via the Software center?

2. have you ever had an issue, that when you logged in it didn't ask your root password, and when i try to change the Login prompt and click unlock, it dose nothing...[/QUOTE]

For Software Center, those errors are not common with everyone. Seems like you are effected by this bug.

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/785117](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/785117)

[http://ubuntuforums.org/showthread.php?t=1665901](http://ubuntuforums.org/showthread.php?t=1665901)

Apparently, I couldn't find an answer to that problem. Might be, some other user can.

And for the other one, do you mean you've set it to auto-login and can't seem to be able to change the Login Screen properties?

---

### Post by Jlbbly on 2011-06-13
all i did was uninstall Ubuntu, and reinstalled it, and it seemed to fix it, thank you =D, but I did have an issue upgrading to 11.04 I got an "out of range error" it has something do do with my graphics card, but thanks =D

---

### Post by sikander3786 on 2011-06-14
You are Welcome :)

For the graphics problem, take a look here.

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

