---
title: "automatic sync between computers"
date: 2009-08-30
forum: General Help
---

### Post by osomphane on 2009-08-30
Is there an automatic syncing tool for linux-based systems that is somewhat user-friendly? For windows, Microsoft has created live mesh in which you can sync without limits. For linux(gnome), I have seen ubuntuone and dropbox, but they cap out at 2GB for free and 100GB paid and they force you to upload on cloud storage... so are there any alternatives that make syncing automatic and relatively easy?

Or, what is the software that some websites use to mirror other websites? I assume it is some kind of automatic syncing thing again?

---

### Post by DGortze380 on 2009-08-30
> **osomphane said:**
> Is there an automatic syncing tool for linux-based systems that is somewhat user-friendly? For windows, Microsoft has created live mesh in which you can sync without limits. For linux(gnome), I have seen ubuntuone and dropbox, but they cap out at 2GB for free and 100GB paid and they force you to upload on cloud storage... so are there any alternatives that make syncing automatic and relatively easy?

Or, what is the software that some websites use to mirror other websites? I assume it is some kind of automatic syncing thing again?

rsync and cron

---

### Post by P4man on 2009-08-30
Unison
[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

rsync made easy :)
its in the repositories.

---

### Post by osomphane on 2009-08-31
Isn't unison abandoned? Also, would they allow for the syncing of 3+ computers or only two of them?

---

### Post by P4man on 2009-08-31
> **osomphane said:**
> Isn't unison abandoned? Also, would they allow for the syncing of 3+ computers or only two of them?

Not abandoned afaik, quick look at svn shows a few week old builds, so I guess not. And 3 or 30 comps should work fine.

---

### Post by osomphane on 2009-09-13
well, unison is definitely interesting :) one question for the experience users though, would deleting a file result in a permanent delete on other machines or would it be moved to trash?

---

### Post by noping on 2010-05-13
Combining unison, rsync and cron, I sync a shared folder from 4 computers to one server, and the server has daily backup for past month.

On each computer, unison is called to sync the shared folder every 5 minutes with the server, using cron.

On the server, rsync makes incremental backup so I won't lose any file by accidental deletion. Google for "incremental backup with rsync" gives plenty of example scripts. Alternatively, use backintime package to do the backup, which is much much easier.

---

### Post by alienprdkt on 2010-05-13
any one know of one of these apps that is in real-time ... have looked into gluster but don't need all that, just want to sync a local mounted directory in real-time, from my production machines. Am currecntly using unison which is really nice but would love to upgrade to something in real-time and bi-directional as well. Thanks.

Please let me know if there is something out there that can do the job for free. 

Can't afford the $500 pricetag of [http://filereplicationpro.com/](http://filereplicationpro.com/) right now for a linux solution.

Thanks in advance,

---

### Post by osomphane on 2010-06-14
bump for the poster above :)

---

### Post by DGortze380 on 2010-06-14
> **alienprdkt said:**
> any one know of one of these apps that is in real-time ... have looked into gluster but don't need all that, just want to sync a local mounted directory in real-time, from my production machines. Am currecntly using unison which is really nice but would love to upgrade to something in real-time and bi-directional as well. Thanks.

Please let me know if there is something out there that can do the job for free. 

Can't afford the $500 pricetag of [http://filereplicationpro.com/](http://filereplicationpro.com/) right now for a linux solution.

Thanks in advance,

Define real-time.
Again you could do this with a simple rsync script and cron.

Run it every minute, or two, or five, or ten... etc.

---

### Post by osomphane on 2010-06-14
Maybe something like Windows Live Mesh or Ubuntu One, except that the server would be hosted on your computer. IE - a file system update triggers file propagation for only the file(s) affected (can be supplemented with fixed-interval 8-hour/etc scans to ensure integrity).

---

### Post by bodhi.zazen on 2010-06-14
> **osomphane said:**
> Is there an automatic syncing tool for linux-based systems that is somewhat user-friendly? For windows, Microsoft has created live mesh in which you can sync without limits. For linux(gnome), I have seen ubuntuone and dropbox, but they cap out at 2GB for free and 100GB paid and they force you to upload on cloud storage... so are there any alternatives that make syncing automatic and relatively easy?

Or, what is the software that some websites use to mirror other websites? I assume it is some kind of automatic syncing thing again?

I advise you use rsync

---

### Post by alienprdkt on 2010-09-24
> **DGortze380 said:**
> Define real-time.
Again you could do this with a simple rsync script and cron.

Run it every minute, or two, or five, or ten... etc.

This would work great how to throttle bandwidth with rsync. How to have rsync only copy new or modified files? 

What was looking for over rsync was a GUI where I could set all of these functions rather then trying to find the correct switch and syntax, but I don't think an app like this exists.

So back to man rsync I guess.

---

### Post by bodhi.zazen on 2010-09-24
If you want a gui, use grsync

[http://www.opbyte.it/grsync/screenshot.html](http://www.opbyte.it/grsync/screenshot.html)

rsync was designed to update only files that have changed, cool 'eh ?

[http://www.cyberciti.biz/tips/linux-use-rsync-transfer-mirror-files-directories.html](http://www.cyberciti.biz/tips/linux-use-rsync-transfer-mirror-files-directories.html)

> 
**So what is unique about rsync?**

 It can perform differential uploads and downloads (synchronization)  of files across the network, transferring only data that has changed.  **The rsync remote-update protocol allows rsync to transfer just the  differences between two sets  of  files**  across the network connection.

---

### Post by Jorell00 on 2010-09-24
I never really got on with rsync  and have been using freefilesync for the past few months and seems to do what i need , Hope it helps you.

[http://sourceforge.net/projects/freefilesync/]("http://sourceforge.net/projects/freefilesync/")

---

### Post by velmont on 2010-10-08
OK, why do people keep recommending rsync when Unison is quite clearly superior?

Don't get me wrong, I used rsync in the old days as well, I never tried Unison because it didn't sound like what I was looking for. However, I was wrong. :-)

You want **realtime sync**? Look no further than Unison! They say you can run unison in cron every 5 minutes. Well, that is OK, but bump unison cron up to 30 minutes and use instead **incron**.

incron runs a command when a file changes. So you could run unison -batch when a new file is made, or an old file is saved.

I also have unison keep 3 versions of my files, when they get exchanged. So that if I destroy a file, I can get it back. It also works with deleting. If I delete a file, I can find it on my server again.



I use this just like a free and extremely powerful dropbox. I'm syncing all my computers like this.

If I want to make a folder web accessible (like Documents/Small stuff/Ubuntu posters), I just go to my server and make this symlink

```
public_html/ubuntu-posters -> ../Documents/Small stuff/Ubuntu
```

And voila, it's web accessible, and updated quickly automatically for me.

---

