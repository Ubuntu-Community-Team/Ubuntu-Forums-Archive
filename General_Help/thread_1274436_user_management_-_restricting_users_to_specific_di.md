---
title: "user management - restricting users to specific directories."
date: 2009-09-24
forum: General Help
---

### Post by bobonthenet on 2009-09-24
[LIST=1]
[/LIST]I need some help with user management and my numerous google searches are only turning up lists of commands.  Here is exactly what I'm trying to do:

I have already created a new user (ex. "newuser") and given it the home directory /home/newuser.  What I want to do is restrict that users access so that it can only see what is in that personal home directory and nothing else unless a symbolic link is created within that home directory.  Or more specifically I would like to allow that user to have access to /var/www/newuser which would be seen as something like "webdir" within their own directory.  I know how to create the links but I do not know how to restrict the users access in this way.  I also want them to have read/write access to anything located within a subdirectory contained in their personal home or linked directory.

I hope that was clear, even as I write this I'm figuring out bits and pieces of what I hope to accomplish but I haven't seen a clear guide on how to do everything I want here.

---

### Post by michy99 on 2009-09-24
Maybe this tutorial can be of help:

[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

---

