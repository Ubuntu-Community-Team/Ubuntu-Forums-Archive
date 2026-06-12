---
title: "how to run software updates from a terminal?"
date: 2010-11-16
forum: General Help
---

### Post by raymondvillain on 2010-11-16
Tried to update Ubunt Server (32 bit edition) from 7.10 to 9.10 and ran into graphics problems.  Would like to update again, but don't know how to do it from a command line.

Any suggestions?

---

### Post by mobilediesel on 2010-11-16
> **raymondvillain said:**
> Tried to update Ubunt Server (32 bit edition) from 7.10 to 9.10 and ran into graphics problems.  Would like to update again, but don't know how to do it from a command line.

Any suggestions?

To check for updates:
```
sudo apt-get update
```
To apply updates:
```
sudo apt-get upgrade
```
To upgrade to newer version:
```
sudo apt-get dist-upgrade
```

It won't go straight from 7.10 to 9.10. it will only go one version at a time except when you have an LTS version, then you can go from LTS to LTS.

---

### Post by shadow120 on 2010-11-16
```
sudo apt-get dist-upgrade
```

---

### Post by raymondvillain on 2010-11-16
If I run sudo apt-get update will it choose a server version automatically?

And to upgrade, do I need to specify the distribution?

Thanks for all the help.

---

### Post by mobilediesel on 2010-11-16
> **raymondvillain said:**
> If I run sudo apt-get update will it choose a server version automatically?

And to upgrade, do I need to specify the distribution?

Thanks for all the help.

sudo apt-get update will only update currently installed packages. sudo apt-get dist-upgrade does the actual upgrade to a new version and will generally only go to the following version number. So from 7.10 it would go to 8.04 then 8.10 then 9.04 then 9.10. although from 8.04 you should be able to to go 10.04 since that's the next LTS version.

---

### Post by blur xc on 2010-11-16
> **mobilediesel said:**
> sudo apt-get update will only update currently installed packages. sudo apt-get dist-upgrade does the actual upgrade to a new version and will generally only go to the following version number. So from 7.10 it would go to 8.04 then 8.10 then 9.04 then 9.10. although from 8.04 you should be able to to go 10.04 since that's the next LTS version.

Have you done that?  I don't think that's true...  I've done apt-get dist-upgrade before and it did not upgrade me to the next version.  It's just a more aggressive upgrade, that installs more stuff, removes things (could break stuff), etc..., etc..., new kernel version, whatever.

To upgrade to a new Ubuntu verison see this post:  [http://ubuntuforums.org/showpost.php?p=8322347&postcount=6](http://ubuntuforums.org/showpost.php?p=8322347&postcount=6)  

And I have done that before.  Oddly, it's a very slow process, much slower than (at least w/ my fios internet connection) downloading a new iso, burning it to a cd, and doing a clean install.

BM

---

### Post by raymondvillain on 2010-11-16
Thanks again for the help.  I've just applied all this knowledge to upgrade to version 9.10, but I can't get it to go to 10.04 or 10.10, which is available for downloading and burning on a CD.

Do I just keep on "sudo apt-get update" until I get 10.10 installed?

---

### Post by Chronon on 2010-11-16
> **mobilediesel said:**
> sudo apt-get **update** will only update currently installed packages. sudo apt-get dist-upgrade does the actual upgrade to a new version and will generally only go to the following version number. So from 7.10 it would go to 8.04 then 8.10 then 9.04 then 9.10. although from 8.04 you should be able to to go 10.04 since that's the next LTS version.
According to my understanding:
"update" gets the versions of currently installed packages (and their dependencies).  Once the list is updated you can "upgrade", which will install new versions of currently installed software.  "dist-upgrade" is required for any changes that involve installing new packages (or removing currently installed ones).

You can view the man page for "apt-get" for more details.

===========
raymondvillain: I would do a fresh install if possible.  It will almost certainly result in a cleaner system than trying to do so many upgrades.

---

### Post by mobilediesel on 2010-11-16
> **blur xc said:**
> Have you done that?  I don't think that's true...  I've done apt-get dist-upgrade before and it did not upgrade me to the next version.  It's just a more aggressive upgrade, that installs more stuff, removes things (could break stuff), etc..., etc..., new kernel version, whatever.

To upgrade to a new Ubuntu verison see this post:  [http://ubuntuforums.org/showpost.php?p=8322347&postcount=6](http://ubuntuforums.org/showpost.php?p=8322347&postcount=6)  

And I have done that before.  Oddly, it's a very slow process, much slower than (at least w/ my fios internet connection) downloading a new iso, burning it to a cd, and doing a clean install.

BM
I could definitely be wrong about it since I've never done that. I'm still running 8.04 and I'll probably just do a clean install of 10.10 or possibly 11.04. Yeah I'm totally lazy about upgrading things when everything's working.
> **raymondvillain said:**
> Thanks again for the help.  I've just applied all this knowledge to upgrade to version 9.10, but I can't get it to go to 10.04 or 10.10, which is available for downloading and burning on a CD.

Do I just keep on "sudo apt-get update" until I get 10.10 installed?
As Chronon says in the post before this one, a clean install is the best bet for not breaking things. Obviously that first requires backing up anything you don't want to lose.

---

