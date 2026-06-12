---
title: "A couple problems I could use help with, please"
date: 2010-07-19
forum: General Help
---

### Post by dfd001 on 2010-07-19
I had Ubuntu on C drive. but had no room left.  I deleted, and re-installed on newly reformatted HD (E:drive...hey, Windows labeled it, not me;))

Anyhow, everything, near as I can tell, is working, with the following exceptions:

1.  Windows sees the drive as a 320 gb HD, labeled as E:.  The only thing on it is ubuntu, which takes up about 17gb.   (there is a 500mb partician, listed as F:)  But ubuntu says I only have 13 GB freespace remaining.  The 500 MB partician shows up in 'places/computer' as 320 GB HD.  What happened to all of my HD capacity?  Ubuntu should have close to 300 GB to play with, not 13 GB.  How can I fix this?

2.  I installed VUZE from the ubuntu software center.  I did not work.  (couldn't connect, of find any torrents or torrent sites).  I downloaded Vuze from their website, unpacked it and installed it.  I ran a (I think its called) shellscript application, and it works fine.  The problem is that it will not run from the desktop.  I can copy it, or move it to desktop, and it will not work.  I have to open the folder I unpacked it into and run it from there.  Is that normal, or is there a fix for that?  (Also, how do I delete the one I got from software center.  Believe it or not, they are actually 2 seperate programs.)

3.  I installed 7zip from software center, and it says its installed, but I can't find it.  Where does ubuntu put these programs, in not in system, administration or applications?

Finally, I still have the issue of missing root (or boot) disk when I boot up.  Sometimes it boots on the first time, other times I have to reboot 1 to 3 times.  I sent for the actual install disk (I installed with wubi) and I guess I will have to tolerate that until it arrives, and hope that cures the problem.  (I tried downloading/burning disk, but...well...don't ask:()

Thanks for your help/information.

---

### Post by lordskid on 2010-07-19
> 
2. I installed VUZE from the ubuntu software center. I did not work. (couldn't connect, of find any torrents or torrent sites). I downloaded Vuze from their website, unpacked it and installed it. I ran a (I think its called) shellscript application, and it works fine. The problem is that it will not run from the desktop. I can copy it, or move it to desktop, and it will not work. I have to open the folder I unpacked it into and run it from there. Is that normal, or is there a fix for that?

what exactly was the download? was it source tarballs? can you post what command you typed in the terminal? Also you can take note of the directory you installed this second vuze then create a desktop-launcher 
```

right-click on the desktop
click create launcher
on the command textbox type the directory then the file e.g. ~/username/vuze-x.xx.xx/vuze
then just click this shortcut/launcher to run vuze

```
> 
 (Also, how do I delete the one I got from software center. Believe it or not, they are actually 2 seperate programs.)


#2 remove it from System -> Administration -> Synaptic Package Manager
#3 is installed as support for tar so there are no GUI's or menu entries.

---

### Post by Agent ME on 2010-07-19
1. Did you install it with "./configure && make && sudo make install"? Going into the directory and doing "sudo make remove" or "sudo make uninstall" should do the trick.

3. Installing 7zip adds the 7z command line program, and integrates support for creating and extracting .7z files in the file browser (Nautilus). No separate GUI for 7zip needed.

---

### Post by bcbc on 2010-07-19
> **dfd001 said:**
> 1.  Windows sees the drive as a 320 gb HD, labeled as E:.  The only thing on it is ubuntu, which takes up about 17gb.   (there is a 500mb partician, listed as F:)  But ubuntu says I only have 13 GB freespace remaining.  The 500 MB partician shows up in 'places/computer' as 320 GB HD.  What happened to all of my HD capacity?  Ubuntu should have close to 300 GB to play with, not 13 GB.  How can I fix this?
...

Finally, I still have the issue of missing root (or boot) disk when I boot up.  Sometimes it boots on the first time, other times I have to reboot 1 to 3 times.  I sent for the actual install disk (I installed with wubi) and I guess I will have to tolerate that until it arrives, and hope that cures the problem.  (I tried downloading/burning disk, but...well...don't ask:()

Thanks for your help/information.
With wubi you tell it how big the install should be - and it creates a virtual disk in that size (root.disk). That's the max size it sees, regardless whether you installed it on a 320GB drive. You can still access that space under the /host directory, but your root (/) install is 17GB (this is the max size for installing any ubuntu apps + any data stored under /home).

If you want to use the whole 320GB you need to do a direct install. If you can't burn a disk you can migrate a wubi install, but you really should figure out how to burn a cd as you need one (almost guaranteed you'll have to boot from it at some point).

Regarding the missing root, I can't say what's causing this, but running the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") might turn up some clues.

But if I were you I'd just try and figure out how to lose the wubi and do a regular install so you can get the 320GB you want.

---

### Post by dfd001 on 2010-07-19
> **bcbc said:**
> With wubi you tell it how big the install should be - and it creates a virtual disk in that size (root.disk). That's the max size it sees, regardless whether you installed it on a 320GB drive. You can still access that space under the /host directory, but your root (/) install is 17GB (this is the max size for installing any ubuntu apps + any data stored under /home).

If you want to use the whole 320GB you need to do a direct install. If you can't burn a disk you can migrate a wubi install, but you really should figure out how to burn a cd as you need one (almost guaranteed you'll have to boot from it at some point).

Regarding the missing root, I can't say what's causing this, but running the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") might turn up some clues.

But if I were you I'd just try and figure out how to lose the wubi and do a regular install so you can get the 320GB you want.

Thanks for the reply.  The disk burn has since been cured (replacing a burner that is over 5 yrs old did not hurt either;))  That said, my question now is will I loose what I have now, or will the disk upgrade?  (Do I have to delete the system I have at this time?)

Thanks.

---

### Post by oldfred on 2010-07-19
I would backup /home and make a list of all installed packages whether you try the move or not.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

HOWTO: migrate wubi install to partition 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Old conversion LVPM, see Alternative Instructions 
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

---

### Post by bcbc on 2010-07-20
> **dfd001 said:**
> Thanks for the reply.  The disk burn has since been cured (replacing a burner that is over 5 yrs old did not hurt either;))  That said, my question now is will I loose what I have now, or will the disk upgrade?  (Do I have to delete the system I have at this time?)

Thanks.

There are some options to migrate a wubi install to partition (see links in oldfred's post). But they all migrate to a different partition than the one it's on. Split your E: and you're in business. 

It is possible to [migrate]("http://ubuntuforums.org/showpost.php?p=9570445&postcount=12") just using the wubi root.disk and a live CD, but that's a very hands-on process and you still need to copy the root.disk off the partition you are migrating to.

You have to weigh up the effort to reinstall vs migrate.

---

### Post by 3rdalbum on 2010-07-20
7zip is a command-line program. It basically just adds the ability for Linux archiving tools (such as Ubuntu's preinstalled Archive Manager/File Roller) to work with 7zip archives.

---

