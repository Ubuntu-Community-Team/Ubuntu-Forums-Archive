---
title: "Hang over"
date: 2010-10-03
forum: General Help
---

### Post by msakms on 2010-10-03
I've been running my PC for a non-stop uptime of a week or so. All of a sudden it stopped working and my mouse wouldn't even move that I had to do a hard reset. I'm using almost all the features ubuntu has to offer and all my hardware works perfectly. I'm looking for some way to figure out what happened. Many thanks in advance.

---

### Post by harrismh777 on 2010-10-04
> **msakms said:**
> All of a sudden it stopped working and my mouse wouldn't even move that I had to do a hard reset....I'm looking for some way to figure out what happened. Many thanks in advance.

In the first place, do not assume that since your mouse won't work that the system is dead. Sometimes the system is "up" but the interface xorg is dead, or other.
Can you login to the machine from the network with ssh? This question should be asked and tried before a reset.
Also, was the keyboard also dead?  If not, does the key combo ctrl-alt-F1 bring up a terminal?  can you login?

The only thing you can really do at this point is to paw through the logs and see if you can determine generally what happened. The logs are located in /var/log    You are going to want to look through messages, syslog, user.log, and xorg logs.

Did you have "kernel panic" on the monitor? 

You may have been hacked (not likely) or you may have had some kind of overflow ...  like logs filled up, memory leak crashed kernel, some driver bug, etc...

The bottom line is that you're going to have to try to reproduce the error (log it) and pass the info on in a bug report. On the other hand, if you were hacked, you are going to have to button that thing up a bit...

Without any info to go on I'm just wagging here....


:confused:

---

