---
title: "Sound works does not work when NIS user logged in."
date: 2006-04-20
forum: General Help
---

### Post by BrianK on 2006-04-20
I'm guessing this is some sort of setup problem, but I can't seem to find it.

If I log in as the user I created during install, sound works great, but if I log in to an NIS user's account, I get no sound.  I also can't do things like open up the network-admin tool or run updates - it asks for a password, then does nothing.

I checked permissions of /dev/dsp - it is setup by default to ug+rw.  I changed it to a+rw, but that didn't help.

I'm sure it's a simple setup thing, but where is it?

This is Breezy.

Thanks.

---

### Post by BrianK on 2006-04-22
As it turns out, it's not just NIS users, it's any user that gets added. 

Sound works great for root and the user I added during install, but no other users added since.

---

### Post by BrianK on 2006-04-28
Sorry to keep bumping this, but surely someone besides myself has added a user and run into this problem?

Partial Answer:
For regular added users, you have to go to System > Admin > Users/Groups
Then click "show all users", select your new user, click the "Priveledges" tab, and set priviledges - one of which is "Use sound devices"

I haven't tried with NIS users yet because I'm not at the office & won't be for a few more days.. but at least this gets the ball rolling if anyone else has this issue.

---

