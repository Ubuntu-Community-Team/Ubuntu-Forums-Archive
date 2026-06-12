---
title: "Cant extract tar archive to /"
date: 2010-01-05
forum: General Help
---

### Post by bramming on 2010-01-05
Hi. I installed windows xp on a separate partition yesterday. It turned out, that windows screwed up my MBR. I tried to fix it but i think it just got worse and worse (i used like 6 hours trying to fix it. became desperate :S ) so i booted up a livecd and took a backup of my linux partition mounted at /media/disk/ with the following command
 ```
tar cvpzf UbuntuBackup.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys /media/disk
```

Now i have a tar file that starts with /media/disk and then contains the system. I reinstalled xp and ubuntu, and now everything boots up perfectly. However i cant restore my backup :( i now have UbuntuBackup.tgz placed at /. I tried to restore it by cd'ing to / and issuing the following command:
```
sudo tar xvzf UbuntuBackup.tgz
```
However, that just creates a folder named disk in /media/. 
After a lot of searching the web, i found the following command
```
sudo tar xvzf UbuntuBackup.tgz media/disk
```
However, that doesnt extract the contents of media/disk as i thought it would. it creates the exact same /media/disk/ directory.
i also tried ```
sudo tar xvzf UbuntuBackup.tgz media/disk -C /

```
but still no luck. 

So to summarize: im looking for a way i can extract the backup files to my "/" directory without having it create /media/disk. 

Thanks alot for reading all this. All help is much appreciated

---

### Post by Leppie on 2010-01-05
open a root nautilus and then try opening the archive with package manager and drag and drop.
```
$gksudo nautilus --no-desktop
```

---

### Post by amauk on 2010-01-05
Probably the easiest is creating a symlink from /media/disk to /
```
sudo ln -s / /media/disk
```

Then extract the archive as normal
```
sudo tar -xvzf UbuntuBackup.tgz /
```

then take out the symlink
```
sudo rm /media/disk
```

---

### Post by bramming on 2010-01-05
Thanks Leppie and amauk :)

@amauk: I am extracting at this very moment, and it seems to work !! Its such a relief that it finally works. Thanks so much!

---

### Post by amauk on 2010-01-05
no probs

---

