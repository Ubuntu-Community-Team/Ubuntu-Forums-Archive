---
title: "update fiirefox"
date: 2006-05-10
forum: General Help
---

### Post by 1337hacker on 2006-05-10
how do i update firefox from the default firefox on breezy?

i did sudo apt-get install firefox
it says i have the newest version but i have version 1.0something

---

### Post by oyvindaa on 2006-05-10
EDIT: double post, sorry.

---

### Post by oyvindaa on 2006-05-10
You can update it from Automatix. Make sure you back up your bookmarks though, and it will install all plugins needed.

[http://easylinux.info/wiki/Ubuntu#Installing_additional_software_.28Automatix.29](http://easylinux.info/wiki/Ubuntu#Installing_additional_software_.28Automatix.29)

---

### Post by openmind on 2006-05-10
That's because you're using the one from Breezy's Repos. You can install Firefox independently of the repos [Here.]("https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28Firefox%29")

You still have to update as root, but that's not so hard.

---

### Post by ampop on 2006-05-10
I installed Firefox 1.5 and I had some problems:
[http://www.ubuntuforums.org/showthread.php?t=171114](http://www.ubuntuforums.org/showthread.php?t=171114)
[http://www.ubuntuforums.org/showthread.php?t=171696](http://www.ubuntuforums.org/showthread.php?t=171696)

The problem was solved here:
[http://www.ubuntuforums.org/showthread.php?t=171696](http://www.ubuntuforums.org/showthread.php?t=171696)

---

### Post by openmind on 2006-05-10
[quote=ampop]I installed Firefox 1.5 and I had some problems:
[http://www.ubuntuforums.org/showthread.php?t=171114]("http://www.ubuntuforums.org/showthread.php?t=171114")
[http://www.ubuntuforums.org/showthread.php?t=171696]("http://www.ubuntuforums.org/showthread.php?t=171696")

The problem was solved here:
[http://www.ubuntuforums.org/showthread.php?t=171696]("http://www.ubuntuforums.org/showthread.php?t=171696")[/quote] Yes, Ubuntu needs some Library files with it's packaged Firefox, so it's not a good idea to delete the packaged version, just install the new one and link to it.

I'm running 1.5.0.3 and it works great. It didn't want to load some extensions, but I force them with Nightly Tools and everything's cool.

---

