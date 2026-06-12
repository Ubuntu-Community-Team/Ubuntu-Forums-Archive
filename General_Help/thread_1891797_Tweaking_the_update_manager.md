---
title: "Tweaking the update manager?"
date: 2011-12-06
forum: General Help
---

### Post by Francis4344 on 2011-12-06
I am using Ubuntu 11.04, Classic Desktop.

Is there a way to configure the update manager to prevent the downloads and installation of many useless updates? 

For example, I dont use Firefox, so no upgrade necessary. Same goes for a whole bunch of English language package I dont need (using the French version), and so on.

Any idea?

Thanks!

---

### Post by oldtimer7777 on 2011-12-06
> **Francis4344 said:**
> I am using Ubuntu 11.04, Classic Desktop.

Is there a way to configure the update manager to prevent the downloads and installation of many useless updates? 

For example, I dont use Firefox, so no upgrade necessary. Same goes for a whole bunch of English language package I dont need (using the French version), and so on.

Any idea?

Thanks!

Uninstall whatever you don't want in Synaptic Package Manager.

sudo apt-get install synaptic
gksudo synaptic

Search for whatever you don't want running or updating on your system and uninstall them.

If you are going to keep something, it is better to let it update normally.

---

### Post by pqwoerituytrueiwoq on 2011-12-06
go into synaptic and lock the version

---

### Post by Francis4344 on 2011-12-08
Well, I dont think the first suggestion will cut it. For example, I still get update for Firefox even tough I already removed it.

So the question remains open for now... :)

---

