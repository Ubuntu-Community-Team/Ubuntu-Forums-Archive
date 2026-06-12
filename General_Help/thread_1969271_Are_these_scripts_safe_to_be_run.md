---
title: "Are these scripts safe to be run?"
date: 2012-04-29
forum: General Help
---

### Post by brunces on 2012-04-29
Hello, guys.

I have created two scripts as follow:

Script name: UPDATESYS
```
#!/bin/sh
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Script name: CLEANSYS
```
#!/bin/sh
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
```

Whenever I need, I run the UPDATESYS script; and from time to time I run the CLEANSYS script. I also installed GTKORPHAN and always use it after running the CLEANSYS script.

What I want to know is... are they safe to be run? I mean, is there any command I shouldn't use frequently or shouldn't use at all?

For example, I've been told not to use "dist-upgrade" very often. Really? Why not?

Thanks for your time, guys. :)

--- EDITED ---

I forgot to mention... I use Ubuntu 12.04 LTS (Final Release) with Gnome Shell 3.4.1. :)

brunces

---

### Post by Finalfantasykid on 2012-04-29
From experience I only have had to use dist-upgrade to fix dependency issues and stuff like that.  If that is what you are using it for, then that is fine.  If all you mean to do is apply updates like you would in the update-manager, then just apt-get update then apt-get upgrade should have to be done.

The second one IMO is perfectly fine to use as often as you want.

---

### Post by thnewguy on 2012-04-29
No, and they probably won't work as they are presented.

The reason you've been warned against scripting dist-upgrade is it attempts to do a complete upgrade to the latest version of Ubuntu. It's the sort of thing you should do after performing a backup and then watch to make sure it goes as planned.

Things like "clean" are pretty safe, but "autoremove", maybe not. Do you really want your system removing packages without your expressed confirmation? What if your package database gets corrupted and it un-installs half your system?

Just doing a normal update && upgrade is probably fine. Just remember to include the "-y" flag on your command line, otherwise it will prompt you for confirmation before the upgrade happens.

---

### Post by brunces on 2012-04-29
Finalfantasykid, thanks for answer. :)

> **thnewguy said:**
> Things like "clean" are pretty safe, but "autoremove", maybe not. Do you really want your system removing packages without your expressed confirmation? What if your package database gets corrupted and it un-installs half your system

thnewguy, thanks for your answer. According to what you mentioned, now I have another question... If my package database gets corrupted, how would I know and what should I do to fix it?

I'm new to Linux, so it's very good to get some useful tips from your knowledge and experience, guys. By the way, I'm taking dist-upgrade out of the script. Thanks. :)

brunces

---

### Post by CharlesA on 2012-04-29
> **thnewguy said:**
> No, and they probably won't work as they are presented.

The reason you've been warned against scripting dist-upgrade is it attempts to do a complete upgrade to the latest version of Ubuntu. It's the sort of thing you should do after performing a backup and then watch to make sure it goes as planned.

dist-upgrade doesn't upgrade you to the latest version of ubuntu. It allows apt-get to install new packages instead of only upgrading current packages (which is what a normal upgrade does).

Just stuck with doing apt-get upgrade unless there are packages being held back.

---

### Post by lisati on 2012-04-29
> **thnewguy said:**
> 
The reason you've been warned against scripting dist-upgrade is it attempts to do a complete upgrade to the latest version of Ubuntu.
Not exactly, at least not on any of my machines. It doesn't, for example, upgrade from 11.10 to 12.04

This is discussed here: [http://www.linuxquestions.org/questions/fedora-35/apt-get-question-dist-upgrade-vs-upgrade-219920/](http://www.linuxquestions.org/questions/fedora-35/apt-get-question-dist-upgrade-vs-upgrade-219920/)

---

### Post by brunces on 2012-04-29
> **CharlesA said:**
> Just stuck with doing apt-get upgrade unless there are packages being held back.

CharlesA, thanks for your answer. But how would I know there are packages being held back? In this case, isn't it better to keep dist-upgrade in the script so I can make sure every time there are packages being held back, they will be installed? Is this a valid thought?

Using dist-upgrade is not harmful, is it? If so, I understand the point in not using it. But if not, what's the problem? Or am I missing something? (As I said before, I'm new to Linux, so maybe I'm missing something. Something I don't know yet.) :)

Thanks.

brunces

---

### Post by CharlesA on 2012-04-30
apt-get will tell you if a package is being held back before before prompting if you want to continue or not:

```
ubuntu@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic[/B]
The following packages will be upgraded:
  apport apport-gtk firefox firefox-globalmenu firefox-gnome-support
  firefox-locale-en firefox-locale-es firefox-locale-pt firefox-locale-zh-hans
  linux-libc-dev python-apport python-problem-report
12 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 21.6 MB of archives.
After this operation, 616 kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

If something is held back, you can use dist-upgrade to install it.

---

### Post by brunces on 2012-04-30
> **CharlesA said:**
> apt-get will tell you if a package is being held back before before prompting if you want to continue or not.

Huuuuuum. Cooool! I had never paid attention to that before. Good to know. Thanks, CharlesA. :)

By the way, thnewguy, my doubt still stands... If my package database gets corrupted, how would I know and what should I do to fix it?

brunces

---

### Post by brunces on 2012-05-01
Up! :)

By the way, nobody commented on the GTKORPHAN. Is it safe to use? Thanks.

brunces

---

### Post by CharlesA on 2012-05-01
> **brunces said:**
> Up! :)

By the way, nobody commented on the GTKORPHAN. Is it safe to use? Thanks.

brunces
Never used it.

---

