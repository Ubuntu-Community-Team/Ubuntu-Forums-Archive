---
title: "Update Manager Lists Items that Never Get Updated 8.04 LTS"
date: 2011-02-19
forum: General Help
---

### Post by allan.w.macdonald on 2011-02-19
I am running 8.04 LTS on a Dell Inspiron 1525.

Update Manager lists a bunch of items that just stay there forever - they never update, they never go away and the check boxes cannot even be checked.

Alot of these are "language-pack-gnome-xxx" updates.

I also have one "skype" update that never goes away and can't be checked.

Something's wrong and I don't know how to fix it.

I want to eventually upgrade the entire OS but I am afraid to do so if my system has problems.  I want the update manager window to be completely empty.  I want these items to actually update or go away.

I don't have a degree in computer science so please be easy on me when it comes to terminal commands.

I tried searching for this problem and, although I'm sure the topic has come up before, I can't seem to find a set of search terms that puts the topic within the top 10 results.

Thanks for your help, in advance.

Cheers,

Allan

---

### Post by Old_Grey_Wolf on 2011-02-19
Enter these commands and see if it fixes the problem. If not, post back to the forum.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by allan.w.macdonald on 2011-02-25
Hi,

Thanks Mr. Old_Grey_Wolf.  Sorry for not responding to you sooner - I got busy with other stuff.

Unfortunately, those commands did not fix the problem.

If I knew where Update Manager kept its information, I could perhaps peruse the files, and try to see where the problem is, perhaps post some more info, or even maybe delete the offending entries (whatever that means).  I assume the data is stored in a plain text file somewhere.  Nevertheless, I have no idea where to look.

I can't seem to figure out what the difference is between the APT utility and Update Manager.  Is Update Manager just a front end for APT or is it a completely different program?

There is an apt command called "apt-get clean".  Would this be able to fix my problem or does apt keep its information in a different place from where Update Manager does?

What about commands such as "apt-get autoremove"  Would that actually do anything?

If I run the command "apt-cache show language-pack-gnome-kw", for example, which is one of those items in Update Manager that never goes away, I don't see anything useful.  What I do see is several entries for this package, each one a different version.  Why are there several entries?  Does Ubuntu really keep copies of each version of each package, every time it updates a package?  I am confused.

Also, the package showing in Update Manager is Version 1:8.04+20100117, which is the first version that appears in the list of these packages when I run apt-get show from the command line.  That's weird.  Is Update Manager somehow ignoring the info in the apt cache - for these particular packages?

---

### Post by allan.w.macdonald on 2011-02-26
I just found out that there's another forum called "Installation and Upgrades".  Perhaps I should try posting this question to that forum.

If anybody is watching this, and agrees with that (or not), please advise.

---

### Post by allan.w.macdonald on 2011-02-26
Another update:

I tried the commands:

```

sudo apt-get clean
sudo apt-get update

```

I didn't see anything useful there.  Just a list of "hits", whatever that means.

Then, when I ran:

```

sudo apt-get upgrade

```

I got the following output:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  language-pack-gnome-kw language-pack-gnome-kw-base language-pack-gnome-mai language-pack-gnome-mai-base
  language-pack-gnome-pap language-pack-gnome-pap-base language-pack-gnome-sa language-pack-gnome-sa-base skype
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

```

This produced a hint to the problem.  I don't understand though; what does "kept back" mean?  And, why would a package be "kept back"?  Is there something wrong somewhere?  How can I fix this?

Frankly, I don't care about the language packs - those are for languages that I doubt I will ever use.  I don't understand why my machine needs these anyway.  If I could just remove those, and if that made them go away from the list of "recommended updates" in Update Manager, without breaking anything else, then I'd be quite happy.

However, I do care about the skype upgrade - I use this program and would certainly like it to be upgraded to the latest release.

Also, if I eventually decide to upgrade the OS, I certainly don't want any weird issues hanging around that might get carried over to the new OS.

p.s.  Note to Moderator: Perhaps this thread should be "moved" to another forum, such as Installation and Upgrades.

---

### Post by JKyleOKC on 2011-02-26
> **allan.w.macdonald said:**
> Frankly, I don't care about the language packs - those are for fairly unusual languages.  I don't understand why my machine needs these anyway.  If I could just remove those, and if that made them go away from the list of "recommended updates" in Update Manager, without breaking anything else, then I'd be quite happy.There's a package called "localepurge" that will remove all of those unwanted localization files from your system. You can find it in Synaptic by typing "locale" into the search box at the top of the dialog; it was the topmost item when I just checked.

When you install it it will ask you to configure the language(s) you want to keep, and will then get rid of the files for all the others. Very impressive savings in disk space! However I don't know whether it will clean out the update list while it's at it...

The "held back" just means that those packages are NOT being upgraded when you apply updates. I see such lines only when I have unchecked the corresponding packages on the update list.

EDIT: Most all of these update packages are front ends for dpkg, which is the Debian Package Manager program. From the GUI I prefer to use Synaptic, and from the command line apt-get seems to be the most friendly. Most of the time, though, I use Synaptic because it can show me more information at once. For years I was strongly against the whole idea of the GUI, but finally reversed my feelings on the matter after discovering how much it could simplify things in many situations. These days I use both GUI and CLI, depending on which is the best tool for a specific task.

---

### Post by allan.w.macdonald on 2011-02-27
Hi Jim,

Thanks for your input.

I tried installing "localepurge", but ran into some scary problems so I abandoned that approach.

Instead, I merely removed the offending language packs individually using Synaptic.

Nevertheless, I still have the issue of not being able to upgrade a package that I do want to keep - namely, skype.  I understand, literally, what "kept back" means.  What I want to know is *why* it is being "kept back".

Taking your suggestion to try Synaptic to do the upgrade, I opened Synaptic and tried to mark skype for upgrade.  Here's what came out of Synaptic's unresolvable dependencies error box:

```

skype:
  Depends: libasound2 (>1.0.16) but 1.0.15-3ubuntu4 is to be installed
  Depends: libgcc1 (>=1:4.3) but 1:4.2.4-1ubuntu4 is to be installed
  Depends: libqt4-dbus (>=4.4.3) but 4.4.0-1ubuntu5~hardy1 is to be installed
  Depends: libqt4-network (>=4.4.3) but 4.4.0-1ubuntu5~hardy1 is to be installed
  Depends: libqtcore4 (>=4.4.3) but 4.4.0-1ubuntu5~hardy1 is to be installed
  Depends: libqtgui4 (>=4.4.3) but 4.4.0-1ubuntu5~hardy1 is to be installed
  Depends: libstdc++6 (>=4.3) but 4.2.4-1ubuntu4 is to be installed

```

Questions:

1. Why doesn't apt-get upgrade show me these errors?  Why does it just say "kept back"?  How can I get apt-get to give me more informative feedback?

2. Same question above might apply to Update Manager as well (the listed upgrade is just grayed out with no feedback and no means to select).

3. What does Synaptic mean by "to be installed"?  According to a search using Synaptic, these items *are* actually installed, not "to be" installed.

4. The dependencies seem to have later versions than the "latest version" of the packages that are installed on my system.  How can I fix this (or is it even possible)?

Thanks in advance.

Allan

---

### Post by JKyleOKC on 2011-02-27
The only one of your questions that I can even guess at an answer for is #4; the rest require more knowledge of the inner workings of the various package-management tools than I have.

I suspect that you're getting skype through a "ppa" in your sources.lst rather than direct from the official repositories (if not, then there appears to be a problem with its dependency list that needs a bug report, but I've not seen any other mention so don't think it's very likely). My own copy of Synaptic does not list skype at all, which tends to confirm this guess.

I think that the skype package in the ppa probably is NOT tied to any specific version of *buntu, and the newer versions of the dependencies most likely are those supplied with later versions of *buntu than 8.04. If this is the case, an upgrade to 10.04 LTS might solve the dependency problem automatically. However I can't recommend trying this on a system that's otherwise working properly, since I had several days of tweaking to do when I made such a move, just to regain my previous functionality. In particular I had to tweak the video settings quite a bit, and the "plymouth" addition to the newer version has taken me several months to learn how to live with it!

---

### Post by allan.w.macdonald on 2011-02-28
Thanks Jim!

I think your guess is probably correct and an OS upgrade might solve my problems.  I was planning on doing that at some point anyway.

Since the skype issue is the only one left for me to resolve, I guess I am happy for now and might as well go the route of upgrading the OS.

Thanks for all your help, Jim.  I guess this question is answered.

---

