---
title: "Sata"
date: 2006-03-09
forum: General Help
---

### Post by harley on 2006-03-09
ok my hard drive manger under system is seeing my SATA drive how do i set it up so i can explore the file system and watch/listen to music and movies on this drive?
it is in NTFS format..also split pertitions 
/dev/sda1 is one and
/dev/sda5 is the other

---

### Post by Sutekh on 2006-03-09
You need to open a terminal window to enter these commands.  

You should create a backup of the fstab before editing it
```
sudo cp /etc/fstab /etc/fstab_backup
```
Then you can edit it using 
```
sudo gedit /etc/fstab
```
Once you have opened the fstab then you need to add the lines to mount the SATA drives

```
[COLOR="Blue"]/dev/sda1[/COLOR]    [COLOR="Red"]/media/windows1[/COLOR]   [COLOR="Green"]ntfs[/COLOR]   [COLOR="DarkOrchid"]nls=utf8,umask=0222[/COLOR]   0   0
[COLOR="Blue"]/dev/sda5[/COLOR]    [COLOR="Red"]/media/windows2[/COLOR]   [COLOR="Green"]ntfs[/COLOR]   [COLOR="DarkOrchid"]nls=utf8,umask=0222[/COLOR]   0   0
```

 - You'll have to create the folders for the drives to mounted to.  You can use whatever you like in place of [COLOR="Red"]/media/windows1[/COLOR] and [COLOR="Red"]/media/windows2[/COLOR] 

 - [COLOR="DarkOrchid"]nls=utf8,umask=0222[/COLOR] - these options set the character encoding to utf8 (for special chars) and sets the **umask**.  The umask is important as it restricts the access to the drive.  I can explain this more, but for now just know that [COLOR="DarkOrchid"]umask=0222[/COLOR] only allows read and execute access to the partition NOT write

---

### Post by rfruth on 2006-03-09
SATA 80 GB here, yea STA1  is the first partition on the 1st drive, Nautilus 2.12.1 works fine for me


[ATTACH]6889[/ATTACH]

---

