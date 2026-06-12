---
title: "Firefox stops loading pages after a while"
date: 2012-07-16
forum: General Help
---

### Post by sdasilva on 2012-07-16
I'm running Ubuntu 12.04 (precise) 32-bit with Firefox 13.0.1 Mozilla FireFox for Ubuntu canonical - 1.0.

After a while firefox just stops loading pages. I installed firebug and most of the connections just show up as aborted.

Usually this is after browsing Udacity and viewing about a dozen or so sections (about three dozen youtube videos in a row), but it's really after a large enough number of any page loads. When this happens pages won't load correctly for any website, usually showing up empty, or half-empty if there's any browser cache.

Restarting firefox always solves it. It seems like some kind of memory leak.

Has anyone else encountered this? Any way to fix it?

---

### Post by vasa1 on 2012-07-16
Do you really need Firebug? That is one heavy extension. Have you tried safe mode or a new profile?

---

### Post by sdasilva on 2012-07-16
No, I don't need firebug. I only installed it to get an idea of what's going on. Anyway, FireFox shouldn't stop responding just because I have firebug installed.

I did some more digging and found that after each youtube video at least, there seems to be one or more extra files in use by firefox.

"lsof -p <firefox pid>" show a long list of /tmp/mozilla_audio_sample (deleted)

I haven't tried it yet (and it's getting a bit late for me) but I assume that when it reaches my ulimit -n (1024), I'll see the problem again.

After about three dozen videos (which is less than half a lecture unit on Udacity; the videos are all very short), I have over 580 open file handles. Seems like there's a file handle leak somewhere.

---

### Post by sdasilva on 2012-07-17
Found it!
I couldn't find anyone else with the same problem on a recent FF version so I started thinking what I might have that might be uncommon. The answer: the add-on [Collusion]("https://addons.mozilla.org/en-US/firefox/addon/collusion/?src=api"). I tried it out after watching a TED video. It keeps track of what websites keep track of you. Apparently it also keeps a hold on a lot of files you use.

After I removed the add-on lsof stayed stable around 280-290 file descriptors.
I tried adding it back and it went up again, to over 450.

Problem solved.

---

