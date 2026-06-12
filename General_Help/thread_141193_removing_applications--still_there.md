---
title: "removing applications--still there"
date: 2006-03-07
forum: General Help
---

### Post by closeyourwindows on 2006-03-07
When I go to remove application using apt-get remove filename I still have pieces of the app all over the place.  I can do a locate for that app that I just removed and I can find it in /usr and in /bin etc....  is there a way to completley remove the app and all of its tracks in one nice command.  it gets tiresome to locate the file and going to each directory and removing it manually. I have a 12 GB hard drive on the laptop and like to try out new apps and it is quickly filling up.

---

### Post by Xian on 2006-03-07
$ sudo apt-get remove --purge <packagename>

---

### Post by aysiu on 2006-03-07
I'm sure there's a command-line way to do it, but I don't know what it is. In Synaptic Package Manager, mark it for **complete** removal; then, click Apply.

---

### Post by closeyourwindows on 2006-03-07
```
nate@uborama:~$ sudo apt-get remove --purge gtkpod
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  gtkpod*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 2040kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ...
dpkg: serious warning: files list file for package `mythtv-frontend' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mythtv-database' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mythtv-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mythtv-backend' missing, assuming package has no files currently installed.
130347 files and directories currently installed.)
Removing gtkpod ...
Purging configuration files for gtkpod ...
nate@uborama:~$ locate gtkpod
/usr/share/gnome-app-install/gtkpod.desktop
/home/nate/.icons/SnowIsh-1.0/scalable/apps/gtkpod.svg
/home/nate/.gtkpod
/home/nate/.gtkpod/prefs
nate@uborama:~$

```

and there it is, I still have .gtkpod and the preferences.  this is like that for everything although the purge did decrease the number of files I have to delete it is still there.

---

### Post by aysiu on 2006-03-07
I wonder if the *locate* database needs some time to get updated. Can you verify that those files are actually there and not just found in the results of the *locate* command?

---

### Post by closeyourwindows on 2006-03-07
```
nate@uborama:~$ locate gtkpod
/usr/share/gnome-app-install/gtkpod.desktop
/home/nate/.icons/SnowIsh-1.0/scalable/apps/gtkpod.svg
/home/nate/.gtkpod
/home/nate/.gtkpod/prefs
nate@uborama:~$ sudo rm -r .gtkpod/
nate@uborama:~$ locate gtkpod
/usr/share/gnome-app-install/gtkpod.desktop
/home/nate/.icons/SnowIsh-1.0/scalable/apps/gtkpod.svg
nate@uborama:~$ sudo rm -r /usr/share/gnome-app-install/gtkpod.desktop
nate@uborama:~$

```

and I was able to see the directories in the home drive

---

### Post by arnieboy on 2006-03-07
to update the database do this:
```
sudo updatedb
```
then run ```
slocate <filename>
```

---

### Post by aysiu on 2006-03-07
You know, I think it's gone.

First of all, the icons... icon themes usually have an icon for every major application out there, whether you have it installed or not.

Secondly, gnome-app-install... go to the /usr/share/gnome-app-install directory, and you'll see it has a ***.desktop file for just about everything out there. I went there for my vanilla Ubuntu installation (on my "test" computer) and it had .desktop files for aMule, AmaroK, aMSN, Audacity, Banshee, and a host of other applications I never installed.

The user preferences in ~/.gtkpod I don't think ever get uninstalled, as those were never installed in the first place--those are *user* preferences. You can manually delete those, though.

---

### Post by closeyourwindows on 2006-03-07
```
nate@uborama:~$ sudo apt-get remove --purge gtkpod
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  gtkpod*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 2040kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ...
dpkg: serious warning: files list file for package `mythtv-frontend' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mythtv-database' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mythtv-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mythtv-backend' missing, assuming package has no files currently installed.
130347 files and directories currently installed.)
Removing gtkpod ...
Purging configuration files for gtkpod ...
nate@uborama:~$ locate gtkpod
/home/nate/.icons/SnowIsh-1.0/scalable/apps/gtkpod.svg
nate@uborama:~$ sudo updatedb
nate@uborama:~$ slocate gtkpod
/var/cache/apt/archives/gtkpod_0.94.0-1_i386.deb
/home/nate/.icons/SnowIsh-1.0/scalable/apps/gtkpod.svg
nate@uborama:~$


```

so this time when I looked for the file it did not come up with it all over the place.  I had to reinstall it and then uninstall it.  I will try it with another app.

---

### Post by closeyourwindows on 2006-03-07
so I went to uninstall amarok.  here is the first part:

```
nate@uborama:~$ sudo apt-get remove --purge gtkpod
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  gtkpod*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 2040kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ...
dpkg: serious warning: files list file for package `mythtv-frontend' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mythtv-database' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mythtv-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mythtv-backend' missing, assuming package has no files currently installed.
130347 files and directories currently installed.)
Removing gtkpod ...
Purging configuration files for gtkpod ...
nate@uborama:~$ locate gtkpod
/home/nate/.icons/SnowIsh-1.0/scalable/apps/gtkpod.svg
nate@uborama:~$ sudo updatedb
nate@uborama:~$ slocate gtkpod
/var/cache/apt/archives/gtkpod_0.94.0-1_i386.deb
/home/nate/.icons/SnowIsh-1.0/scalable/apps/gtkpod.svg
nate@uborama:~$ sudo apt-get remove --purge amarok
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  amarok* amarok-gstreamer* kubuntu-desktop*
0 upgraded, 0 newly installed, 3 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 17.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ...
dpkg: serious warning: files list file for package `mythtv-frontend' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mythtv-database' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mythtv-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mythtv-backend' missing, assuming package has no files currently installed.
130301 files and directories currently installed.)
Removing kubuntu-desktop ...
Removing amarok ...
Purging configuration files for amarok ...
Removing amarok-gstreamer ...
nate@uborama:~$ locate amarok
/usr/share/doc/kde/HTML/en/khelpcenter/userguide/amarok-icon.png
/usr/share/doc/kde/HTML/en/khelpcenter/userguide/amarok.png
/usr/share/doc/kde/HTML/en/khelpcenter/kubuntu/images/C/kubuntu-amarok.png
/usr/share/gnome-app-install/amarok.desktop
/usr/share/services/katapult_amarokcatalog.desktop
/usr/share/kubuntu-default-settings/kde-profile/default/share/config/amarokrc
/usr/lib/kde3/katapult_amarokcatalog.so
/usr/lib/kde3/katapult_amarokcatalog.la
/home/nate/.icons/OSX/scalable/apps/amarok.png
/home/nate/.kde/share/config/amarokrc
/home/nate/.kde/share/apps/amarok
/home/nate/.kde/share/apps/amarok/undo
/home/nate/.kde/share/apps/amarok/albumcovers
/home/nate/.kde/share/apps/amarok/albumcovers/cache
/home/nate/.kde/share/apps/amarok/albumcovers/cache/100@nocover.png
/home/nate/.kde/share/apps/amarok/albumcovers/cache/50@nocover.png
/home/nate/.kde/share/apps/amarok/albumcovers/tagcover
/home/nate/.kde/share/apps/amarok/albumcovers/large
/home/nate/.kde/share/apps/amarok/collection.db
/home/nate/.kde/share/apps/amarok/collection_scan.log
/home/nate/.kde/share/apps/amarok/contextbrowser.html
/home/nate/.kde/share/apps/amarok/current.xml
/home/nate/.kde/share/apps/amarok/playlistbrowser_save.xml
/home/nate/.kde/share/apps/amarok/podcastbrowser_save.xml
/home/nate/.kde/share/apps/amarok/streambrowser_save.xml
/home/nate/.kde/share/apps/amarok/partybrowser_save.xml
/home/nate/.kde/share/apps/amarok/submit.xml
/home/nate/.kde/share/apps/amarok/statusbar.log.0
/home/nate/.kde/share/apps/amarok/smartplaylistbrowser_save.xml
nate@uborama:~$


```
```
nate@uborama:~$ sudo updatedb
nate@uborama:~$ slocate amarok
/usr/share/doc/kde/HTML/en/khelpcenter/userguide/amarok-icon.png
/usr/share/doc/kde/HTML/en/khelpcenter/userguide/amarok.png
/usr/share/doc/kde/HTML/en/khelpcenter/kubuntu/images/C/kubuntu-amarok.png
/usr/share/gnome-app-install/amarok.desktop
/usr/share/services/katapult_amarokcatalog.desktop
/usr/share/kubuntu-default-settings/kde-profile/default/share/config/amarokrc
/usr/lib/kde3/katapult_amarokcatalog.so
/usr/lib/kde3/katapult_amarokcatalog.la
/home/nate/.icons/OSX/scalable/apps/amarok.png
/home/nate/.kde/share/config/amarokrc
/home/nate/.kde/share/apps/amarok
/home/nate/.kde/share/apps/amarok/undo
/home/nate/.kde/share/apps/amarok/albumcovers
/home/nate/.kde/share/apps/amarok/albumcovers/cache
/home/nate/.kde/share/apps/amarok/albumcovers/cache/100@nocover.png
/home/nate/.kde/share/apps/amarok/albumcovers/cache/50@nocover.png
/home/nate/.kde/share/apps/amarok/albumcovers/tagcover
/home/nate/.kde/share/apps/amarok/albumcovers/large
/home/nate/.kde/share/apps/amarok/collection.db
/home/nate/.kde/share/apps/amarok/collection_scan.log
/home/nate/.kde/share/apps/amarok/contextbrowser.html
/home/nate/.kde/share/apps/amarok/current.xml
/home/nate/.kde/share/apps/amarok/playlistbrowser_save.xml
/home/nate/.kde/share/apps/amarok/podcastbrowser_save.xml
/home/nate/.kde/share/apps/amarok/streambrowser_save.xml
/home/nate/.kde/share/apps/amarok/partybrowser_save.xml
/home/nate/.kde/share/apps/amarok/submit.xml
/home/nate/.kde/share/apps/amarok/statusbar.log.0
/home/nate/.kde/share/apps/amarok/smartplaylistbrowser_save.xml
nate@uborama:~$


```and here is the second part of that. and finally the third:
```
nate@uborama:~$ cd .kde/share/apps/amarok/
nate@uborama:~/.kde/share/apps/amarok$ ls
albumcovers          partybrowser_save.xml          streambrowser_save.xml
collection.db        playlistbrowser_save.xml       submit.xml
collection_scan.log  podcastbrowser_save.xml        undo
contextbrowser.html  smartplaylistbrowser_save.xml
current.xml          statusbar.log.0


```

---

### Post by closeyourwindows on 2006-03-07
so after deleting all the directories and reinstalling amarok and then deleting, the  directories were not there.  there got to be a better way to remove the apps and all the files and directories associated with it.   

I tried to delete all files that had amarok in it but cannot come up with the proper syntax.

---

