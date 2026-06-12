---
title: "Backing up - what do I save?"
date: 2010-01-01
forum: General Help
---

### Post by Robster2 on 2010-01-01
I want install Lucid Linux when it is released.

I have bought a Terabyte external drive. 

I have saved directories home and above. 

What happens with programs like MySQL they seem to store files outside the home directory tree.

What other files/directories should I save?

---

### Post by VCoolio on 2010-01-01
Exactly, don't forget mysql files; there is a mysql command to make a backup, don't remember right now but you can google it. Depending on your setup maybe /var/www needs a backup.

Also, if you have themes / icons installed system wide, backup 
/usr/share/icons and /usr/share/themes

The following files maybe to check what it looked like if you encounter problems:
/etc/X11/xorg.conf
/etc/apt/sources.list (with your added repositories)
/etc/fstab (if you have drives / partitions that need to be mounted on boot)

If you use mpd, backup your mpd.conf file.

---

### Post by john newbuntu on 2010-01-01
If you have time on your hands, you can just script the whole thing.  Now that you have a backup of /home directory (or perhaps a partition having /home), do a fresh install of Lucid when it comes out and then run your script that would update /etc/passwd, /etc/group pwconv, installing all extra tools using apt-get, reconfiguring mysql, php and apache settings and any other customizations you have made.  Of course make the right backups first.
Then it is just a one time running of script once Lucid (or for that matter any newer version) gets installed.
Note that mysql admin has its own backups that you can create and restore.

---

### Post by ardchoille42 on 2010-01-01
I wrote a [simple backup script]("http://ubuntuforums.org/showthread.php?t=1369540") that takes the worry out of backing up your home directory.

---

### Post by Robster2 on 2010-01-02
Thank you for your replies.  MySQL databases are in /var/lib/mysql/

Thank you for script idea.

---

### Post by QIII on 2010-01-02
If you would like to save time trying to restore the applications you have installed using apt/Synaptic/Software Center, go to the terminal and type

```
dpkg --get-selections > installed-software
```Then save your /home partition.  When you have /home back in place on your new installation

```
dpkg --set-selections < installed-software
```Then

```
dselect-upgrade
```You may first have to install dselect
```
sudo apt-get install dselect
```

will retrieve and reinstall the current versions for your new version.

---

