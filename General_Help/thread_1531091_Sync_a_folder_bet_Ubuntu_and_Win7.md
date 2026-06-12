---
title: "Sync a folder bet Ubuntu and Win7"
date: 2010-07-14
forum: General Help
---

### Post by teddy379 on 2010-07-14
How can I sync a folder between Ubuntu's main drive (ext4) and Windows 7... My case is, I want to get Pidgin (using it on Ubuntu and Win7) saving the chat logs in one "common" folder. I tried using the "Make Link" thing but on Win7 the folder I made link to appeared as a file. So yea, basically I wanna know how to sync a folder. Also if someone could help me, the chat logs saved by Pidgin in Win7 are saved somewhere in Documents and Settings, probably not giving me the option to change where the logs get saved. So any help with that? Thanks in advance

---

### Post by sanderd17 on 2010-07-14
don't know if dropbox can do this but there's no harm in trying it.

---

### Post by Haylz on 2010-07-14
If you're dual booting Windows 7 and Ubuntu, you can access the Windows folders from Ubuntu by firstly clicking "Places" and then "Home Folder". Then click on "File System" and go to the folder called "host". Those are your Windows files...  :)

---

### Post by Marlonsm on 2010-07-14
> **Haylz said:**
> If you're dual booting Windows 7 and Ubuntu, you can access the Windows folders from Ubuntu by firstly clicking "Places" and then "Home Folder". Then click on "File System" and go to the folder called "host". Those are your Windows files...  :)

The host folder only works if Ubuntu was installed with Wubi (the "Inside Windows" option).
If it was not, your Windows partition should be in the Media folder, I think.

---

### Post by WorMzy on 2010-07-14
There's no need to sync two folders, just mount --bind, inside Linux, the folder on Windows that you want to the logs to be kept to where the logs are stored by default.

e.g. if the logs are kept in ~/.pidgin/logs, and you want to be able to access them from the "C:\Documents and Settings\USERNAME\pidgin logs", then all you need to do is create two lines in your /etc/fstab file. The first will mount the "C:\" to a folder in /media, and the second will "bind" the relative path to the "\DOC~1\USER~1\pidgin logs" folder to the folder in your ~ directory.

Firstly though, move the already existing log files to the Windows folder, mount --bind will not delete the files in the Linux directory, but it will make them inaccessable.

After you've moved the logs (or at least made a backup of them all in another Linux folder), find out which partition is your Windows partition with
```
sudo blkid -c /dev/null
```
In my example, I identify ```
/dev/sda1: UUID="[COLOR="Red"]7A5C94995C94522D[/COLOR]" TYPE="ntfs"
``` as the Windows partition.

Next, edit fstab with
```
gksu gedit /etc/fstab
```
To get it to mount the Windows partition automatically at boot time, we need to add a new line at the end of the file, like the following:

```
UUID=[COLOR="Red"]7A5C94995C94522D[/COLOR] /media/Windows ntfs user,uid=1000,gid=1000,umask=022,exec,rw 0 0
```

We also need to add a line to get it to bind the correct folder to the right place, so add another new line with the following content:
```
/media/Windows/Documents\040and\040Settings/USERNAME/pidgin\040logs /home/USERNAME/.pidgin/logs none bind 0 0
```

Finally, make sure that the folder we're trying to mount Windows partition to actually exists by running
```
sudo mkdir /media/Windows
```

See if it all works by running
```
sudo umount -a && sudo mount -a
```

If you get no errors, then it'll work fine every time you boot into Ubuntu.

If you didn't copy the logs to the Windows log folder before, you can now copy the backups you made instead to ~/.pidgin/logs _or_ "/media/Windows/Documents and Settings/USERNAME/pidgin logs".

---

