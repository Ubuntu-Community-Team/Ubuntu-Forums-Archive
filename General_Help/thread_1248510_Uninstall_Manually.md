---
title: "Uninstall Manually"
date: 2009-08-24
forum: General Help
---

### Post by jesuisbenjamin on 2009-08-24
Some time ago i downloaded Google Earth. The whole thing doesn't work and i don't want to make it work any more.
Although i found threads on how to install manually Google Earth, i could not find anything on how to uninstall.

So how can i uninstall manually a package i installed manually? (because it doesn't show up in my add/remove applications)

---

### Post by sahabcse on 2009-08-24
#sudo apt-get purge googleearth
or

#sudo apt-get remove googleearth

for more info about package management pls follow below url

[http://ubuntulinux.co.in/package-installation-over-command-propmpt.php](http://ubuntulinux.co.in/package-installation-over-command-propmpt.php)

---

### Post by P4man on 2009-08-24
One reason why you want to stick to the repositories whenever possible. Google earth isn't in the default repositories, but it is available in the medibuntu repo's:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If you had installed from there, it would have been a lot easier.

Anyway, to get rid of it now, im basing myself upon this thread:
[http://ubuntuforums.org/showthread.php?t=208254](http://ubuntuforums.org/showthread.php?t=208254)

(last post). 

My shorter and easier version:

Open a terminal
type ```

cd google-earth
sudo ./uninstall
```

---

### Post by jesuisbenjamin on 2009-08-24
That was nice. Thanks. What was the ./ for in the command?

---

### Post by P4man on 2009-08-24
./ means current directory.
It may seem odd if you're used to DOS, but in linux, the current directory is NOT in the path. So if you'd execute "uninstall" it would look everywhere in the path, but not the directory you are currently in.

---

