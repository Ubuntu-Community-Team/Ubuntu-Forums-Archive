---
title: "Is Ubuntu 10.10 a stable version?"
date: 2010-11-10
forum: General Help
---

### Post by Taak on 2010-11-10
Ok, this could look quite no-sense but...
[LIST=1]
[*]Why does update manager doesn't tell me that ubuntu 10.10 is out? I'm running 10.04.1 LTS. I have to do alt-F2 "update-manager -d" in order to see the 10.10 message even if ubuntu is config to notice me of normal releases.
[*]And then just before the update begins, the official readme says that 10.10 is (at the moment) a RELEASE CANDIDATE version. Just an old not-updated readme?
[*]Why does Ubuntu official home page annunces 10.10 as a stable version?
[/LIST]

---

### Post by ki4jgt on 2010-11-10
Have you updated your repositories?

---

### Post by TeoBigusGeekus on 2010-11-10
In Update Manager you can tick the option for notifications of new releases.
Maverick IS a stable release, I don't know why you're getting this message.
Word of warning: if lucid works for you, don't change anything.

---

### Post by Taak on 2010-11-10
> **ki4jgt said:**
> Have you updated your repositories?
 
I didn't do anything. With the previous updates all worked fine. What should I do?
 
> **TeoBigusGeekus said:**
> In Update Manager you can tick the option for notifications of new releases.
 
Yes, of course, it's correctly set.
 
> **TeoBigusGeekus said:**
> Maverick IS a stable release, I don't know why you're getting this message.
 
The official readme that show just before the update says it's a Release Candidate.
 
> **TeoBigusGeekus said:**
> Word of warning: if lucid works for you, don't change anything.
 
Why? No improvements in 10.10?

---

### Post by TeoBigusGeekus on 2010-11-10
> **Taak said:**
> Why? No improvements in 10.10?
Minor, but they come hand to hand with a lot of bugs as well.

---

### Post by ki4jgt on 2010-11-10
10.10 is mostly more apealing, than anything. It fixes sound issues and some other stuff for some and breaks things for others, but all in all. It only offer a few more features than 10.04 plus some security related issues

As for updating your repos. I assumed you may have done a fresh install. If not then it may be something else. Try an update from the terminal do a sudo apt-get update type in your password and then after it updates try alt-f2 and update-manager -d again.

---

### Post by Taak on 2010-11-10
Typing alt-f2 and then "update-manager -d" it works. 
 
However I don't understand why ubuntu doesn't tell me that there's a new version automatically.
 
I have just installed a new ubuntu 10.04.1 LTS on another machine, and same problem: no default 10.10 release prompt. 
 
Update manager is set to tell me about every release.

---

### Post by ki4jgt on 2010-11-10
Basically apt-get and synaptic and Ubuntu software manager are just programs which allow you to install other programs. To have a current list of these programs, it must get a new directory of these programs every few days. This catalog of software is called repositories there is one software repository for every program.

In laymans terms: Ubuntu must connect to Ubuntu.com every now and then and ask if these repositories have new software in them. If you have one of the programs installed and there are updates, it notifies you that there are newer versions, If you want to install a program from Ubuntu Software Center, these repositories tell Ubuntu where to download the files from, but if it doesn't connect to Ubuntu.com then it has no way of knowing what has been updated. So if you install a fresh install, of 10.04, then when the 10.04 cd was made. That's the repositories which are on your hard drive. Your computer automatically updates your repositories at certain time intervals. Which ever you choose in the software sources on the updates tab.

Basically Update-manager can not tell you that there are updates, b/c it hasn't updated the repositories yet, So it doesn't know.

---

### Post by foureyesboy on 2010-11-10
10.10 is released on Oct 10, 2010.  It's not release candidate nor beta.

Ubuntu releases very half year, and its version takes the form of "yy.mm".  Knowing this will understand that 10.10 is not an update or subversion release of 10.04.

And every two year, a Long Term Support (LTS) is released and so happened 10.04 is the LTS.  It'll be maintained and supported for a longer period of time (at least 2 years until the next LTS is released, I've forgotten for exact).

So you may stay in 10.04 as long as you like unless you choose to upgrade it to 10.10 by invoking "update-manager -d" as you already know.

---

### Post by Taak on 2010-11-10
Ok very clear, thank you.
 
So there's a readme mistake because it says "Release candidate"

---

### Post by coffeecat on 2010-11-10
> **Taak said:**
> So there's a readme mistake because it says "Release candidate"

I don't think so. I'm in my Lucid installation. I went into Software Sources and changed the release upgrade option from LTS to Normal Releases. I then opened Update Manager and was told, "New Ubuntu release '10.10' is available". I clicked on the 'Upgrade' button and got a Cancel/Upgrade window with this message:

> = Welcome to Ubuntu 10.10 'Maverick Meerkat' =

The Ubuntu team is proud to announce Ubuntu 10.10 'Maverick Meerkat'.

To see what's new in this release, visit:
  [http://www.ubuntu.com/desktop/features](http://www.ubuntu.com/desktop/features)

Ubuntu is a Linux distribution for your desktop or server, with a fast
and easy install, regular releases, a tight selection of excellent
applications installed by default, and almost any other software you
can imagine available through the network. 

We hope you enjoy Ubuntu.

== Feedback and Helping ==

If you would like to help shape Ubuntu, take a look at the list of 
ways you can participate at

  [http://www.ubuntu.com/community/participate/](http://www.ubuntu.com/community/participate/)

Your comments, bug reports, patches and suggestions will help ensure
that our next release is the best release of Ubuntu ever.  If you feel
that you have found a bug please read:

  [http://help.ubuntu.com/community/ReportingBugs](http://help.ubuntu.com/community/ReportingBugs)

Then report bugs using apport in Ubuntu.  For example:

  ubuntu-bug linux

will open a bug report in Launchpad regarding the linux package.

If you have a question, or if you think you may have found a bug but 
aren't sure, first try asking on the #ubuntu or #ubuntu-bugs IRC 
channels on Freenode, on the Ubuntu Users mailing list, or on the 
Ubuntu forums:

  [http://help.ubuntu.com/community/InternetRelayChat](http://help.ubuntu.com/community/InternetRelayChat)
  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-users](http://lists.ubuntu.com/mailman/listinfo/ubuntu-users)
  [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/)


== More Information ==

You can find out more about Ubuntu on our website, IRC channel and wiki.
If you're new to Ubuntu, please visit:

  [http://www.ubuntu.com/](http://www.ubuntu.com/)


To sign up for future Ubuntu announcements, please subscribe to Ubuntu's 
very low volume announcement list at:

  [http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce)Nothing about release candidate that I can see. Have you done a 'check' in update manager, 'reload' in Synaptic or 'sudo apt-get update'?

---

