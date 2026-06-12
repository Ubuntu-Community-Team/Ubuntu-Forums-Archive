---
title: "How to move hidden folder from /home to another location"
date: 2010-11-03
forum: General Help
---

### Post by arapaho on 2010-11-03
How to move hidden folder from /home to another location - on another partition? Is it possible? I'd like to move some folders for example ./thunderbird or so that I wouldn't need to make a backup. Or at least is it possible that program can right files to two folders, or that everything from /home./thunderbird would copy automatically to ./thunderbird on another partition every time there is a change? Is it possible to  write a script or something? I use luckybackup but I would like to be able to forget about backups and make script or program to do it for me.

---

### Post by ivanovnegro on 2010-11-03
Just do it via drag and drop.
You can find it when you are in Nautilus in View and then Show hidden files.
You will find there all your home stuff like Firefox configurations, Thunderbird...
(.mozilla for example) Then just move them to another location. Later you can move them e.g. on a new install back to your Home folder and the configurations will be the same, I do this always when Im doing fresh installs, but I only take the important things, like Firefox, mediaplayer databases, etc.

---

### Post by Barriehie on 2010-11-03
My .mozilla folder is actually located on my backup drive and I have a symlink in ~/ that points to it.  Once daily a crontab entry runs a backup script at 4:00 AM that backs up everything and using 'find' I keep a sliding window of 5 backups.

To write files at every change would probably require some kind of daemon to watch the directory.

---

### Post by arapaho on 2010-11-03
It seems that a symlink was what I needed. I created 
```
ln -s /home/arapaho/.thunderbird /media/backup/.thunderbird
```
1. But I'm not sure yet if I can remove/delete what the original .thunderbird folder on /home contains leaving this folder empty (to get some free space)? Does symlink just copy data from source to destination or creates a kind of redirection and "tells' the program to write data in this new folder?

Basically I don't want to keep on /home any data from applications that change often the content of their folders. That's seems to me a better solution in case of system re-installation or just making copies of entire system.

2. And what do you do in case of /home re-installation? Just install programs and create symlinks again and the programs starts to read from folders on /backup?

---

### Post by Vaphell on 2010-11-03
symlinks are redirections (you can kill redirection, but the target is untouched), hardlinks however are physical bonds - when you kill one, you kill the other.

---

### Post by Barriehie on 2010-11-03
> **arapaho said:**
> It seems that a symlink was what I needed. I created 
```
ln -s /home/arapaho/.thunderbird /media/backup/.thunderbird
```
1. But I'm not sure yet if I can remove/delete what the original .thunderbird folder on /home contains leaving this folder empty (to get some free space)? Does symlink just copy data from source to destination or creates a kind of redirection and "tells' the program to write data in this new folder?

Basically I don't want to keep on /home any data from applications that change often the content of their folders. That's seems to me a better solution in case of system re-installation or just making copies of entire system.

2. And what do you do in case of /home re-installation? Just install programs and create symlinks again and the programs starts to read from folders on /backup?

What I did was:
```

rsync -av /home/barrie/.mozilla /media/backup/
rm -rf /home/barrie/.mozilla
ln -s /media/backup/.mozilla /home/barrie/
```

In the event of reinstalling $HOME you'ld have to remove the symlink BEFORE installing any software or the software will just follow the link and overwrite /media/backkup/*.some_software_package_config_folder*  Ideally, at least for me, I've got $HOME on its own drive, /media/backup is another drive, and I boot from another drive.  Gotta keep 'em seperated... ;)

---

### Post by arapaho on 2010-11-03
> **Barriehie said:**
> In the event of reinstalling $HOME you'ld have to remove the symlink BEFORE installing any software or the software will just follow the link and overwrite /media/backkup/*.some_software_package_config_folder*  Ideally, at least for me, I've got $HOME on its own drive, /media/backup is another drive, and I boot from another drive.  Gotta keep 'em seperated... ;)
I'm not sure if I understand you correctly. It seems to me that when /home is reinstalled and root too, there is no active symlinks in the system, because it is a new system. So the /backup./thunderbird will be a normal folder without symlink function and connection to the new system. Is that correct?

```
rm -rf
```
Does above command remove symlink?

I have /root, /home and /backup - 3 separate partitions. I do have some extra backups of whole /root and /home. But in case these backups fail, and I loose /home by accident  - what I have to do is (having ./thunderbird on /backup):
1. Install system on /root and /home
2. Install applications (so far they doesn't connect to backup)
3. Synchronize backup with new home:
```
rsync -av /media/backup/.thunderbird /home/arapaho/.thunderbird /
```
4. Make a new symlink from home to backup. Right?

Or do I have to remove symlink from backup first? 
```
rm -rf /media/backup/.thunderbird
```

Assume that it is a new system. Will this /backup folder still have symlink properties or it will become a normal folder?

---

### Post by Barriehie on 2010-11-03
> **arapaho said:**
> I'm not sure if I understand you correctly. It seems to me that when /home is reinstalled and root too, there is no active symlinks in the system, because it is a new system. So the /backup./thunderbird will be a normal folder without symlink function and connection to the new system. Is that correct?

yes!

> **arapaho said:**
> ```
rm -rf
```
Does above command remove symlink?
Be carefull with that one!
```

rm -rf /path/folder
```

> **arapaho said:**
> I have /root, /home and /backup - 3 separate partitions. I do have some extra backups of whole /root and /home. But in case these backups fail, and I loose /home by accident  - what I have to do is (having ./thunderbird on /backup):
1. Install system on /root and /home
2. Install applications (so far they doesn't connect to backup)
3. Synchronize backup with new home:
```
rsync -av /media/backup/.thunderbird /home/arapaho/.thunderbird /
```
4. Make a new symlink from home to backup. Right?

Have to watch the trailing /'s!
```

rsync -av /media/backup/.thunderbird /home/arapaho/.thunderbird
```

> **arapaho said:**
> Or do I have to remove symlink from backup first? 
```
rm -rf /media/backup/.thunderbird
```
Wait, the symlink is in/on /home/arapaho/symlink and it points to /media/backup/.thunderbird

> **arapaho said:**
> Assume that it is a new system. Will this /backup folder still have symlink properties or it will become a normal folder?

The backup folder will still exist and once the media is mounted the symlink in $HOME will still 'reach' it.

---

### Post by efflandt on 2010-11-03
> **arapaho said:**
> It seems that a symlink was what I needed. I created 
```
ln -s /home/arapaho/.thunderbird /media/backup/.thunderbird
```1. But I'm not sure yet if I can remove/delete what the original .thunderbird folder on /home contains leaving this folder empty (to get some free space)? Does symlink just copy data from source to destination or creates a kind of redirection and "tells' the program to write data in this new folder?

Basically I don't want to keep on /home any data from applications that change often the content of their folders. That's seems to me a better solution in case of system re-installation or just making copies of entire system.

2. And what do you do in case of /home re-installation? Just install programs and create symlinks again and the programs starts to read from folders on /backup?

What you did was create a symbolic link (like a shortcut in Windows) at /media/backup/.thunderbird that points to the real data directory (target) at /home/arapaho/.thunderbird.  So don't try to remove **/home/arapaho/.thunderbird** or you would no longer have that data (the data itself is not in /media/backup).

So it sounds like what you really want to do is move the data to /media/backup and put a symlink to that in your home directory.  But first check if /media/backup/.thunderbird is a symlink with **ls -l /media/backup**, and if it is a symlink remove it **rm /media/data/.thunderbird** then do:

```
mv /home/arapaho/.thunderbird /media/backup
ln -s /media/backup/.thunderbird /home/arapaho/.thunderbird
```But you have been doing a bunch of things and not sure where you actually have the data now.  So if in doubt, post the output of **ls -al ~** and **ls -al /media/backup** so we could tell where the real data is now.

---

### Post by arapaho on 2010-11-04
> **efflandt said:**
> What you did was create a symbolic link (like a shortcut in Windows) at /media/backup/.thunderbird that points to the real data directory (target) at /home/arapaho/.thunderbird.  So don't try to remove **/home/arapaho/.thunderbird** or you would no longer have that data (the data itself is not in /media/backup).
You are right. I checked this. I created a text file in /home/arapaho/.thunderbird and it appeared right afterwards in /media/backup/.thunderbird. And then I changed content of this file in source and it changed in /media/backup/.thunderbird too. Then I did it the other way round. I changed content of this file first in /media/backup/.thunderbird and the source file changed immediately. So it looks like a symlink synchronize the content of both folders at the exact moment the change take place.

> **efflandt said:**
> (the data itself is not in /media/backup)
It seems to me that both folders source and destination have exact the same data.

> **efflandt said:**
> So it sounds like what you really want to do is move the data to /media/backup and put a symlink to that in your home directory.  But first check if /media/backup/.thunderbird is a symlink with **ls -l /media/backup**, and if it is a symlink remove it **rm /media/data/.thunderbird** then do:
```
mv /home/arapaho/.thunderbird /media/backup
ln -s /media/backup/.thunderbird /home/arapaho/.thunderbird
```But you have been doing a bunch of things and not sure where you actually have the data now.  So if in doubt, post the output of **ls -al ~** and **ls -al /media/backup** so we could tell where the real data is now.
I'm not sure if this is a right solution because a symlink seems to work both ways regardless of where the change take place. 

What I would really like to do is:
1. First solution: to "cheat' an aplication so that it would work as if its the only folder with data was in /media/backup/.thunderbird  - in that case it would be great if /home/arapaho/.thunderbird could exist but without necessity to store data. I wish it could work as a kind of shortcut to a another folder. And the program could write its data only to that folder on backup partition. But this seems to be impossible with symlink command because it has this 'synchronize' feature.
2. Second solution: stay with symlink option and don't bother myself about a little space on hard disk. Symlink seems to be a great backup option with synchronize feature in real time.  But in this case the problem is: how to prevent the data on /media/backup from disappearing when /home folder is lost?

---

### Post by Barriehie on 2010-11-04
A symlink, when invoked with -s, is just a pointer.  You won't lose the data on /media/backup unless you, or software, explicitly remove it.  I do the same thing with my ~/Pictures folder.  Real data is on /media/backup/Pictures and a symlink in ~/.  If you're in the ~ dir and then cd ./Pictures it will look, via pwd command, like you're in $HOME/Pictures but you're really in /media/backup/Pictures.  Go with the symlink!

---

### Post by arapaho on 2010-11-04
I followed efflandt and Barriehie advice and everything works as I planned. This topic can be a great HOW TO.  :guitar:
Thank all of you for your help. =D>

---

### Post by Barriehie on 2010-11-04
:)  Glad you got it.  I do the same thing with the file/folders in my /var/www folder for my webpage.  Symlinks in their pointing to ~/www/whatever.

---

### Post by dcstar on 2010-11-04
> **arapaho said:**
> You are right. I checked this. I created a text file in /home/arapaho/.thunderbird and it appeared right afterwards in /media/backup/.thunderbird. And then I changed content of this file in source and it changed in /media/backup/.thunderbird too. Then I did it the other way round. I changed content of this file first in /media/backup/.thunderbird and the source file changed immediately. **So it looks like a symlink synchronize the content of both folders at the exact moment the change take place.**
...........

There is no "syncronization", "syncronization" implies that data in different locations is kept the same - **your data is only in one location**.

Links (soft or hard links) are just multiple ways of pointing to the same - singular - file/folder.

Hard links can only exist on the same filesystem, soft links (Symlinks) can cross any mounted filesystem - as long as the various filesystems support all the legal Linux filenames/attributes (NTFS does **not** do this).

---

