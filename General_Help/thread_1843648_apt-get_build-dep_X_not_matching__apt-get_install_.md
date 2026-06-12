---
title: "apt-get build-dep X not matching  apt-get install -s X"
date: 2011-09-13
forum: General Help
---

### Post by scottstensland on 2011-09-13
sudo apt-get build-dep XXXX

says :

E: Unable to find a source package for XXXX

frustratingly, 

sudo apt-get install -s XXXX

says it wants to install many necessary packages
Is my local cache stale ?  If so how do I refresh so build-dep will work correctly ?
Essentially, I want to install necessary packages, without installing package X
I have seen this across several different packages, currently for package : phatch
Getting same symptom when using different mirrors
Ubuntu Oneiric beta 1 

sudo apt-get update

has no impact

apt-cache search X

does correctly find package X ---- How can I make build-dep see same package X ?

---

