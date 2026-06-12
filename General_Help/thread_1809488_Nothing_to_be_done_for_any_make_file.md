---
title: "Nothing to be done for any make file"
date: 2011-07-21
forum: General Help
---

### Post by blueeyedlion on 2011-07-21
I just found a makefile tutorial, I tried it, and it worked.

Now, 2 days later, whenever I try to make a makefile, it outputs that there is nothing to be done for that file.  What happened?

---

### Post by gzarkadas on 2011-07-21
If you are running again the tutorial, then this message simply states that because you didn't changed any files, no action is necessary.

In general what 'make' does is to check whether the *dependencies* (the files that produce the final *target* of the making process) have changed since the last invocation of 'make'. If they did, it performs any actions necessary to produce again the final target; if they didn't then target is already up-to-date and nothing needs to be done.

---

### Post by blueeyedlion on 2011-07-21
Yes, the tutorial explained that.
My problem is that when I delete all the object and executable files that the makefile makes, the makefile still does nothing.

---

### Post by blueeyedlion on 2011-07-21
As it turns out, I was forgetting the "-f" option.

---

