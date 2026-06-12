---
title: "Gnome Dial Up Tool"
date: 2006-04-28
forum: General Help
---

### Post by cssutto on 2006-04-28
Is there a way to set this up or perhaps have two of them?

I have two ISP's and I use the one best suited to the area I am in at the time.

It is too much pain to reconfigure every time when traveling.

And the ISP that is cheapest and OK for home is not very good on the road.

CSSJR

---

### Post by Gannin on 2006-04-29
Does the dialup tool you use have a command-line interface available?  When you use it, do you use it as root (or with a sudo command) or as a regular user?

If you use it as a regular user, and if it does have a command-line interface available, then why not set up an extra user specifically for your on-the-road dialup profile.  Then when you're traveling, you can login to Gnome like normal, then bring up a console and switch to the other user (su otherusername), and then initiate the connection using that user, so it'll use the dialup profile you set up for when you're traveling.

---

