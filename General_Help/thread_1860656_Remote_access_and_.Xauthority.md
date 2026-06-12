---
title: "Remote access and .Xauthority"
date: 2011-10-15
forum: General Help
---

### Post by promet on 2011-10-15
Hello,

I have remote login issues from time to time, mostly to do with running X-Window applications remotely and NXServer logins. 

I've been able to track back and fix my problems by realizing that they all seem to trace back to .Xauthority issues. That is, my server seems to get confused about the status of my .Xauthority permission when I log in remotely as "myself".

This can be solved I've found, by simply deleting my .Xauthority file, logging out,  and then logging back into the machine. It is a pretty sloppy solution though, and I am wondering. Is it considered "best practice" to create a different user than one's server default to do remote operations with? Thus, I assume, getting around all of the permission conflicts?

I'd like to do all of my operations as my default user though. Anyone have any ideas about not confusing .Xauthority without having to create a secondary user?

Please let me know if this seems unclear and I will try and rephrase.

Thanks!

---

