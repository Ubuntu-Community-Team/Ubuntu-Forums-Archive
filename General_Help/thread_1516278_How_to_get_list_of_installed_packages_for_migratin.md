---
title: "How to get list of installed packages for migrating between machines?"
date: 2010-06-23
forum: General Help
---

### Post by otakuj462 on 2010-06-23
Hi,

I'm migrating to a new Lucid Lynx machine, and I'd like to install all of the packages that I currently have installed on my old machine. Is there a way to query a list of all packages that are currently installed on a particular system, such that I could simply throw this list at apt-get on a new system?

Please let me know. Thanks,

Jake

---

### Post by Rubi1200 on 2010-06-23
See this:

[http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)

---

### Post by oldfred on 2010-06-23
If all your debs are current and you do not want to download all new files Rubi1200 way looks good. I also have seen recommendations for aptonCD but have not used it.

If installing to a newer version or downloading is not an issue.

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

I have used the commands
    dpkg --get-selections | grep -v deinstall > ubuntu-files
or
 dpkg --get-selections > ubuntu-files
 
I also periodically run the above command and save into /home so my backup has a list reasonably current. I used it to recreate my Karmic on my portable and for my upgrade to Lucid. The first time I used it was from my Jaunty which was upgraded in place for about 3 years. List had a lot of older programs, so be sure to houseclean in synaptic before running if that applies.

List with explanations of programs, not for reinstall
dpkg -l > ~/Desktop/installed_programs.txt

---

### Post by otakuj462 on 2010-06-23
Thanks, that was exactly what I needed to know!

Jake

---

