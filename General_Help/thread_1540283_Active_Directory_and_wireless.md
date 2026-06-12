---
title: "Active Directory and wireless"
date: 2010-07-27
forum: General Help
---

### Post by Bufke on 2010-07-27
Has anyone had success in getting likewise open or another tool to allow domain users to log in with wireless networking? I have an issue where GDM comes up, users attempts to log in and gets authentication error. After a few minutes it works. Centrify has the same issue.

I've tried removing network-manager and using /etc/network/interfaces to set up networking, which helps, but there's a 1-3 minute delay before a user may log in for the first time after a reboot. My theory is gdm gets loaded before networking is up. There's got to be a work around for this. Even having gdm just hanging for a minute while it waits for networking would be acceptable.

---

### Post by cowillia on 2010-07-29
Thanks for the post, I suspect you are in the right neighborhood. (I noticed you also mentioned the slow wireless performance on your blog on davidmburke.com...)

Talking with some of my top *NIX engineers, we think we might be on to a fix for your wifi performance issue. Stay tuned.

As we start to take a look at this issue in more detail, please post any feedback/ideas you have in our community site - [http://community.centrify.com](http://community.centrify.com).

Corey - a Centrify product manager

---

