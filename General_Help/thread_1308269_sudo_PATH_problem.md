---
title: "sudo PATH problem"
date: 2009-10-31
forum: General Help
---

### Post by fstephens on 2009-10-31
I can't execute programs in the user's bin directory that require sudo. I just get a "command not found" error. I can execute other commands(scripts) in the ~/bin directory that don't require root privileges.
I have tried lots of things with the sudoers file, .profile, /etc/profile and on and on without a solution.
"env" show the path with ~/bin, "sudo env" does not.

This always worked before.
I suspect it has something to do with my changing the default username, but now I am unsure what the problem really is.

Ubuntu 9.04 Live CD built from scratch. BASH shell
Any help appreciated!
Thanks

---

