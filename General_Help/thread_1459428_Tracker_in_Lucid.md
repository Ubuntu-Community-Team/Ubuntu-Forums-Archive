---
title: "Tracker in Lucid"
date: 2010-04-21
forum: General Help
---

### Post by Sesivany on 2010-04-21
I have been using Ubuntu 10.04 Lucid Lynx for some time and I have some problems with Tracker (the searching tool):

1. It looks like it reindexes after every turning on a computer. It always starts at 0/55234 files.
2. It doesn't index e-mails in Evolution. I'm using IMAP, but all mail is marked for offline use. So it's on the harddisk. And it worked in older versions of Ubuntu.
3. GUI is totally different than the one which is shown on the website of Tracker ([http://projects.gnome.org/tracker/documentation.html](http://projects.gnome.org/tracker/documentation.html)). How is it possible? Is Ubuntu using some old version? Moreover the Czech translation is lost in Lucid. It was 100% translated in Karmic, and now it's completely English.

Do you have any information about Tracker related to these problems?

---

### Post by lxme on 2010-05-01
Hello, 

I am annoyed too that Tracker doesn't index my emails in Evolution. Any idea ?
Tracker plugin in Evolution is enabled, but I feel like it's not really working. If I disable it, then reenable it evolution just crashes

---

### Post by svegress on 2010-05-18
I hope I am not giving the wrong advice here.  Please someone drop from a great height if I am.

While Tracker is based on a very strong theoretic base, it is only just beginning to fulfil its promise.  I can see why Beagle has been shelved but it did have the best functionality with the least bugs in previous editions of Ubuntu.  That all changed with Lucid.  Tracker, for better or worse, has become our only real choice so I had to make it work.

Unfortunately, the version of Tracker that came with 10.4 was nothing but trouble.  Desperation sent me upstream to use [http://ppa.launchpad.net/tracker-team/tracker-unstable/ubuntu](http://ppa.launchpad.net/tracker-team/tracker-unstable/ubuntu).  The "unstable" 0.8.0 is far more stable.  And it has many excellent little tweaks that make it friendlier.

I know it breaks the Ubuntu Phiosophy of lagging to ensure stability, but this unstable code does do a pretty fair job of indexing without going corrupt.

If you look at [http://git.gnome.org/browse/tracker/](http://git.gnome.org/browse/tracker/) you will see some of the intense bug fixing and enhancement--including an update to the Czech translation.

I have a very large knowledge base on my computer including emails, pictures, videos and documents that I interrogate almost hourly in my job.  Tracker 0.8.0, while it still lacks the finesse of Beagle, does the job adequately.

Now, if it would only deal with my Thunderbird mail, I would be happy.

---

