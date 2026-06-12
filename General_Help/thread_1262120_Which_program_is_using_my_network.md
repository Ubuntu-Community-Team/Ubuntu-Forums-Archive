---
title: "Which program is using my network?"
date: 2009-09-09
forum: General Help
---

### Post by cguy on 2009-09-09
Something downloads from the Internet @ ~5MiB/s.
How can I find out which program does it?

Hmm... now it stopped!

What's going on? A few GB were downloaded. (~3)

---

### Post by ivelasco on 2009-09-09
Wich is your network topology?how many PC's?Do you use a router....??

---

### Post by cguy on 2009-09-09
Only 1 PC on a PPPoE network, no router.

I tried netstat - don't understand a thing
and iftop - renders useless now, after the downloader is dead

---

### Post by Whiffle on 2009-09-09
"netstat -c" in terminal will show whats connecting to where and how, but probably not why...

---

### Post by flugh on 2009-09-09
Posting from Windows, can't test this, and my brain is dusty. But try:

fuser -n tcp -p #port number netstat shows#

to see what's using a port currently. Doesn't do you any good now of course, but it's handy for future situations. fuser also has a -k switch to kill processes. Somewhere on your hard drive should be about 3GB of data you don't recognize. Get in /, do a 'df' (maybe some flags to add to it, not sure offhand), and look for hidden/dot dirs with large amounts of data. Also check /var/log/messages to see if there's any oddball logins. Or are you sure you didn't tell apt to dist-upgrade or something?

Just babblings of an old man. I'll go take a nap now.

---

### Post by cguy on 2009-09-10
The hard drives are as occupied as they were before and the logs don't show any login attempt except mine.

I'm positive I didn't run any update.

---

