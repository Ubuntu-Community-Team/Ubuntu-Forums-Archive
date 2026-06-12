---
title: "Removing *buntu-desktop packages"
date: 2010-01-14
forum: General Help
---

### Post by kernco on 2010-01-14
I wanted to figure out if this is a bug or by design.  If a user does the following:
[LIST=1]
[*]Install Ubuntu from CD
[*]Run "apt-get install kubuntu-desktop"
[*]Run "apt-get remove kubuntu-desktop"
[*]Run "apt-get autoremove"
[/LIST]
The system will be restored to a pure Ubuntu installation.  The same thing works if we swap Ubuntu and Kubuntu in the above steps to install ubuntu-desktop on a Kubuntu installation, then return to a pure Kubuntu system.  However, the following does not work:
[LIST=1]
[*]Install Ubuntu from CD
[*]Run "apt-get install kubuntu-desktop"
[*]Run "apt-get remove ubuntu-desktop"
[*]Run "apt-get autoremove"
[/LIST]
One would expect that to result in a pure Kubuntu system, but removing the ubuntu-desktop package in that case only removes that single package, it doesn't cascade down through the dependency tree.

In other words, if one installs *buntu from a CD, then removes the *buntu-desktop package, it has virtually no effect on the system.  However, if one installs the *buntu-desktop package through apt-get then later removes it, it properly cleans up all the packages that were installed when the *buntu-desktop package was installed.

I've seen people saying here in the forums not to worry about choosing Gnome or KDE because they can both be run on the same system easily, which is very true.  However I've often had problems with running both at the same time, and it seems to be getting worse with each new release.  For example, since Ubuntu adopted pulseaudio, I've found it impossible to get sound working in both KDE and Gnome at the same time.  From what I'm describing here, it seems to be very difficult to move from a pure Ubuntu installation to a pure Kubuntu one without reinstalling from CD.  You can easily go to a dual-environment system then back to what you originally had, but making the full transition is hard.

---

### Post by bodhi.zazen on 2010-01-14
This is because the *-desktop is a "meta package" and lists all the others as dependencies. 

As you can see, they do not remove so easily.

See : [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by kernco on 2010-01-14
They **do** remove easily if they were installed via apt-get, though.  That's the point of my post.  It's only when they were installed at the start (by Ubiquity?) that they are hard to remove.

---

