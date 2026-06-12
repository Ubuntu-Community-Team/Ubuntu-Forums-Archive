---
title: "Why does an app that is locked get updated? Feature or Bug?"
date: 2012-09-07
forum: General Help
---

### Post by grahams on 2012-09-07
As thunderbird 15 breaks several plugins I locked it at v14 in synaptic. However this was ignored and thunderbird was updated to 15 and the plugins broke :-( 

I thought I must have forgotten to lock it, but Synaptic shows it is locked, but on v15. Surely this is a bug

---

### Post by grahams on 2012-09-08
I successfully locked tb via the command line

# echo "thunderbird hold" |dpkg --set-selections

This should be the same as Synaptic's Package->Lock Version, looks like a bug in Synaptic

---

### Post by sgage on 2012-09-08
> **grahams said:**
> As thunderbird 15 breaks several plugins I locked it at v14 in synaptic. However this was ignored and thunderbird was updated to 15 and the plugins broke :-( 

I thought I must have forgotten to lock it, but Synaptic shows it is locked, but on v15. Surely this is a bug

A lock that works for Synaptic will not work for apt-get, and for all I know (I don't use it) the Update Manager. Screwy, but there it is.

---

### Post by dcstar on 2012-09-09
> **grahams said:**
> As thunderbird 15 breaks several plugins I locked it at v14 in synaptic. However this was ignored and thunderbird was updated to 15 and the plugins broke :-( 

I thought I must have forgotten to lock it, but Synaptic shows it is locked, but on v15. Surely this is a bug

Add your name to this ancient & still unfixed bug:

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/42178](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/42178)

---

