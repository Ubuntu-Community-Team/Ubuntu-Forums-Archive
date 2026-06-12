---
title: "how can I tell when a bug fix makes it to the repository?"
date: 2010-01-13
forum: General Help
---

### Post by cometdog on 2010-01-13
I'm wondering how I can tell when a bug fix makes it to the repository.  Is there a general way to determine this from the status in launchpad, or by searching for the bug in some list somewhere?

In my case I was badly affected by the following bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/446394](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/446394)

Unfortunately this one made me totally unable to connect to wireless at work, which is essential.  I had to work around by downgrading to and locking in Jaunty's version of network-manager and network-manager-gnome.

The workaround causes some other problems, though, so I'd like to be able to revert to the Karmic versions of the packages as soon as possible.  And here is my difficulty.  I have these locked at older (Jaunty) versions so I will never see the updates.  And even if I could find out whether updates to the buggy Karmic versions have been released, I would need to know if the updates fix the specific bug I'm interested in.

In this case the bug is marked as "fix committed," but as far as I can tell that doesn't really mean anything with respect to the Karmic main repository.

---

### Post by philinux on 2010-01-13
The status will change to "fix released".

---

### Post by cometdog on 2010-01-13
Thanks for the quick response!

That is the behavior I would have expected.

But this bug report seems to say that is not how it works

[https://bugs.launchpad.net/malone/+bug/163694](https://bugs.launchpad.net/malone/+bug/163694)
> But this doesn't work for Ubuntu (bug 90738 ), where a bug is marked Fix Released while the vast majority of users are still using versions with the bug unfixed.

and the bug referenced there (90738 ) says the following:

[https://bugs.launchpad.net/malone/+bug/90738](https://bugs.launchpad.net/malone/+bug/90738)
> In Ubuntu, months or even years pass before a released fix propagates out to users. Meanwhile, users who encounter the bug search for information and do not find it (resulting in duplicate reports)

---

