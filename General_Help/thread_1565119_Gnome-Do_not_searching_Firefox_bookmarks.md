---
title: "Gnome-Do not searching Firefox bookmarks"
date: 2010-08-31
forum: General Help
---

### Post by gldearman on 2010-08-31
Hi, everyone,

I just installed Gnome-Do for the first time on my Ubuntu 10.04 machine.  I have the Firefox plugin for Gnome-Do installed and enabled.  Supposedly, that means that Gnome-Do will be able to search my Firefox bookmarks.

But, it doesn't work.  No matter what bookmark I try to search for, it is not found.

When I launch Gnome-Do, from the terminal I get an error message.  It's quite lengthy, and I can't figure out how to redirect it to a text file to post the full text here.  But the gist of it was that "Firefox Places" encountered an error; object reference not set to instance of an object.

I've tried disabling and re-enabling the Firefox plugin for Gnome-Do, to see if that forces it to index bookmarks.  I've also tried forcing Firefox to export its bookmarks to an html file.  Neither approach helped.

I've searched, and found several references to this problem in these forums, but not had any resolution.  Can anyone help?

Thanks!

---

### Post by gldearman on 2010-09-01
Well, after searching around, I found [this]("https://bugs.launchpad.net/do/+bug/205824") on launchpad.  So, my problem appears to be a known bug in Gnome-Do, confirmed as of January.

If anyone wants to see the full error text I'm getting, it is in that bug report.

So, is *anyone* here able to get Gnome-Do to launch URLs?

Does anyone know a workaround?

This is kind of a dealbreaker for me.  If Do can't open websites, it's not that useful.  I can already launch applications pretty easily.

---

### Post by pros on 2011-01-15
[https://bugs.launchpad.net/do/+bug/205824](https://bugs.launchpad.net/do/+bug/205824)
This works...

[https://bugs.launchpad.net/do/+bug/205824/+attachment/1776862/+files/Firefox.dll]("https://bugs.launchpad.net/do/+bug/205824/+attachment/1776862/+files/Firefox.dll")

The proposed patch, solves this problem in Lucid and Maverick.
Just replace the file in /usr/lib/gnome-do/plugins.

---

### Post by pros on 2011-01-15
[https://bugs.launchpad.net/do/+bug/205824](https://bugs.launchpad.net/do/+bug/205824)
This works...

[https://bugs.launchpad.net/do/+bug/205824/+attachment/1776862/+files/Firefox.dll]("https://bugs.launchpad.net/do/+bug/205824/+attachment/1776862/+files/Firefox.dll")

The proposed patch, solves this problem in Lucid and Maverick.
Just replace the file in /usr/lib/gnome-do/plugins.

---

