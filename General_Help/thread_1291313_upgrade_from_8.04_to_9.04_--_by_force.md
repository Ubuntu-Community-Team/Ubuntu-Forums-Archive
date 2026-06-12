---
title: "upgrade from 8.04 to 9.04 -- by force"
date: 2009-10-14
forum: General Help
---

### Post by jettero on 2009-10-14
I've been thinking about changing all the hardy to jaunty in my sources.list and issuing:

apt-get update
apt-get upgrade

looks like about 600 megs of .debs... 

I figure it'll break stuff, but I figure I can fix it too.

Has anyone tried this?

---

### Post by redilyn on 2009-10-16
I've never tried that myself but I wouldn't bother if it was me.

Why not just use the update manager?

Press ALT+F2
```

gksudo update-manager -d

```

You may have to do this twice if it upgrades you to 8.10 before 9.04.

Atleast it is the safe and reliable way of doing thingsd]

---

### Post by jettero on 2009-10-19
> **redilyn said:**
> 
You may have to do this twice if it upgrades you to 8.10 before 9.04.

Atleast it is the safe and reliable way of doing thingsd]

I don't want to do it twice.  That's an extra 600megs of downloads for no good reason.  I don't mind if a few things break -- I can fix 'em.  I imagine people have tried it and it worked fine, was hoping to find other like minded peoples.

---

### Post by redilyn on 2009-10-19
Did you atleast try that command I gave you?

```

To upgrade from 8.04 to Kubuntu 9.04, over the Internet, use the following procedure.

   1. Ensure your system is up to date with Adept Updater
   2. Run Adept Manager
   3. Click Fetch Updates
   4. The Version Upgrade button will appear, click it.

```

The instructions above are for kubuntu but I suspect it is probably the same for ubuntu using update-manager.

---

### Post by jettero on 2009-10-19
> **redilyn said:**
> Did you atleast try that command I gave you?

Why would I do that? I just explained I don't want to upgrade twice.

---

### Post by redilyn on 2009-10-19
Maybe I didn't explain myself clearly....

From what I can gather from what I just posted is that you can upgrade directly from 8.04 to 9.04 in kubuntu.

So I stands to reason that you should be able to upgrade directly from ubuntu 8.04 to 9.04. In ubuntu you would use the update-manager instead of adept manager.

The command would be:
```

gksudo update-manager -d

```

In the window that opens it will tell you wether it is 8.10 or 9.04 you will be upgrading too.

I was asking if you had run the command and check to see what version it was offering.

Edit: Nevermind, this can't be done with update-manager. "You can only directly upgrade to Ubuntu 9.04 from Ubuntu 8.10"

Cheers

---

