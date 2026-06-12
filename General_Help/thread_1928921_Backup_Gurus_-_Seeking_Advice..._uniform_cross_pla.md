---
title: "Backup Gurus - Seeking Advice... uniform cross platform backup tool?"
date: 2012-02-21
forum: General Help
---

### Post by Roasted on 2012-02-21
I have my domain set up, my file server, ssh keys, etc. Now I just need to figure out exactly how I'll rig up an array of computers, ranging from Ubuntu to XP to 7, to back up automatically to my file server.

Rsync of course is an instant win, however if I use rsync via command line and my ssh keys have a password, is there a way to save that? I forget if I run it the first time if it gets saved or not or if the user is prompted for it each time.

Deja Dup - solid choice for linux to linux, but what about the windows clients? Is there a Deja-Dup-like alternative to Windows clients? I want the backup process to be similar, so if my Ubuntu clients are backing up 10mb slices of data, I'd like the Windows backup to be similar.

luckyBackup - I see luckyBackup has a scheduler, is based on rsync, and easy to use. This is... well... awesome. It also looks like it has a Linux and Windows port. However, luckyBackup doesn't save the ssh password. I need to put it in each and every single time. Blah. I tried to use Gnome's password keyring tool to hold it but it made no difference.

Ultimately, I'm curious what you guys think. All of the above suggestions are solid but I'm at the point where I'd like a little more input from other people. What are you guys using for backing up data remotely? Any other suggestions?

---

### Post by dragonfly41 on 2012-02-21
I've only just started using Grsync which is a front end GUI to rsync ..

[COLOR=Navy]**sudo apt-get install grsync**[/COLOR]

[http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)

Grsync allows rsync sessions to be saved.


[COLOR=Navy]**Grsync for windows**[/COLOR]

[http://sourceforge.net/projects/grsync-win/](http://sourceforge.net/projects/grsync-win/)


You have to check what options to tick and research to see what they do.

e.g. in my case .. I'm backing up /root partition

in Extra Options run us superuser
in Advanced Options copy symlinks as symlinks

.....

See one tutorial here ..

[http://www.makeuseof.com/tag/reasons-grsync-awesome-syncing-tool-crossplatform/](http://www.makeuseof.com/tag/reasons-grsync-awesome-syncing-tool-crossplatform/)

> Are you editing files you don&#8217;t have permission for? Be sure to check &#8220;Run as superuser&#8221; to ensure everything will transfer properly. You can also execute commands before and after the sync is completed.

Want to discover what the other checkboxes do? Hover your mouse over them for a pop-up explanation.

---

### Post by Grenage on 2012-02-21
I used keys only, which simplifying the process; is there a reason you're using a key and a phrase?

Unison was the windows client we used, this was a few years ago, but it looks like it's still active.

---

### Post by Roasted on 2012-02-21
> **Grenage said:**
> I used keys only, which simplifying the process; is there a reason you're using a key and a phrase?

Unison was the windows client we used, this was a few years ago, but it looks like it's still active.

What exactly are you referencing when you said you used "keys only?" Can you elaborate a little bit?

---

### Post by TheFu on 2012-02-21
rsync alone is not suitable for most backup requirements. It is great for many things where you need a mirror copy - like for large media file backups.

For OS, apps and data backups you want more - incremental and multiple versions in addition to encryption.  Other *best practices for backups:* [http://blog.jdpfu.com/2011/11/12/best-practices-for-home-desktop-computer-backups](http://blog.jdpfu.com/2011/11/12/best-practices-for-home-desktop-computer-backups)

You didn't say which OS your file server is running. If Linux, it will be easier to locally mount a backup area onto Windows machines and treat it like a local storage area.  Having a single cross-platform of backup solution forces you towards:
* **Duplicity**
* **Duplicati**
* **Bacula**
* Commercial tools like netbackup

I'm not a fan of backup methods that don't leave the backup areas in a usable file system. For this reason, you may want to check out **rdiff-backup**.  I've had issues with the win32 port of rdiff-backup, but it is soooooo very nice on Linux that I don't care.  Out of 20 systems here, 18 are Linux.

Anyway, even if you decide to use rsync, that is still much better than not doing backups at all.

---

### Post by Grenage on 2012-02-22
> **Roasted said:**
> What exactly are you referencing when you said you used "keys only?" Can you elaborate a little bit?

Hi Roasted,

In the scenario we had, we used keys without pass-phrases (the servers were physically secured).

---

