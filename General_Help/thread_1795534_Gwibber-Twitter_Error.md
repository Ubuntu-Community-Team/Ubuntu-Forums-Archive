---
title: "Gwibber-Twitter Error"
date: 2011-07-02
forum: General Help
---

### Post by moore.bryan on 2011-07-02
For the past couple days I've been getting an error ("This application is not allowed to access or delete your direct messages"). According to [this]("http://osdir.com/ml/twitter-development-talk@googlegroups.com/2011-05/msg00678.html") it would appear it's Ubuntu's "job" to reauthorize their "tokens" to allow proper use of the Twitter API; does anyone know if this is happening?

---

### Post by joris1977 on 2011-07-03
Same issue here. I am not really sure what is going on. I don't really use twitter a lot and the message doesn't give a lot of information.

---

### Post by robbiemacg on 2011-07-03
Well, I'll bump this. I've just encountered the same issue.

---

### Post by moore.bryan on 2011-07-03
Well, I'm going to assume it's confirmed, particularly because of the thread I referenced above. Does anyone know if this has been reported as a bug?

---

### Post by robbiemacg on 2011-07-03
Took a look at the Gwibber launchpad page earlier. It does appear the issue's been noted.
[https://bugs.launchpad.net/gwibber/+bug/789851](https://bugs.launchpad.net/gwibber/+bug/789851)

---

### Post by robbiemacg on 2011-07-03
While it is a clumsy solution in my opinion, you can apparently manage this problem by removing and reauthorizing your Twitter account within Gwibber.

[http://groups.google.com/group/twitter-api-announce/browse_thread/thread/4956a4dd169be70c?pli=1](http://groups.google.com/group/twitter-api-announce/browse_thread/thread/4956a4dd169be70c?pli=1)

---

### Post by moore.bryan on 2011-07-04
> **robbiemacg said:**
> Took a look at the Gwibber launchpad page earlier. It does appear the issue's been noted.
[https://bugs.launchpad.net/gwibber/+bug/789851](https://bugs.launchpad.net/gwibber/+bug/789851)
Thanks for that, robbiemacg; I hadn't even thought of checking the LP page. The discussion their looks like it's a simple fix, so I wonder why the handful of minutes hasn't been spent fixing this issue if they/we knew about it a while back.

> **robbiemacg said:**
> While it is a clumsy solution in my opinion, you can apparently manage this problem by removing and reauthorizing your Twitter account within Gwibber.

[http://groups.google.com/group/twitter-api-announce/browse_thread/thread/4956a4dd169be70c?pli=1](http://groups.google.com/group/twitter-api-announce/browse_thread/thread/4956a4dd169be70c?pli=1)
Thanks for this, as well...

---

### Post by robbiemacg on 2011-07-04
Cheers. 
Unfortunate that this issue had to impact end users at all given the amount of lead-time available, but, I'm not a contributing dev, so I guess I can't complain too much.

---

### Post by moore.bryan on 2011-07-04
True, on both accounts.

---

### Post by lolwhites on 2011-07-07
Have removed and re-entered my Twitter account details but the issue persists.

---

### Post by Flopy on 2011-07-11
It's not enough to just remove/add the Twitter account info on Gwibber. You have to actually go to [http://twitter.com/settings/applications](http://twitter.com/settings/applications) and Revoke Access to it, THEN you can re-add the Twitter info on Gwibber.

After that, your Twitter application settings for Ubuntu should say: "read, write, and direct messages access"

---

### Post by LordNodens on 2011-07-11
Well, I didn't have to do that in order Twitter to give me read, write, and direct messages access. Just removing and re-adding my account worked.

---

### Post by lolwhites on 2011-07-11
I removed the account from Gwibber, killed the program with *killall gwibber-service*, revoked access, fired up Gwibber again and added my account, but the issue persists :(

---

### Post by moore.bryan on 2011-07-11
> **Flopy said:**
> It's not enough to just remove/add the Twitter account info on Gwibber. You have to actually go to [http://twitter.com/settings/applications](http://twitter.com/settings/applications) and Revoke Access to it, THEN you can re-add the Twitter info on Gwibber.

After that, your Twitter application settings for Ubuntu should say: "read, write, and direct messages access"
I also didn't have to go through all this...

> **LordNodens said:**
> Well, I didn't have to do that in order Twitter to give me read, write, and direct messages access. Just removing and re-adding my account worked.

> **lolwhites said:**
> I removed the account from Gwibber, killed the program with *killall gwibber-service*, revoked access, fired up Gwibber again and added my account, but the issue persists :(
Hmm... perhaps it's something else, then. Does it throw-up any other errors?

---

### Post by lolwhites on 2011-07-11
> Does it throw-up any other errors?

No, but it just presented the last 5 replies as new, and I can't see the message any more, so maybe it worked this time. Fingers crossed anyway...

EDIT - spoke to soon, the message still appears.

---

### Post by moore.bryan on 2011-07-11
How about running a [Backtrace]("https://wiki.ubuntu.com/Backtrace")?

---

### Post by lolwhites on 2011-07-11
Have tried following the instructions you link to without success. All I get are errors like *Could not link to process*.

However running Gwibber in debug mode yields the following message in terminal when the "not allowed" message appears:

> {}
/usr/lib/python2.7/dist-packages/gwibber/gwui.py:870: GtkWarning: gtk_box_pack: assertion `child->parent == NULL' failed
  self.pack_start(content_area, False)


---

### Post by moore.bryan on 2011-07-11
Sorry, chap, I'm all out of ideas... perhaps someone more knowledgable than me will wander into this thread.

---

