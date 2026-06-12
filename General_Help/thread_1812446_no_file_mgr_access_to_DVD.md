---
title: "no file mgr access to DVD"
date: 2011-07-26
forum: General Help
---

### Post by DrScum on 2011-07-26
When I insert a DVD and try to access with file manager 
I get the following:

The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "VIDEO_TS"

Is there a way to fix this?

What I did so far is the following:
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get -q update
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring
sudo apt-get -q update
sudo aptitude install libdvdcss2

This sequence of commands was recommended to me from DawieS thread# 1812259
in relation to another DVD-drive issue I had.

---

### Post by DrScum on 2011-07-26
I transferred this post to the Multimedia & Video forum.

Don't know how to delete it here though!

---

