---
title: "IP address getting added to hosts.deny"
date: 2012-09-16
forum: General Help
---

### Post by goodvikings on 2012-09-16
Hi All

I have an issue where whenever I restart the ssh server on ubuntu server, the main IP that I use to access the box is getting added to /etc/hosts.deny

As you can imagine, it's pretty damn annoying.

Any ideas on what could be causing this? Googling around suggests something with denyhosts config files in /var/lib/denyhosts but I'm not sure on how to edit these to fix this issue.

Cheers

[Edit:] On inspection, it's not whenever ssh server is restarted, but I'm not sure what the time pattern is, it just keeps reappearing there

---

### Post by goodvikings on 2012-09-16
Bumpin

---

### Post by iponeverything on 2012-09-16
did around in your memory and try last time you were messing with tcpwrappers or some log monitoring utility to automatically muck with your hosts.deny -

Or a quick solution would be set the immutable bit on hosts.deny when you get it the way that you want it.

if you watch the logs you might see the culprit complain it can't modify the file..

---

