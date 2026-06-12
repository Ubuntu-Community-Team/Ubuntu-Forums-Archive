---
title: "Strange crash"
date: 2012-01-18
forum: General Help
---

### Post by riemannia on 2012-01-18
So, I've installed Ubuntu 11.10 as the sole operating system on my Cr-48 and it keeps crashing.  Every once in a while, Chromium will crash, if Spotify is playing it will stop and suggest that the hard drive is full (this seems very unlikely), the time will be set to another time zone (pacific time, I think), the accessibility, volume, bluetooth, wireless, battery, and chat icons disappear from the top bar (I use Gnome shell), and going to the Activities menu, all the application icons from the Windows sidebar and also from the Application submenu have disappeared.  Then, the screen goes black with white text and in addition to the standard stuff about bluetooth and pulseaudio initializing I get the following errors:

[1407.137073] EXT4-fs (sda 1): previous I/O error to superblock detected
[1407.137219] EXT4-fs error (device sda 1): ext4_find_entry:934:inode #261124 comm lightdm: reading directory iblock 0
[1407.137441] EXT4-fs (sda 1): previous I/O error to superblock detected
[1407.137569] EXT4-fs error (device sda 1): ext4_find_entry:934:inode #522241 comm lightdm: reading directory iblock 0

And then a whole bunch of similar errors pop out.  Any suggestions?

EDIT: I forgot to mention, I've also tried just reinstalling once.  Error continued to manifest itself

---

### Post by wolfen69 on 2012-01-18
Try this:
```
sudo touch /forcefsck
```
and reboot. It will check your file system for errors.

---

### Post by riemannia on 2012-01-18
Thanks for the response.  I tried forcefcsk, to no avail. The crash still occurs regularly.  Nothing came up when in ran the scan, I assume the results of the scan aren't saved in a file somewhere?

---

