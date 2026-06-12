---
title: "Beagle, user_xattr, and removing them"
date: 2006-06-01
forum: General Help
---

### Post by Mamour on 2006-06-01
Hi all,

I've tried using Beagle, but have been extremly disappointed with its performance. Reading their FAQ, I see that it could be improved by enabling user_xattr on my filesystems.

Now, sure, I could give this a go. Yet, if nothing goes better, I'll want to get rid of all the metadata Beagle'll probably spray across my files. Thus, is there any easy way to disable and clean all xattr data from a filesystem?

Thanks in advance!

---

### Post by frenkel on 2006-06-01
[QUOTE=Mamour]Hi all,

I've tried using Beagle, but have been extremly disappointed with its performance. Reading their FAQ, I see that it could be improved by enabling user_xattr on my filesystems.

Now, sure, I could give this a go. Yet, if nothing goes better, I'll want to get rid of all the metadata Beagle'll probably spray across my files. Thus, is there any easy way to disable and clean all xattr data from a filesystem?

Thanks in advance![/QUOTE]
If you disable them again, it's automatically removed also. (At least it was on my reiserfs partition)

---

### Post by Hezekiah on 2006-06-01
For the beagle performance issue - I'm using the user_xattr approach on my laptop,and while it takes beagle a while to build up its database initially, once the initial sweep of your information is complete the process seems to go much easier and quicker.

Depending on how much data you have and how actively you are using the computer while the indexing is going on, the initial scan can take quite a while.

---

### Post by FryerFox on 2006-06-01
To make it go much faster, you can shut down Beagle, set the BEAGLE_EXERCISE_THE_DOG variable, and restart it. That will make it use all available CPU time to index.

```
beagle-shutdown
export BEAGLE_EXERCISE_THE_DOG=1
beagled
```

After a reboot, the variable will no longer be set, so you don't have to do anything to make it go back to the way it was.

A good way to see what's going on is:
```
beagle-index-info
```

---

