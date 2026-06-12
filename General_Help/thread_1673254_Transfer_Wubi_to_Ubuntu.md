---
title: "Transfer Wubi to Ubuntu"
date: 2011-01-22
forum: General Help
---

### Post by qwertyjjj on 2011-01-22
Is there a way to backup all settings from Wubi and transfer them to a full install of Ubuntu? I would also need to transfer the Thunderbird and Firefox settings plus installed apps like wine, Skype, etc.

Secondly, to install Ubuntu do I need to completely wipe the drive and get rid of Windows or will the install disc do that for me?

df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/loop0             7805344   5562424   1846428  76% /
none                   1026412       280   1026132   1% /dev
none                   1030788       428   1030360   1% /dev/shm
none                   1030788       196   1030592   1% /var/run
none                   1030788         0   1030788   0% /var/lock
none                   1030788         0   1030788   0% /lib/init/rw
/dev/sda2             58508728  49378284   9130444  85% /host

I have grub version 0.97 so cannot follow one of the FAQs as it says I need 1.96 or higher.

---

### Post by aldee96 on 2011-01-22
i were using wubi before, then i moved to full install because i love linux:D. by the way what is the version of ubuntu you are using in wubi?  for the 9.10(CMIIW) and before you could googling for answer. but for the above, i couldnt find any solutions maybe someone would help. because i want to move to full instalation to from wubi from my another computer

*RECOMMEND*You could use Apt-onCD to copy all of the packages you have downloaded and make an *.ISO file, so you can burned it to a CD/DVD, and make sure you have enough room for your ubuntu virtual disk to createe the *.ISO file, but for the setting maybe someone could help*RECOMMEND*

---

### Post by qwertyjjj on 2011-01-22
> **aldee96 said:**
> i were using wubi before, then i moved to full install because i love linux:D. by the way what is the version of ubuntu you are using in wubi?  for the 9.10(CMIIW) and before you could googling for answer. but for the above, i couldnt find any solutions maybe someone would help. because i want to move to full instalation to from wubi from my another computer

*RECOMMEND*You could use Apt-onCD to copy all of the packages you have downloaded and make an *.ISO file, so you can burned it to a CD/DVD, and make sure you have enough room for your ubuntu virtual disk to createe the *.ISO file, but for the setting maybe someone could help*RECOMMEND*

So, I install apt-oncd and that copies all my profile folders and appas and then I just delete all the partitions?
Can I just format the Windows partition and then enlarge the Ubuntu partition /dev/loop0 ?

I tired using this but my grub will not update past v0.97 and the FAQ says not to use it unless you have v1.6.+

I checked gparted but it doesn;t seem to list the Wubi partition at all, just the Windows partition.

---

### Post by aldee96 on 2011-01-22
> **qwertyjjj said:**
> So, I install apt-oncd and that copies all my profile folders and appas and then I just delete all the partitions?
Can I just format the Windows partition and then enlarge the Ubuntu partition /dev/loop0 ?

I tired using this but my grub will not update past v0.97 and the FAQ says not to use it unless you have v1.6.+

I checked gparted but it doesn;t seem to list the Wubi partition at all, just the Windows partition.

no just your downloaded packages(codecs,apps,library) not the folders and your profile settings

your ubuntu partition is a virtual disk it means it's not a real partition, it's just a folder in windows but act like a partition, that's why gparted won't recognize it

you could done the fresh install, your profile could be configured offline, but the application is not. so i think uninstall wubi, and create the real partition for ubuntu, because if your windows attacked by virus, your ubuntu would be attacked, it's so vulnerable in wubi. so why you don't take a risk to feel the real linux

---

### Post by qwertyjjj on 2011-01-22
> **aldee96 said:**
> no just your downloaded packages(codecs,apps,library) not the folders and your profile settings

your ubuntu partition is a virtual disk it means it's not a real partition, it's just a folder in windows but act like a partition, that's why gparted won't recognize it

you could done the fresh install, your profile could be configured offline, but the application is not. so i think uninstall wubi, and create the real partition for ubuntu, because if your windows attacked by virus, your ubuntu would be attacked, it's so vulnerable in wubi. so why you don't take a risk to feel the real linux

Well, that's what I want to do but I'd like to keep the installed apps and Mozilla profiles so I don;t have to recopy everything.
Do I just copy the home folder and then copy and past it into the Live Ubuntu folder after I have used the Live CD to install it?

And how do I delete Windows? Will the CD do it or do I have to format it first?

---

### Post by vanadium on 2011-01-22
If the Ubuntu version you are going to reinstall is exactly the same as your Wubi install (e.g. Ubuntu 10.04), then it is probably safe to backup your user home directory and restore that in the new install. This will reinstate all your user settings and data. You eventually will need to reinstall software using software center as well.

To backup your user data, you need to make a "mirror" copy, i.e. a copy that contains all your files including file attributes. This can be achieved with rsync using the -a (archive) option. The destination file system needs to be formatted in a linux file system such as ext4 for this to work.

An alternative could be to create a tar archive. In that case, the only requirement for the destination file system is that it can take large files. This excludes a fat file system, but includes ntfs next to linux file systems.

When you are ready to reinstall, yes, the installation program can automatically whipe and reformat your drive, if you wish to install only Ubuntu.

---

### Post by qwertyjjj on 2011-01-22
> **vanadium said:**
> If the Ubuntu version you are going to reinstall is exactly the same as your Wubi install (e.g. Ubuntu 10.04), then it is probably safe to backup your user home directory and restore that in the new install. This will reinstate all your user settings and data. You eventually will need to reinstall software using software center as well.

To backup your user data, you need to make a "mirror" copy, i.e. a copy that contains all your files including file attributes. This can be achieved with rsync using the -a (archive) option. The destination file system needs to be formatted in a linux file system such as ext4 for this to work.

An alternative could be to create a tar archive. In that case, the only requirement for the destination file system is that it can take large files. This excludes a fat file system, but includes ntfs next to linux file systems.

When you are ready to reinstall, yes, the installation program can automatically whipe and reformat your drive, if you wish to install only Ubuntu.

Do I copy the entire filesystem or just /home?

I tired the entire filesystem but I get an error denied. DO I need to do this on the command line?

---

### Post by oldfred on 2011-01-22
Please see this thread.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)


Your /home has all your user settings and files, but not the programs themselves. But you can export a list of installed apps and reimport it.

---

### Post by qwertyjjj on 2011-01-22
> **oldfred said:**
> Please see this thread.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)


Your /home has all your user settings and files, but not the programs themselves. But you can export a list of installed apps and reimport it.

Already trued that but it doesn;t describe how to delete the windows partition.
Also it says this:
If the output of the following shows version 0.97 then please do not continue

My grub will not update to anything other than 0.97

---

### Post by oldfred on 2011-01-22
If your wubi is still using grub 0.97, it may be better just to back up everything and do a new install of the 10.04.1 or 10.10 versions with grub2.

You can download the CD and test to make sure the new versions work. Backup /home including the hidden files as that is where a lot of data is like your Firefox & Thunderbird data profiles are. If you did any system changes you may want to backup /etc but if a new version you may not need the same settings so do not copy it back, but use it for reference if need be.

If deleting windows you can just repartition using gparted. If you have room I would keep windows for a while then reformat it after installing Ubuntu. But if no room then just back up & use gparted to set up new partitions.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by bcbc on 2011-01-22
> **qwertyjjj said:**
> Already trued that but it doesn;t describe how to delete the windows partition.
Also it says this:
If the output of the following shows version 0.97 then please do not continue

My grub will not update to anything other than 0.97

There's a separate instruction set for migrating wubi (versions 9.04 and later) with grub 0.97 that's been confirmed by 2 people (and me). But it's manual only - not currently supported by the script. [http://ubuntuforums.org/showpost.php?p=9894476&postcount=92](http://ubuntuforums.org/showpost.php?p=9894476&postcount=92)

The documentation and warnings from Post#1 apply - e.g. the mkfs command is very dangerous if you specify the wrong partition. So please don't use it if you aren't comfortable with the commands.

---

