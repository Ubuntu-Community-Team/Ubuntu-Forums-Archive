---
title: "Update Manager, Package manager won't work."
date: 2011-05-24
forum: General Help
---

### Post by tylortylor on 2011-05-24
Ubuntu 11.04

My Update manager encounters a problem when you try to open it. This pops up;

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

Now I have this annoying - sign by my clock.

I try to open package manager and this pops up:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Please help me out asap. Thank you.

---

### Post by linuxinstalledfromhdd on 2011-05-24
I would do a purge PPA on any new PPA's you have added to your system lately.  Try to outline any steps you have made to change your system prior to this issue occuring, and try backtrack a solution that way.

---

### Post by tylortylor on 2011-05-24
> **linuxinstalledfromhdd said:**
> I would do a purge PPA on any new PPA's you have added to your system lately.  Try to outline any steps you have made to change your system prior to this issue occuring, and try backtrack a solution that way. I have no Idea what I did. It was working fine one day, and then it stoped. A lot of things didn't work right after I upgraded to 11.04, when the update froze and I had to shut it down. Is there anyway I can down grade to 10.10?

---

### Post by tylortylor on 2011-05-24
New problem: When I try to get new software from the software system, If you click on a category or search, it never stops loading.

---

### Post by tylortylor on 2011-05-24
Any body? Please. I'm desperate.

---

### Post by plucky on 2011-05-24
> 'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n _Translation-en, E:The package lists or status file could not be parsed or opened.'


Have you tried searching for the error on the forum?

See [Here](http://ubuntuforums.org/showthread.php?t=1749469&highlight=E%3A+Encountered+section+Package%3A+header)

Good Luck

---

### Post by linuxinstalledfromhdd on 2011-05-24
Just downgrade for now. 11.04 is the latest version, and we are still trying to get the bugs out of it.  You can file a formal bug report. If you need help with something like that, let us know.

---

### Post by tylortylor on 2011-05-24
> **linuxinstalledfromhdd said:**
> Just downgrade for now. 11.04 is the latest version, and we are still trying to get the bugs out of it.  You can file a formal bug report. If you need help with something like that, let us know.
How do I downgrade?

---

### Post by linuxinstalledfromhdd on 2011-05-24
I would try a bootable stick of Ubuntu on a USB flash drive and test your hardware with it first to see if you like the performance. 

Download an iso of Ubuntu you want. 

From the desktop...

System >> Administration >> Startup Disc Creator

Format the USB drive.

and create a live USB Ubuntu stick with it.  You probably don't need it to be "persistent".

---

### Post by tylortylor on 2011-05-24
Will that delete all of my files and bookmarks?

---

### Post by linuxinstalledfromhdd on 2011-05-24
No, it's just to check your system to see if it performs differently.  Don't install it. Just boot from the live usb stick for now, and check it out.

---

### Post by wildmanne39 on 2011-05-25
> **tylortylor said:**
> Ubuntu 11.04

My Update manager encounters a problem when you try to open it. This pops up;

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

Now I have this annoying - sign by my clock.

I try to open package manager and this pops up:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Please help me out asap. Thank you.

Hi, alot of people have had that problem and some have fixed it by deleting the file that is giving them the error,that was after they ran all the commands to fix it and nothing worked. I am not saying to do it just giving you the information.

---

### Post by tylortylor on 2011-05-25
I went to bed early last night thinking I was going to fix it today, but when I turned it on, It was better.

---

### Post by wildmanne39 on 2011-05-25
> **tylortylor said:**
> I went to bed early last night thinking I was going to fix it today, but when I turned it on, It was better.

LoL that is good.

---

