---
title: "Permissions Help!"
date: 2010-12-22
forum: General Help
---

### Post by wafflesausage on 2010-12-22
I recently bork'd my FreeBSD (i know that it's not Ubuntu, but let's just pretend, the solution should be the same anyway) install. About 5 days prior, I made a backup in tar form and did not preserver permissions. I reinstalled the system and everything works as expected if it's run as root, but other users have problems with permissions. When a non-root user tries to run startx, they get an error message saying ```
xauth: creating new authority file /home/user/.serverauth.5193

Fatal server error:
Cannot move old log file (/var/log/Xorg.0.log" to "/var/log/Xorg.0.log.old"

Please consult the The X.Org Foundation support
at http://wiki.x.org
 for help

giving up
xinit: Permission denied (errno 13): unable to connect to X server
xinit: No such process (errno 3): Server error.
```

Does anyone have any idea how one would go about fixing this? Are there any directories that I should also chmod?
Thank you all in advance for any help. It will be GREATLY appreciated!

---

