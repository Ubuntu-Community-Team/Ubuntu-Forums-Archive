---
title: "&quot;porting&quot; ubuntu settings to new install"
date: 2010-11-05
forum: General Help
---

### Post by xieon on 2010-11-05
I doubt there's already a program like this, but it would be nice if you could port all the settings & installed packages from one installation of ubuntu to another.

I'm slowly going through my computers and removing files/backing up what I need, and reformatting/partitioning disks then reinstalling OS's. (dual boot windows/ubuntu).

With my laptop there was little problem, I backed up the entire harddrive to external, then did clean install, and have been working since, but my desktop has significant more space/things to do. So while I'm working out everything, I'm still using ubuntu, and have a ton of customizations/settings/packages.

Is there any easy way I could move them to a new installation of ubuntu? Could re-install, then boot from live cd, and paste old files over new installation. Although I doubt it's that simple, be nice if there was a program that made a list of all extra packages, exported to a file, then could import/install lists of packages.

Since it's doubtful I'll get to move packages, should I just copy over the home folder, then manually reinstall all the packages?

---

### Post by ajgreeny on 2010-11-05
The biggest saving will probably be to copy everything in /var/cache/apt/archives from your backup of the disk, and then copy the .deb files from that to your new installation's same folder.  You could try copying folders such as /etc where many configuration details are stored, in totality, but I am not sure that will work.

The /var/cache/apt/archives will save a lot of downloading of packages when you come to reinstall all the packages you added.

---

### Post by ironic.demise on 2010-11-05
why not copy all of the directories from /home/$USER beginning with .?

[http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)

---

### Post by ajgreeny on 2010-11-05
I was assuming that would be done without fail.  Perhaps I should not make such assumptions.

All the configurations for applications in your /home, are hidden, starting with . and will not show in a linux file manager unless you enable such a view.

---

### Post by ironic.demise on 2010-11-07
> **ajgreeny said:**
> I was assuming that would be done without fail.  Perhaps I should not make such assumptions.

All the configurations for applications in your /home, are hidden, starting with . and will not show in a linux file manager unless you enable such a view.

pressing ctrl+h in nautilus will show them
or ls -la in terminal

---

