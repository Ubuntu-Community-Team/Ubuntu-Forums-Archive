---
title: "Authorization Dialog for &quot;accessing this site&quot; pops up (no internet browser open!)"
date: 2012-05-09
forum: General Help
---

### Post by birdzhavefangs on 2012-05-09
An Authorization Dialog keeps popping up, regardless of whether or not my internet browser is open.  It claims the site is "cname prod site" and prompts for a username and password.  It pops up about every 15 minutes, but I keep closing it.  The most recent change I made before this started happening was to enable the weather display on the toolbar.

I have Ubuntu 10.04 LTS, Gnome version 2.30.2

[IMG]http://i123.photobucket.com/albums/o305/birdzhavefangs/authdialog.png[/IMG]

I guess my question is, why is it happening, and how can I get it to stop?

---

### Post by Ms. Daisy on 2012-05-10
Do you have any servers running on this computer?

What is your DNS set to?

---

### Post by birdzhavefangs on 2012-05-11
Yes, I have Apache installed, but it shouldn't be running (well, it was accidentally, but I turned it off and it's still happening).

And I'm using google's public DNS lookup (8.8.8.8 and 8.8.4.4).

---

### Post by birdzhavefangs on 2012-05-12
The problem continues to persist after multiple reboots, flushing my dns cache, and renewing my ip settings.  It's starting to drive me batty!

---

### Post by birdzhavefangs on 2012-05-19
In case anyone wondered, I traced the problem to Akregator (my RSS reader) and a specific feed.  Deleting the feed and re-adding it eliminated the problem.

---

