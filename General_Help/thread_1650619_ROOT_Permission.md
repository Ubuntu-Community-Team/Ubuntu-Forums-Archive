---
title: "ROOT Permission"
date: 2010-12-21
forum: General Help
---

### Post by spindler on 2010-12-21
I cannot save a file in my user directory.  I also cannot rename the file to make a copy of it.   My ROOT user name has Administrator privileges and the file is owned by the ROOT user.  It also has the same group that my ROOT user has. 

The only thing different is I changed the owner of the folder to match my BASIC user so that BASIC user can read and write to the directory.   The BASIC user is actually my working user that I use so I can limit the privileges for daily tasks. 

I want to allow my ROOT user the ability to save and rewrite any file anywhere on the system.    How do I allow the root user full control of coping a file from any directory to any directory or renaming a file?

Thanks,

Spindler

---

### Post by efflandt on 2010-12-21
When you say ROOT are you referring to the actual user called "root", or the admin user that you configured when you first installed?  If you want to do something you do not have permission to do you have to put **sudo** and space before the command.  But then you may need to watch directory/file ownership and might need to **sudo chown** and/or sudo chgrp the file, or the normal user may not be able to alter it.

You are not really suppose to run as "root" unless you really know what you are doing.  And then it should only be as long as necessary to do whatever group of commands you need to do as root.  Although, running as an admin user is not a problem, because you still need to use sudo to do anything that has to be done as root.

---

### Post by spindler on 2010-12-22
Well....I am not using the ROOT user.  I have a user that is an administrator.

I have used sudo before with other commands to get work done.   I never have done this with vi or gedit before.  Of course once i tried i was able to edit my file.

Thanks a lot for helping me.  I am good to go now. 

Spindler.

---

### Post by Vectorferret on 2010-12-22
> **spindler said:**
> Well....I am not using the ROOT user.  I have a user that is an administrator.

I have used sudo before with other commands to get work done.   I never have done this with vi or gedit before.  Of course once i tried i was able to edit my file.

Thanks a lot for helping me.  I am good to go now. 

Spindler.
If using gedit, use gksu instead of sudo. It's more secure for graphical applications. (You may know that already, just giving a heads up.) vi or nano are just fine with normal sudo or using sudo -i to actually become root in that shell (extreme caution).

---

