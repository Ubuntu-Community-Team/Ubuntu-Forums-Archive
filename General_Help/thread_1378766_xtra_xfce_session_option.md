---
title: "xtra xfce session option"
date: 2010-01-11
forum: General Help
---

### Post by hawthornso23 on 2010-01-11
I've just installed xubuntu-desktop to have a play with it. So far so good. I'm having fun. However when I login there are two entries for xfce under `sessions' in the login screen. Both are functional and behave identically (that is I don't seem to have two different types of xfce session). 

Presumably there is a doubled entry in a config file somewhere. Can anyone point me at the right file?

Update:  found it. 
The place to look is /usr/share/xsessions .
In my case this contained both an " Xfce Session "  desktop file and also (for some unknown reason) a link to this desktop file also called " Xfce Session ". I'm going to delete the link and I confidently expect this will fix the problem. If it doesn't I'll post a followup.

---

### Post by hawthornso23 on 2010-01-12
Ok - that fixed it. But this is a clarification since the problem isn't quite as simple as I thought.

I was looking at the directory through a file browser. And of course .desktop files don't tell you their true names if you look at them in that way.

ls -l  in a terminal revealed the true name of the link to be  default.desktop

Ahah!

So this is more of a subtle user interface issue because in the gdm you don't see  anything displayed about `default' - you just see two identical  Xfce sessions . And they really are identical because one is actually a link to the other.

So - what to do?

After 10 seconds of contemplation I decided that a system default session doesn't make sense for me anyway. I don't want to inflict Xfce as a default on the other members of the family just because I decided to have a play with it, and   \usr\share\xsessions  clearly applies to all users. So I went ahead and deleted the default.desktop link. 

This absolutely fixed the problem as far as I am concerned. Everything now behaves as one would expect.  No duplicate sessions - last used session (per user) as default. However I guess it leaves me operating without a global "default session" - whatever that means. So far I haven't missed it - it seems to be about as useful as an appendix. But someone must have stuck it in there for a reason so I suppose it is remotely possible deleting this might cause problems down the track.

---

