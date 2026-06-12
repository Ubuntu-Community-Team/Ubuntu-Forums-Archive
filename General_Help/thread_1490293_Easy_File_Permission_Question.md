---
title: "Easy File Permission Question"
date: 2010-05-22
forum: General Help
---

### Post by xxilus on 2010-05-22
I am trying to configure a multi user Ubuntu system, and I need some help on the file permissions.
First I started changing most things to 750 like the home directory, and all of the user directories.
Then I changed /bin to 750 and, then quickly changed it back once I noticed that the users could no longer use commands inside ssh like 'ls' or 'cd'
that makes sense.

But I don't want to go through every single system file saying yes or no.
Clearly I also need to block of apache.
Is there any way to prevent file listing on /

Why is Ubuntu so lenient? The default allows other users to look at eachothers files.
IS there a simple command I can run to set all of these permissions to a better level, while leaving all of the basics still working for the other users?

Oh yea, and can somebody please run this command on their ubuntu box?
```
ls / -n
```
I really screwed up the file permissions here, and I think it might cause problems in the future If I don't correct it.

or is there some kind of built in Ubuntu file permission repair utility like OS X?

---

