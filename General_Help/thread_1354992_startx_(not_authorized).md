---
title: "startx (not authorized)"
date: 2009-12-14
forum: General Help
---

### Post by android6011 on 2009-12-14
When I do startx I get

"X: user not authorized to run the X server, aborting."

I did dpkg-reconfigure x11-common and see that Console Users Only is selected. 

I also see an option for anybody but I assume that would be unsafe as I am also using this as a nas computer etc.

Any suggestions?

---

### Post by solar george on 2009-12-14
According to 
```
man Xwrapper.config
```

       allowed_users
              may  be set to one of the following values: rootonly, console, or anybody.  rootonly indicates that only the root user may start the X server; console indicates that root, or any
              user whose controlling TTY is a virtual console, may start the X server; and anybody indicates that any user may start the X server.

So you've got the choice between allowing local users (thats what you've got selected), root only or everyone.

---

