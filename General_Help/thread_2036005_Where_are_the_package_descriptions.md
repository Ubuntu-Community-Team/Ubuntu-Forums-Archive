---
title: "Where are the package descriptions?"
date: 2012-07-31
forum: General Help
---

### Post by Skaperen on 2012-07-31
I visit [[FONT=Courier New][COLOR=Blue]http://packages.ubuntu.com/[/COLOR][/FONT]]("http://packages.ubuntu.com/") and select **hardy (8.04LTS)** and look up some packages.  When I get to the page for the selected package, I see a description.  For example [[FONT=Courier New][COLOR=Blue]http://packages.ubuntu.com/hardy/otherosfs/hercules[/COLOR][/FONT]]("http://packages.ubuntu.com/hardy/otherosfs/hercules") has a good description suitable to deciding if the package is what I really want.  However when I select **precise (12.04)** and go to the same package at [[FONT=Courier New][COLOR=Blue]http://packages.ubuntu.com/precise/otherosfs/hercules[/COLOR][/FONT]]("http://packages.ubuntu.com/precise/otherosfs/hercules")_ there is no description_.  This seems to be the case for other packages for precise, too.  **Where did the descriptions go?**

---

### Post by black veils on 2012-08-02
you could try [here]("https://apps.ubuntu.com/cat/") instead, or use synaptic

---

### Post by Cheesehead on 2012-08-02
The descriptions of every package in the repos is already cached on your system. Use Software Center, Synaptic or the "apt-cache search" or "apt-cache show" commands to search/display them.

---

### Post by Skaperen on 2012-08-05
> **black veils said:**
> you could try [here]("https://apps.ubuntu.com/cat/") instead, or use synaptic
This works!

---

### Post by Skaperen on 2012-08-05
> **Cheesehead said:**
> The descriptions of every package in the repos is already cached on your system. Use Software Center, Synaptic or the "apt-cache search" or "apt-cache show" commands to search/display them.
True, but there are issues.  It only shows the installed version of Ubuntu.  Some packages may be new in later versions.  And the web site provides an easier means to find packages by class of purpose (and it was sufficient for the purpose when it did provide descriptions).  The command line just doesn't have that convenience.

---

