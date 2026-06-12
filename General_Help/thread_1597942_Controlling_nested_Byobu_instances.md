---
title: "Controlling nested Byobu instances"
date: 2010-10-15
forum: General Help
---

### Post by jordon on 2010-10-15
I'm just starting out with Byobu/Screen. I like the default F-key bindings for Byobu, but when I log in to a remote machine and try to use Byobu there, I can't control it with the F-keys; the local instance of Byobu intercepts them.

I've found out that it's possible to [control a nested Screen]("http://blog.bigsmoke.us/2009/01/11/gnu-screen-within-screen") by adding an extra a after Ctrl-a. For example, if "Ctrl-a c" opens a new window in the local Screen, "Ctrl-a a c" opens a new window in the remote Screen. This works in Byobu/Screen even though both the local and remote instances are set to use the F-key bindings.

I'd rather be able to use the F-key bindings for both. Is this somehow possible, or do I have to use the default Screen key bindings on the inner Screen?

---

