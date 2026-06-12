---
title: "live folder/file sync?"
date: 2010-09-02
forum: General Help
---

### Post by lkejke on 2010-09-02
I want to have a process running (constantly, quietly, invisibly) in the background that syncs changes I make in one volume/folder to another volume/folder (on the same machine).

I have looked at unison. It's a great app but requires manual operation to sync each time, or a CRON job. Cron isn't a good solution. I need instant updates/sync the moment I modify a file or folder.

I am currently just working one one machine, but eventually I would like to live sync to a remote server.

Surely this is a common task/process for admin/developer types!?

I've been looking for a couple of days and can't find a solution.

---

### Post by DemonBob on 2010-09-02
Only thing i can find, that would be realtime is below. But i have not used it. 

[http://www.drbd.org/](http://www.drbd.org/)

---

### Post by Ghost_Mazal on 2010-09-02
Sorry , didn't see cron is not an option for you

---

### Post by lmarmisa on 2010-09-02
It sounds a bit strange your "requeriments". 

Do you need two different physical copies for your files?. If no, a symbolic link (command ln -s) could be a perfect solution.

If you are looking for redundancy, a [RAID level 1]("http://en.wikipedia.org/wiki/RAID") could be your solution.

Solutions of the type Cloud could be also interesting for you:

[https://one.ubuntu.com/](https://one.ubuntu.com/)

[https://www.dropbox.com/](https://www.dropbox.com/)

---

### Post by DemonBob on 2010-09-02
FYI on my above post. 

[https://help.ubuntu.com/9.04/serverguide/C/drbd.html#drbd-configuration](https://help.ubuntu.com/9.04/serverguide/C/drbd.html#drbd-configuration)

---

### Post by lkejke on 2010-09-02
> **lmarmisa said:**
> It sounds a bit strange your "requeriments". 

Do you need two different physical copies for your files?. If no, a symbolic link (command ln -s) could be a perfect solution.

If you are looking for redundancy, a [RAID level 1]("http://en.wikipedia.org/wiki/RAID") could be your solution.

Solutions of the type Cloud could be also interesting for you:

[https://one.ubuntu.com/](https://one.ubuntu.com/)

[https://www.dropbox.com/](https://www.dropbox.com/)

Not so basic as Dropbox and not so major as RAID.

Basically, I want to choose both locations (e.g. 1- my server, 2- my portable USB hard drive), and have changes to selected folders immediately sync'd no matter which side I edit. My initial aim is to sync /var/www with my USB hard drive. I am running Apache locally (running Ubuntu on a single partition/volume) but I want to edit from my portable USB hard drive, which I regularly unplug and take to other work stations. Later, I will also want to "push" live changes from my local development environment (this machine) to a networked server. Much later, I want to "push" live changes over a secure remote connection.

Ubuntu One and Dropbox are fantastic services. I have accounts with both and use them for syncing my regular documents (office, music, videos etc.) but my current need is more about sync'ing custom local locations.

I thought this would be a fairly obvious basic process; a file is edited in one location and the system process immediately syndicates the change to other configured locations on the same host, over a network, or to a remote server.

I would call this something like "live push sync". Clearly, Ubunto One and Dropbox do this kind of "push" sync. I just want to be the owner of the whole service/process.

Is this not something anyone has ever wanted to do before?

Damn my "techagination" (technology imagination).

In the meantime I will be using Unision to manually propagate changes.

---

### Post by lkejke on 2010-09-02
I should add, I used to use Espresso on Mac, which cleverly kept a full copy of everything locally but sync'd to the server every time you saved a document you edited.

I no longer use Mac.

I still like Mac.

Free is better.

---

