---
title: "junk in home directory"
date: 2010-02-01
forum: General Help
---

### Post by mringer on 2010-02-01
I recently found an awful lot of junk files in my home directory, mostly
in directories that start with a dot e.g.  /home/my home/.mozilla
So I did

cd ~
du -chs .??*

and found 3.5 GB. After pruning, I find < 250 MB of files that I have
knowingly created. What is happening is that I installed some programs, 
say xyz , tried them out and decided they were unsatisfactory, deleted 
them. The un-installer for  xyz  deletes the actual program but
meanwhile  xyz
has installed lots of config files or status files  in 
/home/my home/.xyz  and the un-installer does not delete these. 

So if you are running short of space or if backups take forever, it 
might be worthwhile to do the above command or maybe

cd /home
sudo du -chs */.??*

---

### Post by tom4everitt on 2010-02-01
Yes! It is generally a good idea to remove the associated settings folder when uninstalling a program. This is especially important when reinstalling a malfunctioning program, since it is more often the settings that are causing the error in the first place.

---

### Post by mcduck on 2010-02-01
Most of the configuration files for programs are just simple, small text files that truly don't take any noticeable amount of space. The only hidden directories that might take more space are the ones that your web browser uses as cache, and the one that contains thumbnail cache for the file manager. (Of course you might have installed some other program that keeps some kind of cache there). Instead of nuking all the settings you should just look if you see any config directories for programs you don't have any more, and remove them. Definitely don't remove alll the dotfiles/directories, that would rereset all your programs and your desktop to default settings, and delete all your passwords, networks and so on...

(and no, removing user confguration files when uninstalling a program is not an option.  System-wide configs are removed if you use the "--purge"-option with apt-get (or "Mark for complete removal" in Synaptic), but user configs belong to the user, and should not ever be removed by any admin task. While doing that migh seem like a smart idea on a computer with only a single user, it would be pretty horrible thing to do on a multi-user system.)

edit: On my system, with most config files copied over through all ugrades dating from Ubuntu 5.04 the biggest hidden directory in home is .mozilla (38,6MB) containing firefox settings, extensions & cche. Two other big ones are .covers (23,1MB, album covers for music players) and .thumbnails (10,4MB, file manager's thumbnail cache). All the others are so small that they are meaningless when considering disk space usage on any hard drive that's in gigabytes range. Their size varies between 2MB and 4Kb per directory/file)

---

### Post by tom4everitt on 2010-02-02
> **mcduck said:**
> 

(and no, removing user confguration files when uninstalling a program is not an option.  System-wide configs are removed if you use the "--purge"-option with apt-get (or "Mark for complete removal" in Synaptic), but user configs belong to the user, and should not ever be removed by any admin task. While doing that migh seem like a smart idea on a computer with only a single user, it would be pretty horrible thing to do on a multi-user system.)



Of course, but a common reason to want to reinstall a program is that it is not functioning. And the most common reason for a program suddenly malfunctioning is not its binaries, but its settings.

---

### Post by mcduck on 2010-02-02
> **tom4everitt said:**
> Of course, but a common reason to want to reinstall a program is that it is not functioning. And the most common reason for a program suddenly malfunctioning is not its binaries, but its settings.

In that case the settings should be removed (or better yet, just renamed) from the user who's having problems, not from every user.

---

### Post by 3rdalbum on 2010-02-02
> **mcduck said:**
> In that case the settings should be removed (or better yet, just renamed) from the user who's having problems, not from every user.

Exactly; that's why I recommend removing your dot-settings files as a first step if you're suddenly having trouble with a program. The number of times people say "xyz program isn't working properly anymore... I tried uninstalling it and reinstalling it twice but it didn't make any difference" gets on my nerves, actually.

---

