---
title: "A few questions about backup"
date: 2012-04-18
forum: General Help
---

### Post by Jaxke on 2012-04-18
Hi.

It has come time to do a reinstall(need to upgrade to 64bit, and at the same time to 12.04). I've never done this before, and I need some help.

1. Do I need to backup my home folder? When upgrading Windows, personal files will be copied automatically to the upgraded OS. Is it the same in Ubuntu?

2. What folders should I backup? The nescassary ones, like installed programs etc.

Thanks for help.

---

### Post by sudodus on 2012-04-18
> **Jaxke said:**
> Hi.

It has come time to do a reinstall(need to upgrade to 64bit, and at the same time to 12.04). I've never done this before, and I need some help.

1. Do I need to backup my home folder? When upgrading Windows, personal files will be copied automatically to the upgraded OS. Is it the same in Ubuntu?

2. What folders should I backup? The nescassary ones, like installed programs etc.

Thanks for help.

Reinstalling and upgrading is always risky, but tough guys don't backup their data. They try to use the advanced recovery tools instead ;-) In other words, I'm glad you asked *now*, and I recommend strongly, that you backup up at least all your personal data. But it might be a good idea to backup the whole home folder, because then you get also the settings for several programs. You might get some problems with that because you switch to 64-bits, but it is worth trying.

I don't think you can upgrade automatically from a 32-bit to 64-bit system. The easiest way is probably to

- backup your personal data
- make a fresh install of 12.04
- copy your personal data to where you want them.

Finally, you can expect less problems with bugs, if you wait until 12.04 is officially released, and maybe even a couple of weeks longer. But the present version is already very nice :-)

---

### Post by Jaxke on 2012-04-18
> **sudodus said:**
> Reinstalling and upgrading is always risky, but tough guys don't backup their data. They try to use the advanced recovery tools instead ;-) In other words, I'm glad you asked *now*, and I recommend strongly, that you backup up at least all your personal data. But it might be a good idea to backup the whole home folder, because then you get also the settings for several programs. You might get some problems with that because you switch to 64-bits, but it is worth trying.

I don't think you can upgrade automatically from a 32-bit to 64-bit system. The easiest way is probably to

- backup your personal data
- make a fresh install of 12.04
- copy your personal data to where you want them.

Finally, you can expect less problems with bugs, if you wait until 12.04 is officially released, and maybe even a couple of weeks longer. But the present version is already very nice :-)
Yeah, I can't afford losing my data :D

I was also thinking about waiting for the final 12.04 to come out, but my PC is running so slow(I have 6gigs of RAM, but settings show I only have 2.6Gb. I reckon it's because of the 32bit installation)) right now so I rather update to the beta and after that, go to the final version. By the way, any ETA for the final?

Also, how can I backup my installed apps and settings?

Thanks for help, I'mma start backing up my home -> now :guitar:

---

### Post by sudodus on 2012-04-18
> **Jaxke said:**
> ... By the way, any ETA for the final?

Also, how can I backup my installed apps and settings?

Within April, I think within 10 days from today (12.04 means year 2012, month 4).

There are so many ways. Some ways use GUI tools, other ways use terminal commands or scrips. I often use a ***Clonezilla*** live CD or USB drive to make complete images of my whole drives or partitions. You can also try ***Simple Backup***, which will guide you to what is important to back-up.

You can also use ***rsync*** from the command line. There are several backup tools available. I suggest that you search these Ubuntu Forums for backup and browse the internet for ***backup linux*** to find what suits you.

---

### Post by Dngrsone on 2012-04-18
Last I heard, it was April 29th for the official release.

You will want to back up your entire /home folder, and any folders/partitions where you keep data (for instance, I have an ntfs /Data folder which holds my music and other files I need to see from Win 7).

When I installed 12.04-beta2 64-bit, it *did not* recognize my two installed operating systems (the aforementioned Win 7 and 10.04) to import data and settings from, so you might want to take some notes on what programs you currently have and want to use in the new version.

---

### Post by Jaxke on 2012-04-18
I ran TAR backup(didn't see these comments :( )

I got a following error:

```
Exiting with failure status due to previous errors

```

The process took a long time so I assume everything went alright... I have to ignore...

Thanks for replies!

---

### Post by sudodus on 2012-04-18
> **Jaxke said:**
> I ran TAR backup(didn't see these comments :( )

I got a following error:

```
Exiting with failure status due to previous errors

```

The process took a long time so I assume everything went alright... I have to ignore...

Thanks for replies!
I would not rely on a backup that finished with an error message!!!

---

### Post by Dngrsone on 2012-04-18
> **Jaxke said:**
> I ran TAR backup(didn't see these comments :( )

I got a following error:

```
Exiting with failure status due to previous errors

```

The process took a long time so I assume everything went alright... I have to ignore...

Thanks for replies!

Ignore at your data's peril

---

### Post by oldfred on 2012-04-18
A lot of old time users like tar, I happen to like rsync as I can do partial or just what I think is most important.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

If you export the list of installed apps, edit it to exclude those that have changed, obsoleted, and old kernels. It is just a text file. I found I was reinstalling python2.5 with my new installs and current is 2.7.
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

If you do not have a separate /home. This makes new installs easier as you can reuse your old /home if you DO NOT reformat it as part of a manual install or Something Else.
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Since 12.04 is still in beta, you should make a new 25GB / (root) partition to test that it works. You then can still boot old install. I used to find I forgot something and by rebooting into old install then was able to find it. And upgraded /home may not work well with old install as some settings get upgraded also.

---

### Post by Jaxke on 2012-04-18
Yeah, it sounds stupid to ignore errors, but

```
Note: At the end of the process you might get a message along the lines  of 'tar: Error exit delayed from previous errors' or something, but in  most cases you can just ignore that.
```from [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

EDT: Dammit, I have different error :o Looks like I'll have to do it the Fred's way

---

### Post by Roasted on 2012-04-18
There's two threads going on now I just posted semi lengthy responses to. I suggest you check them out as I think they might have some information you may find useful.

Discussion about splitting root and home partitions:

[http://ubuntuforums.org/showthread.php?t=1960992](http://ubuntuforums.org/showthread.php?t=1960992)



Discussion about Grsync, Deja Dup, rsync, etc:

[http://ubuntuforums.org/showthread.php?t=1960131](http://ubuntuforums.org/showthread.php?t=1960131)

---

### Post by Jaxke on 2012-04-19
OK, I did the bakup with TAR, and re-installed system. I got all(boot, etc, var etc.) those folders on my /home now. Which folders should I move to get my installed programs and settings back?

I already tried this morning, and replaced every folder in root, but I got an error at boot-up so I did "re-re-install". I'm not doing it again, that's why I'm asking :D

Thanks

---

### Post by oldfred on 2012-04-19
You cannot easily copy programs as they are installed in several places.

Only if same version and you have not housecleaned. But no guarantees on dependency issues if you partially housecleaned.
Location of downloaded debs
/var/cache/apt/archives/
Then you can reinstall with:
sudo apt-get install --no-download <package name>

Otherwise from old install export a list of installed applications and use that to download and reinstall. If a new version of Ubuntu you may want to houseclean out older apps. The exported list is just a text file. I found I was still reinstalling python2.5 and some other older applications I knew I did not need to reinstall.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by SeijiSensei on 2012-04-19
If you don't do so already, I would strongly recommend putting /home on a separate partition when you install the new system.  I makes life much easier during subsequent installations, though this is by no means an alternative to backups.

Tar will throw an error if a file changes during the course of the archive being created.  On any active system, this is almost guaranteed to happen since the system will be writing to logs and doing other self-maintenance tasks that changes the contents of files.  No backup system, even rsync, is invulnerable to this on an active machine. At least with rsync, once the first back up takes place, the incremental list of files on subsequent backups is not usually that long.  You'll have an easier time determining which files have changed during the backup and deciding whether it matters to you or not.

---

### Post by Jaxke on 2012-04-19
> **oldfred said:**
> You cannot easily copy programs as they are installed in several places.

Only if same version and you have not housecleaned. But no guarantees on dependency issues if you partially housecleaned.
Location of downloaded debs
/var/cache/apt/archives/
Then you can reinstall with:
sudo apt-get install --no-download <package name>

Otherwise from old install export a list of installed applications and use that to download and reinstall. If a new version of Ubuntu you may want to houseclean out older apps. The exported list is just a text file. I found I was still reinstalling python2.5 and some other older applications I knew I did not need to reinstall.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
Thanks! I'll do that. Let's hope I manage to restore my apps :D 

@SeijiSensei Thanks for the tip! I'll copy my home folder and backup file to my "recovery partition"(just an extra Ubuntu installation if something goes wrong)

:guitar:

E: I did enter those commands, and the last one took fifteen minutes, but yet no packages were installed... I didn't make any .txt file of installed packages at my last installation...

---

### Post by Dngrsone on 2012-04-19
[QUOTE=Jaxke;11856867 I'll copy my home folder and backup file to my "recovery partition"(just an extra Ubuntu installation if something goes wrong)[/QUOTE]

The problem with a 'recovery partition' is that it resides on the same drive as your working OS.  If the drive fails, then you have lost everything.

... been there, done that.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]

---

### Post by Jaxke on 2012-04-21
> **Dngrsone said:**
> The problem with a 'recovery partition' is that it resides on the same drive as your working OS.  If the drive fails, then you have lost everything.

... been there, done that.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]
It's a whole different partition. It works if my main Ubuntu crashes. Just like Windows partition.

Anyone have a tip to restore the programs?

---

### Post by Zill on 2012-04-21
> **Jaxke said:**
> It's a whole different partition. It works if my main Ubuntu crashes. Just like Windows partition.
The point is that a disk drive is a single electro-mechanical device that can (and does!) fail.  In this case, the number of partitions is irrelevant as the data in *all* partitions will be inaccessible.  If you don't believe this then just power down your PC.  Pull either the power or the data plug on your HDD.  Power up the PC again and see if you can boot any of the partitions. ;-)

> **Jaxke said:**
> Anyone have a tip to restore the programs?
If you don't have a suitable list of installed applications then I guess this is not possible.  My recommendation is to install all the programs you need as you go along.  This will ensure the correct (latest) versions are installed.

---

### Post by Dngrsone on 2012-04-21
> **Jaxke said:**
> It's a whole different partition. It works if my main Ubuntu crashes. Just like Windows partition.

Does it reside on an entirely different disk drive?  Even so, what happens if there is a catastrophic PSU failure that blows everything up?

For that matter, what if an airplane falls on your computer?

My point is, a backup is not a backup until you have multiple copies in multiple locations.  A second partition on the same storage device *is not* a second location.

But... you know your system and situation best; I'm not losing sleep over this.

---

