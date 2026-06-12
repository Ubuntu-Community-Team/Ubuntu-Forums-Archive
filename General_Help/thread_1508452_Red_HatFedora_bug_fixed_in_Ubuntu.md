---
title: "Red Hat/Fedora bug fixed in Ubuntu?"
date: 2010-06-13
forum: General Help
---

### Post by Frogbarf on 2010-06-13
I discovered a bug in Hardy (8.04 LTS) a month or so ago. It appears to be known to the Red Hat/Fedora people and there's a fix for it. I'm wondering 
[LIST=1]
[*]if it's been fixed in later versions of Ubuntu
[*]if so, is it possible to retrofit the corrected version of Pango into 8.04
[*]if so, how (in words of one syllable)
[/LIST]

Google searches showed nothing.

[https://bugzilla.redhat.com/show_bug.cgi?id=450699]("https://bugzilla.redhat.com/show_bug.cgi?id=450699")

[https://bugzilla.gnome.org/show_bug.cgi?id=481203]("https://bugzilla.gnome.org/show_bug.cgi?id=481203")

---

### Post by dcstar on 2010-06-13
> **Frogbarf said:**
> I discovered a bug in Hardy (8.04 LTS) a month or so ago. It appears to be known to the Red Hat/Fedora people and there's a fix for it. I'm wondering 
[LIST=1]
[*]if it's been fixed in later versions of Ubuntu
[*]if so, is it possible to retrofit the corrected version of Pango into 8.04
[*]if so, how (in words of one syllable)
[/LIST]

Google searches showed nothing.

[https://bugzilla.redhat.com/show_bug.cgi?id=450699]("https://bugzilla.redhat.com/show_bug.cgi?id=450699")

[https://bugzilla.gnome.org/show_bug.cgi?id=481203]("https://bugzilla.gnome.org/show_bug.cgi?id=481203")

[LIST=1]
[*]Check the version of the package to see if the updated version is installed,
[*]If not then report the bug and refer to the other package bugs.
[/LIST]

---

### Post by Frogbarf on 2010-06-13
> **dcstar said:**
> [LIST=1]
[*]Check the version of the package to see if the updated version is installed,
[*]If not then report the bug and refer to the other package bugs.
[/LIST]

These are the versions for installed packages in 8.04 relating to Pango:

gstreamer 0.10-x ————— 0.10.18-3
libgtk2.0-cil ————— 1.0-0
libpango 1.0-0 ————— 1.20.5-0ubuntu1.1
linpango 1.0-common ————— 1.20.5-0ubuntu1.1

In Lucid 10.4, the respective vesions (according to the web) are:

0.10.28-1
2.12.9-4
1.28.0-0ubuntu2
[not found]

So there's been some updating, but whether this particular bug fix is involved I can't tell. Suggestions?

---

### Post by bodhi.zazen on 2010-06-13
Are you suffering from this bug ?

If so you should report it on Launchpad.

If you are and you are asking if you can install a fix from somewhere, you could either 

1. Download the source package. The Fedora bug report indicates you need 

> Font fixed in lohit-fonts-2.3.8. Please wait for an update in pango for final[FONT=monospace] [/FONT]resolve.

lohig-fonts-2.3.8

2. If you can not find the source code, you can try importing the .rpm using alien. Aline should be a last resort as it can cause breakage.

---

### Post by Frogbarf on 2010-06-13
> **bodhi.zazen said:**
> Are you suffering from this bug ?

If so you should report it on Launchpad.

If you are and you are asking if you can install a fix from somewhere, you could either 

1. Download the source package. The Fedora bug report indicates you need 



lohig-fonts-2.3.8

2. If you can not find the source code, you can try importing the .rpm using alien. Alien should be a last resort as it can cause breakage.

I wouldn't claim my mental state is one of suffering. In fact, the only visible sign of the bug is on the Wikipedia page "Tamil script", where one line in one table is mis-laid out. It's nearly a trivial bug as far as I am concerned, and given that I have a nice stable system, I'm naturally loath to fiddle with its innards too much!

As it happens, I have the Lohit Tamil font in v. 2.4.4, even later that the one recommended, so what I'm seeing is strictly due to a buglet in Pango.

I guess my real question is, if you become aware of a fix in another distro, how can you find out if that fix has been incorporated into Ubuntu? Presumably, the source code for Pango will have a comment noting the fix, but eeeeek! I'm not a C programmer!

---

### Post by bodhi.zazen on 2010-06-13
> **Frogbarf said:**
> I wouldn't claim my mental state is one of suffering. In fact, the only visible sign of the bug is on the Wikipedia page "Tamil script", where one line in one table is mis-laid out. It's nearly a trivial bug as far as I am concerned, and given that I have a nice stable system, I'm naturally loath to fiddle with its innards too much!

As it happens, I have the Lohit Tamil font in v. 2.4.4, even later that the one recommended, so what I'm seeing is strictly due to a buglet in Pango.

I guess my real question is, if you become aware of a fix in another distro, how can you find out if that fix has been incorporated into Ubuntu? Presumably, the source code for Pango will have a comment noting the fix, but eeeeek! I'm not a C programmer!

It obviously depends on the distro. Just because it is a bug in Fedora does not mean it is a problem in Ubuntu.

If it is a problem in Ubuntu, you would file a bug report on Launchpad.

Some packages are not written by Ubuntu developers, and in that case they would pass the bug report "upstream".

If a fix has been released upstream, the fix would be repackaged by the Ubuntu team.

If you are interested in packaging , see:

[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)

[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

Those pages may go over you head, but they should give you a general sense of how a package is taken from source code and packaged into a .deb

There are a number of steps in the process of going from say writing an application in C , patching the source code, and making a .deb

Again in some cases the pachages is written from start to finish by Ubuntu developers, in others, gnome for example, they take the source code and simply package it (although the processes may not be so simple, lol).

---

