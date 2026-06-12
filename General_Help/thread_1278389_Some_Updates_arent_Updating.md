---
title: "Some Updates arent Updating"
date: 2009-09-29
forum: General Help
---

### Post by iheartubuntu on 2009-09-29
I have several updates that need updating, but they are grayed out in the update manager.

A few of the ones grayed out are:

-cups
-pidgin


also what look important are:

-linux headers generic
-linux image generic
-linux restricted modules generic

Now, Ive tried going into Synaptic Package Manager and I am able search on these (like "cups") and can manually update them, but Id rather just have it all work within the Update Manager.

Any tips on making this just work properly? Thanks for any help!

---

### Post by slakkie on 2009-09-29
Guess it needs to remove/install some packages before you can install them...

What you could do is:

```

sudo aptitude update
sudo aptitude safe-upgrade # Like you will do with synaptic
sudo aptitude full-upgrade # Which is similar to dist-upgrade (it is dist-upgrade..)

```

My guess is that full-upgrade will upgrade those packages. What OS are your running? lsb_release -a.

---

### Post by iheartubuntu on 2009-09-29
Thanks for the help. Strangely, after I updated the "cups" program within synaptic, all of the other programs became available to update, which I did and now everything is updated!

---

