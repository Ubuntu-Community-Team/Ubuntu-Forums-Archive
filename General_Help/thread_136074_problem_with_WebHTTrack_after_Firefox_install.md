---
title: "problem with WebHTTrack after Firefox install"
date: 2006-02-25
forum: General Help
---

### Post by nedkelly on 2006-02-25
Hi

I have a problem with WebHTTrack after I installed Firefox 1.5.1 with Automatix, when I start WebHTTrack I get the following message

```

nedkelly@ubuntu:~$ webhttrack
/usr/bin/webhttrack(7531): launching /usr/bin/x-www-browser
/usr/bin/webhttrack(7531): spawning regular browser..

run-mozilla.sh: Cannot execute /opt/firefox/x-www-browser-bin.

/usr/bin/webhttrack(7531): waiting for browser to terminate..

```

And i just hangs there

Does any one know how to fix this?

---

### Post by nedkelly on 2006-03-06
Hi 

Asked in an other forum and got the answer there, I write it here if other get the same problem:

Open a console and type

*sudo ln -s firefox-bin /opt/firefox/x-www-browser-bin*

---

### Post by jetpeach on 2006-03-07
oh thanks you for following up and answering this!!!  it's been driving me nutz!!!

---

