---
title: "Removing unused dot (hidden) folders in the home directory!"
date: 2010-06-01
forum: General Help
---

### Post by Rytron on 2010-06-01
Hi.
If someone manually partitions their home and root drives and overtime they end up with a lot of dot folders (.burgerspace for example) in their home directory. Is there a quick way to get rid of all the dot folders whose program is no longer installed? For example if I completely removed BurgerSpace in Synaptic, the .burgerspace folder would remain. Overtime this can lead to many folders that are surplus to requirements.

---

### Post by dino99 on 2010-06-01
cant answer directly but i use gconf-cleaner and bleachbit (as admin) to make room time to time

---

### Post by ajgreeny on 2010-06-01
You can get rid of any of those hidden folders in your home folder or partition, but don't forget that should you want to reinstall the program in future, all the configuration details in there will be lost and you may have to set everything up again.

Perhaps best to back them up to a separate disk and then remove those folders, just in case.

On a general note, you can remove anything you want in your own home, without stopping the computer from working; it just won't have any of your files any more.

---

### Post by obscurant1st on 2010-06-01
i think that purge option while removing an application via apt-get will work! :)

---

### Post by amauk on 2010-06-01
Open Synaptic
Bottom left, there's some buttons (for specifying how packages are grouped)
click "Status"
click "Not installed (residual config)"
this shows all packages not installed, but have stuff left over (config files, library dependancies not used by anything else, etc.)

You can highlight them all, and do a complete removal (AKA purge)

*edit*
typo

---

### Post by ajgreeny on 2010-06-01
No, sorry amauk and obscurant1st, but the purge option, or completely remove in synaptic does not remove anything from your home folder.  It removes any configs from /etc and other filesystem folders but not /home.

You will have to remove all of those manually.

---

### Post by acrazyplayer on 2010-06-01
Yup will have to remove them manually. The easiest way would be to normally delete them unless of course you need permission to do so in which case just use this in the terminal "sudo nautilus" then you can delete to your hearts content.

---

### Post by dFlyer on 2010-06-01
from the command line you can remove a folder with rm -rf (folder name). just be very careful with the rm -rf command as you can wipe all folder with a (.* *). I think you can also do it from file browser. Select hidden files and right click on folder you want to delete and select delete or move to trash.

---

### Post by Rytron on 2010-06-01
Thanks guys. Manually deleting looks like the best option.

---

### Post by dtmbmw325i on 2010-06-01
I just want to add a word of caution, something I missed once.  If you are using sudo nautilus to remove folders you must remember to empty the trash for ROOT.  I ended up with a full hard drive and didn't know why and found this.  Just thought I would add a word of caution.

---

### Post by Rytron on 2010-06-02
> **dtmbmw325i said:**
> I just want to add a word of caution, something I missed once.  If you are using sudo nautilus to remove folders you must remember to empty the trash for ROOT.  I ended up with a full hard drive and didn't know why and found this.  Just thought I would add a word of caution.

Thank you dtmbmw325i. That can easily be overlooked. Cheers.

Would the command be something like this?

# Method 1
```
sudo rm -rf ~/.local/share/Trash/files/*
```
or
# Method 2
```
sudo rm -Rf ~/.Trash/*
```

Update: This root trash can be viewed like so:
```
gksudo nautilus /root/.local/share/Trash/
```

---

