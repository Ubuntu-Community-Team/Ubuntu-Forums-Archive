---
title: "HOWTO: Firefox Cache on RAM for fast surfing"
date: 2012-01-25
forum: General Help
---

### Post by Wagtail. on 2012-01-25
Moving the cache folder of firefox is a great thing to do, because it will reduce the amount of I/O of hard-drive, much more faster, and less noisier.
you could easly then work on that drive, to achieve extra speed.
Here I will try to cover how to create a RAMDISK which you could load your cache, for quicker and smoother surfing.

[B]Create a RAM-DISK on start-up.
[/B]1. Go to the terminal, and access root:
```
sudo -i
```2. access the startup file and modify it:
```
gedit /etc/rc.local
```3. before exit 0, write the following code, I think 512MB will be enough for cache, don't forget to write your user name. 
```
mkdir /tmp/ram
 mount -t tmpfs -o size=512M,mode=750 tmpfs /tmp/ram/
 chown -R USERNAME /tmp/ram/ 
```save and exit.
4. now edit the boot configuration, write on the terminal:
```
gedit /etc/default/grub

```and change the GRUB_CMDLINE_LINUX="" to:
```

  GRUB_CMDLINE_LINUX=”ramdisk=512000&#8243;

```5. Reboot and check if the ramdisk is there, should be in /tmp/ram each time you booting.

**Backup the cache**
because each time you restart the computer all data that is stored in RAM will be deleted, then we need to back up the cache files so that your browser will not download each time the data on the sites you already visited.
for this, create a new script in init.d folder.
1. write the following code on the terminal, after accessing root:
```
gedit /etc/init.d/rambackup.sh
```and insert the following code, and don't forger to **change your username.**
```

#!/bin/sh
####################################
#
# Simple backup script, to backup RAMDISK
#
####################################
echo "Backing up RAM files..."
# What to backup. 
backup_files="/tmp/ram"

# Where to backup to.
dest="/home/YOUR_USER_NAME/Templates/Backups"

# Create archive filename.
day=$(date +%A)
hostname=$(hostname -s)
archive_file="rambackup.tgz"

```Save the file and exit gedit.
2. access again to the start-up file and modify it, to restore the backup each boot.
```
gedit /etc/rc.local
```write the following code, before "exit 0" but not before creating the RAMDISK
```

echo "Restores RAM from backup..."
cd /
sudo tar -xzvf /home/YOUR_USER_NAME/Templates/Backups/rambackup.tgz
echo "Restore successful!";

```save and exit.
3. Create the folder Backups, in your user Templates, you don't must, but you will have to change the code.
4. Sync the rambackup.sh to activate each log out and shutdown, write the following code in the terminal to make the code executable:
```

chmod +x rambackup.sh

```and to make the script execute each Shut down and restart.
```

sudo ln -s /etc/init.d/rambackup.sh /etc/rc0.d/K10bkupram.sh
sudo ln -s /etc/init.d/rambackup.sh /etc/rc6.d/K10bkupram.sh

```[B]Modifing Cache directory:
[/B]1. Enter Firefox, and insert in the address bar: about:config
2. run a search for "browser.cache.disk.parent_directory".
if you have such Name then change the value to the address of ramdisk, insert : "/tmp/ram/"
if you **don't  **have the name, create one with the exact name "browser.cache.disk.parent_directory", and change the value to the above.
3. change the value of "browser.cache.disk.enable" to **true**, and set the maximum amount of memory "browser.cache.disk.capacity" less then the memory of the ramdisk, something like 480000.
4. Restart firefox.

After you restart you will see the difference.
each shut-down all the cache is copied to the hard-drive, and on boot copied back to the ram disk, enabling to use that RAM DISK as a super-fast Hard-drive, you could then work on it if you want.

Improvements, fix and notes will happily accept!

---

### Post by kyfho23 on 2012-03-15
The 4th point: in the Backing up the cache section

*chmod +x rambackup.sh*

should read:

**chmod +x  /etc/init.d/rambackup.sh**

---

### Post by lovinglinux on 2012-04-14
A lot simpler method: [http://www.webgapps.org/tutorials/firefox/optimization/ramdisk-cache](http://www.webgapps.org/tutorials/firefox/optimization/ramdisk-cache)

---

### Post by dcstar on 2012-04-15
Or stop wasting your time and simply install the "Cache Status" Add-on and set the respective cache values as you like (or do the same thing manually in the Firefox about:config settings).

Why do people over-complicate simple tasks?

---

