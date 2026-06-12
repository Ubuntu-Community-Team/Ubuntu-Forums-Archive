---
title: "Would like example &quot;ls / -l&quot; output from a working mythbox !"
date: 2011-11-04
forum: General Help
---

### Post by Raptor Ramjet on 2011-11-04
Hello,

I recently had a problem on my Mythbuntu 11.04 box where I was trying to fix a directory in /var/lib/mythtv/video which had "?????????" permissions set on it (no idea how this came to be ?)  Whilst trying to rectify this problem I inadvertently issued a chown command on the root directory and, despite catching this alomst immediately with "Ctrl+C", this killed the box.

So after a lot of effort I have managed to mostly recover my system by restoring ownership based on another kubuntu desktop and the system now *mostly* works fine. However... there are several parts of the system that are still not working (audio plays in myth front end but not from VLC or other media apps, I can't view the systems audio properties from a desktop session, I can't run the "Users and groups" dialog from the desktop etc. etc.)

Now given that it was all working fine before my chown problem I am pretty confident that I've simply missed setting some files/directories back to the correct owner. 

And whilst I realise that it would be relatively simple to just reinstall everything I'd prefer to try and fix the problem as I've already done quite a bit of work to get the system back up and running.  Plus it's a reasonable (if thoroughly tedious)  learning exercise.

So... I was therefore wondering if anyone could be kind enough to give me a file containing the output from "ls / -l" from a working MythTV box ? (e.g. a list showing the ownership and permissions of all system files on the box) which I can compare with my system.

Obviously I'd expect you to edit out the contents of any directories you don't want (or need) to show me as I'm not interested in anyone's media collection or recordings etc.  

However I am very interested in who should be the owner of all system files as I've obviously missed resetting the ownership of some file systm objects and would like to get the box working without doing a reinstall.

Thanks in advance.

---

