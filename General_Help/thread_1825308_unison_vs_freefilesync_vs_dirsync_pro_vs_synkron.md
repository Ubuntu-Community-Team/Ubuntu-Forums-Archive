---
title: "unison vs freefilesync vs dirsync pro vs synkron"
date: 2011-08-15
forum: General Help
---

### Post by dafreez on 2011-08-15
Hi,

I have a home server that houses all my files accessible over SSHFS.

I am looking for a tool that can bidirectionally sync the Documents Folder on the server with the one on my netbook, so that I can keep my work-flow up to date on both regularly. (the directory in question contains mostly MSOffice files and a few PDFs. It is about 1.5GB in size, most of which never changes.

From what Ive read all the apps I mention will do the trick. Which would you recommend I use and why?

Note: I am leaning towards Unison, as it seems to have good SSH support which is important (as I often have to synchronize away from my LAN). Do the other three have any speed/feature advantages which I would be missing in Unison?

Thanx!

---

### Post by tredegar on 2011-08-15
Dropbox works for me.
It integrates with nautilus.
You can keep your files "private", or generate a publishable link to them. Up to 2GB is free.
Link: [Dropbox]("http://db.tt/QM4IxUx")
It is not open-source :(

---

### Post by dcstar on 2011-08-15
> **dafreez said:**
> Hi,

I have a home server that houses all my files accessible over SSHFS.

I am looking for a tool that can bidirectionally sync the Documents Folder on the server with the one on my netbook, so that I can keep my work-flow up to date on both regularly. (the directory in question contains mostly MSOffice files and a few PDFs. It is about 1.5GB in size, most of which never changes.

From what Ive read all the apps I mention will do the trick. Which would you recommend I use and why?

Note: I am leaning towards Unison, as it seems to have good SSH support which is important (as I often have to synchronize away from my LAN). Do the other three have any speed/feature advantages which I would be missing in Unison?

Thanx!

Unison is basically a nice front end for rsync, I use it and it does the job for me and it has command line options that you can put in cron jobs.

---

### Post by aeiah on 2011-08-15
> **dcstar said:**
> Unison is basically a nice front end for rsync, I use it and it does the job for me and it has command line options that you can put in cron jobs.

it isnt a front-end for rsync, but it is very similar. i too use unison and it runs fine. occasionally you get conflicts if it cant decide which version of a file is the newest (if you've made changes on two systems at the same time) but if you're the only user it probably won't happen. when a conflict does happen it tells you about it and doesn't lose either version.

---

### Post by fragos on 2011-08-15
I've been happy with Unison for years. In the past I've used it with a FAT memory stick to carry my working files between a home Linux and work Windows system. Unison also runs on Windows. These days I use it to sync my desktop and Laptop working files over Wifi mounting with NFS, both systems running Ubuntu.

---

### Post by dafreez on 2011-08-16
Thanks for the feedback. Guess Ill go with Unison.

---

