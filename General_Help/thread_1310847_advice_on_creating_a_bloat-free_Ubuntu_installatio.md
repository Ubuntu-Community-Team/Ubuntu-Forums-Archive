---
title: "advice on creating a bloat-free Ubuntu installation"
date: 2009-11-02
forum: General Help
---

### Post by F for Fragging on 2009-11-02
Recently after upgrading to Karmic I started thinking about ways to remove Ubuntu’s bloat. I remember the years old thread _[HowTo: Speed up ubuntu boot process]("http://ubuntuforums.org/showthread.php?t=89491")_ which advised on disabling unnecessary services. But that thread hasn’t been updated to Karmic, where applying the advice from that thread is problematic because of the transition to upstart in Karmic, as I read in the thread _[ubuntu 9.10 services-admin application is missing]("http://ubuntuforums.org/showthread.php?t=1294610")_. I’m not sure if any noticeable performance improvements can be attained by disabling services, but possibly anyone could please write a similar new thread describing which services could be disabled in Karmic?

What would also be useful would be a new thread with advice specifically for Karmic covering which unnecessary packages could be removed. The most recent thread which did that is _[Remove Unnecessary Packages and Other Random Tidbits]("http://ubuntuforums.org/showthread.php?t=820804")_, but it is more than a year old. Also it would be better if it could give advice per use case, e.g. remove these if you don’t use non-Latin fonts, these if you don’t need accessibility tools, and so on.

Though I’m not sure if the difficulty would be worth the savings in disk space (because Ubuntu doesn’t consume much space by default anyway) I’m considering to to use the alternate CD (not the _[minimal CD]("http://ubuntuforums.org/showthread.php?t=1155961")_ because that downloads everything from the Internet) to install Ubuntu and decide for myself what packages are going to be installed. That way I can start with only the bare essentials to give me GNOME desktop. Would it be a good idea to follow these instructions for _[installation on low memory systems]("http://https://help.ubuntu.com/community/Installation/LowMemorySystems")_ then to install a command line system first? I assume that after having done that an apt-get command to install xserver-xorg, gdm, nautilus would pull in all the basics along with the necessary dependencies. But that page does not describe how to make it so that X.org and GDM load automatically after booting, like the desktop CD’s installer would do by default? And is there a package list somewhere so I could see which packages the desktop CD installs, so I’d know what to install if I’d want to replicate a desktop CD install minus the bloat?

---

