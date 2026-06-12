---
title: "Firefox stuck at 3.6.6?"
date: 2010-11-14
forum: General Help
---

### Post by dalesd on 2010-11-14
I'm running Ubuntu 10.04 64-bit and my Firefox is stuck at version 3.6.6.  Mozilla shows the current version is 3.6.12.  What's going on?  3.6.6 is over four months old and has had several security flaws fixed.  Why am I so far behind?

---

### Post by [Shawn] on 2010-11-14
Hi there!
Give this a try..
Go to terminal **Applications>Accessories>Terminal** and type
```
sudo apt-get install firefox
``` and it should update then.
However, If it does not try reinstalling:
```
sudo apt-get remove firefox
``` and then once it's done uninstalling:
```
sudo apt-get install firefox
```

Hope this helps! :)

---

### Post by dalesd on 2010-11-14
I did a sudo apt-get update, then:
```
~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
Remove wants to also take out my Songbird.
```
~$ sudo apt-get remove firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firefox firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support
  firefox-branding firefox-gnome-support songbird
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
After this operation, 101MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```
  But I'm happy with Songbird and now that development has ceased, I don't want to mess with it.  I've had all sorts of problems with gstreamer every time I upgraded Songbird in the past.

None of this gets to the real issue: Why isn't Firefox updating?

---

### Post by yuki-nagato on 2010-11-14
> **dalesd said:**
> But I'm happy with Songbird and now that development has ceased, I don't want to mess with it.  I've had all sorts of problems with gstreamer every time I upgraded Songbird in the past.

None of this gets to the real issue: Why isn't Firefox updating?

this may be another option: add [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu)
to your list of repositories and reload the software repositories.  the ppa listed above is the mozilla daily repository which in addition to having the latest updates, also has firefox 4

---

### Post by pqwoerituytrueiwoq on 2010-11-14
> **yuki-nagato said:**
> this may be another option: add [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu)
to your list of repositories and reload the software repositories.  the ppa listed above is the mozilla daily repository which in addition to having the latest updates, also has firefox 4
the latest stable version 3.6.12 at the moment
[https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa")
edit:
if it is not there is is in [http://www.getdeb.net/updates/Ubuntu/10.04](http://www.getdeb.net/updates/Ubuntu/10.04)
edit2:
it is one one of these
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=175646&stc=1&d=1289783254[/IMG]

---

