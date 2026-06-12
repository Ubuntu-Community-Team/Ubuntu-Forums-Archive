---
title: "backup list of installed apps"
date: 2010-06-23
forum: General Help
---

### Post by jesuisbenjamin on 2010-06-23
Hi there,

I came across a thread the other day and can't find it again. It answered the following question:

How to make a backup of installed applications? 

In the answer there was some program which would create a file listing all installed apps and store it in /home. On updating the OS or re-installing, the file would be used to re-install all apps listed.

Does it ring a bell? Anyone?

Thanks.
B.

---

### Post by giddyup306 on 2010-06-23
There is a plugin for Firefox called Umarks.  I'm not 100% how it works (or if it's the same program you're thinking of).

---

### Post by Rubi1200 on 2010-06-23
This?

[http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)

---

### Post by jesuisbenjamin on 2010-06-23
> **Rubi1200 said:**
> This?

[http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)

yes! thanks! :)

---

### Post by Rubi1200 on 2010-06-23
No problem!

):P

---

### Post by oldfred on 2010-06-23
If installing to a new version of Ubuntu, you may not want to reinstall older debs as newer versions are available.

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

---

