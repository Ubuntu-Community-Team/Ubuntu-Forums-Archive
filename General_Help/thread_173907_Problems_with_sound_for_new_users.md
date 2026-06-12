---
title: "Problems with sound for new users"
date: 2006-05-11
forum: General Help
---

### Post by tsb on 2006-05-11
I added a new user, but when they log in it said that they don't have access to dev/dsp. and they didn't have sound  So, I changed the file permissions on dev/dsp so that the new user now has sound.  However, KMix doesn't use the mixer and displays a red 'X'.

How can I fix this so tha sound works just like the original user?

Thanks.

---

### Post by Seaman on 2006-05-11
What command (flags) did you use when you added the user(s)?

However, this should solve it;
```
sudo adduser <username> audio
```

You can read more about it on the [Ubuntu Wiki]("https://wiki.ubuntu.com/AddUsersHowto").

---

### Post by tsb on 2006-05-11
I didn't change any of the defaults when adding the user.

Your command solved the issue.  Thanks for that and the link.  :)

---

