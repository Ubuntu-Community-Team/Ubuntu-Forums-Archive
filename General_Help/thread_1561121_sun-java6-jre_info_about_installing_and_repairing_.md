---
title: "sun-java6-jre info about installing and repairing mistakes"
date: 2010-08-25
forum: General Help
---

### Post by COKEDUDE on 2010-08-25
[IMG]http://i255.photobucket.com/albums/hh133/COKEDUDEUSF/configuring_sun-java6-jre.jpg[/IMG]

In case you are not aware of how to click the ok button you need hit the tab button then hit enter. I did not know this and messed up the package. In order to fix this problem it is quite tricky so read on. It is not as simple as deleting and reinstalling as you would hope and think. 

You get this nice message. The reason this happens is because there is a lock file that was not properly removed. You will have to manually remove the lock file. 
```
sudo apt-get upgrade -f --no-download dist-upgrade sun-java6-jre
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

[http://ubuntuforums.org/showthread.php?t=631128&highlight=lock](http://ubuntuforums.org/showthread.php?t=631128&highlight=lock)
These 2 commands remove the lock files. 
```
sudo rm /var/lib/dpkg/lock  -> Deletes the lock file
sudo rm -r /tmp/*  -> Deletes what is inside the /tmp directory, but be careful to use /tmp/* not /tmp
```

These 2 commands fix and reinstall java for you. 
```
sudo dpkg --configure -a   -> Tries to fix the dpkg system
sudo apt-get install -f  -> Tries to fix the apt-get system
```

This method is untested. I know what I said above works. 
[http://ubuntuforums.org/showthread.php?t=709160&highlight=lock](http://ubuntuforums.org/showthread.php?t=709160&highlight=lock)

---

