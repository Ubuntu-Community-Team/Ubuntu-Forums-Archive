---
title: "How to delete Java cache? Sun Java."
date: 2012-02-16
forum: General Help
---

### Post by Uberjannie on 2012-02-16
Hi.

I am having problems with a website which seems to gather informasjon from Java Cache.
Problem is, I have no idea how to delete Java Cache on Ubuntu since the whole Oracle thing happened.
On Icedtea it is easy, but how do you delete this cache on Ubuntu 11 when it is Sun Java installed?

-Best regards
-Jannie

---

### Post by Gremlinzzz on 2012-02-16
in All Applications look for Java control panel
 click settings in temporary Internet files:popcorn:

---

### Post by Uberjannie on 2012-02-16
> **Gremlinzzz said:**
> in All Applications look for Java control panel
 click settings in temporary Internet files:popcorn:

Hi.

This is what I am talking about, the JCP is missing.
It doesnt seem to be installed anymore. I know it did back when it was in the repositories, but ever since it ended with 6u26, I cant seem to find it anymore.

---

### Post by Uberjannie on 2012-02-16
Is it enough to delete everything in /home/user/.java/deployment/ ?

---

### Post by Gremlinzzz on 2012-02-16
believe so:popcorn:
I'll do it and see if it empties the cache brb

it worked empty the cache

---

### Post by Uberjannie on 2012-02-16
> **Gremlinzzz said:**
> believe so:popcorn:
I'll do it and see if it empties the cache brb

it worked empty the cache

Awesome, thanks :)

---

### Post by Andrew_P on 2012-04-21
Since Sun Java was removed from the Canonical repositories in February 2012, there is no more Sun Java on Ubuntu installations.  I had it on Lucid Lynx 10.04.1 LTS, but due to a variety of reasons I decided to start over with a new hard drive, using 10.04.4 LTS in March.  My machine, therefore, doesn't have a trace of Sun Java on it anywhere.

I looked in my home directory and there is no .java folder there at all.  Instead, I find an ".icedteaplugin" folder that has a "cache" subfolder.  Presumably, wiping out everything in the "cache" folder should be the same as clearing the Java cache from the Java Control Panel.  Also, this installation of Ubuntu, having only OpenJDK, doesn't have a Java Control Panel as far as I can determine.

I wrote a little script, placed in ~/.gnome2/nautilus-scripts, that can be accessed from the Nautilus right-click menu to easily clear the files.  It could also be set up as a desktop launcher and accessed from the GNOME Applications menu:

#!/bin/bash
#
# Nautilus script -> clear Java cache on machines that are running OpenJDK
rm -fr ~/.icedteaplugin/cache/http/*
rm -fr ~/.icedteaplugin/cache/https/*

---

