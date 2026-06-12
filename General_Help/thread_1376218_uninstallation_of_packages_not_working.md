---
title: "uninstallation of packages not working?"
date: 2010-01-08
forum: General Help
---

### Post by pythonscript on 2010-01-08
Someone posted this command in another thread, and I'm wondering how to fully take advantage of it:

```
dpkg -l | grep "^rc" | awk "{print \$2}" | xargs sudo apt-get purge -y
```

I presume that this command removes all residual config files, but when I run it, I get messages saying that the packages are not installed, so they can't be removed. How can I remove these configuration files? In my case, the list is about 120 packages long, and I'd really like to free up this space. Thanks!

---

### Post by warfacegod on 2010-01-08
```
sudo apt-get auto remove
```


```
sudo apt-get install localepurge
```


Assuming your native language is English, check the _en_ languages you shouldn't need the rest.


Here's another way to get some space back.

[http://ubuntuforums.org/showthread.php?t=820804&highlight=cover+manager]("http://ubuntuforums.org/showthread.php?t=820804&highlight=cover+manager")

And remember, always be careful.

---

### Post by 3rdalbum on 2010-01-08
> **pythonscript said:**
> Someone posted this command in another thread, and I'm wondering how to fully take advantage of it:

```
dpkg -l | grep "^rc" | awk "{print \$2}" | xargs sudo apt-get purge -y
```

I presume that this command removes all residual config files, but when I run it, I get messages saying that the packages are not installed, so they can't be removed. How can I remove these configuration files? In my case, the list is about 120 packages long, and I'd really like to free up this space. Thanks!

If you're using Ubuntu Desktop, you can do this in Synaptic. Go to the Status button and click on "Not Installed (residual config)". Select everything that's listed in the right pane, right-click and choose "Mark for Complete Removal". Click Apply.

Congratulations, you've now freed up 500kb worth of config files.

---

### Post by pythonscript on 2010-01-09
> **3rdalbum said:**
> If you're using Ubuntu Desktop, you can do this in Synaptic. Go to the Status button and click on "Not Installed (residual config)". Select everything that's listed in the right pane, right-click and choose "Mark for Complete Removal". Click Apply.

Congratulations, you've now freed up 500kb worth of config files.

Thanks for the tip; I never used synaptic for package management (working from the terminal most of the time), but this seems to be the best way of removing these files.

---

