---
title: "upgrade to Natty doesn't work?!"
date: 2012-02-12
forum: General Help
---

### Post by qwertyjjj on 2012-02-12
I'm trying to upgrade from Meerkat to Natty but get an error through the update manager.
Is there another way to upgrade?

Preparing, I get this:
[I]Third party sources disabled
Some third party entries in your sources.list were disabled. You can re-enable them after the upgrade with the 'software-properties' tool or your package manager.
[/I]
then...

after "Setting new software channels", I get the following error:
[I][B]Could not determine the upgrade

An unresolvable problem occurred while calculating the upgrade:
Can not mark 'ubuntu-desktop' for upgrade

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu[/B][/I]

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

I unticked all my 3rd party repos in snyaptic and restarted the upgrade but same error.

---

### Post by dino99 on 2012-02-12
this "unresolvable problem occurred while calculating the upgrade" is all around this forum, you should get a few usefull comments.

---

### Post by 2F4U on 2012-02-12
While the problems are probably caused by some third-party software, you can try to upgrade through the alternate CD. The method is described here:

[https://help.ubuntu.com/community/NattyUpgrades](https://help.ubuntu.com/community/NattyUpgrades)

You don't even have to burn a CD (how to do that is also on that page).

---

### Post by qwertyjjj on 2012-02-12
got it started with the command line but now this:

Processing triggers for python-support ...
Errors were encountered while processing:
 ubuntu-desktop
Exception during pm.DoInstall():  E:Sub-process /usr/bin/dpkg returned an error code (1)

Could not install the upgrades

The upgrade has aborted. Your system could be in an unusable state. A
recovery will run now (dpkg --configure -a).

dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on software-center; however:
  Package software-center is not installed.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-desktop

Upgrade complete

The upgrade has completed but there were errors during the upgrade
process.

To continue please press [ENTER]

---

### Post by bluexrider on 2012-02-12
I have always done a fresh install because of upgrade issues between releases. I recommend backing your files and any applications you may want to save and then resort to a FRESH install. AFAIK this is the way to go......

---

### Post by qwertyjjj on 2012-02-12
> **bluexrider said:**
> I have always done a fresh install because of upgrade issues between releases. I recommend backing your files and any applications you may want to save and then resort to a FRESH install. AFAIK this is the way to go......

Might be difficult as I had a lot of saved links on the gnome panel and other stuff.

So, if I put Natty on a CD, how do I copy all my files back after?
That includes any files in apache folders, saved settings for porgrams I installed, etc.?

The computer has now throttled back down to 800, which is a problem I first had when using Meerkat.

---

### Post by bluexrider on 2012-02-12
For applications I use 'aptoncd'. You can save those precious applications you installed from other PPA's and re-install them because it is configured in .DEB fairly straightforward. 

Make a copy of your sources.list and /var/lib/apt/lists folder with its contents.

Back up your /Home folder, this is where all your personal configurations are set. I have my /Home folder on its separate partition. I advise you to consider doing the same. Having /home on a separate partition makes it  very easy to wipe out and reinstall Linux without losing any of your data. 

Good information as to what to backup is here [http://www.desktoplinux.com/articles/AT2280165098.html?regen=yes&display=yes](http://www.desktoplinux.com/articles/AT2280165098.html?regen=yes&display=yes)

The upgrade you intend does not include Gnome 3 therefore your settings may remain the same once the OS is installed and you point Ubuntu at your /Home folder.

Other information from Ubuntu as to how to backup your system  
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by qwertyjjj on 2012-02-13
> **bluexrider said:**
> For applications I use 'aptoncd'. You can save those precious applications you installed from other PPA's and re-install them because it is configured in .DEB fairly straightforward. 

Make a copy of your sources.list and /var/lib/apt/lists folder with its contents.

Back up your /Home folder, this is where all your personal configurations are set. I have my /Home folder on its separate partition. I advise you to consider doing the same. Having /home on a separate partition makes it  very easy to wipe out and reinstall Linux without losing any of your data. 

Good information as to what to backup is here [http://www.desktoplinux.com/articles/AT2280165098.html?regen=yes&display=yes](http://www.desktoplinux.com/articles/AT2280165098.html?regen=yes&display=yes)

The upgrade you intend does not include Gnome 3 therefore your settings may remain the same once the OS is installed and you point Ubuntu at your /Home folder.

Other information from Ubuntu as to how to backup your system  
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

I tried to reinstall from backup tar and that royally messe dup my grub.
So, I did a fresh install of Ocelot.
How can I copy the home folder from the tarball to the home on computer?
I tried:
sudo tar - xvpzf /media/External_HD/backup.tar.gz /home -C /home but it just hangs

Also, I have files in var/www and I need all my mysql data too.

---

### Post by bluexrider on 2012-02-13
short tutorial on how to backup/restore [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

I really cannot answer specific questions about tar balls. I do not utilize that type of backup.

Just realized from your statement that you went to Ocelot. Now you may NOT retain those settings once restored because now you are into Gnome 3.

---

### Post by qwertyjjj on 2012-02-13
> **bluexrider said:**
> short tutorial on how to backup/restore [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

I really cannot answer specific questions about tar balls. I do not utilize that type of backup.

That's the tutorial that messed up my system in the first place.

---

### Post by bluexrider on 2012-02-13
BTW are you dual booting or using WUBI?

---

### Post by qwertyjjj on 2012-02-13
> **bluexrider said:**
> BTW are you dual booting or using WUBI?

No, only install is Ubuntu.
When I backed up I booted from a lIve CD.

---

### Post by bluexrider on 2012-02-13
Good that will make things a little easier.

Is your backup on an external hard drive or at least a separate partition?

---

### Post by qwertyjjj on 2012-02-13
> **bluexrider said:**
> Good that will make things a little easier.

Is your backup on an external hard drive or at least a separate partition?

external usb, /media/External_HD when booted with live cd
I can get access to the home and var folder in the tar but not quite sure whether that will restore all my software in Ocelot.
I thought I could reinstall the software as needed but if I load all the settings now from the backup then that might mess things up when I install the software later?

---

### Post by bluexrider on 2012-02-13
> **qwertyjjj said:**
> external usb, /media/External_HD when booted with live cd
I can get access to the home and var folder in the tar but not quite sure whether that will restore all my software in Ocelot.
I thought I could reinstall the software as needed but if I load all the settings now from the backup then that might mess things up when I install the software later?

If you are going to keep Ocelot or not, this is what I would do. Not to say this is everyone's 'cup of tea' but it works for me. My partitioning 

HD 500Gb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3917    31457280   83  Linux
/dev/sda2   *        3917        7833    31455232   83  Linux
/dev/sda3           38377       60802   180129793    5  Extended
/dev/sda4  /Home 7833       38377   245342208   83  Linux
/dev/sda5           38377       60219   175446016   83  Linux
/dev/sda6           60219       60802     4682752   82  Linux swap / Solaris

---

### Post by qwertyjjj on 2012-02-13
> **bluexrider said:**
> If you are going to keep Ocelot or not, this is what I would do. Not to say this is everyone's 'cup of tea' but it works for me. My partitioning 

HD 500Gb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3917    31457280   83  Linux
/dev/sda2   *        3917        7833    31455232   83  Linux
/dev/sda3           38377       60802   180129793    5  Extended
/dev/sda4  /Home 7833       38377   245342208   83  Linux
/dev/sda5           38377       60219   175446016   83  Linux
/dev/sda6           60219       60802     4682752   82  Linux swap / Solaris

Sorry, do you mean install the backed up home as a new partition?
Can;t I just copy all the files in home to new home directory?

---

### Post by bluexrider on 2012-02-13
Sure. You can. 

I was trying to point out that if you had your /Home on a separate partition, god forbid, if your system got messed up again you would still have your /Home/USER/all-my-personal-files-and-settings intact.

---

### Post by qwertyjjj on 2012-02-13
> **bluexrider said:**
> Sure. You can. 

I was trying to point out that if you had your /Home on a separate partition, god forbid, if your system got messed up again you would still have your /Home/USER/all-my-personal-files-and-settings intact.

Thanks - I think I'll try this first.
How can I copy the following tarred folders to the new installation of ocelot?
/home
/var/www
/usr/lib/mysql - is this the only folder I need for mysql?

If I copy home in that way, should I install the software first? eg Thunderbird should be installed before I copy my profile over?

---

### Post by bluexrider on 2012-02-13
Again from post #9
I have not used TAR to back up or restore. That said. I would think it would be fairly straight forward.

where as:

tar -xvpzf /where_your_backup_is/backup.tar.gz -C [COLOR=Red]/home

this will overwrite EVERY file in your /home folder


[COLOR=Black]I cannot say what result this will have on your settings. 

HOPE IT WORKS FOR YOU.[/COLOR]

[/COLOR]

---

