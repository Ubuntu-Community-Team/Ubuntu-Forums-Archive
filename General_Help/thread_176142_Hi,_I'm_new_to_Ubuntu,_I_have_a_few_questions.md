---
title: "Hi, I'm new to Ubuntu, I have a few questions"
date: 2006-05-14
forum: General Help
---

### Post by Koori23 on 2006-05-14
Hi, I bought Ubuntu with a book at Borders last night. The book saved me hours of making stupid mistakes.. Trust me, without that book "Ubuntu for Beginners", I would have been somewhat lost.

I do have a few questions though..

Okay, is Dapper in RC stages still? When it's deemed stable, will I just be able to click "Software update" like normal?

Why isn't Opera listed anywhere, is it because it's proprietary?

Is the Firestarter Firewall program just a front end to IP Tables?

When I allocated space to Ubuntu, I only allocated 47GB.. I have a 200GB disk, with only 50GB allocated to XP.  So, I have about half the harddrive unallocated, is it possible to move my /home folder to a different logical drive without too much trouble?

Since Ubuntu 5.10 uses Firefox 1.0.8 and OOO.org 1.9, what kind of security risks does this pose? Updated versions of each are on vendor websites.

Honestly, I was only going to "Play" with Linux but, after 3 hours of playing around.. I have it up and running to the point that I don't even need Windows for my day to day work.. Many thanks to the community for this great work.

---

### Post by louis_nichols on 2006-05-14
[QUOTE=Koori23] Hi, I bought Ubuntu with a book at Borders last night. The book saved me hours of making stupid mistakes.. Trust me, without that book "Ubuntu for Beginners", I would have been somewhat lost.

I do have a few questions though..

Okay, is Dapper in RC stages still? [/QUOTE]
Yes it is. Scheduled to be released on 1st of June.

[QUOTE=Koori23] When it's deemed stable, will I just be able to click "Software update" like normal?[/QUOTE]

not quite. You have to edit the file with repo addresses (/etc/apt/sources.list) to point to the dapper repo, then run the command

```
sudo apt-get update && sudo apt-get dist-upgrade
```

[QUOTE=Koori23]Why isn't Opera listed anywhere, is it because it's proprietary?[/QUOTE]yes. not only does opera's licence prevent it from being distributed, but closed source is not compatible with ubuntu's filosophy. it can be installed pretty easily, though.

[QUOTE=Koori23]Is the Firestarter Firewall program just a front end to IP Tables?[/QUOTE]yes it is. anyways, the default ubuntu install doesn't really need you to configure a firewall, since it has no listening daemons.

[QUOTE=Koori23]When I allocated space to Ubuntu, I only allocated 47GB.. I have a 200GB disk, with only 50GB allocated to XP.  So, I have about half the harddrive unallocated, is it possible to move my /home folder to a different logical drive without too much trouble?[/QUOTE]
sure. Just format it as ext3 or reiserfs, then backup your home partition (info [here]("https://wiki.ubuntu.com/BackupYourSystem") - just adapt it to contain your /home folder only). After this, add this line to the file /etc/fstab:

```
/dev/<path to partition> /home           <ext3 or reiserfs> defaults        0       2
``` and reboot. After reboot, login and restore the backup you made (best done from terminal interface). [COLOR="Red"]NOTE[/COLOR]: make sure the backup you make is not stored under your home folder and, after making this backup, before reboot, you completely wipe clean the folder /home.

[QUOTE=Koori23]Since Ubuntu 5.10 uses Firefox 1.0.8 and OOO.org 1.9, what kind of security risks does this pose? Updated versions of each are on vendor websites.[/QUOTE] Each version of the two pieces of software is updated. Ff 1.5 is a different version of the of Firefox, but this doesn't mean that Ff 1.0.x becomes outdated. It gets the security updates for 18 months after Breezy's release. You can install ff 1.5 easily tho. Info [here]("https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28new%29%7C%28firefox%29") 

[QUOTE=Koori23]Honestly, I was only going to "Play" with Linux but, after 3 hours of playing around.. I have it up and running to the point that I don't even need Windows for my day to day work.. Many thanks to the community for this great work.[/QUOTE]I know what you mean! Wellcome to ubuntu! :)

EDIT: small correction

---

