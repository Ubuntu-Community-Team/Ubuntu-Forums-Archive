---
title: "Roaming profiles, simultaneous login?"
date: 2010-07-07
forum: General Help
---

### Post by talz13 on 2010-07-07
I've been thinking about setting up roaming profiles so that I can access my profile and settings from any computer in the house that has ubuntu booting on it.  One thing that concerns me is, what happens if I log in using my profile from more than one computer at the same time?

A couple examples:
1.  I'm working on something on one pc, and go downstairs.  A little while later I fire up a laptop down there and want to browse the web.  What would happen?

2.  I am logged in to my desktop, but let it go to standby.  I later log on to a different pc on the network and load the same profile that was logged in (but in standby).  What happens to the state of the profile when the desktop wakes up again?

Hopefully these scenarios are handled in some fashion, but if they are not, I'd at least like to know what to expect.

---

### Post by Yarui on 2010-07-07
There is built in support for multiple logins.  If you install a vnc or ssh server, you can log in with the profile you are already logged into without any problems.

---

### Post by talz13 on 2010-07-08
> **Yarui said:**
> There is built in support for multiple logins.  If you install a vnc or ssh server, you can log in with the profile you are already logged into without any problems.

That's the point though... I have a headless, always on server where the profiles will be stored, but it does not have (and I do not want it to have!) X running.

I want to be able to take my profile from an existing desktop and put it on the server so that it can be used remotely by any PC on the lan, and the profile will be cached on that PC in the event that it leaves the network (i.e. I take a laptop out for the day).

---

### Post by Yarui on 2010-07-08
Oh, I see.  Maybe you could describe what you are hoping to do in a bit more depth.  What kind of behavior you would like the program to have.  What data you want to sync across multiple PCs and what you want it to do in the case that multiple computers are using the same account.

What you are describing sounds like the kind of thing that would have to be built to meet your needs.  I'm not saying there isn't any software out there that does something similar to what you want, but if no one has anything to suggest it may be something you could build yourself.

Generally if I want to do something specialized like this my first thought is "I could probably write a program or script that will do that for me."  I rarely go to the trouble of searching for software that already exists for these kinds of things, so I don't really know a lot about software that does things like that.

---

### Post by talz13 on 2010-07-09
I think what I'm looking for is something like ldap and nfs home dirs, with a sync to local home of some kind for offline use.  I've just started looking at ldap and I think it's a good starting point.

---

