---
title: "User profile can't write to disk: 0 bytes"
date: 2009-09-03
forum: General Help
---

### Post by cleentrax on 2009-09-03
Running Jaunty on a home theater PC. I have a root boot disk that is not full, but is claiming to be full, at least for the main user profile. (0 bytes available.)

Update manager says it doesn't have enough space to run (needs 60mb) but I can run aptitude dist-upgrade in the terminal as root (not as the user).

If I run "df -Th -x tmpfs" in the terminal it tells me that I am using about 890G of 912G, at 100% usage. It used to be 905G of 912G, but I deleted 15G of files, and emptied the trash, and it still says 100% usage.

System monitor reports 21.9G free, but 0 bytes available.

I cannot run GParted as user because I get the following error: "Failed to run /usr/sbin/gparted as user root. Unable to copy the user's Xauthorization file."

I ran fsck on a reboot, and it found some errors and fixed them, but I didn't get any improvement in behavior that I could see.

Is there just a corrupt file somewhere that is easy to fix? Or do I have a hardware problem? Or do I need to do a clean reinstall? Most files and pictures are backed up but I would hate to lose my user customizations and all my app settings.

---

### Post by drs305 on 2009-09-03
If you have your /boot or any other system or /home folder on a separate partition make sure it is not full. Even if the *system* is reporting space, each system partition will need a bit of space as well. I'd start by looking at your root partition, which you say is reporting full.

Here is a link to a guide to help users find out what is taking up space and how to remedy a 'disk-full' condition.

[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

While exploring the problem unmount all non-system partitions so the problem isn't 'hidden' by extraneous reports.

---

### Post by cleentrax on 2009-09-03
Thanks for the reply. I only have one root partition, and it has 21gb free but 0 available. There is no separate partition, except for swap and for an external drive that has some backups on it.

---

### Post by cleentrax on 2009-09-03
An additional piece of information I just learned: Shortly before it started acting up, it had a forced reboot due to a toddler pressing the shiny blue led power button. Possible corrupt user file that is causing this?

Is that why I would get the "Unable to copy the user's Xauthorization file" message?

---

### Post by drs305 on 2009-09-03
> **cleentrax said:**
> Is that why I would get the "Unable to copy the user's Xauthorization file" message?

Often it is a lack of disk space, but it could be the file became corrupt during the power loss.

Check the status/permissions of the file:
```

ls -l .Xauthority

```
> -rw-r----- 1 username username 152 2009-09-03 16:22 .Xauthority

If you are not the owner or the permissions are incorrect:
```

sudo cp ~/.Xauthority ~/.Xauthority.bad
sudo chown username:username ~/.Xauthority
chmod 600 ~/.Xauthority

```

---

### Post by cleentrax on 2009-09-04
bump... anyone know why my user profile would be read-only or corrupted like this?

---

### Post by drs305 on 2009-09-04
> **cleentrax said:**
> bump... anyone know why my user profile would be read-only or corrupted like this?

I believe there were reports in the past that the use of *sudo* instead of *gksudo* was blamed for corrupting portions of the /home directory, including this file. I can't speak from experience that this happens to the .Xauthority file.

When opening graphical apps such as nautilus and gedit, always use *gksudo*. For terminal commands which won't open a graphical app, such as blkid and fdisk, use *sudo*.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Has your problem been resolved, by the way?

*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by cleentrax on 2009-09-05
> **drs305 said:**
> 
Has your problem been resolved, by the way?


Sadly, no. Thanks for the help. I changed permissions and ownership on the .Xauthority file, which fixed that particular error, but the disk is still not writable by the user, only by root.

---

