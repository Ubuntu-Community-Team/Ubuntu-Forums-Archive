---
title: "Mounting drive at login instead of boot?"
date: 2011-05-20
forum: General Help
---

### Post by Ranko Kohime on 2011-05-20
As the title says, I'm looking for a way to auto-mount a drive at login.

Purpose being that I'm going to mount the drive under ~/Media, but the home folder is encrypted, and thus inaccessible when fstab is read.

---

### Post by Mr. Shannon on 2011-05-21
The easiest way would probably be to put the mount command in a bash script and have it run at startup by using **Startup Applications** located at **System->Preferences->Startup Applications** in Gnome.  For unity you can probably search for **Startup Applications**.

If you need help making the script and getting it to run just ask here.

---

### Post by linuxinstalledfromhdd on 2011-05-21
create a bash script as stated above..   put it in a path directory.. make sure to chmod 755 the script file, and you can have it run at bootup phase

---

### Post by Ranko Kohime on 2011-05-21
> **Mr. Shannon said:**
> The easiest way would probably be to put the mount command in a bash script and have it run at startup by using **Startup Applications** located at **System->Preferences->Startup Applications** in Gnome.  For unity you can probably search for **Startup Applications**.

If you need help making the script and getting it to run just ask here.
I can make that script, but I can't seem to use mount without sudo.  I'd like to avoid typing in my password twice.

---

### Post by tredegar on 2011-05-21
If you make an entry for the disk in fstab (yes, fstab will fail to mount the device but...) *you* will be able to mount it without sudo, because there is an entry for it in fstab that defines how it should be mounted.

---

### Post by Mr. Shannon on 2011-05-21
Try the instructions [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1000796") on how to let a non administrator use mount with a specific volume.

---

### Post by Ranko Kohime on 2011-05-21
Ah, I see now.

Thank you, all.  :D

---

### Post by Ranko Kohime on 2011-10-28
Coming back to this, I never did get the thing to work, even with the "user" option in /etc/fstab, and I've since changed my configuration again, to include even more problems.  :D

Originally, entering in the UUID or the device path (/dev/sdb, and I also tried with /dev/sdb1), still did not allow me to mount without using sudo.

Still trying to mount /dev/sdb (no 1, drive not partitioned, whole disk is formatted in this instance), to ~/Media, only this time it's encrypted, so the drive needs to be unlocked, and /dev/dm-0 needs to be mounted to ~/Media.

The password for this encrypted volume is stored in the user's keychain, so unlocking the drive merely requires a single click in the Disk Utility (palimpsest, I believe)  I can't seem to find the command line equivalent in the encryption documentation for Ubuntu.

---

