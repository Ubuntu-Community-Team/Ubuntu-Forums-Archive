---
title: "Is There any &quot;System Restore&quot; things in Ubuntu?"
date: 2011-02-01
forum: General Help
---

### Post by aldee96 on 2011-02-01
Hi, i just realised how useful system restore is, so i really want to have it on my ubuntu. is there any apps for it or there's a built in apps? i think it's very useful if there's an accident

---

### Post by garvinrick4 on 2011-02-01
#No there is nothing to restore file system to a previous date and or time in linux that I have ever heard or read about.
#I would say learn how to use a Live Cd (install Cd using Try Ubuntu) and the chroot command which puts you into root
of a install while in live Cd.

---

### Post by Carson5696 on 2011-02-01
Here you go: [https://blueprints.launchpad.net/ubuntu/+spec/system-restore;](https://blueprints.launchpad.net/ubuntu/+spec/system-restore;))

---

### Post by tredegar on 2011-02-01
[Back In Time]("http://freshmeat.net/projects/backintime") ?

It is in the ubuntu repositories.

---

### Post by aldee96 on 2011-02-02
> **Carson5696 said:**
> Here you go: [https://blueprints.launchpad.net/ubuntu/+spec/system-restore;](https://blueprints.launchpad.net/ubuntu/+spec/system-restore;))

the link is broken it's not working

---

### Post by aldee96 on 2011-02-02
> **tredegar said:**
> [Back In Time]("http://freshmeat.net/projects/backintime") ?

It is in the ubuntu repositories.


for the file backup i put it in another partition so i don't need the backup. i'd prefer the AptOnCd for the application backup, all that i want is sytem backup that restore the whole system settings so if i did any mistakes, it's not a problem

---

### Post by JOHNNYG713 on 2011-02-02
> **Carson5696 said:**
> Here you go: [https/blueprints.launchpad.net/ubuntu/+spec/system-restore  ]("https://blueprints.launchpad.net/ubuntu/+spec/system-restore;")
[;]("https://blueprints.launchpad.net/ubuntu/+spec/system-restore;")) 

 The link is broken but it doesn't matter, ! This is a Blueprint and is not yet available, but should be soon !! at least they are working on it !! :p

---

### Post by Elfy on 2011-02-02
> **aldee96 said:**
> the link is broken it's not working

[https://blueprints.launchpad.net/ubuntu/+spec/system-restore](https://blueprints.launchpad.net/ubuntu/+spec/system-restore)

4 years old and not looking likely ...

---

### Post by mastablasta on 2011-02-02
> **aldee96 said:**
> for the file backup i put it in another partition so i don't need the backup. i'd prefer the AptOnCd for the application backup, all that i want is sytem backup that restore the whole system settings so if i did any mistakes, it's not a problem
 
 
I think Linux mint backup tool has an option to save/bacup system settings (the other option is to back up data). They developed the tool because their system upgrade is done through clean install. 
[http://community.linuxmint.com/tutorial/view/2](http://community.linuxmint.com/tutorial/view/2)
 
 
you can use PPA to install it i believe: [http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html](http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html)

---

### Post by drewsus on 2011-02-02
Remastersys?

---

### Post by diamoph on 2011-02-12
I've just been using [ubuntu tweak]("http://ubuntu-tweak.com/") to make quick, easy backups of settings. Takes seconds to backup, uses next to no space, has never failed to restore desktop and programs.

Keep in mind this does not backup files and programs properly, just settings so that any bad system changes can be removed without affecting file structure. If you need a proper backup or image don't rely on this program, just better for quick recovery.


The settings to backup your system can be found on the left side under "Desktop Recovery", you must backup "Desktop" "Applications" and "Settings". Unfortunately there isn't any option to do this automatically, but if you do it after you feel your system is stable that should be enough.

---

