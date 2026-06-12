---
title: "User Switching in 9.10"
date: 2010-01-27
forum: General Help
---

### Post by mjm1231 on 2010-01-27
I just installed ubuntu 9.10 after running xubuntu 8.10 on an older machine for about a year and a half. Much to my surprise, Switch User no longer appears to be an option. I followed the links at the bottom of this thread:
[http://ubuntuforums.org/showthread.php?t=1374581](http://ubuntuforums.org/showthread.php?t=1374581)

I was able to add the switch user applet to the panel, but it doesn't work. I get a login screen with the current username and no ability to enter a different name. There is a switch user button on this screen as well, but pressing it just returns the same screen again. When selecting Switch User from the applet, an error appears: 
"Unable to start new display
The name org.gnome.DisplayManager was not provided by any .service files"

Why was fast user switching removed in this release, and how can I get it working again?

---

### Post by zvacet on 2010-01-28
Did you add another user in system>admin>users&groups?I know it is a bit trivial to ask but I'm not sure that I understand your question well.Sorry for asking.Probably my broken English.

---

### Post by mjm1231 on 2010-01-28
Yes, I have 3 user accounts added, 2 of which have rights to administer the system. It is these two which I was attempting to switch between. The third account has never logged in yet.

I also have installed kde-desktop with the intent of trying out kde (though I have to say, for the first time ever I am really enjoying how the gnome environment works). I believe I also changed the default display manager at the same time, so that it is the kde login display which appears at startup. Just as I am typing this, I have a feeling this is the problem. I will test this out tonight.

---

### Post by mjm1231 on 2010-01-28
Yep, that was it. The display manager must be the same as the running desktop environment for Switch User to work.

---

