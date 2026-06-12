---
title: "A Problem Occurred When Checking For Updates"
date: 2011-06-19
forum: General Help
---

### Post by OldBoy44 on 2011-06-19
Hi all,

My screen has a red circle with a white line through it on the top right hand corner with the above error message. I had attempted to download VirtualBox twice after thinking the original download was faulty.
The OS is 11.04 Classic (no effects)

After a search I thought the following command might help -
```

sudo apt-get update && sudo apt-get upgrade

```This returned the following -
E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read

Is this helpful in knowing how I can fix the problem?
Any suggestions would be very helpful if they were in the simplest language - I am really very inexperienced in the technical area of Ubuntu.

I hope some kind user may help.
Thank you.

---

### Post by Old_Grey_Wolf on 2011-06-19
Enter this command in a terminal```
cat /etc/apt/sources.list
```
then paste the output between the CODE tags.

---

### Post by OldBoy44 on 2011-06-19
Thanks Old_Gray_Wolf
Here is result -

```

#deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
deb http://download.virtualbox.org/virtualbox/debian  contrib


```

---

### Post by Old_Grey_Wolf on 2011-06-19
The line with ```
deb http://download.virtualbox.org/virtualbox/debian  contrib
``` should be ```
deb http://download.virtualbox.org/virtualbox/debian natty contrib
```

Use gksudo gedit /etc/apt/sources.list to edit that line.

---

### Post by OldBoy44 on 2011-06-19
Thanks Old_Gray_Wolf

I have an amended file in the text editor but I am at a loss to know what to do with it.

- :(

Thanks , I will try to do that!

---

### Post by Old_Grey_Wolf on 2011-06-19
> **aussiebean said:**
> Thanks Old_Gray_Wolf

I have an amended file in the text editor but I am at a loss to know what to do with it.

- :(

Use ```
gksudo gedit /etc/apt/sources.list
``` to edit that line then save it.

---

### Post by Old_Grey_Wolf on 2011-06-19
And, after you save it run ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by OldBoy44 on 2011-06-19
Error message returned -

gedit:2096 Gtk WARNING **:Attempting to set the permissions of '/root/local/share/recently-used.xbel', but failed : No such file or directory

* Ignored error message and ran command as suggested - Looks like that has corrected the problem


Thanks very much Old_Gray_Wolf for your patience.

Cheers,

---

### Post by Old_Grey_Wolf on 2011-06-19
> **aussiebean said:**
> Error message returned -

gedit:2096 Gtk WARNING **:Attempting to set the permissions of '/root/local/share/recently-used.xbel', but failed : No such file or directory

* Ignored error message and ran command as suggested - Looks like that has corrected the problem


Thanks very much Old_Gray_Wolf for your patience.

Cheers,

The error message is a little annoyance that people have seen in Natty. Apparently the directory /root/.local/share doesn't exist. The error can be ignored.

---

