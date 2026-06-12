---
title: "Update Manager (10.04LTS) - Just updates - right? Wrong."
date: 2012-01-27
forum: General Help
---

### Post by cryptotheslow on 2012-01-27
Hi,

OK - I thought the automatic update in Ubuntu soley pulled down updates for the packages you already elected to install. That belief was wrong.

Just got the typical Update Manager notification - had a quick look through the list - a bunch of X11 and Firefox updates on the face of it - so kicked it off. Then while it was in progress noticed, right at the bottom of the list:

xul-ext-ubufox (New install)

Screenie attached - sorry it's all greyed out, the update was in progress.

So the question is - why is **_Update_ Manager** merrily installing new packages?

Sure it seems to be some kind of Ubuntu integration package for Firefox - and is no doubt fine, but doesn't it rather go against the philosophy that an **update** manager should just **update** stuff not install new stuff?

Another question it raises for me is - can this only occur as a push of the package from Canonical or can already installed packages somehow indicate that they now require new packages installed and Update Manager happily includes them in the next round of updates?

Hopefully not the latter - especially with the latest releases of Ubuntu, where updates can be OK'd by unprivileged users.

Answers on a postcard :D

Thanks
crypto

---

### Post by wolfen69 on 2012-01-27
Did you notice the size of the file? 58kb. New install doesn't necessarily mean completely new packages. It had to wipe out what you had and *re*-install. It's not adding new applications.

---

### Post by yetiman64 on 2012-01-27
xul-ext-ubufox is a dependency of both ubufox (ticked for update above it) and ubuntu-desktop. It may not necessarily be entirely new as wolfen69 mentions.

Edit: Just noted you're on 10.04, if the version of firefox is being updated (unsure of this myself, been quite a while since I've used Lucid) then it could possibly be related to that and may be a newer dependency of the latest firefox / xulrunner installs.

---

### Post by cryptotheslow on 2012-01-27
Thanks wolfen69 and yetiman64

xul-ext-ubufox is a virtual package provided by ubufox as I see here: [http://packages.ubuntu.com/search?keywords=xul-ext-ubufox](http://packages.ubuntu.com/search?keywords=xul-ext-ubufox)

I can find no mention of release dates there - so no idea if it is new or re-install.

If it is just a re-install of an existing package then Update Manager needs to be a little smarter and mark it as ***(Re-install)*** rather than ***(New Install)*** - but then why mark it as anything, this is just an automated update right? The average user doesn't care if that involves overwriting a few files or removing and reloading the whole thing...  as long as it's just a tick box.

Still puzzled :/

---

### Post by 2F4U on 2012-01-28
If you use apt-get you have the option of apt-get upgrade and apt-get dist-upgrade. While upgrade just installs newer versions of existing packages, dist-upgrade could also install new packages as a dependency of existing packages. As far as I know, Update Manages works the same as dist-upgrade.

---

### Post by dcstar on 2012-01-28
> **yetiman64 said:**
> xul-ext-ubufox is a dependency of both ubufox (ticked for update above it) and ubuntu-desktop. It may not necessarily be entirely new as wolfen69 mentions.

Edit: Just noted you're on 10.04, if the version of firefox is being updated (unsure of this myself, been quite a while since I've used Lucid) then it could possibly be related to that and may be a newer dependency of the latest firefox / xulrunner installs.

Developers can decide to split up packages or add new packages to existing installations so there is nothing that the Update Manager has done wrong if this is the case.

If these things are not installed then chances are the update will not work and the software will be broken.

---

### Post by cryptotheslow on 2012-01-28
OK. I understand better now.

Thanks everyone :D

---

