---
title: "Recursive File Permissions"
date: 2010-04-16
forum: General Help
---

### Post by christguard on 2010-04-16
Hey guys,
   My buddy and I are starting a website based of a linux server he built. We have just learned about file permissions and I understand that system now (Felt like I was going back to college learning that, lol! Well, most of my linux experience has been that way! hehe). Anywho, we are hosting our site out of the /var/www directory, and i changed the group owner of /www/ and the permissions. worked fine. The problem is, every new file I make (or ssh over) has limited permissions and I have to go change them manually. Is there a way to do this recursively (like the -R option in chgrp) or better yet, tell linux I want every file in this folder to have set permissions and ever file put in thereafter? THanks!

---

### Post by gmargo on 2010-04-16
The chmod(1) command has an -R option, just like chgrp(1).  However, you probably don't want to use it since you probably want to apply different permissions to directories vs files.

Here are three simple find(1) commands that will change the directories vs files permissions.

```

# Assume 755 for directories, 644 for files.
cd /var/www                 # or whatever directory
find . -type d -print -exec chmod 755 {} \;        # Changes all directory permissions

find . -type f -print -exec chmod 644 {} \;        # Changes all file permissions

# What if you have CGI files that need execute permissions, in the cgi-bin directory?
find cgi-bin -type f -print -exec chmod 755 {} \;


```

---

