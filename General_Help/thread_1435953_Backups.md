---
title: "Backups"
date: 2010-03-22
forum: General Help
---

### Post by bigseb on 2010-03-22
Is there anyway to backup all my installed drivers? I thinking of doing a complete reinstall but don't want to have download everything again due to bandwidth limitations. I'm particularly wanting to backup all the Nvidia stuff.

---

### Post by Herman on 2010-03-22
I'm not sure about drivers specifically.

Generally speaking it's a good idea to make a backup of all your .deb files in /var/cache/apt/archives.

Just use a sudo command to copy them all to the new /var/cache/apt/archives/ before you let the system get an update.

If you do that, most of your .deb files for the programs you're going to install will already be there, so you won't need to be re-download each one from the internet. 
That saves you a lot of waiting time and bandwidth too.
```
sudo cp /var/cache/apt/archives/*.deb /media/disk/archives/
```Where: '/media/disk/archives is the path to the directory where you want to make a backup of your .deb files, (perhaps in a USB flash memory stick).

After you re-install, 
```
sudo cp /media/disk/archives/*.deb /var/cache/apt/archives
```And then run sudo apt-get update and sudo apt-get upgrade and install your software so on ...

Don't bother storing your backed up collection of .deb packages for too long as they will soon be superceded by newer version of the same packages.

---

### Post by bigseb on 2010-03-22
Interesting. Since I'm new to this let me just see if I understand what's being said here. CP probably means copy, right? After that would be the from and to destinations? This would basically overwrite the contents of the second folder with the contents of the first?

---

### Post by Herman on 2010-03-22
:D Yes, that's correct, cp is short for copy, from back in the days when computers were as big as houses, and they used to have to hit computer keys with 10 lb sledgehammers. They abbreviated a lot of commands to save energy. (Just joking).

> After that would be the from and to destinations? That's right.

If you go and take a look in /var/cache/apt/archives, (by clicking the up arrow from your /home/bigseb twice to get to the top of our file system tree, (or / ), and look around your /var directory and navigating until you find cache/apt/archives and take a look around in there you'll find a lot of files with the .deb filename extension. Those are our software packages, and those can be copied to another Ubuntu installation and used again, providing it's another Ubuntu of the same version.

If you insert a USB flash memory stick, you'll probably notice it will be mounted and an icon will appear on your desktop for you to open to access the files.
That's not the real mount point for your USB drive though, it's only a shortcut, (or 'symlink' in Linux spiel). The real mount point for your USB is in /media, and if you go and look in there you'll find a folder you can open to see the all the files in your USB drive.

Now for example if the name automatically given to that folder was 'disk', and you made an empty directory inside your USB drive called 'archives', then running the command '
cp /var/cache/apt/archives/*.deb /media/disk/archives/' will create copies all of your .deb files from /var/cache/apt/archives and put them in your USB drive, inside your floder called 'archives'.

Then after you re-install, when you run the same command except in reverse, it will fill up the /var/cache/apt/archives directory in your new installation with the files from your USB disk which you downloaded in your previous installation.
Yes, it may overwrite any that may happen to be there, but only if they happen to have the exact same file name, which would mean they're the same file anyway, so it wouldn't matter. Usually, the /var/cache/apt/archives in a new install will be empty or nearly so anyway.

It's a great way to save a lot of downloading time and bandwidth.

---

